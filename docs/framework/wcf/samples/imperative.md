---
title: Imperative
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f7ce807-c0e4-407a-92a6-22abafb40b51
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 378d27898ec69ae1d014abd7c8a59693058b62bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imperative"></a><span data-ttu-id="b0ea5-102">Imperative</span><span class="sxs-lookup"><span data-stu-id="b0ea5-102">Imperative</span></span>
<span data-ttu-id="b0ea5-103">Cet exemple montre comment définir un <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> pour un service à l’aide de code, au lieu de définir la `wsHttpBinding` dans la configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-103">This sample demonstrates how to define a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> for a service using code, instead of defining the `wsHttpBinding` binding in configuration.</span></span> <span data-ttu-id="b0ea5-104">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0ea5-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b0ea5-106">Le code suivant montre comment définir une liaison dans le code de façon impérative.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-106">The following code demonstrates how to define a binding imperatively in code.</span></span>  
  
```  
public static void Main()  
{  
    WSHttpBinding binding = new WSHttpBinding();  
    binding.Name = "binding1";  
    binding.HostNameComparisonMode =  
        HostNameComparisonMode.StrongWildcard;  
    binding.Security.Mode = SecurityMode.Message;  
    binding.ReliableSession.Enabled = false;  
    binding.TransactionFlow = false;  
  
    Uri baseAddress =   
        new Uri("http://localhost:8000/servicemodelsamples/service");  
  
    // Create a ServiceHost for the CalculatorService type and provide the base address.  
    using(ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
    {  
        serviceHost.AddServiceEndpoint(typeof(ICalculator),   
                                       binding, baseAddress);  
        // Open the ServiceHostBase to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
        // Close the ServiceHostBase to shutdown the service.  
        serviceHost.Close();                        
    }             
}  
```  
  
 <span data-ttu-id="b0ea5-107">Le client crée un canal pour communiquer avec le service, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-107">The client creates a channel to communicate with the service as shown in the following sample code.</span></span>  
  
```  
WSHttpBinding binding = new WSHttpBinding();  
binding.Name = "binding1";  
binding.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
binding.Security.Mode = SecurityMode.Message;  
binding.ReliableSession.Enabled = false;  
binding.TransactionFlow = false;  
  
String url = "http://localhost:8000/servicemodelsamples/service";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding,address);  
ICalculator channel = channelFactory.CreateChannel();  
```  
  
 <span data-ttu-id="b0ea5-108">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-108">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b0ea5-109">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-109">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b0ea5-110">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="b0ea5-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b0ea5-111">Vérifiez que vous avez effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0ea5-111">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b0ea5-112">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0ea5-112">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b0ea5-113">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0ea5-113">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0ea5-114">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-114">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b0ea5-115">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b0ea5-116">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b0ea5-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0ea5-117">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="b0ea5-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="b0ea5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0ea5-118">See Also</span></span>
