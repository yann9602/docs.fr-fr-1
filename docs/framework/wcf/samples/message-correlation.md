---
title: Message Correlation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54b7b7d9ba247f329fbf3c9040c641e3194d3bfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="message-correlation"></a><span data-ttu-id="328c3-102">Message Correlation</span><span class="sxs-lookup"><span data-stu-id="328c3-102">Message Correlation</span></span>
<span data-ttu-id="328c3-103">Cet exemple montre comment une application MSMQ (Message Queuing) peut envoyer un message MSMQ à un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et comment les messages peuvent être corrélés entre les applications de l'émetteur et du récepteur, dans un scénario demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="328c3-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="328c3-104">Cet exemple utilise la liaison msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="328c3-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="328c3-105">Dans le cas présent, le service est une application console auto-hébergée qui vous permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="328c3-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="328c3-106">k</span><span class="sxs-lookup"><span data-stu-id="328c3-106">k</span></span>  
  
 <span data-ttu-id="328c3-107">Le service traite le message reçu de l'expéditeur et lui renvoie un message de réponse.</span><span class="sxs-lookup"><span data-stu-id="328c3-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="328c3-108">L'expéditeur met en corrélation la réponse qu'il a reçue à la demande qu'il a envoyée à l'origine.</span><span class="sxs-lookup"><span data-stu-id="328c3-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="328c3-109">Les propriétés `MessageID` et `CorrelationID` du message sont utilisées pour mettre en corrélation les messages de demande et de réponse.</span><span class="sxs-lookup"><span data-stu-id="328c3-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="328c3-110">Le contrat de service `IOrderProcessor` définit une opération de service unidirectionnelle qui convient à l'utilisation de la mise en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="328c3-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="328c3-111">Un message MSMQ n'ayant pas d'en-tête Action, il n'est donc pas possible de mapper automatiquement des messages MSMQ différents aux contrats d'opération.</span><span class="sxs-lookup"><span data-stu-id="328c3-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="328c3-112">Par conséquent, il ne peut y avoir qu'un seul contrat d'opération dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="328c3-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="328c3-113">Si vous souhaitez définir plusieurs contrats d'opération dans le service, l'application doit fournir des informations sur l'en-tête dans le message MSMQ (par exemple, l'étiquette ou correlationID) qui peut être utilisé pour déterminer le contrat d'opération à distribuer.</span><span class="sxs-lookup"><span data-stu-id="328c3-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="328c3-114">Cela est illustré dans le [personnalisé Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="328c3-114">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="328c3-115">En outre, le message MSMQ ne contient pas d'informations concernant les en-têtes qui sont mappés à différents paramètres du contrat d'opération.</span><span class="sxs-lookup"><span data-stu-id="328c3-115">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="328c3-116">Par conséquent, il ne peut y avoir qu'un seul paramètre dans le contrat d'opération.</span><span class="sxs-lookup"><span data-stu-id="328c3-116">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="328c3-117">Le paramètre est de type <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` qui contient le message MSMQ sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="328c3-117">The parameter is of type <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` which contains the underlying MSMQ message.</span></span> <span data-ttu-id="328c3-118">Le type « T » dans la classe `MsmqMessage<T>` représente les données sérialisées dans le corps du message MSMQ.</span><span class="sxs-lookup"><span data-stu-id="328c3-118">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="328c3-119">Dans cet exemple, le type `PurchaseOrder` est sérialisé dans le corps du message MSMQ.</span><span class="sxs-lookup"><span data-stu-id="328c3-119">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```  
  
 <span data-ttu-id="328c3-120">L'opération de service traite le bon de commande et en affiche le contenu et l'état dans la fenêtre de console du service.</span><span class="sxs-lookup"><span data-stu-id="328c3-120">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="328c3-121">L'<xref:System.ServiceModel.OperationBehaviorAttribute> configure l'opération pour l'inscrire dans une transaction avec la file d'attente et marquer la transaction comme complète lorsque l'opération est retournée.</span><span class="sxs-lookup"><span data-stu-id="328c3-121">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="328c3-122">Le `PurchaseOrder` contient les détails de la commande qui doivent être traités par le service.</span><span class="sxs-lookup"><span data-stu-id="328c3-122">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>  
  
```  
// Service class that implements the service contract.  
public class OrderProcessorService : IOrderProcessor  
{  
   [OperationBehavior(TransactionScopeRequired = true,   
          TransactionAutoComplete = true)]  
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)  
   {  
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;  
       Random statusIndexer = new Random();  
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
       Console.WriteLine("Processing {0} ", po);  
       //Send a response to the client that the order has been received   
         and is pending fullfillment.   
       SendResponse(ordermsg);  
    }  
  
    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)  
    {  
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");  
  
        //Set the correlation ID such that the client can correlate the response to the order.  
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);  
        orderResponsemsg.CorrelationId = ordermsg.Id;  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.SendOrderResponse(orderResponsemsg);  
            scope.Complete();  
        }  
  
        client.Close();  
    }  
}  
```  
  
 <span data-ttu-id="328c3-123">Le service utilise un client `OrderResponseClient` personnalisé pour envoyer le message MSMQ à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="328c3-123">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="328c3-124">L'application qui reçoit et traite le message étant une application MSMQ et non pas une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], il n'y a pas de contrat de service implicite entre les deux applications.</span><span class="sxs-lookup"><span data-stu-id="328c3-124">Because the application that receives and processes the message is an MSMQ application and not a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="328c3-125">Par conséquent, nous ne pouvons pas créer de proxy à l'aide de l'outil Svcutil.exe dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="328c3-125">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="328c3-126">Le proxy personnalisé est essentiellement le même pour toutes les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui utilisent la liaison `msmqIntegrationBinding` pour envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="328c3-126">The custom proxy is essentially the same for all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="328c3-127">Contrairement aux autres proxys, il n'inclut pas de plage d'opérations de service.</span><span class="sxs-lookup"><span data-stu-id="328c3-127">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="328c3-128">Il s'agit uniquement d'une opération d'envoi de message.</span><span class="sxs-lookup"><span data-stu-id="328c3-128">It is a submit message operation only.</span></span>  
  
```  
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderResponse  
{  
  
    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]  
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse  
{  
  
    public OrderResponseClient()  
    { }  
  
    public OrderResponseClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SendOrderResponse(msg);  
    }  
}  
```  
  
 <span data-ttu-id="328c3-129">Le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="328c3-129">The service is self hosted.</span></span> <span data-ttu-id="328c3-130">Lors de l'utilisation du transport d'intégration MSMQ, la file d'attente utilisée doit être créée au préalable.</span><span class="sxs-lookup"><span data-stu-id="328c3-130">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="328c3-131">Cela peut s'effectuer manuellement ou via le code.</span><span class="sxs-lookup"><span data-stu-id="328c3-131">This can be done manually or through code.</span></span> <span data-ttu-id="328c3-132">Dans cet exemple, le service contient le code <xref:System.Messaging> pour vérifier l'existence de la file d'attente et la créer si besoin.</span><span class="sxs-lookup"><span data-stu-id="328c3-132">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="328c3-133">Le nom de la file d'attente est lu depuis le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="328c3-133">The queue name is read from the configuration file.</span></span>  
  
```  
public static void Main()  
{  
       // Get the MSMQ queue name from application settings in configuration.  
      string queueName =   
                ConfigurationManager.AppSettings["orderQueueName"];  
      // Create the transacted MSMQ queue if necessary.  
      if (!MessageQueue.Exists(queueName))  
                MessageQueue.Create(queueName, true);  
     // Create a ServiceHost for the OrderProcessorService type.  
     using (ServiceHost serviceHost = new   
                   ServiceHost(typeof(OrderProcessorService)))  
     {  
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
  
 <span data-ttu-id="328c3-134">La file d'attente MSMQ à laquelle les demandes de bon de commande sont envoyées est spécifiée dans la section appSettings du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="328c3-134">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="328c3-135">Les points de terminaison du client et du service sont définis dans la section system.serviceModel du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="328c3-135">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="328c3-136">Tous deux spécifient la liaison `msmqIntegrationbinding`.</span><span class="sxs-lookup"><span data-stu-id="328c3-136">Both specify the `msmqIntegrationbinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
  
<system.serviceModel>  
  <client>  
    <endpoint    name="OrderResponseEndpoint"   
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"  
              binding="msmqIntegrationBinding"  
              bindingConfiguration="OrderProcessorBinding"   
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">  
    </endpoint>  
  </client>  
  
  <services>  
    <service   
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"  
                            binding="msmqIntegrationBinding"  
                bindingConfiguration="OrderProcessorBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">  
      </endpoint>  
    </service>  
  </services>  
  
  <bindings>  
    <msmqIntegrationBinding>  
      <binding name="OrderProcessorBinding" >  
        <security mode="None" />  
      </binding>  
    </msmqIntegrationBinding>  
  </bindings>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="328c3-137">L'application cliente utilise <xref:System.Messaging> pour envoyer un message durable et transactionnel à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="328c3-137">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="328c3-138">Le corps du message contient le bon de commande.</span><span class="sxs-lookup"><span data-stu-id="328c3-138">The message's body contains the purchase order.</span></span>  
  
```  
static void PlaceOrder()  
{  
    //Connect to the queue  
    MessageQueue orderQueue =   
            new MessageQueue(  
                    ConfigurationManager.AppSettings["orderQueueName"])   
    // Create the purchase order.  
    PurchaseOrder po = new PurchaseOrder();  
    po.CustomerId = "somecustomer.com";  
    po.PONumber = Guid.NewGuid().ToString();  
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
    lineItem1.ProductId = "Blue Widget";  
    lineItem1.Quantity = 54;  
    lineItem1.UnitCost = 29.99F;  
  
    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
    lineItem2.ProductId = "Red Widget";  
    lineItem2.Quantity = 890;  
    lineItem2.UnitCost = 45.89F;  
  
    po.orderLineItems = new PurchaseOrderLineItem[2];  
    po.orderLineItems[0] = lineItem1;  
    po.orderLineItems[1] = lineItem2;  
  
    Message msg = new Message();  
    msg.UseDeadLetterQueue = true;  
    msg.Body = po;  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new      
     TransactionScope(TransactionScopeOption.Required))  
    {  
        // Submit the purchase order.  
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
        // Complete the transaction.  
        scope.Complete();  
    }  
    //Save the messageID for order response correlation.  
    orderMessageID = msg.Id;  
    Console.WriteLine("Placed the order, waiting for response...");  
}  
```  
  
 <span data-ttu-id="328c3-139">La file d'attente MSMQ à partir de laquelle les réponses à la commande sont reçues est spécifiée dans une section appSettings du fichier de configuration, comme le montre l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="328c3-139">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="328c3-140">Le nom de la file d'attente utilise un point (.) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="328c3-140">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="328c3-141">L'adresse du point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spécifie un schéma msmq.formatname et utilise « localhost » pour l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="328c3-141">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="328c3-142">Un nom de format correct suit msmq.formatname dans l'URI d'après les règles d'adressage MSMQ.</span><span class="sxs-lookup"><span data-stu-id="328c3-142">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="328c3-143">L'application cliente enregistre l'`messageID` du message de demande de commande qu'elle envoie au service et attend une réponse du service.</span><span class="sxs-lookup"><span data-stu-id="328c3-143">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="328c3-144">Une fois qu'une réponse arrive dans la file d'attente, le client le met en corrélation avec le message de commande qu'il a envoyé à l'aide de la propriété `correlationID` du message, qui contient l'`messageID` du message de commande que le client a envoyé au service à l'origine.</span><span class="sxs-lookup"><span data-stu-id="328c3-144">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>  
  
```  
static void DisplayOrderStatus()  
{  
    MessageQueue orderResponseQueue = new   
     MessageQueue(ConfigurationManager.AppSettings              
                  ["orderResponseQueueName"]);  
    //Create a transaction scope.  
    bool responseReceived = false;  
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;  
    while (!responseReceived)  
    {  
       Message responseMsg;  
       using (TransactionScope scope2 = new    
         TransactionScope(TransactionScopeOption.Required))  
       {  
          //Receive the Order Response message.  
          responseMsg =   
              orderResponseQueue.Receive  
                   (MessageQueueTransactionType.Automatic);  
          scope2.Complete();  
     }  
     responseMsg.Formatter = new   
     System.Messaging.XmlMessageFormatter(new Type[] {   
         typeof(PurchaseOrder) });  
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;  
    //Check if the response is for the order placed.  
    if (orderMessageID == responseMsg.CorrelationId)  
    {  
       responseReceived = true;  
       Console.WriteLine("Status of current Order: OrderID-{0},Order   
            Status-{1}", responsepo.PONumber, responsepo.Status);  
    }  
    else  
    {  
       Console.WriteLine("Status of previous Order: OrderID-{0},Order    
            Status-{1}", responsepo.PONumber, responsepo.Status);  
    }  
  }  
}  
```  
  
 <span data-ttu-id="328c3-145">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="328c3-145">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="328c3-146">Vous pouvez voir le service recevoir des messages du client et renvoyer une réponse au client.</span><span class="sxs-lookup"><span data-stu-id="328c3-146">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="328c3-147">Le client affiche la réponse reçue du service.</span><span class="sxs-lookup"><span data-stu-id="328c3-147">The client displays the response received from the service.</span></span> <span data-ttu-id="328c3-148">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="328c3-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="328c3-149">Cet exemple requiert l'installation de MSMQ (Message Queuing).</span><span class="sxs-lookup"><span data-stu-id="328c3-149">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="328c3-150">Consultez les instructions d'installation de MSMQ dans la section « Voir aussi ».</span><span class="sxs-lookup"><span data-stu-id="328c3-150">See the MSMQ installation instructions in the See Also section.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="328c3-151">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="328c3-151">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="328c3-152">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="328c3-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="328c3-153">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="328c3-153">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="328c3-154">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="328c3-154">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="328c3-155">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="328c3-155">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="328c3-156">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="328c3-156">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="328c3-157">Ouvrez le Gestionnaire de serveur dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="328c3-157">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="328c3-158">Développez le **fonctionnalités** onglet.</span><span class="sxs-lookup"><span data-stu-id="328c3-158">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="328c3-159">Avec le bouton droit **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="328c3-159">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="328c3-160">Vérifiez le **transactionnel** boîte.</span><span class="sxs-lookup"><span data-stu-id="328c3-160">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="328c3-161">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="328c3-161">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="328c3-162">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="328c3-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="328c3-163">Pour exécuter l’exemple dans une configuration sur un seul ordinateur, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="328c3-163">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="328c3-164">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="328c3-164">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="328c3-165">Copiez les fichiers programme du service figurant dans le dossier \service\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="328c3-165">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="328c3-166">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="328c3-166">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="328c3-167">Dans le fichier Client.exe.config, dans orderQueueName, remplacez « . » par le nom de l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="328c3-167">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="328c3-168">Dans le fichier Service.exe.config, modifiez l'adresse de point de terminaison client afin de remplacer « . » par le nom de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="328c3-168">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>  
  
5.  <span data-ttu-id="328c3-169">Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="328c3-169">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
6.  <span data-ttu-id="328c3-170">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="328c3-170">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="328c3-171">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="328c3-171">The samples may already be installed on your computer.</span></span> <span data-ttu-id="328c3-172">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="328c3-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="328c3-173">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="328c3-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="328c3-174">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="328c3-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="328c3-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="328c3-175">See Also</span></span>  
 [<span data-ttu-id="328c3-176">Queuing dans WCF</span><span class="sxs-lookup"><span data-stu-id="328c3-176">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="328c3-177">Message Queuing</span><span class="sxs-lookup"><span data-stu-id="328c3-177">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)
