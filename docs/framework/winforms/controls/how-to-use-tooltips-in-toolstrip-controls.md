---
title: "Comment&#160;: utiliser des info-bulles dans des contr&#244;les ToolStrip | Microsoft Docs"
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
  - "barres d'outils (Windows Forms), ajouter des info-bulles"
  - "ToolStrip (contrôle Windows Forms), ajouter des info-bulles"
  - "info-bulles (Windows Forms), ajouter"
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: utiliser des info-bulles dans des contr&#244;les ToolStrip
Vous pouvez afficher <xref:System.Windows.Forms.ToolTip> pour le contrôle <xref:System.Windows.Forms.ToolStrip> de votre choix en affectant à la propriété <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> du contrôle la valeur `true`.  
  
### Pour afficher une info\-bulle  
  
-   Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> du contrôle la valeur `true`.  
  
     La valeur par défaut de <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=fullName> est `true`, et la valeur par défaut de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=fullName> et de <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=fullName> est `false`.  
  
### Pour utiliser la propriété ToolTipText pour le texte d'info\-bulle d'un ToolStripButton  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> du bouton la valeur `true`.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=fullName> du bouton la valeur `false`.  
  
     La propriété `AutoToolTip` a par défaut la valeur `true` pour <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton> et <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     <xref:System.Windows.Forms.ToolStripButton> utilise par défaut sa propriété `Text` pour le texte <xref:System.Windows.Forms.ToolTip>.  Utilisez cette procédure pour afficher un texte personnalisé dans <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Si vous affectez à <xref:System.Windows.Forms.ToolStripItemDisplayStyle> la valeur <xref:System.Windows.Forms.ToolStripItemDisplayStyle> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle>, aucun texte ne figure sur le bouton, mais l'info\-bulle s'affiche néanmoins.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>   
 <xref:System.Windows.Forms.ToolStripButton>   
 <xref:System.Windows.Forms.ToolStripDropDownButton>   
 <xref:System.Windows.Forms.ToolStripSplitButton>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)