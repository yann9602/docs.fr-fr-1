---
title: Validation de base
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d388b3d6acad28e4ff952f72aa64a607d745f307
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-validation"></a><span data-ttu-id="f97cb-102">Validation de base</span><span class="sxs-lookup"><span data-stu-id="f97cb-102">Basic Validation</span></span>
<span data-ttu-id="f97cb-103">Cet exemple se compose d'une activité, `CreateProduct`, qui valide que son argument `Cost` est plus petit ou égal à son argument `Price`.</span><span class="sxs-lookup"><span data-stu-id="f97cb-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="f97cb-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="f97cb-104">Sample Details</span></span>  
 <span data-ttu-id="f97cb-105">Deux auteurs utilisent la validation, l'auteur d'activité (qui crée la logique de validation pour l'activité) et l'auteur de workflow qui appelle des services de validation sur un workflow spécifique.</span><span class="sxs-lookup"><span data-stu-id="f97cb-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="f97cb-106">Dans ce scénario, l'auteur d'activité souhaite faire en sorte que chaque instance de son activité ait un coût inférieur ou égal au prix.</span><span class="sxs-lookup"><span data-stu-id="f97cb-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="f97cb-107">L'auteur d'activité (à l'intérieur de l'activité) doit effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f97cb-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="f97cb-108">Créer une contrainte (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="f97cb-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="f97cb-109">Il s'agit de l'emplacement de toute la logique de validation.</span><span class="sxs-lookup"><span data-stu-id="f97cb-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="f97cb-110">Substituer `System.Activities.CodeActivity.OnGetConstraints()` et ajouter la contrainte (`PriceGreaterThanCost`) aux contraintes <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="f97cb-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="f97cb-111">L'auteur de workflow (programme principal) doit effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f97cb-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="f97cb-112">Créer un workflow avec une instance de l'activité à valider (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="f97cb-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="f97cb-113">Appeler <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, qui retourne une collection <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="f97cb-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="f97cb-114">(Facultatif) Imprimer les objets <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="f97cb-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f97cb-115">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f97cb-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f97cb-116">Ouvrez l'exemple de solution BasicValidation.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f97cb-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f97cb-117">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="f97cb-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f97cb-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f97cb-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f97cb-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f97cb-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f97cb-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f97cb-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f97cb-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f97cb-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`  
  
## <a name="see-also"></a><span data-ttu-id="f97cb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f97cb-122">See Also</span></span>
