---
title: "Composition de l'activité de base"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 047948552471b33af8690b526db7c416e87f897a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-activity-composition"></a><span data-ttu-id="d710f-102">Composition de l'activité de base</span><span class="sxs-lookup"><span data-stu-id="d710f-102">Basic Activity Composition</span></span>
<span data-ttu-id="d710f-103">Cet exemple montre comment composer des activités personnalisées et des activités fournies par le système pour générer d'autres activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="d710f-103">This sample demonstrates how to compose custom activities and system-provided activities to build more custom activities.</span></span>  
  
 <span data-ttu-id="d710f-104">Le workflow, à l'aide de l'activité Survey, planifie l'enquête avec une liste de questions, puis fournit en sortie les réponses reçues.</span><span class="sxs-lookup"><span data-stu-id="d710f-104">The workflow using the Survey activity schedules the Survey with a list of questions, and then outputs the responses received.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d710f-105">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="d710f-105">Sample Details</span></span>  
 <span data-ttu-id="d710f-106">Cet exemple utilise trois activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="d710f-106">This sample uses three custom activities.</span></span> <span data-ttu-id="d710f-107">`ReadLine`est un simple <xref:System.Activities.NativeActivity> \<chaîne > qui crée un <xref:System.Activities.Bookmark> lorsque planifiés et définit ensuite la `Return` <xref:System.Activities.OutArgument%601> à la valeur avec laquelle le <xref:System.Activities.Bookmark> est repris.</span><span class="sxs-lookup"><span data-stu-id="d710f-107">`ReadLine` is a simple <xref:System.Activities.NativeActivity>\<string> that creates a <xref:System.Activities.Bookmark> when scheduled, and then sets the `Return`<xref:System.Activities.OutArgument%601> to the value with which the <xref:System.Activities.Bookmark> is resumed.</span></span> <span data-ttu-id="d710f-108">`Prompt`est un <xref:System.Activities.Activity%601> \<string > qui prend une <xref:System.Activities.InArgument%601>< chaîne\> nommé `Text` et retourne les utilisateurs de réponse dans le `Result` <xref:System.Activities.OutArgument%601> \<chaîne >.</span><span class="sxs-lookup"><span data-stu-id="d710f-108">`Prompt` is an <xref:System.Activities.Activity%601>\<string> that takes an <xref:System.Activities.InArgument%601><string\> named `Text` and returns the users response in the `Result`<xref:System.Activities.OutArgument%601>\<string>.</span></span> <span data-ttu-id="d710f-109">L'activité `Prompt` utilise les activités <xref:System.Activities.Statements.Sequence> et <xref:System.Activities.Statements.WriteLine> fournies dans le cadre du .NET Framework, et incorpore également l'activité `ReadLine` personnalisée pour l'obtention de l'entrée d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d710f-109">The `Prompt` activity uses the <xref:System.Activities.Statements.Sequence> and <xref:System.Activities.Statements.WriteLine> activities that ship as part of the .NET Framework, and also incorporates the custom `ReadLine` activity for getting user input.</span></span> <span data-ttu-id="d710f-110">La dernière activité personnalisée est l'activité `Survey`.</span><span class="sxs-lookup"><span data-stu-id="d710f-110">The last custom activity is the `Survey` activity.</span></span> <span data-ttu-id="d710f-111">Il s’agit d’un <xref:System.Activities.Activity>< ICollection\<chaîne >>.</span><span class="sxs-lookup"><span data-stu-id="d710f-111">It is an <xref:System.Activities.Activity><ICollection\<string>>.</span></span>  <span data-ttu-id="d710f-112">Cette activité prend une <xref:System.Activities.InArgument%601>< IEnumerable < chaîne\>> nommé `Questions` et remplit la `Result` des arguments avec les réponses.</span><span class="sxs-lookup"><span data-stu-id="d710f-112">This activity takes an <xref:System.Activities.InArgument%601><IEnumerable<string\>> named `Questions` and populates the `Result` out argument with the responses.</span></span> <span data-ttu-id="d710f-113">L'activité `Survey` utilise <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> et <xref:System.Activities.Statements.AddToCollection%601> du .NET Framework et emploie l'activité `Prompt` pour poser les questions de l'enquête et obtenir des réponses.</span><span class="sxs-lookup"><span data-stu-id="d710f-113">The `Survey` activity uses <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> and <xref:System.Activities.Statements.AddToCollection%601> from the .NET Framework and employs the `Prompt` activity for asking the survey questions and getting responses.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d710f-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="d710f-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d710f-115">Ouvrez le **BasicActivityComposition.sln** exemple de solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d710f-115">Open the **BasicActivityComposition.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d710f-116">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="d710f-116">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d710f-117">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d710f-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d710f-118">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d710f-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d710f-119">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d710f-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d710f-120">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d710f-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`