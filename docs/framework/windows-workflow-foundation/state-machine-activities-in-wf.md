---
title: "Activit&#233;s de l&#39;ordinateur d&#39;&#233;tat dans WF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Activit&#233;s de l&#39;ordinateur d&#39;&#233;tat dans WF
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] fournit plusieurs activités et concepteurs d'activités fournis par le système pour créer des workflows de machine à états.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Exécute des activités contenues à l'aide du modèle de machine à états familier.|  
|<xref:System.Activities.Statements.State>|Représente un état au sein d'une machine à états.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Représente un état d'arrêt au sein d'une machine à états.<xref:System.Activities.Core.Presentation.FinalState> est un concepteur d'activités qui en cas d'utilisation crée un <xref:System.Activities.Statements.State> préconfiguré comme état d'arrêt.Pour plus d'informations, consultez [Concepteur d'activités FinalState](../Topic/FinalState%20Activity%20Designer.md).|  
|<xref:System.Activities.Statements.Transition>|Représente la transition entre deux états.Il n'existe aucun élément **Boîte à outils** pour <xref:System.Activities.Statements.Transition> ; les transitions sont créées sur le concepteur de workflow en faisant glisser une ligne entre deux états, ou en déposant un état sur les triangles qui s'affichent lorsqu'un état se trouve sur un autre.Pour plus d'informations, consultez [Concepteur d'activités de transition](../Topic/Transition%20Activity%20Designer.md).|  
  
## Voir aussi  
 [Didacticiel de mise en route](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)