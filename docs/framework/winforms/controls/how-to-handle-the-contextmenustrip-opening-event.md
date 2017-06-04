---
title: "Comment&#160;: g&#233;rer l&#39;&#233;v&#233;nement d&#39;ouverture ContextMenuStrip | Microsoft Docs"
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
  - "menus contextuels, gestion des événements"
  - "ContextMenuStrip (contrôle Windows Forms)"
  - "gestion des événements, menus contextuels"
  - "menus contextuels, gestion des événements"
  - "ToolStrip (contrôle Windows Forms)"
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: g&#233;rer l&#39;&#233;v&#233;nement d&#39;ouverture ContextMenuStrip
Vous pouvez personnaliser le comportement de votre contrôle <xref:System.Windows.Forms.ContextMenuStrip> en gérant l'événement <xref:System.Windows.Forms.ToolStripDropDown.Opening>.  
  
## Exemple  
 L'exemple de code suivant montre comment gérer l'événement <xref:System.Windows.Forms.ToolStripDropDown.Opening>.  Le gestionnaire d'événements ajoute des éléments dynamiquement à un contrôle <xref:System.Windows.Forms.ContextMenuStrip>.  Pour obtenir l'exemple de code complet, consultez [Comment : ajouter dynamiquement des éléments ToolStrip](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Donnez à la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=fullName> la valeur `true` pour empêcher le menu de s'ouvrir.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>   
 <xref:System.Windows.Forms.ToolStripDropDown>   
 [ToolStrip, contrôle](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)