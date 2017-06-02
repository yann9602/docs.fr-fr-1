---
title: "Comment&#160;: d&#233;tecter lorsque le pointeur de la souris est sur un ToolStripItem | Microsoft Docs"
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
  - "souris, détecter un mouvement sur les barres d'outils"
  - "barres d'outils (Windows Forms), détecter le mouvement de la souris"
  - "ToolStrip (contrôle Windows Forms), détecter le mouvement de la souris"
  - "ToolStripItem (classe), détecter le mouvement de la souris"
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: d&#233;tecter lorsque le pointeur de la souris est sur un ToolStripItem
Utilisez la procédure suivante pour détecter si le pointeur de la souris se trouve sur <xref:System.Windows.Forms.ToolStripItem>.  
  
### Pour détecter si le pointeur se trouve sur un ToolStripItem  
  
-   Utilisez la propriété <xref:System.Windows.Forms.ToolStripItem.Selected%2A> pour les éléments dans lesquels <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> a la valeur `true`.  
  
     Cela vous empêchera de devoir synchroniser les événements <xref:System.Windows.Forms.ToolStripItem.MouseEnter> et <xref:System.Windows.Forms.ToolStripItem.MouseLeave>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)