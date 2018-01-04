---
title: "Activité For"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3305defd4f2819a3ebe9d3b7429ddac11ae6833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="for-activity"></a><span data-ttu-id="31100-102">Activité For</span><span class="sxs-lookup"><span data-stu-id="31100-102">For Activity</span></span>
<span data-ttu-id="31100-103">L'exemple For montre comment générer une activité personnalisée qui hérite de <xref:System.Activities.NativeActivity>, et l'utiliser dans un workflow pour exécuter un exemple réel.</span><span class="sxs-lookup"><span data-stu-id="31100-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="31100-104">L'activité personnalisée incluse dans cet exemple fonctionne comme l'instruction C# `for`.</span><span class="sxs-lookup"><span data-stu-id="31100-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="31100-105">T</span><span class="sxs-lookup"><span data-stu-id="31100-105">T</span></span>  
  
 <span data-ttu-id="31100-106">L'activité personnalisée `For` a des propriétés nommées `InitAction`, `IterationAction`, `Condition` et `Body` qui correspondent respectivement à l'instruction d'initialisation, à l'instruction itérative, à la condition de continuation et à l'instruction du corps se trouvant dans la instruction standard C# `For`.</span><span class="sxs-lookup"><span data-stu-id="31100-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="31100-107">Le tableau suivant décrit les fichiers de clés de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="31100-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="31100-108">Fichier</span><span class="sxs-lookup"><span data-stu-id="31100-108">File</span></span>|<span data-ttu-id="31100-109">Description</span><span class="sxs-lookup"><span data-stu-id="31100-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="31100-110">For.cs</span><span class="sxs-lookup"><span data-stu-id="31100-110">For.cs</span></span>|<span data-ttu-id="31100-111">Définition de classe pour l'activité personnalisée `For`, qui étend la classe <xref:System.Activities.NativeActivity> pour fournir les fonctionnalités de l'instruction C# `For`.</span><span class="sxs-lookup"><span data-stu-id="31100-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="31100-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="31100-112">Program.cs</span></span>|<span data-ttu-id="31100-113">Application cliente qui effectue le travail itératif de base sur une collection à l'aide de l'activité `For` personnalisée.</span><span class="sxs-lookup"><span data-stu-id="31100-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="31100-114">Lorsque vous utilisez l'activité personnalisée `For`, vérifiez que la propriété `Condition` est définie ; sinon, une boucle infinie pourrait se produire.</span><span class="sxs-lookup"><span data-stu-id="31100-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="31100-115">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="31100-115">Demonstrates</span></span>  
 <span data-ttu-id="31100-116">Créez une activité personnalisée qui hérite de l'activité <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="31100-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="31100-117">Discussion</span><span class="sxs-lookup"><span data-stu-id="31100-117">Discussion</span></span>  
 <span data-ttu-id="31100-118">Le tableau suivant décrit les propriétés de l'activité incluse dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="31100-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="31100-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="31100-119">InitAction</span></span>  
 <span data-ttu-id="31100-120">Instruction d'initialisation</span><span class="sxs-lookup"><span data-stu-id="31100-120">Initialization statement</span></span>  
  
 <span data-ttu-id="31100-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="31100-121">IterationAction</span></span>  
 <span data-ttu-id="31100-122">Instruction itérative</span><span class="sxs-lookup"><span data-stu-id="31100-122">Iterative statement</span></span>  
  
 <span data-ttu-id="31100-123">Condition</span><span class="sxs-lookup"><span data-stu-id="31100-123">Condition</span></span>  
 <span data-ttu-id="31100-124">Instruction de continuation</span><span class="sxs-lookup"><span data-stu-id="31100-124">Continuation statement</span></span>  
  
 <span data-ttu-id="31100-125">Corps</span><span class="sxs-lookup"><span data-stu-id="31100-125">Body</span></span>  
 <span data-ttu-id="31100-126">Instruction du corps</span><span class="sxs-lookup"><span data-stu-id="31100-126">Body statement</span></span>  
  
 <span data-ttu-id="31100-127">L'activité hérite de <xref:System.Activities.NativeActivity> pour accéder à des fonctionnalités de runtime telles que la planification de l'exécution d'activités supplémentaires, à l'aide de l'une des méthodes `ScheduleActivity` de <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="31100-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="31100-128">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="31100-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="31100-129">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution For.sln.</span><span class="sxs-lookup"><span data-stu-id="31100-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="31100-130">Générez la solution en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="31100-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="31100-131">Exécutez la solution en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="31100-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31100-132">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31100-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31100-133">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="31100-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="31100-134">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="31100-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31100-135">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="31100-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`