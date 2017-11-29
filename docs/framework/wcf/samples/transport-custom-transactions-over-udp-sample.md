---
title: 'Transport: Custom Transactions over UDP Sample'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c1586b763d98776468322144019407c7c6cc27a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="e2f1b-102">Transport: Custom Transactions over UDP Sample</span><span class="sxs-lookup"><span data-stu-id="e2f1b-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="e2f1b-103">Cet exemple est basé sur le [Transport : UDP](../../../../docs/framework/wcf/samples/transport-udp.md) présenté dans le [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] [Transport extensibilité](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="e2f1b-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)][Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="e2f1b-104">Il étend l'exemple UDP Transport afin de prendre en charge le flux de transactions personnalisé et présente l'utilisation de la propriété <xref:System.ServiceModel.Channels.TransactionMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="e2f1b-105">Modifications du code dans l'exemple UDP Transport</span><span class="sxs-lookup"><span data-stu-id="e2f1b-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="e2f1b-106">Pour illustrer le flux de transactions, l'exemple modifie le contrat de service de `ICalculatorContract` afin qu'une portée de transaction soit requise pour `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="e2f1b-107">L'exemple ajoute également un paramètre `System.Guid` supplémentaire au contrat de l'opération `Add`.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="e2f1b-108">Ce paramètre permet de transmettre l’identificateur de la transaction cliente au service.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);              
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="e2f1b-109">Le [Transport : UDP](../../../../docs/framework/wcf/samples/transport-udp.md) utilise les paquets UDP pour transmettre des messages entre un client et un service.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="e2f1b-110">Le [Transport : exemple de Transport personnalisé](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) utilise le même mécanisme de transport des messages, mais lorsqu’une transaction est transmise, il est inséré dans le paquet UDP, ainsi que le message encodé.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="e2f1b-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` est une méthode d'assistance qui contient de nouvelles fonctionnalités permettant de fusionner le jeton de propagation de la transaction actuelle avec l'entité de message, et de le placer dans une mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="e2f1b-112">Pour le transport du flux de transactions personnalisé, l'implémentation du client doit connaître les opérations de service qui requièrent le flux de transactions et transmettre ces informations à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2f1b-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="e2f1b-113">Un mécanisme doit également permettre de transmettre la transaction utilisateur à la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="e2f1b-114">Cet exemple utilise des « inspecteurs de message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] » pour obtenir ces informations.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-114">This sample uses "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message inspectors" to obtain this information.</span></span> <span data-ttu-id="e2f1b-115">L'inspecteur de message client implémenté ici et appelé `TransactionFlowInspector` effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="e2f1b-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
-   <span data-ttu-id="e2f1b-116">Il détermine si une transaction doit être transmise pour une action de message donnée (cette opération a lieu dans `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="e2f1b-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
-   <span data-ttu-id="e2f1b-117">Il joint la transaction ambiante actuelle au message à l'aide de `TransactionFlowProperty`, si une transaction doit être transmise (cette opération s'effectue dans `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="e2f1b-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;             
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;              
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="e2f1b-118">Le `TransactionFlowInspector` lui-même est passé à l'infrastructure à l'aide d'un comportement personnalisé : `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="e2f1b-119">Le mécanisme précédent étant en place, le code utilisateur crée un `TransactionScope` avant d'appeler l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="e2f1b-120">L'inspecteur de message veille à ce que la transaction soit passée au transport si elle doit être transmise à l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());               
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }               
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="e2f1b-121">Après réception d'un paquet UDP émanant du client, le service désérialise ce paquet afin d'extraire le message et éventuellement une transaction.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="e2f1b-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` est la méthode d'assistance qui annule le processus de sérialisation effectué par `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="e2f1b-123">Si une transaction a été transmise, elle est ajoutée au message dans `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="e2f1b-124">Cela garantit que le répartiteur sélectionne la transaction au moment de la distribution et l'utilise lors de l'appel de l'opération de service traitée par le message.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e2f1b-125">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="e2f1b-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e2f1b-126">Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2f1b-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="e2f1b-127">L’exemple actuel doit être exécutée de façon similaire à la [Transport : UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="e2f1b-128">Pour l'exécuter, démarrez le service avec UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="e2f1b-129">Si vous exécutez [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], vous devez démarrer le service avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="e2f1b-130">Pour ce faire, cliquez sur UdpTestService.exe dans [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] et cliquez sur **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-130">To do so, right-click UdpTestService.exe in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="e2f1b-131">La sortie suivante est alors générée.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  <span data-ttu-id="e2f1b-132">À ce stade, vous pouvez démarrer le client en exécutant UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="e2f1b-133">La sortie générée par le client se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  <span data-ttu-id="e2f1b-134">La sortie du service se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-134">The service output is as follows.</span></span>  
  
    ```  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6.  <span data-ttu-id="e2f1b-135">L'application de service affiche le message `The client transaction has flowed to the service` si elle peut faire correspondre l'identificateur de transaction envoyé par le client (dans le paramètre `clientTransactionId` de l'opération `CalculatorService.Add()`) à l'identificateur de la transaction de service.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="e2f1b-136">Une correspondance est obtenue uniquement si la transaction cliente est transmise au service.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7.  <span data-ttu-id="e2f1b-137">Pour exécuter l'application cliente sur des points de terminaison publiés à l'aide de la configuration, appuyez sur ENTRÉE dans la fenêtre d'application de service, puis réexécutez le client test.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="e2f1b-138">La sortie suivante doit s'afficher sur le service.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  <span data-ttu-id="e2f1b-139">L'exécution du client sur le service génère maintenant une sortie similaire à la précédente.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="e2f1b-140">Pour régénérer la configuration et le code client à l'aide de Svcutil.exe, démarrez l'application de service, puis exécutez la commande Svcutil.exe suivante à partir du répertoire racine de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="e2f1b-141">Svcutil.exe ne générant pas de configuration d'extension de liaison pour `sampleProfileUdpBinding`, vous devez donc l'ajouter manuellement.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>      
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2f1b-142">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2f1b-143">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e2f1b-144">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2f1b-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2f1b-145">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="e2f1b-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="e2f1b-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2f1b-146">See Also</span></span>  
 [<span data-ttu-id="e2f1b-147">Transport : UDP</span><span class="sxs-lookup"><span data-stu-id="e2f1b-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
