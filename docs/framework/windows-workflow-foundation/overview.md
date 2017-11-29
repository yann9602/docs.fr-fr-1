---
title: Vue d'ensemble de Windows Workflow
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f60d5a7fb0bcc1f38fda470e5f44938fc0fa011f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-workflow-overview"></a>Vue d'ensemble de Windows Workflow
Un flux de travail est un ensemble d’unités élémentaires appelé *activités* qui sont stockés sous la forme d’un modèle qui décrit un processus réel. Les workflows offrent un moyen de décrire l'ordre d'exécution et les relations de dépendance entre des éléments de travail de courte ou longue durée. Ce travail s'effectue à travers le modèle de démarrage à l'arrêt et les activités peuvent être exécutées par des utilisateurs ou par les fonctions système.  
  
## <a name="workflow-run-time-engine"></a>Moteur d'exécution de workflow  
 Chaque instance de workflow en cours d'exécution est créée et gérée par un moteur d'exécution in-process avec lequel le processus hôte interagit par le biais de l'un des éléments suivants :  
  
-   Un <xref:System.Activities.WorkflowInvoker>, qui appelle le workflow comme une méthode.  
  
-   Un <xref:System.Activities.WorkflowApplication> pour contrôler explicitement l'exécution d'une instance de workflow unique.  
  
-   Un <xref:System.ServiceModel.WorkflowServiceHost> pour les interactions basées sur des messages dans les scénarios à plusieurs instances.  
  
 Chacune de ces classes encapsule le runtime de l'activité principale représenté en tant que <xref:System.Activities.ActivityInstance> responsable de l'exécution de l'activité. Un domaine d'application peut comporter plusieurs objets <xref:System.Activities.ActivityInstance> fonctionnant simultanément.  
  
 Chacun des trois objets d'interaction hôtes précédents est créé à partir d'une arborescence d'activités appelée programme de workflow. À l'aide de ces types ou d'un hôte personnalisé qui encapsule <xref:System.Activities.ActivityInstance>, les workflows peuvent être exécutés à l'intérieur de n'importe quel processus Windows, notamment des applications console, des applications basées sur les formulaires, des services Windows, des sites Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] et des services [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
 ![Composants de flux de travail dans le processus hôte](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Composants de workflow dans le processus hôte  
  
## <a name="interaction-between-workflow-components"></a>Interaction entre composants de workflow  
 Le diagramme suivant montre comment les composants de workflow interagissent les uns avec les autres.  
  
 ![Interaction de flux de travail](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")  
  
 Dans le diagramme précédent, la méthode <xref:System.Activities.WorkflowInvoker.Invoke%2A> de classe <xref:System.Activities.WorkflowInvoker> est utilisée pour appeler plusieurs instances de workflow. <xref:System.Activities.WorkflowInvoker> est utilisé pour les workflows légers ne nécessitant pas de gestion à partir de l'hôte ; les workflows qui nécessitent d'être gérés à partir de l'hôte (tel qu'une reprise <xref:System.Activities.Bookmark>) doivent être exécutés avec <xref:System.Activities.WorkflowApplication.Run%2A> à la place. Il n'est pas nécessaire d'attendre qu'une instance de workflow soit terminée avant d'en appeler une autre ; le moteur de runtime prend en charge plusieurs instances de workflow simultanément.  Les workflows appelés sont les suivants :  
  
-   Une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> enfant. <xref:System.Activities.Variable> de l'activité parente est lié à un <xref:System.Activities.InArgument> de l'activité enfant. [!INCLUDE[crabout](../../../includes/crabout-md.md)]sur les variables, arguments et la liaison, consultez [Variables et Arguments](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
-   Une activité personnalisée appelée `ReadLine`. Un <xref:System.Activities.OutArgument> de l'activité `ReadLine` est retourné à la méthode  <xref:System.Activities.WorkflowInvoker.Invoke%2A> appelante.  
  
-   Une activité personnalisée qui dérive de la classe abstraite <xref:System.Activities.CodeActivity>. Le <xref:System.Activities.CodeActivity> peut accéder aux fonctionnalités d'exécution (telles que le suivi et les propriétés) à l'aide du <xref:System.Activities.CodeActivityContext> qui est disponible en tant que paramètre de la méthode <xref:System.Activities.CodeActivity.Execute%2A>. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Ces fonctionnalités d’exécution, consultez [suivi et traçage de Workflow](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) et [propriétés d’exécution de Workflow](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Server 2006 ou WF ? Choix de l’outil de Workflow approprié pour votre projet](http://go.microsoft.com/fwlink/?LinkId=154901)
