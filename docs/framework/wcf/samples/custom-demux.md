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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d4a460adfb8076f5d2c0fe273511e6de80be4ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-demux"></a><span data-ttu-id="251e3-102">Custom Demux</span><span class="sxs-lookup"><span data-stu-id="251e3-102">Custom Demux</span></span>
<span data-ttu-id="251e3-103">Cet exemple montre comment les en-têtes de message MSMQ peuvent être mappés à différentes opérations de service afin que [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] les services qui utilisent <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ne sont pas limités à l’utilisation d’une opération de service comme illustré dans le [de Message Queuing Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) et [Windows Communication Foundation à Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemples.</span><span class="sxs-lookup"><span data-stu-id="251e3-103">This sample demonstrates how MSMQ message headers can be mapped to different service operations so that [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> are not limited to using one service operation as demonstrated in the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) and [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) samples.</span></span>  
  
 <span data-ttu-id="251e3-104">Dans cet exemple, le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="251e3-104">The service in this sample is a self-hosted console application to enable you to observe the service that receives queued messages.</span></span>  
  
 <span data-ttu-id="251e3-105">Le contrat de service est `IOrderProcessor`, et il définit un service unidirectionnel pouvant être utilisé avec des files d'attente.</span><span class="sxs-lookup"><span data-stu-id="251e3-105">The service contract is `IOrderProcessor`, and defines a one-way service that is suitable for use with queues.</span></span>  
  
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
  
 <span data-ttu-id="251e3-106">Un message MSMQ n'a pas d'en-tête Action.</span><span class="sxs-lookup"><span data-stu-id="251e3-106">An MSMQ message does not have an Action header.</span></span> <span data-ttu-id="251e3-107">Il n'est pas possible de mapper automatiquement différents messages MSMQ aux contrats d'opération.</span><span class="sxs-lookup"><span data-stu-id="251e3-107">It is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="251e3-108">Par conséquent, il ne peut y avoir qu'un seul contrat d'opération.</span><span class="sxs-lookup"><span data-stu-id="251e3-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="251e3-109">Pour passer outre cette limitation, le service implémente la méthode <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> de l'interface <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>.</span><span class="sxs-lookup"><span data-stu-id="251e3-109">To overcome this limitation, the service implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method of the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span></span> <span data-ttu-id="251e3-110">La méthode <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> permet au service de mapper un en-tête donné du message à une opération de service particulière.</span><span class="sxs-lookup"><span data-stu-id="251e3-110">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method enables the service to map a given header of the message to a particular service operation.</span></span> <span data-ttu-id="251e3-111">Dans cet exemple, l'en-tête d'étiquette du message est mappé aux opérations de service.</span><span class="sxs-lookup"><span data-stu-id="251e3-111">In this sample, the message's label header is mapped to the service operations.</span></span> <span data-ttu-id="251e3-112">Le paramètre `Name` du contrat d'opération détermine quelle opération de service doit être distribuée pour une étiquette de message donnée.</span><span class="sxs-lookup"><span data-stu-id="251e3-112">The `Name` parameter of the operation contract determines which service operation must be dispatched for a given message label.</span></span> <span data-ttu-id="251e3-113">Par exemple, si l'en-tête d'étiquette du message contient « SubmitPurchaseOrder », l'opération de service « SubmitPurchaseOrder » est appelée.</span><span class="sxs-lookup"><span data-stu-id="251e3-113">For example, if the message's label header contains "SubmitPurchaseOrder", the "SubmitPurchaseOrder" service operation is invoked.</span></span>  
  
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
  
 <span data-ttu-id="251e3-114">Le service doit implémenter la méthode <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> de l'interface <xref:System.ServiceModel.Description.IContractBehavior> comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="251e3-114">The service must implement the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> method of the <xref:System.ServiceModel.Description.IContractBehavior> interface as shown in the following sample code.</span></span> <span data-ttu-id="251e3-115">Le `OperationSelector` personnalisé est alors appliqué à l'exécution du répartiteur de l'infrastructure du service.</span><span class="sxs-lookup"><span data-stu-id="251e3-115">This applies the custom `OperationSelector` to the service framework dispatch runtime.</span></span>  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 <span data-ttu-id="251e3-116">Un message doit traverser le <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> du répartiteur avant d'arriver à OperationSelector.</span><span class="sxs-lookup"><span data-stu-id="251e3-116">A message must pass through the dispatcher's <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> before getting to the OperationSelector.</span></span> <span data-ttu-id="251e3-117">Par défaut, un message est rejeté si son action n'est trouvée sur aucun des contrats implémentés par le service.</span><span class="sxs-lookup"><span data-stu-id="251e3-117">By default a message is rejected if its action cannot be found on any contract implemented by the service.</span></span> <span data-ttu-id="251e3-118">Pour éviter ce contrôle, nous implémentons un <xref:System.ServiceModel.Description.IEndpointBehavior> nommé `MatchAllFilterBehavior` qui permet à tout message de traverser le `ContractFilter`, en appliquant le <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> comme suit.</span><span class="sxs-lookup"><span data-stu-id="251e3-118">To avoid this check, we implement an <xref:System.ServiceModel.Description.IEndpointBehavior> named `MatchAllFilterBehavior`, which allows any message to pass through the `ContractFilter` by applying the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> as follows.</span></span>  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 <span data-ttu-id="251e3-119">Lorsqu'un message est reçu par le service, l'opération de service appropriée est distribuée à l'aide des informations fournies par l'en-tête d'étiquette.</span><span class="sxs-lookup"><span data-stu-id="251e3-119">When a message is received by the service, the appropriate service operation is dispatched using the information provided by the label header.</span></span> <span data-ttu-id="251e3-120">Le corps du message est désérialisé dans un objet `PurchaseOrder`, comme affiché dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="251e3-120">The body of the message is deserialized into a `PurchaseOrder` object, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="251e3-121">Le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="251e3-121">The service is self-hosted.</span></span> <span data-ttu-id="251e3-122">Lors de l'utilisation de MSMQ, la file d'attente utilisée doit être créée en avance.</span><span class="sxs-lookup"><span data-stu-id="251e3-122">When using the MSMQ, the queue that is used must be created in advance.</span></span> <span data-ttu-id="251e3-123">Cela peut s'effectuer manuellement ou via le code.</span><span class="sxs-lookup"><span data-stu-id="251e3-123">This can be done manually or through code.</span></span> <span data-ttu-id="251e3-124">Dans cet exemple, le service contient du code permettant de vérifier l'existence de la file d'attente et de la créer, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="251e3-124">In this sample, the service contains code to check for the existence of the queue and creates it if the queue does not exist.</span></span> <span data-ttu-id="251e3-125">Le nom de la file d'attente est lu depuis le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="251e3-125">The queue name is read from the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="251e3-126">Le nom de la file d'attente MSMQ est spécifié dans la section appSettings de ce fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="251e3-126">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="251e3-127">Le nom de la file d'attente utilise un point (.) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="251e3-127">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="251e3-128">L'adresse du point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spécifie un schéma msmq.formatname et utilise « localhost » pour l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="251e3-128">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="251e3-129">Une adresse de file d'attente correctement mise en forme d'après les règles d'adressage de nom du format MSMQ suit le schéma.</span><span class="sxs-lookup"><span data-stu-id="251e3-129">What follows the scheme is a properly formatted queue address according to the MSMQ Format name addressing guidelines.</span></span>  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="251e3-130">Cet exemple requiert l’installation de [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).</span><span class="sxs-lookup"><span data-stu-id="251e3-130">This sample requires the installation of [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).</span></span>  
  
 <span data-ttu-id="251e3-131">Démarrez le service et exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="251e3-131">Start the service and run the client.</span></span>  
  
 <span data-ttu-id="251e3-132">La sortie suivante s'affiche sur le client.</span><span class="sxs-lookup"><span data-stu-id="251e3-132">The following output is seen on the client.</span></span>  
  
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
  
 <span data-ttu-id="251e3-133">La sortie suivante doit être vue sur le service.</span><span class="sxs-lookup"><span data-stu-id="251e3-133">The following output must be seen on the service.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="251e3-134">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="251e3-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="251e3-135">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="251e3-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="251e3-136">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="251e3-136">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="251e3-137">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="251e3-137">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="251e3-138">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="251e3-138">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="251e3-139">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="251e3-139">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="251e3-140">Ouvrez le Gestionnaire de serveur dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="251e3-140">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="251e3-141">Développez le **fonctionnalités** onglet.</span><span class="sxs-lookup"><span data-stu-id="251e3-141">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="251e3-142">Avec le bouton droit **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="251e3-142">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="251e3-143">Vérifiez le **transactionnel** boîte.</span><span class="sxs-lookup"><span data-stu-id="251e3-143">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="251e3-144">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="251e3-144">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="251e3-145">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="251e3-145">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="251e3-146">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="251e3-146">To run the sample in a single- or cross- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="251e3-147">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="251e3-147">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="251e3-148">Copiez les fichiers programme du service figurant dans le dossier \service\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="251e3-148">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="251e3-149">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="251e3-149">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="251e3-150">Dans le fichier Client.exe.config, dans orderQueueName, remplacez « . » par le nom de l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="251e3-150">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="251e3-151">Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="251e3-151">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="251e3-152">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="251e3-152">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="251e3-153">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="251e3-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="251e3-154">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="251e3-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="251e3-155">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="251e3-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="251e3-156">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="251e3-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a><span data-ttu-id="251e3-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="251e3-157">See Also</span></span>  
 [<span data-ttu-id="251e3-158">Queuing dans WCF</span><span class="sxs-lookup"><span data-stu-id="251e3-158">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="251e3-159">Message Queuing</span><span class="sxs-lookup"><span data-stu-id="251e3-159">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=95143)
