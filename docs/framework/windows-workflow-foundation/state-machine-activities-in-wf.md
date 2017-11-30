---
title: "Activités de l'ordinateur d'état dans WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5056557c9fee74e9a16b235220c797e1f6356ce3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="state-machine-activities-in-wf"></a>Activités de l'ordinateur d'état dans WF
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] fournit plusieurs activités et concepteurs d'activités fournis par le système pour créer des workflows de machine à états.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Exécute des activités contenues à l'aide du modèle de machine à états familier.|  
|<xref:System.Activities.Statements.State>|Représente un état dans un ordinateur d'état.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Représente un état d'arrêt au sein d'une machine à états. <xref:System.Activities.Core.Presentation.FinalState> est un concepteur d'activités qui en cas d'utilisation crée un <xref:System.Activities.Statements.State> préconfiguré comme état d'arrêt. Pour plus d’informations, consultez [Concepteur d’activités FinalState](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|Représente la transition entre deux états. Il est sans **boîte à outils** d’élément pour <xref:System.Activities.Statements.Transition>; les transitions sont créées sur le Concepteur de workflow en faisant glisser une ligne entre deux États, ou en déposant un état sur les triangles qui s’affichent lorsqu’un état se trouve sur un autre . Pour plus d’informations, consultez [Concepteur d’activités Transition](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel Bien démarrer](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
