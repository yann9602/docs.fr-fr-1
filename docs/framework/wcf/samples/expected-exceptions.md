---
title: Expected Exceptions
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77ddddd51229712f85bc780889169e159c1c83e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="expected-exceptions"></a><span data-ttu-id="aebf1-102">Expected Exceptions</span><span class="sxs-lookup"><span data-stu-id="aebf1-102">Expected Exceptions</span></span>
<span data-ttu-id="aebf1-103">Cet exemple montre comment intercepter des exceptions attendues lors de l'utilisation d'un client typé.</span><span class="sxs-lookup"><span data-stu-id="aebf1-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="aebf1-104">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="aebf1-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="aebf1-105">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="aebf1-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aebf1-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="aebf1-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="aebf1-107">Cet exemple illustre l'interception et la gestion des deux types d'exception attendues que les programmes corrects doivent gérer : `TimeoutException` et `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="aebf1-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="aebf1-108">Les exceptions levées depuis les méthodes de communication sur un client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont soit attendues, soit inattendues.</span><span class="sxs-lookup"><span data-stu-id="aebf1-108">Exceptions that are thrown from communication methods on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client are either expected or unexpected.</span></span> <span data-ttu-id="aebf1-109">Les exceptions inattendues incluent les pannes catastrophiques comme `OutOfMemoryException` et les erreurs de programmation comme `ArgumentNullException` ou `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="aebf1-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="aebf1-110">En général, il n'y a aucune utilité à gérer des erreurs inattendues, donc vous ne devez pas les intercepter lors de l'appel à une méthode de communication du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aebf1-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client communication method.</span></span>  
  
 <span data-ttu-id="aebf1-111">Les exceptions attendues depuis les méthodes de communication sur un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] incluent `TimeoutException`, `CommunicationException` et toute classe dérivée de `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="aebf1-111">Expected exceptions from communication methods on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="aebf1-112">Celles-ci indiquent un problème pendant la communication qui peut être géré sans risque en abandonnant le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et en signalant un échec de communication.</span><span class="sxs-lookup"><span data-stu-id="aebf1-112">These indicate a problem during communication that can be safely handled by aborting the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and reporting a communication failure.</span></span> <span data-ttu-id="aebf1-113">Étant donné que des facteurs externes peuvent provoquer ces erreurs dans toute application, les applications correctes doivent intercepter ces exceptions et récupérer lorsqu'elles se produisent.</span><span class="sxs-lookup"><span data-stu-id="aebf1-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="aebf1-114">Il existe plusieurs classes dérivées de `CommunicationException` qu'un client peut lever.</span><span class="sxs-lookup"><span data-stu-id="aebf1-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="aebf1-115">Dans certains cas, les applications en interceptent et procèdent à un traitement spécial, mais laissent les autres être traitées comme `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="aebf1-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="aebf1-116">Cela peut être accompli en interceptant le type d'exception plus spécifique en premier, puis en interceptant `CommunicationException` dans une clause « catch » ultérieure.</span><span class="sxs-lookup"><span data-stu-id="aebf1-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="aebf1-117">Le code qui appelle une méthode de communication cliente doit intercepter `TimeoutException` et `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="aebf1-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="aebf1-118">Pour gérer de telles erreurs, il est possible d'abandonner le client et de signaler l'échec de communication.</span><span class="sxs-lookup"><span data-stu-id="aebf1-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```  
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="aebf1-119">Si une exception attendue se produit, le client peut ou ne peut pas être utilisable après-coup.</span><span class="sxs-lookup"><span data-stu-id="aebf1-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="aebf1-120">Pour déterminer si le client est encore utilisable, vérifiez que la propriété `State` est `CommunicationState`.Opened.</span><span class="sxs-lookup"><span data-stu-id="aebf1-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="aebf1-121">Si le client est toujours ouvert, il est encore utilisable.</span><span class="sxs-lookup"><span data-stu-id="aebf1-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="aebf1-122">Sinon, vous devez abandonner le client et libérer toutes les références à ce dernier.</span><span class="sxs-lookup"><span data-stu-id="aebf1-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="aebf1-123">Vous pouvez observer que bien souvent les clients qui ont une session ne sont plus utilisables après une exception, et les clients qui n'ont pas de session sont encore utilisables après une exception.</span><span class="sxs-lookup"><span data-stu-id="aebf1-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="aebf1-124">Toutefois, cela n'est pas garanti, donc si vous souhaitez essayer de continuer à utiliser le client après une exception, votre application doit vérifier la propriété `State` pour vérifier le client est encore ouvert.</span><span class="sxs-lookup"><span data-stu-id="aebf1-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="aebf1-125">Lorsque vous exécutez l'exemple, les exceptions et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="aebf1-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="aebf1-126">Le processus client exécute deux scénarios, qui essaient tous deux d'appeler `Add` puis `Divide`.</span><span class="sxs-lookup"><span data-stu-id="aebf1-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="aebf1-127">Le premier scénario simule un problème de réseau en abandonnant le client avant de faire appel à `Divide`.</span><span class="sxs-lookup"><span data-stu-id="aebf1-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="aebf1-128">Le deuxième scénario provoque une condition de délai d'attente en définissant un délai d'attente trop court pour que la méthode se termine.</span><span class="sxs-lookup"><span data-stu-id="aebf1-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="aebf1-129">Le processus client est censé donner le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="aebf1-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aebf1-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="aebf1-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="aebf1-131">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aebf1-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="aebf1-132">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aebf1-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="aebf1-133">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aebf1-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aebf1-134">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aebf1-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aebf1-135">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="aebf1-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aebf1-136">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="aebf1-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aebf1-137">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="aebf1-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a><span data-ttu-id="aebf1-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aebf1-138">See Also</span></span>
