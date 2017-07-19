---
title: "BackgroundWorker, composant | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "modèle asynchrone"
  - "opérations d'arrière-plan"
  - "tâches en arrière-plan"
  - "BackgroundWorker (composant)"
  - "composants (Windows Forms), asynchrones"
  - "formulaires, opérations d'arrière-plan"
  - "formulaires, multithreading"
  - "threads (Windows Forms), opérations d'arrière-plan"
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# BackgroundWorker, composant
Le composant `BackgroundWorker` permet à votre formulaire ou contrôle d'exécuter une opération de façon asynchrone.  
  
## Dans cette section  
 [Vue d'ensemble du composant BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 Décrit le composant `BackgroundWorker` qui vous donne la possibilité d'exécuter des opérations à longue durée d'exécution de façon asynchrone \("à l'arrière\-plan"\) sur un autre thread que le thread d'interface utilisateur principal de votre application.  
  
 [Procédure pas à pas : exécution d'une opération en arrière\-plan](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 Montre comment utiliser le composant `BackgroundWorker` dans le concepteur pour exécuter une opération à longue durée d'exécution sur un thread distinct.  
  
 [Comment : exécuter une opération en arrière\-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 Montre comment utiliser le composant `BackgroundWorker` pour exécuter une opération à longue durée d'exécution sur un thread distinct.  
  
 [Procédure pas à pas : implémentation d'un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 Crée une application à l'aide du concepteur qui effectue des calculs mathématiques de manière asynchrone.  
  
 [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 Crée une application qui effectue des calculs mathématiques de façon asynchrone.  
  
 [Comment : télécharger un fichier en arrière\-plan](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 Montre comment utiliser le composant `BackgroundWorker` pour télécharger un fichier sur un thread distinct.  
  
## Référence  
 <xref:System.ComponentModel.BackgroundWorker>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 Décrit le type qui contient les données pour l'événement <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>.  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 Décrit le type qui contient les données pour l'événement <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>.  
  
## Rubriques connexes  
 [Event\-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 Décrit comment le modèle asynchrone permet de profiter des avantages des applications multithread tout en masquant de nombreux problèmes complexes inhérents à la conception multithread.