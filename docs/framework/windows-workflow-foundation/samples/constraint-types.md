---
title: Types de contraintes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d42be018b6a92237b5914c180d329138fb95e7dc
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="constraint-types"></a><span data-ttu-id="5dab6-102">Types de contraintes</span><span class="sxs-lookup"><span data-stu-id="5dab6-102">Constraint Types</span></span>
<span data-ttu-id="5dab6-103">Cet exemple illustre deux façons différentes d'appliquer des contraintes à un workflow, une à partir de l'intérieur de l'activité (génération) et l'autre à partir de l'extérieur de l'activité (stratégie).</span><span class="sxs-lookup"><span data-stu-id="5dab6-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="5dab6-104">Dans ce scénario, un auteur d'activité (d'un éditeur de logiciels tiers) souhaite valider la relation entre deux arguments.</span><span class="sxs-lookup"><span data-stu-id="5dab6-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="5dab6-105">Dans ce cas, le coût doit être inférieur ou égal au prix.</span><span class="sxs-lookup"><span data-stu-id="5dab6-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="5dab6-106">Il s'agit d'une contrainte de génération de validation générale.</span><span class="sxs-lookup"><span data-stu-id="5dab6-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="5dab6-107">Un propriétaire de magasin souhaite ensuite ajouter une validation à cette activité générique.</span><span class="sxs-lookup"><span data-stu-id="5dab6-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="5dab6-108">Dans son cas, il souhaite que le prix de la majorité de ses produits soit égal ou inférieur à 9,99 $.</span><span class="sxs-lookup"><span data-stu-id="5dab6-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="5dab6-109">Il utilise ainsi une contrainte de stratégie qui est au-dessus de l'activité `CreateProduct`.</span><span class="sxs-lookup"><span data-stu-id="5dab6-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="5dab6-110">Dans l'exemple :</span><span class="sxs-lookup"><span data-stu-id="5dab6-110">In the sample:</span></span>  
  
 <span data-ttu-id="5dab6-111">L'auteur d'activité (génération) doit :</span><span class="sxs-lookup"><span data-stu-id="5dab6-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="5dab6-112">Créer une contrainte (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="5dab6-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="5dab6-113">Il s'agit de l'emplacement de toute la logique de validation.</span><span class="sxs-lookup"><span data-stu-id="5dab6-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="5dab6-114">Substituer `System.Activities.CodeActivity.OnGetConstraints()` et ajouter la contrainte (`PriceGreaterThanCost`) aux contraintes <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="5dab6-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="5dab6-115">L'auteur de workflow (stratégie) doit effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5dab6-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="5dab6-116">Créer un workflow avec une instance de l'activité à valider (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="5dab6-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="5dab6-117">Créer une contrainte (`MaxPrice`).</span><span class="sxs-lookup"><span data-stu-id="5dab6-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="5dab6-118">Créer une instance <xref:System.Activities.Validation.ValidationSettings> (`validationSettings`) et ajouter la contrainte (`MaxPrice`) à la collection `AdditionalConstraints`.</span><span class="sxs-lookup"><span data-stu-id="5dab6-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="5dab6-119">Ici, l'auteur de workflow peut ajouter des contraintes de stratégie à toute activité, telle qu'une séquence ou un parallèle.</span><span class="sxs-lookup"><span data-stu-id="5dab6-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="5dab6-120">Appeler <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, qui retourne une collection <xref:System.Activities.Validation.ValidationResults> d'objets <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="5dab6-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="5dab6-121">(Facultatif) Imprimer les objets <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="5dab6-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5dab6-122">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5dab6-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5dab6-123">Ouvrez l'exemple de solution ConstraintTypes.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dab6-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5dab6-124">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="5dab6-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5dab6-125">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5dab6-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5dab6-126">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5dab6-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5dab6-127">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5dab6-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5dab6-128">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5dab6-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`