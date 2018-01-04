---
title: "Mise en route avec l'écriture d'une activité personnalisée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 568c25574fa5c3536f1c7678f2705c19719c62d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="38de8-102">Mise en route avec l'écriture d'une activité personnalisée</span><span class="sxs-lookup"><span data-stu-id="38de8-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="38de8-103">Cet exemple montre comment définir une activité personnalisée simple en XAML.</span><span class="sxs-lookup"><span data-stu-id="38de8-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="38de8-104">Le nom `Rhyme` est attribué à l'activité, et sa logique est une séquence de trois activités <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="38de8-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="38de8-105">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="38de8-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="38de8-106">Ouvrez le **Simple.sln** exemple de solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38de8-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="38de8-107">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="38de8-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="38de8-108">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="38de8-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38de8-109">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="38de8-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="38de8-110">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="38de8-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38de8-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="38de8-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`