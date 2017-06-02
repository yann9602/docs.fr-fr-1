---
title: "Cr&#233;ation et ex&#233;cution d&#39;une instance de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Cr&#233;ation et ex&#233;cution d&#39;une instance de workflow
Cet exemple montre comment exécuter une instance de workflow.Il indique comment l'exécuter de façon synchrone et de façon asynchrone.  
  
## Démonstrations  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## Discussion  
 La première partie de l'exemple utilise <xref:System.Activities.WorkflowInvoker.Invoke%2A>.Il s'agit de la façon la plus simple d'exécuter un workflow.Les workflows exécutés avec <xref:System.Activities.WorkflowInvoker.Invoke%2A> s'exécutent de façon synchrone.  
  
 La deuxième partie de l'exemple utilise la classe <xref:System.Activities.WorkflowApplication>.<xref:System.Activities.WorkflowApplication> vous permet d'avoir plus de contrôle sur chaque instance, notamment la possibilité d'interagir avec le workflow en cours d'exécution et d'exécuter le workflow de façon asynchrone.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## Voir aussi  
 [Utilisation de WorkflowInvoker et WorkflowApplication](../../../../docs/framework/windows-workflow-foundation//using-workflowinvoker-and-workflowapplication.md)