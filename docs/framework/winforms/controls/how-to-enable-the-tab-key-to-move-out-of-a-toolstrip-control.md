---
title: "Comment&#160;: activer la touche TAB pour sortir d&#39;un contr&#244;le ToolStrip | Microsoft Docs"
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
  - "contrôles (Windows Forms), naviguer entre"
  - "touche TAB, activer"
  - "ToolStrip (contrôle Windows Forms), naviguer depuis"
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: activer la touche TAB pour sortir d&#39;un contr&#244;le ToolStrip
Utilisez la procédure suivante pour permettre à l'utilisateur d'appuyer sur la touche TAB pour sortir de <xref:System.Windows.Forms.ToolStrip> et accéder au contrôle suivant dans l'ordre de tabulation.  
  
 <xref:System.Windows.Forms.ToolStrip> accepte la première pression sur la touche TAB et les touches de direction sélectionnent des éléments dans <xref:System.Windows.Forms.ToolStrip>.  Lorsque l'utilisateur appuie une deuxième fois sur la touche TAB, il accède au contrôle suivant dans l'ordre de tabulation.  
  
### Pour permettre à l'utilisateur d'appuyer sur la touche TAB pour passer d'un contrôle ToolStrip au contrôle suivant  
  
-   Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.TabStop%2A> de <xref:System.Windows.Forms.ToolStrip> la valeur `true`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)