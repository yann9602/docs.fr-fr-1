---
title: Mise en route Tutorial2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc2f081411577094ea1b95c25478822a6c1747c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="8cc7b-102">Didacticiel de mise en route</span><span class="sxs-lookup"><span data-stu-id="8cc7b-102">Getting Started Tutorial</span></span>
<span data-ttu-id="8cc7b-103">Cette section présente un ensemble de rubriques de procédure pas à pas qui vous initient à la programmation d'applications [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8cc7b-103">This section contains a set of walkthrough topics that introduce you to programming [!INCLUDE[wf](../../../includes/wf-md.md)] applications.</span></span> <span data-ttu-id="8cc7b-104">En suivant les procédures dans ces rubriques, vous générerez une application qui est un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="8cc7b-105">La première rubrique du didacticiel vous guide tout au long des étapes de création des activités personnalisées obligatoires pour le workflow.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="8cc7b-106">Dans la deuxième rubrique, ces activités sont assemblées avec les activités de workflow intégrées dans un workflow d'organigramme.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="8cc7b-107">Dans la troisième rubrique, l'application hôte est configurée pour exécuter le workflow et la persistance est introduite dans la dernière rubrique.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="8cc7b-108">Chaque étape de ce processus dépendant des étapes précédentes, nous vous recommandons de les exécuter dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8cc7b-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8cc7b-109">In This Section</span></span>  
 [<span data-ttu-id="8cc7b-110">Guide pratique pour créer une activité</span><span class="sxs-lookup"><span data-stu-id="8cc7b-110">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 <span data-ttu-id="8cc7b-111">Décrit comment créer une activité personnalisée qui dérive de <xref:System.Activities.NativeActivity%601> et comment composer cette activité avec une activité intégrée dans une activité composite à l'aide du concepteur d'activités.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="8cc7b-112">Guide pratique pour créer un workflow</span><span class="sxs-lookup"><span data-stu-id="8cc7b-112">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 <span data-ttu-id="8cc7b-113">Décrit comment créer des workflows d'organigramme, séquentiels et de machine à états à l'aide des activités prédéfinies et des activités personnalisées du didacticiel précédent.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="8cc7b-114">Guide pratique pour exécuter un workflow</span><span class="sxs-lookup"><span data-stu-id="8cc7b-114">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)  
 <span data-ttu-id="8cc7b-115">Décrit comment appeler un workflow à partir d'un environnement hôte, passer des données à l'intérieur et à l'extérieur d'un workflow, et reprendre des signets.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="8cc7b-116">Guide pratique pour créer et exécuter un workflow de longue durée</span><span class="sxs-lookup"><span data-stu-id="8cc7b-116">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="8cc7b-117">Décrit comment ajouter la persistance à une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="8cc7b-118">Guide pratique pour créer un participant de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="8cc7b-118">How to: Create a Custom Tracking Participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="8cc7b-119">Décrit comment créer un participant de suivi personnalisé et un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="8cc7b-120">Guide pratique pour héberger plusieurs versions d’un workflow côte à côte</span><span class="sxs-lookup"><span data-stu-id="8cc7b-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="8cc7b-121">Décrit comment utiliser `WorkflowIdentity` pour héberger plusieurs versions d'un workflow côte à côte.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="8cc7b-122">Guide pratique pour mettre à jour la définition d’une instance de workflow en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="8cc7b-122">How to: Update the Definition of a Running Workflow Instance</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="8cc7b-123">Décrit comment utiliser la mise à jour dynamique pour modifier des instances en cours de exécution de workflow.</span><span class="sxs-lookup"><span data-stu-id="8cc7b-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc7b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cc7b-124">See Also</span></span>  
 [<span data-ttu-id="8cc7b-125">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="8cc7b-125">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
