---
title: "Comment&#160;: &#233;crire du texte renvoy&#233; &#224; la ligne dans un rectangle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "chaînes (Windows Forms), dessiner dans un rectangle"
  - "texte (Windows Forms), dessiner dans un rectangle"
  - "Windows Forms, dessiner un texte dans un rectangle"
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: &#233;crire du texte renvoy&#233; &#224; la ligne dans un rectangle
Vous pouvez dessiner du texte renvoyé à la ligne dans un rectangle en utilisant la méthode surchargée <xref:System.Drawing.Graphics.DrawString%2A> de la classe <xref:System.Drawing.Graphics> qui utilise un paramètre <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF>.  Vous pouvez également utiliser <xref:System.Drawing.Brush> et <xref:System.Drawing.Font>.  
  
 Vous pouvez aussi dessiner du texte renvoyé à la ligne dans un rectangle en utilisant la méthode surchargée <xref:System.Windows.Forms.TextRenderer.DrawText%2A> de <xref:System.Windows.Forms.TextRenderer> qui utilise les paramètres <xref:System.Drawing.Rectangle> et <xref:System.Windows.Forms.TextFormatFlags>.  Vous pouvez également utiliser <xref:System.Drawing.Color> et <xref:System.Drawing.Font>.  
  
 L'illustration suivante affiche la sortie du texte dessiné dans le rectangle lorsque vous utilisez la méthode <xref:System.Drawing.Graphics.DrawString%2A>.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### Pour dessiner du texte renvoyé à la ligne dans un rectangle avec GDI\+  
  
1.  Utilisez la méthode surchargée <xref:System.Drawing.Graphics.DrawString%2A>, en passant le texte que vous voulez, <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> et <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### Pour dessiner du texte renvoyé à la ligne dans un rectangle avec GDI  
  
1.  Utilisez la valeur d'énumération <xref:System.Windows.Forms.TextFormatFlags> pour spécifier que le texte doit être renvoyé à la ligne avec la méthode surchargée <xref:System.Windows.Forms.TextRenderer.DrawText%2A>, en passant le texte que vous voulez, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> et <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## Compilation du code  
 Les exemples précédents nécessitent :  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Comment : écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [Comment : construire des familles de polices et des polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)   
 [Comment : écrire du texte à un emplacement spécifié](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)