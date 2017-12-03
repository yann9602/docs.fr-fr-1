---
title: "Validation des relations des activités"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c5eb87765c3e0f708c80f2194bfd652b17bf991
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="28507-102">Validation des relations des activités</span><span class="sxs-lookup"><span data-stu-id="28507-102">Activity Relationships Validation</span></span>
<span data-ttu-id="28507-103">Cet exemple se compose de trois activités, `CreateCity`, `CreateState` et `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="28507-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="28507-104">`CreateCity` doit être à l'intérieur d'une activité `CreateState`, et `CreateState` à l'intérieur d'une activité `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="28507-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="28507-105">Pour les besoins de cet exemple, la logique de validation est dans le code pour l'activité `CreateState`, et dans XAML pour l'activité `CreateCity`.</span><span class="sxs-lookup"><span data-stu-id="28507-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="28507-106">Les deux contraintes ont le même comportement.</span><span class="sxs-lookup"><span data-stu-id="28507-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="28507-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fournit les trois activités d'assistance suivantes qui permettent au développeur de valider les relations entre les activités :</span><span class="sxs-lookup"><span data-stu-id="28507-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="28507-108">Fournit la collection de toutes les activités qui appartiennent au parent du nœud actuel</span><span class="sxs-lookup"><span data-stu-id="28507-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="28507-109">Fournit la collection de toutes les activités qui appartiennent à la sous-arborescence du nœud actuel, à l'exclusion du nœud actuel</span><span class="sxs-lookup"><span data-stu-id="28507-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="28507-110">Fournit la collection de toutes les activités de la même arborescence que le nœud actuel</span><span class="sxs-lookup"><span data-stu-id="28507-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="28507-111">Dans l'exemple, une activité <xref:System.Activities.Statements.ForEach%601> est utilisée pour parcourir la collection retournée par <xref:System.Activities.Validation.GetParentChain></span><span class="sxs-lookup"><span data-stu-id="28507-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="28507-112">Pour chaque élément de la collection, son type est comparé à `CreateCountry` (ou à `CreateState` si `CreateCity` est validé). Une fois que qu'une correspondance est trouvée, l'indicateur de résultat a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="28507-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="28507-113">Enfin, un <xref:System.Activities.Validation.AssertValidation> est utilisé pour générer une erreur de validation si l'indicateur de résultat a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="28507-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="28507-114">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="28507-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="28507-115">Ouvrez l'exemple de solution ContainmentValidation.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28507-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="28507-116">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="28507-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="28507-117">Appuyez sur Ctrl+F5 pour lancer le programme.</span><span class="sxs-lookup"><span data-stu-id="28507-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28507-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28507-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="28507-119">Recherchez le répertoire (par défaut) suivant avant de continuer :</span><span class="sxs-lookup"><span data-stu-id="28507-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="28507-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="28507-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28507-121">Cet exemple se trouve dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="28507-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
