---
title: "Comment&#160;: cr&#233;er une bordure autour d&#39;un contr&#244;le Windows Form &#224; l&#39;aide du remplissage | Microsoft Docs"
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
  - "contrôles (Windows Forms), Margin (propriété)"
  - "contrôles (Windows Forms), mode Plan"
  - "contrôles (Windows Forms), Padding (propriété)"
  - "Margin (propriété Windows Forms)"
  - "marges"
  - "marges, Windows Forms"
  - "Padding (propriété Windows Forms)"
  - "marge intérieure, Windows Forms"
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: cr&#233;er une bordure autour d&#39;un contr&#244;le Windows Form &#224; l&#39;aide du remplissage
L'exemple de code suivant montre comment créer une bordure ou un cadre autour d'un contrôle <xref:System.Windows.Forms.RichTextBox>.  L'exemple définit la valeur de la propriété <xref:System.Windows.Forms.Padding> d'un contrôle <xref:System.Windows.Forms.Panel> à 5 et attribue à la propriété <xref:System.Windows.Forms.Control.Dock%2A> d'un contrôle enfant <xref:System.Windows.Forms.RichTextBox> la valeur <xref:System.Windows.Forms.DockStyle>.  Le <xref:System.Windows.Forms.Control.BackColor%2A> du contrôle <xref:System.Windows.Forms.Panel> a la valeur <xref:System.Drawing.Color.Blue%2A>, qui crée une bordure bleue autour du contrôle <xref:System.Windows.Forms.RichTextBox>.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.Padding>   
 [Marge et marge intérieure dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)