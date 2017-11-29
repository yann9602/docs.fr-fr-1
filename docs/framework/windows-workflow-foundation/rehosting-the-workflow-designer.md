---
title: "Réhébergement du Workflow Designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e5ca7eec49dec0e9b8896b31147a3cd40ffeef5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="ee3bc-102">Réhébergement du Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="ee3bc-102">Rehosting the Workflow Designer</span></span>
<span data-ttu-id="ee3bc-103">[!INCLUDE[wfd1](../../../includes/wfd1-md.md)] peut être réhébergé dans des environnements en dehors de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] afin de pouvoir créer, modifier et surveiller des workflows.</span><span class="sxs-lookup"><span data-stu-id="ee3bc-103">The [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] can be rehosted in environments outside of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] for the purposes of creating, modifying, and monitoring workflows.</span></span>  
  
 <span data-ttu-id="ee3bc-104">Le type <xref:System.Activities.Presentation.WorkflowDesigner> est un wrapper de la zone de dessin, de la grille des propriétés et d'autres éléments, et expose un modèle de programmation de base conçu pour gérer la majorité des scénarios de réhébergement du concepteur.</span><span class="sxs-lookup"><span data-stu-id="ee3bc-104">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="ee3bc-105">L'hébergement du <xref:System.Activities.Presentation.WorkflowDesigner> à l'intérieur d'une application [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] est un scénario de réhébergement commun pour [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee3bc-105">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application is a common rehosting scenario for [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee3bc-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ee3bc-106">In This Section</span></span>  
 [<span data-ttu-id="ee3bc-107">Tâche 1 : Créer une nouvelle application Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="ee3bc-107">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
  
 [<span data-ttu-id="ee3bc-108">Tâche 2 : Héberger le concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="ee3bc-108">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)  
  
 [<span data-ttu-id="ee3bc-109">Tâche 3 : Créer les volets Toolbox et PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="ee3bc-109">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)  
  
 [<span data-ttu-id="ee3bc-110">Prise en charge des nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de flux de travail réhébergé</span><span class="sxs-lookup"><span data-stu-id="ee3bc-110">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee3bc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee3bc-111">See Also</span></span>  
 [<span data-ttu-id="ee3bc-112">Personnalisation de l’expérience de conception de workflow</span><span class="sxs-lookup"><span data-stu-id="ee3bc-112">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
