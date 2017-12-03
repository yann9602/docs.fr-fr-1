---
title: "Groupe de l'activité conditionnée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0df4ddc6f2cc5404c8153b30df66cda41487691
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="79bb7-102">Groupe de l'activité conditionnée</span><span class="sxs-lookup"><span data-stu-id="79bb7-102">Conditioned Activity Group</span></span>
<span data-ttu-id="79bb7-103">L'exemple illustre une application de réservation de voyages.</span><span class="sxs-lookup"><span data-stu-id="79bb7-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="79bb7-104">Le <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) comporte deux activités de code : une activité de type voiture et une autre de type compagnie aérienne.</span><span class="sxs-lookup"><span data-stu-id="79bb7-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="79bb7-105">Dans le constructeur `SimpleCAGWorkflow`, un objet ArrayList "travelNeedType" est défini avec les types de réservations de voyage requises.</span><span class="sxs-lookup"><span data-stu-id="79bb7-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="79bb7-106">En supprimant l'une ou les deux instructions `travelNeeds.Add`, vous modifiez le comportement du CAG en conséquence.</span><span class="sxs-lookup"><span data-stu-id="79bb7-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="79bb7-107">À la fois, les activités voiture et compagnie aérienne ont leur condition <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> définie avec <xref:System.Workflow.Activities.CodeCondition>.</span><span class="sxs-lookup"><span data-stu-id="79bb7-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="79bb7-108">L'activité Car s'exécute uniquement si la collection `travelNeeds` comporte une entrée `TravelNeeds.Car`, l'activité Airline s'exécute uniquement si la collection `travelNeeds` comporte une entrée `TravelNeeds.Airline`.</span><span class="sxs-lookup"><span data-stu-id="79bb7-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="79bb7-109">L'exécution de chaque activité supprime l'entrée correspondante de la collection.</span><span class="sxs-lookup"><span data-stu-id="79bb7-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="79bb7-110">La condition <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> par défaut spécifie que le CAG doit se terminer lorsque aucun enfant ne s'exécute ou n'est prêt pour l'exécution (selon leurs conditions <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>).</span><span class="sxs-lookup"><span data-stu-id="79bb7-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="79bb7-111">Dans cet exemple, cela signifie que le CAG se termine lorsque la collection `travelNeeds` est vide.</span><span class="sxs-lookup"><span data-stu-id="79bb7-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="79bb7-112">Pour générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="79bb7-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="79bb7-113">Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79bb7-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="79bb7-114">Générez la solution en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="79bb7-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="79bb7-115">Exécutez la solution sans débogage en appuyant sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="79bb7-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="79bb7-116">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="79bb7-116">To run the sample</span></span>  
  
-   <span data-ttu-id="79bb7-117">Dans la fenêtre Invite de commandes du Kit de développement logiciel (SDK), exécutez le fichier .exe dans le dossier SimpleCAG\bin\debug (ou le dossier SimpleCAG\bin pour la version Visual Basic de l'exemple), situé sous le dossier principal de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="79bb7-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="79bb7-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="79bb7-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="79bb7-119">Recherchez le répertoire (par défaut) suivant avant de continuer :</span><span class="sxs-lookup"><span data-stu-id="79bb7-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="79bb7-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="79bb7-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79bb7-121">Cet exemple se trouve dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="79bb7-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="79bb7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79bb7-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
