---
title: "Vue d&#39;ensemble du composant ToolTip (Windows Forms) | Microsoft Docs"
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
  - "ToolTip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ToolTip (composant Windows Forms), à propos du composant ToolTip"
  - "info-bulles (Windows Forms), à propos des info-bulles"
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Vue d&#39;ensemble du composant ToolTip (Windows Forms)
Le composant <xref:System.Windows.Forms.ToolTip> Windows Forms affiche du texte lorsque l'utilisateur pointe sur des contrôles.  Il est possible de l'associer à n'importe quel contrôle.  Par exemple, pour économiser de la place dans un formulaire, vous pouvez afficher une petite icône sur un bouton et utiliser un composant ToolTip pour expliquer la fonction de ce bouton.  
  
## Utilisation du composant ToolTip  
 Un composant <xref:System.Windows.Forms.ToolTip> fournit une propriété `ToolTip` à plusieurs contrôles sur un Windows Form ou autre conteneur.  Par exemple, si vous placez un composant <xref:System.Windows.Forms.ToolTip> dans un formulaire, vous pouvez afficher le texte "Tapez votre nom ici" pour un contrôle <xref:System.Windows.Forms.TextBox> et "Cliquez ici pour enregistrer les modifications" pour un contrôle <xref:System.Windows.Forms.Button>.  
  
 Les principales méthodes du composant <xref:System.Windows.Forms.ToolTip> sont <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> et <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.  Vous pouvez utiliser la méthode <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> pour définir les info\-bulles affichées pour des contrôles.  Pour plus d'informations, consultez [Comment : définir des info\-bulles pour les contrôles d'un Windows Form au moment du design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).  Les propriétés clés sont <xref:System.Windows.Forms.ToolTip.Active%2A>, qui doit recevoir la valeur `true` pour que l'info\-bulle s'affiche, et <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, qui définit la durée d'affichage de la chaîne d'info\-bulle, et indique pendant combien de temps l'utilisateur doit pointer sur le contrôle pour que l'info\-bulle apparaisse, ainsi que le temps qu'il faut pour que les fenêtres d'info\-bulles suivantes pour s'affichent.  Pour plus d'informations, consultez [Comment : modifier la durée avant affichage du composant ToolTip Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolTip>   
 [Comment : définir des info\-bulles pour les contrôles d'un Windows Form au moment du design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)   
 [Comment : modifier la durée avant affichage du composant ToolTip Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)