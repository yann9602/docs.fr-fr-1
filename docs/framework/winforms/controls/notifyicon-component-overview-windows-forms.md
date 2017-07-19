---
title: "Vue d&#39;ensemble du composant NotifyIcon (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NotifyIcon"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "NotifyIcon (composant), à propos du composant NotifyIcon"
  - "icônes de la barre d'état système, à propos des icônes de la barre d'état système"
  - "icônes de la barre d'état système, utiliser dans les Windows Forms"
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble du composant NotifyIcon (Windows Forms)
Le composant Windows Forms <xref:System.Windows.Forms.NotifyIcon> est généralement utilisé pour afficher des icônes pour les processus qui s'exécutent en arrière\-plan et n'affichent pas d'interface utilisateur la plupart du temps.  En guise d'exemple, on pourrait citer un programme antivirus accessible en cliquant sur une icône dans la zone de notification d'état de la barre des tâches.  
  
## Principales propriétés de NotifyIcons  
 Chaque composant <xref:System.Windows.Forms.NotifyIcon> affiche une seule icône dans la zone d'état.  Si vous avez trois processus d'arrière\-plan et que vous voulez afficher une icône pour chacun d'eux, vous devez ajouter trois composants <xref:System.Windows.Forms.NotifyIcon> au formulaire.  Les principales propriétés du composant <xref:System.Windows.Forms.NotifyIcon> sont <xref:System.Windows.Forms.NotifyIcon.Icon%2A> et <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.  La propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A> définit l'icône affichée dans la zone d'état.  Pour que cette icône s'affiche, la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> doit avoir la valeur `true`.  
  
 Si vous utilisez [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], vous avez accès à une grande bibliothèque d'images standard que vous pouvez utiliser avec le contrôle <xref:System.Windows.Forms.NotifyIcon>.  
  
## Options de NotifyIcons  
 Vous pouvez associer des info\-bulles et des menus contextuels à un <xref:System.Windows.Forms.NotifyIcon> pour aider l'utilisateur.  
  
 Vous pouvez afficher des info\-bulles pour un <xref:System.Windows.Forms.NotifyIcon> en appelant la méthode <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> en spécifiant la durée d'affichage souhaitée pour l'info\-bulle.  Vous pouvez également spécifier le texte, l'icône et le titre de l'info\-bulle avec les propriétés <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> et <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectivement.  Vous pouvez aussi associer des info\-bulles et des menus contextuels à des composants <xref:System.Windows.Forms.NotifyIcon>.  Pour plus d'informations, consultez [Vue d'ensemble du composant ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) et [Vue d'ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.NotifyIcon>   
 [NotifyIcon, composant](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)