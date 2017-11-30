---
title: Avoiding Problems with the Using Statement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 123081683f122f68fded94aed5735d7058496366
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="avoiding-problems-with-the-using-statement"></a><span data-ttu-id="37347-102">Avoiding Problems with the Using Statement</span><span class="sxs-lookup"><span data-stu-id="37347-102">Avoiding Problems with the Using Statement</span></span>
<span data-ttu-id="37347-103">Cet exemple vous indique que vous ne devez pas utiliser l'instruction « using » C# pour nettoyer automatiquement les ressources lorsqu'un client typé est utilisé.</span><span class="sxs-lookup"><span data-stu-id="37347-103">This sample demonstrates how you should not use the C# "using" statement to automatically clean up resources when using a typed client.</span></span> <span data-ttu-id="37347-104">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="37347-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="37347-105">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="37347-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37347-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="37347-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="37347-107">Cet exemple contient deux des problèmes fréquents susceptibles de survenir lorsque l'instruction « using » C# est utilisée avec les clients typés ainsi que le code permettant de procéder au nettoyage adéquat après la survenue d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="37347-107">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="37347-108">L'instruction « using » C# provoque l'appel de `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="37347-108">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="37347-109">Cette méthode est identique à la méthode `Close`(), laquelle peut lever des exceptions lorsqu'une erreur réseau se produit.</span><span class="sxs-lookup"><span data-stu-id="37347-109">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="37347-110">L'appel de `Dispose`() se produit de manière implicite au niveau de l'accolade fermante du bloc « using », cette source d'exceptions a peu de chance d'être remarquée par une personne lisant le code ou par la personne chargée de le rédiger.</span><span class="sxs-lookup"><span data-stu-id="37347-110">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="37347-111">Cela représente une source potentielle d'erreurs d'application.</span><span class="sxs-lookup"><span data-stu-id="37347-111">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="37347-112">Le premier problème, illustré dans la méthode `DemonstrateProblemUsingCanThrow`, réside dans le fait que l'accolade fermante lève une exception et que le code figurant après cette accolade ne s'exécute pas :</span><span class="sxs-lookup"><span data-stu-id="37347-112">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```  
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="37347-113">Même si rien à l'intérieur du bloc « using » ne provoque la levée d'une exception ou si toutes les exceptions à l'intérieur de ce bloc sont interceptées, le code `Console.Writeline` peut ne pas s'exécuter, l'appel implicite de `Dispose`() risquant de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="37347-113">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="37347-114">Le second problème, illustré dans la méthode `DemonstrateProblemUsingCanThrowAndMask`, est une autre conséquence du problème résultant de la levée d'une exception par l'accolade fermante :</span><span class="sxs-lookup"><span data-stu-id="37347-114">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```  
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="37347-115">La méthode `Dispose`() survenant à l'intérieur d'un bloc « finally », l'exception `ApplicationException` ne sera pas visible en dehors du bloc « using » si la méthode `Dispose`() échoue.</span><span class="sxs-lookup"><span data-stu-id="37347-115">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="37347-116">Si le code externe doit savoir à quel moment l'exception `ApplicationException` survient, le bloc « using » risque de poser un problème, car il masque cette exception.</span><span class="sxs-lookup"><span data-stu-id="37347-116">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="37347-117">Enfin, cette exemple illustre comment procéder à un nettoyage adéquat lors de la survenue d'exceptions dans `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="37347-117">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="37347-118">Pour ce faire, un bloc essai/interception est utilisé pour signaler les erreurs et appeler la méthode `Abort`.</span><span class="sxs-lookup"><span data-stu-id="37347-118">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="37347-119">Consultez le [attendu des Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample pour plus d’informations sur l’interception d’exceptions à partir des appels du client.</span><span class="sxs-lookup"><span data-stu-id="37347-119">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
```  
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="37347-120">Instruction « using » et ServiceHost : de nombreuses applications d'auto-hébergement ne se contentent pas seulement d'héberger des services et l'appel de la méthode ServiceHost.Close lève rarement une exception. Par conséquent, ces applications peuvent utiliser l'instruction « using » avec ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="37347-120">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="37347-121">Toutefois, n'oubliez pas que l'appel de la méthode ServiceHost.Close peut lever une exception `CommunicationException`. Par conséquent, si votre application continue à s'exécuter après la fermeture de ServiceHost, vous devez éviter d'utiliser l'instruction « using » et vous conformer au modèle mentionné précédemment.</span><span class="sxs-lookup"><span data-stu-id="37347-121">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="37347-122">Lorsque vous exécutez l'exemple, les exceptions et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="37347-122">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="37347-123">Le processus du client exécute trois scénarios qui essaient tous d'appeler `Divide`.</span><span class="sxs-lookup"><span data-stu-id="37347-123">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="37347-124">Le premier scénario contient le code ignoré à cause de l'exception levée par la méthode `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="37347-124">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="37347-125">Le deuxième scénario contient une exception importante masquée à cause de l'exception levée par la méthode `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="37347-125">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="37347-126">Le troisième scénario illustre le processus de nettoyage adéquat.</span><span class="sxs-lookup"><span data-stu-id="37347-126">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="37347-127">Le processus client est censé donner le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="37347-127">The expected output from the client process is:</span></span>  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37347-128">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="37347-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="37347-129">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37347-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="37347-130">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37347-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="37347-131">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37347-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37347-132">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37347-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37347-133">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="37347-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="37347-134">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="37347-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37347-135">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="37347-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="37347-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37347-136">See Also</span></span>
