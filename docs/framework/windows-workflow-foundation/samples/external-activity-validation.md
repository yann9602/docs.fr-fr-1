---
title: "Validation d’activité externe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f45d4ffc04b206db0dfefbdbbe683146e09c767f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="external-activity-validation"></a><span data-ttu-id="9eced-102">Validation d’activité externe</span><span class="sxs-lookup"><span data-stu-id="9eced-102">External Activity Validation</span></span>
<span data-ttu-id="9eced-103">Cet exemple montre comment ajouter une logique de validation à une activité intégrée dont vous n’êtes pas l’auteur.</span><span class="sxs-lookup"><span data-stu-id="9eced-103">This sample shows how to add validation logic to a built-in activity that you are not the author of.</span></span> <span data-ttu-id="9eced-104">La logique de validation consiste à garantir que soit la propriété <xref:System.Activities.Statements.If>, soit la propriété <xref:System.Activities.Statements.If.Then%2A> de toutes les activités <xref:System.Activities.Statements.If.Else%2A> présentes dans le workflow soit définie.</span><span class="sxs-lookup"><span data-stu-id="9eced-104">The validation logic consists of enforcing that all <xref:System.Activities.Statements.If> activities present in the workflow either have their <xref:System.Activities.Statements.If.Then%2A> property set or their <xref:System.Activities.Statements.If.Else%2A> property set.</span></span> <span data-ttu-id="9eced-105">De plus, la logique de validation vérifie que toutes les activités <xref:System.Activities.Statements.Pick> présentes dans le workflow ont plusieurs branches, et si ce n'est pas le cas, un avertissement est généré.</span><span class="sxs-lookup"><span data-stu-id="9eced-105">Also, the validation logic includes checking that all <xref:System.Activities.Statements.Pick> activities present in the workflow have more than one branch, and if that is not the case, a warning is generated.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="9eced-106">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="9eced-106">Sample details</span></span>  
 <span data-ttu-id="9eced-107">Cet exemple crée un workflow avec une instance de chaque activité à valider : l'activité <xref:System.Activities.Statements.If> et l'activité <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="9eced-107">This sample creates a workflow with an instance of each activity to validate: the <xref:System.Activities.Statements.If> activity and the <xref:System.Activities.Statements.Pick> activity.</span></span> <span data-ttu-id="9eced-108">Un <xref:System.Activities.Validation.Constraint> est créé pour chaque comportement de validation.</span><span class="sxs-lookup"><span data-stu-id="9eced-108">A <xref:System.Activities.Validation.Constraint> is created for each validation behavior.</span></span> <span data-ttu-id="9eced-109">Les contraintes créées dans cet exemple sont `ConstraintError_IfShouldHaveThenOrElse` et `ConstraintWarning_PickHasOneBranch`.</span><span class="sxs-lookup"><span data-stu-id="9eced-109">The constraints created in this sample are `ConstraintError_IfShouldHaveThenOrElse` and `ConstraintWarning_PickHasOneBranch`.</span></span> <span data-ttu-id="9eced-110">Ces contraintes sont ensuite ajoutées à la collection `AdditionalConstraints` d'une instance <xref:System.Activities.Validation.ValidationSettings>.</span><span class="sxs-lookup"><span data-stu-id="9eced-110">Next, these constraints are added to the `AdditionalConstraints` collection of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="9eced-111">Enfin, la méthode `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> de <xref:System.Activities.Validation.ActivityValidationServices> est appelée pour valider les activités dans le workflow et les résultats de la validation sont imprimés sur la console.</span><span class="sxs-lookup"><span data-stu-id="9eced-111">Finally, the `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> method of <xref:System.Activities.Validation.ActivityValidationServices> is called to validate the activities in the workflow and the validation results are printed out to the console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9eced-112">Vous pouvez ajouter des contraintes de stratégie à toute activité.</span><span class="sxs-lookup"><span data-stu-id="9eced-112">You can add policy constraints to any activity.</span></span> <span data-ttu-id="9eced-113">Par exemple, vous pouvez ajouter une contrainte de stratégie à une activité <xref:System.Activities.Statements.Sequence> ou <xref:System.Activities.Statements.Parallel>.</span><span class="sxs-lookup"><span data-stu-id="9eced-113">For example, you can add a policy constraint to a <xref:System.Activities.Statements.Sequence> or <xref:System.Activities.Statements.Parallel> activity.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9eced-114">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="9eced-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="9eced-115">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier ExternalActivityValidation.sln.</span><span class="sxs-lookup"><span data-stu-id="9eced-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExternalActivityValidation.sln file.</span></span>  
  
2.  <span data-ttu-id="9eced-116">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="9eced-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9eced-117">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="9eced-117">To run the solution, press Ctrl+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9eced-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9eced-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9eced-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="9eced-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9eced-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9eced-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9eced-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="9eced-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`