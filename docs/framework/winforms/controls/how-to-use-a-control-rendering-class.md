---
title: "Comment&#160;: utiliser une classe de rendu des contr&#244;les | Microsoft Docs"
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
  - "aspect professionnel, rendu des contrôles Windows Forms"
  - "styles visuels, rendu des contrôles Windows Forms"
  - "thèmes visuels, appliquer aux contrôles Windows Forms"
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: utiliser une classe de rendu des contr&#244;les
Cet exemple montre comment utiliser la classe <xref:System.Windows.Forms.ComboBoxRenderer> pour restituer la flèche de déroulement d'un contrôle zone de liste déroulante.  L'exemple se compose de la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> d'un contrôle personnalisé simple.  La propriété <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=fullName> est utilisée pour déterminer si les styles visuels sont activés dans la zone cliente de fenêtres d'application.  Si les styles visuels sont actifs, la méthode <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=fullName> restituera alors la flèche de déroulement avec les styles visuels ; sinon, la méthode <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=fullName> restituera la flèche de déroulement dans le style Windows classique.  
  
## Exemple  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un contrôle personnalisé dérivé de la classe <xref:System.Windows.Forms.Control>.  
  
-   Un <xref:System.Windows.Forms.Form> qui héberge le contrôle personnalisé.  
  
-   Des références aux espaces de noms <xref:System?displayProperty=fullName>, <xref:System.Drawing?displayProperty=fullName>, <xref:System.Windows.Forms?displayProperty=fullName> et <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName>.  
  
## Voir aussi  
 [Rendu des contrôles avec les styles visuels](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)