---
title: "Comment&#160;: configurer la fusion de menus automatique pour les applications MDI | Microsoft Docs"
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
  - "MenuStrip, fusionner"
  - "fusion, de menus automatique"
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: configurer la fusion de menus automatique pour les applications MDI
La procédure suivante indique les étapes de base pour configurer la fusion automatique dans une application d'interface multidocument \(MDI\) avec un <xref:System.Windows.Forms.MenuStrip>.  
  
### Pour configurer la fusion de menus automatique  
  
1.  Créez le formulaire parent MDI en affectant à sa propriété <xref:System.Windows.Forms.Form.IsMdiContainer%2A> la valeur `true`.  
  
2.  Ajoutez un <xref:System.Windows.Forms.MenuStrip> au parent MDI, en définissant sa propriété <xref:System.Windows.Forms.Form.MainMenuStrip%2A> en fonction de ce <xref:System.Windows.Forms.MenuStrip>.  
  
3.  Créez un formulaire enfant MDI et affectez à sa propriété <xref:System.Windows.Forms.Form.MdiParent%2A> le nom du formulaire parent.  
  
4.  Ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire enfant MDI.  
  
5.  Sur le formulaire enfant, affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.Visible%2A> de <xref:System.Windows.Forms.MenuStrip> la valeur `false`.  
  
6.  Ajoutez des éléments de menu à la classe <xref:System.Windows.Forms.MenuStrip> du formulaire enfant que vous souhaitez fusionner avec la classe <xref:System.Windows.Forms.MenuStrip> du formulaire parent lorsque le formulaire enfant est activé.  
  
7.  Utilisez la propriété <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> des éléments de menu dans la classe <xref:System.Windows.Forms.MenuStrip> du formulaire enfant pour contrôler leur fusion dans le formulaire parent.  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)