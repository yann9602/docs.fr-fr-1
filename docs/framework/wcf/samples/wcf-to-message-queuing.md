---
title: "Windows Communication Foundation to Message Queuing | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: 32
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 32
---
# Windows Communication Foundation to Message Queuing
Cet exemple montre comment une application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peut envoyer un message à une application MSMQ \(Message Queuing\).Le service est une application console auto\-hébergée qui vous permet d'observer le service qui reçoit les messages mis en file d'attente.Il n'est pas nécessaire que le service et le client s'exécutent simultanément.  
  
 Le service reçoit des messages de la file d'attente et traite les commandes.Le service crée une file d'attente transactionnelle et définit un gestionnaire de messages reçus, tel qu'indiqué dans l'exemple de code suivant.  
  
```  
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
  
```  
  
 Lorsqu'un message est reçu dans la file d'attente, le gestionnaire de messages `ProcessOrder` est appelé.  
  
```  
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
  
```  
  
 Le service extrait `ProcessOrder` du corps du message MSMQ et traite la commande.  
  
 Le nom de file d'attente MSMQ est spécifié dans une section appSettings du fichier de configuration, tel qu'indiqué dans l'exemple de configuration suivant.  
  
```  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
  
```  
  
> [!NOTE]
>  Le nom de la file d'attente utilise un point \(.\) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès.  
  
 Le client crée une commande fournisseur et la soumet dans l'étendue d'une transaction, tel qu'indiqué dans l'exemple de code suivant.  
  
```  
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
  
```  
  
 Le client utilise un client personnalisé pour envoyer le message MSMQ à la file d'attente.L'application qui reçoit et traite le message étant une application MSMQ et non pas une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], il n'y a pas de contrat de service implicite entre les deux applications.Par conséquent, nous ne pouvons pas créer de proxy à l'aide de l'outil Svcutil.exe dans ce scénario.  
  
 Le client personnalisé est essentiellement le même pour toutes les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui utilisent la liaison `MsmqIntegration` pour envoyer des messages.Contrairement aux autres clients, il n'inclut pas de plage d'opérations de service.Il s'agit uniquement d'une opération d'envoi de message.  
  
```  
  
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```  
  
 Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent à la fois dans les fenêtres de console du service et du client.Vous pouvez voir le service recevoir des messages du client.Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.Par exemple, vous pouvez exécuter le client, l'arrêtez, puis démarrer le service et il recevra toujours ses messages.  
  
> [!NOTE]
>  Cet exemple requiert l'installation de Message Queuing.Consultez les instructions d'installation dans [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94968) \(page pouvant être en anglais\).  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Si le service est exécuté en premier, il vérifie que la file d'attente existe.Si la file d'attente n'existe pas, le service en crée une.Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.Procédez comme suit pour créer une file d'attente dans Windows 2008 :  
  
    1.  Ouvrez le Gestionnaire de serveur dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Développez l'onglet **Fonctionnalités**.  
  
    3.  Cliquez avec le bouton droit sur **Files d'attente de messages privées**, puis cliquez sur **Nouveau**, **File d'attente privée**.  
  
    4.  Activez la case à cocher **Transactionnelle**.  
  
    5.  Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d'attente.  
  
3.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l'exemple dans une configuration à un seul ordinateur, conformez\-vous instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Copiez les fichiers programme du service figurant dans le dossier \\service\\bin\\ \(situé dans le dossier correspondant à votre langue\) sur l'ordinateur de service.  
  
2.  Copiez les fichiers programme du client du dossier \\client\\bin\\ \(situé dans le dossier correspondant à votre langue\) sur l'ordinateur client.  
  
3.  Dans le fichier Client.exe.config, modifiez l'adresse de point de terminaison client afin de remplacer « . » par le nom de l'ordinateur de service.  
  
4.  Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.  
  
5.  Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## Voir aussi  
 [Comment : échanger des messages avec des points de terminaison WCF et des applications Message Queuing](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)   
 [Message Queuing \(page pouvant être en anglais\)](http://go.microsoft.com/fwlink/?LinkId=94968)