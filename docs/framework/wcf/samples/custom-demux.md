---
title: Custom Demux
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: "41"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d7c74648a249ec833f2b0fc8b8f5eea9247dc364
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-demux"></a>Custom Demux
Cet exemple montre comment les en-têtes de message MSMQ peuvent être mappés à différentes opérations de service afin que [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] les services qui utilisent <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ne sont pas limités à l’utilisation d’une opération de service comme illustré dans le [de Message Queuing Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) et [Windows Communication Foundation à Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemples.  
  
 Dans cet exemple, le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.  
  
 Le contrat de service est `IOrderProcessor`, et il définit un service unidirectionnel pouvant être utilisé avec des files d'attente.  
  
```  
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```  
  
 Un message MSMQ n'a pas d'en-tête Action. Il n'est pas possible de mapper automatiquement différents messages MSMQ aux contrats d'opération. Par conséquent, il ne peut y avoir qu'un seul contrat d'opération. Pour passer outre cette limitation, le service implémente la méthode <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> de l'interface <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>. La méthode <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> permet au service de mapper un en-tête donné du message à une opération de service particulière. Dans cet exemple, l'en-tête d'étiquette du message est mappé aux opérations de service. Le paramètre `Name` du contrat d'opération détermine quelle opération de service doit être distribuée pour une étiquette de message donnée. Par exemple, si l'en-tête d'étiquette du message contient « SubmitPurchaseOrder », l'opération de service « SubmitPurchaseOrder » est appelée.  
  
```  
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```  
  
 Le service doit implémenter la méthode <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> de l'interface <xref:System.ServiceModel.Description.IContractBehavior> comme illustré dans l'exemple de code suivant. Le `OperationSelector` personnalisé est alors appliqué à l'exécution du répartiteur de l'infrastructure du service.  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 Un message doit traverser le <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> du répartiteur avant d'arriver à OperationSelector. Par défaut, un message est rejeté si son action n'est trouvée sur aucun des contrats implémentés par le service. Pour éviter ce contrôle, nous implémentons un <xref:System.ServiceModel.Description.IEndpointBehavior> nommé `MatchAllFilterBehavior` qui permet à tout message de traverser le `ContractFilter`, en appliquant le <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> comme suit.  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 Lorsqu'un message est reçu par le service, l'opération de service appropriée est distribuée à l'aide des informations fournies par l'en-tête d'étiquette. Le corps du message est désérialisé dans un objet `PurchaseOrder`, comme affiché dans l'exemple de code suivant.  
  
```  
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```  
  
 Le service est auto-hébergé. Lors de l'utilisation de MSMQ, la file d'attente utilisée doit être créée en avance. Cela peut s'effectuer manuellement ou via le code. Dans cet exemple, le service contient du code permettant de vérifier l'existence de la file d'attente et de la créer, si nécessaire. Le nom de la file d'attente est lu depuis le fichier de configuration.  
  
```  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();  
    }  
}  
```  
  
 Le nom de la file d'attente MSMQ est spécifié dans la section appSettings de ce fichier de configuration.  
  
> [!NOTE]
>  Le nom de la file d'attente utilise un point (.) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès. L'adresse du point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spécifie un schéma msmq.formatname et utilise « localhost » pour l'ordinateur local. Une adresse de file d'attente correctement mise en forme d'après les règles d'adressage de nom du format MSMQ suit le schéma.  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Cet exemple requiert l’installation de [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).  
  
 Démarrez le service et exécutez le client.  
  
 La sortie suivante s'affiche sur le client.  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 La sortie suivante doit être vue sur le service.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Si le service est exécuté en premier, il vérifie que la file d'attente existe. Si la file d'attente n'existe pas, le service en crée une. Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ. Procédez comme suit pour créer une file d'attente dans Windows 2008 :  
  
    1.  Ouvrez le Gestionnaire de serveur dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Développez le **fonctionnalités** onglet.  
  
    3.  Avec le bouton droit **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.  
  
    4.  Vérifiez le **transactionnel** boîte.  
  
    5.  Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.  
  
3.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Copiez les fichiers programme du service figurant dans le dossier \service\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur de service.  
  
2.  Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur client.  
  
3.  Dans le fichier Client.exe.config, dans orderQueueName, remplacez « . » par le nom de l'ordinateur de service.  
  
4.  Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.  
  
5.  Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>Voir aussi  
 [Queuing dans WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143)
