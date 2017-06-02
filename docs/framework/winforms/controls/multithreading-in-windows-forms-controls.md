---
title: "Multithreading dans les contr&#244;les Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "BackgroundWorker (composant)"
  - "BeginInvoke (méthode)"
  - "threads (Windows Forms), contrôles"
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Multithreading dans les contr&#244;les Windows Forms
Dans beaucoup d'applications, vous pouvez rendre votre interface utilisateur plus réactive en exécutant les opérations qui prennent du temps sur un autre thread.  Plusieurs outils sont disponibles pour traiter vos contrôles Windows Forms en multithreading, y compris l'espace de noms <xref:System.Threading>, la méthode <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=fullName> et le composant `BackgroundWorker`.  
  
> [!NOTE]
>  Le composant `BackgroundWorker` remplace et ajoute des fonctionnalités à l'espace de noms <xref:System.Threading> et à la méthode <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=fullName> ; toutefois, ceux\-ci sont conservés pour la compatibilité descendante et une utilisation ultérieure, si tel est votre choix.  Pour plus d'informations, consultez [Vue d'ensemble du composant BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).  
  
## Dans cette section  
 [Comment : faire des appels thread\-safe aux contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Indique comment faire des appels thread\-safe aux contrôles Windows Forms.  
  
 [Comment : utiliser un thread d'arrière\-plan pour rechercher des fichiers](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 Indique comment utiliser l'espace de noms <xref:System.Threading> et la méthode <xref:System.Windows.Forms.Control.BeginInvoke%2A> pour rechercher des fichiers de façon asynchrone.  
  
## Référence  
 <xref:System.ComponentModel.BackgroundWorker>  
 Documente un composant qui encapsule un thread de travail pour les opérations asynchrones.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Documente comment charger un son de manière asynchrone.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Documente comment charger une image de manière asynchrone.  
  
## Rubriques connexes  
 [Comment : exécuter une opération en arrière\-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 Indique comment exécuter une opération prenant du temps avec le composant <xref:System.ComponentModel.BackgroundWorker>.  
  
 [Vue d'ensemble du composant BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 Fournit des rubriques qui décrivent comment utiliser le composant <xref:System.ComponentModel.BackgroundWorker> pour des opérations asynchrones.