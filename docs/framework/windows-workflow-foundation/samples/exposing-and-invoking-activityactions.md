---
title: Exposition et appel d'ActivityActions
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4285718ef1829e9432957278d5ca7959e32e4511
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="2a74d-102">Exposition et appel d'ActivityActions</span><span class="sxs-lookup"><span data-stu-id="2a74d-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="2a74d-103">Cet exemple montre comment développer une activité personnalisée qui a un <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="2a74d-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="2a74d-104">Il montre également comment utiliser cette activité en fournissant une implémentation d'<xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="2a74d-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="2a74d-105">Un <xref:System.Activities.ActivityAction> permet à un auteur d’activité d’exposer des « espaces » avec des signatures spécifiques où l’utilisateur de l’activité peut incorporer un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2a74d-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="2a74d-106">Par exemple, le <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activité (qui fonctionne sur une collection d’éléments), a un <xref:System.Activities.ActivityAction> qui permet à l’utilisateur de l’activité incorporer un comportement qui fonctionne sur l’élément de l’itération actuelle.</span><span class="sxs-lookup"><span data-stu-id="2a74d-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2a74d-107">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="2a74d-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2a74d-108">Ouvrez le **ActivityAction.sln** exemple de solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2a74d-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="2a74d-109">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="2a74d-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a74d-110">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2a74d-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2a74d-111">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2a74d-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2a74d-112">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2a74d-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2a74d-113">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2a74d-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`