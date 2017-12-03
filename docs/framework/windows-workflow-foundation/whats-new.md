---
title: "Quel &#39; nouveauté dans Windows Workflow Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38471f3b41f636a8294c4e240d452361c969ac58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="what39s-new-in-windows-workflow-foundation"></a>Quel &#39; nouveauté dans Windows Workflow Foundation
[!INCLUDE[wf](../../../includes/wf-md.md)] dans [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] modifie plusieurs paradigmes de développement des versions précédentes. Les flux de travail sont désormais plus faciles à créer, à exécuter et à gérer et mettent en œuvre de nombreuses nouvelles fonctionnalités. [!INCLUDE[crabout](../../../includes/crabout-md.md)]migration de .NET 3.0 et 3.5 de .NET des applications de workflow à utiliser la version la plus récente, consultez [conseils de Migration](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>Modèle de l'activité de workflow  
 L'activité est désormais l'unité de base de création d'un flux de travail qui n'est plus créé à l'aide des classes <xref:System.Workflow.Activities.SequentialWorkflowActivity> ou <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. La classe <xref:System.Activities.Activity> fournit l'abstraction de base de comportement de workflow. Les auteurs d'activités peuvent ensuite implémenter <xref:System.Activities.CodeActivity> pour les fonctionnalités d'activités personnalisées de base, ou <xref:System.Activities.NativeActivity> pour les fonctionnalités d'activités personnalisées qui utilisent la portée du runtime. <xref:System.Activities.Activity>est une classe utilisée par les auteurs d’activités pour exprimer les nouveaux comportements de manière déclarative en termes d’autres <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ou <xref:System.Activities.DynamicActivity> d’objets, qu’ils soient personnalisées ou inclus dans le [activités intégrée Bibliothèque](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Options d'activité composite étendues  
 Grâce à la nouvelle et puissante activité de flux de contrôle <xref:System.Activities.Statements.Flowchart>, les auteurs peuvent modéliser des boucles arbitraires et la création de branches conditionnelles. <xref:System.Activities.Statements.Flowchart> fournit un modèle événementiel de programmation qui ne pouvait précédemment être implémenté qu'avec la classe <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. Les flux de travail procéduraux bénéficient de nouvelles activités de contrôle de flux comme <xref:System.Activities.Statements.TryCatch> et <xref:System.Activities.Statements.Switch%601> qui modélisent les structures classiques de contrôle de flux.  
  
## <a name="expanded-built-in-activity-library"></a>Bibliothèque d'activités intégrée étendue  
 Les nouvelles fonctionnalités de la bibliothèque d'activités sont les suivantes :  
  
-   nouvelles activités de contrôle de flux comme <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601> et <xref:System.Activities.Statements.ParallelForEach%601> ;  
  
-   activités pour la manipulation des données membres comme <xref:System.Activities.Statements.Assign> et activités de collection comme <xref:System.Activities.Statements.AddToCollection%601> ;  
  
-   activités pour le contrôle de transactions comme <xref:System.Activities.Statements.TransactionScope> et <xref:System.Activities.Statements.Compensate> ;  
  
-   nouvelles activités de messagerie comme <xref:System.ServiceModel.Activities.SendContent> et <xref:System.ServiceModel.Activities.ReceiveReply>.  
  
## <a name="explicit-activity-data-model"></a>Modèle explicite de données d'activité  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] inclut de nouvelles options de stockage ou de déplacement de données. Les données peuvent être stockées dans une activité à l'aide de l'objet <xref:System.Activities.Variable>. Lors du déplacement de données vers l'intérieur et l'extérieur d'une activité, les types d'arguments spécialisés servent à déterminer quelles données de direction se déplacent. Ces types sont <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument> et <xref:System.Activities.OutArgument>. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Modèle de données Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Options d'hébergement, de persistance et de suivi améliorées  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] comporte des améliorations de persistance, dont les suivantes :  
  
-   Davantage d'options permettent d'exécuter les flux de travail, notamment les objets <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication> et <xref:System.Activities.WorkflowInvoker>.  
  
-   Les données d'état du workflow peuvent être explicitement rendues persistantes à l'aide de l'activité <xref:System.Activities.Statements.Persist>.  
  
-   Un hôte peut rendre persistant un objet <xref:System.Activities.ActivityInstance> sans le décharger.  
  
-   Un flux de travail peut spécifier des zones sans persistance, tout en utilisant des données qui ne peuvent pas être rendues persistantes. De cette façon, la persistance est reportée jusqu'à la fermeture de la zone sans persistance.  
  
-   Les transactions peuvent être passées dans un flux de travail à l'aide de l'objet <xref:System.Activities.Statements.TransactionScope>.  
  
-   L'objet <xref:System.Activities.Tracking.TrackingParticipant> facilite le suivi.  
  
-   L'objet <xref:System.Activities.Tracking.EtwTrackingParticipant> offre le suivi dans le journal des événements système.  
  
-   La reprise d'un flux de travail en attente est désormais gérée à l'aide d'un objet <xref:System.Activities.Bookmark>.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Meilleure capacité à étendre l'expérience du concepteur WF  
 Le nouveau concepteur WF repose sur [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] et fournit un modèle plus facile à utiliser lors du réhébergement du concepteur WF en dehors de Visual Studio, ainsi que des mécanismes simplifiés de création de concepteurs d'activités personnalisées. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Personnalisation de l’expérience de conception de flux de travail](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md).
