---
title: "Procédure : créer un workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b20ca4258204f938d611f431abc5668b88f167b1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="3b372-102">Procédure : créer un workflow</span><span class="sxs-lookup"><span data-stu-id="3b372-102">How to: Create a Workflow</span></span>
<span data-ttu-id="3b372-103">Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="3b372-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="3b372-104">Les rubriques de cette étape de la section dans la création d’un flux de travail qui utilise les deux activités intégrées, telles que la <xref:System.Activities.Statements.Flowchart> activité et les activités personnalisées à partir de la précédente [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="3b372-104">This topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="3b372-105">Le workflow modélise un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="3b372-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="3b372-106">Une seule des rubriques de cette section est nécessaire pour terminer le didacticiel ; vous devez choisir le style qui vous intéresse et suivre cette étape.</span><span class="sxs-lookup"><span data-stu-id="3b372-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="3b372-107">Toutefois, vous pouvez terminer toutes les rubriques si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="3b372-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b372-108">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="3b372-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="3b372-109">Pour terminer cette rubrique, vous devez d’abord terminer [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="3b372-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b372-110">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="3b372-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b372-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3b372-111">In This Section</span></span>  
 [<span data-ttu-id="3b372-112">Guide pratique pour créer un workflow séquentiel</span><span class="sxs-lookup"><span data-stu-id="3b372-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="3b372-113">Décrit comment créer un workflow séquentiel à l'aide de l'activité <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="3b372-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="3b372-114"> d’organigramme</span><span class="sxs-lookup"><span data-stu-id="3b372-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="3b372-115">Décrit comment créer un workflow d'organigramme à l'aide de l'activité <xref:System.Activities.Statements.Flowchart>.</span><span class="sxs-lookup"><span data-stu-id="3b372-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="3b372-116">Guide pratique pour créer un workflow de machine à états</span><span class="sxs-lookup"><span data-stu-id="3b372-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="3b372-117">Décrit comment créer un workflow de machine à états à l'aide de l'activité <xref:System.Activities.Statements.StateMachine>.</span><span class="sxs-lookup"><span data-stu-id="3b372-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b372-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b372-118">See Also</span></span>  
 [<span data-ttu-id="3b372-119">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="3b372-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
