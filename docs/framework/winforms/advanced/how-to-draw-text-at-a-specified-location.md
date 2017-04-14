---
title: "Comment&#160;: &#233;crire du texte &#224; un emplacement sp&#233;cifi&#233; | Microsoft Docs"
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
  - "dessiner du texte"
  - "dessiner du texte, emplacements spécifiés (Windows Forms)"
  - "texte, dessiner à des emplacements spécifiés (Windows Forms)"
  - "Windows Forms, dessiner un texte à un emplacement spécifié"
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: &#233;crire du texte &#224; un emplacement sp&#233;cifi&#233;
Lorsque vous effectuez un dessin personnalisé, vous pouvez dessiner le texte sur une seule ligne horizontale à partir d'un point spécifié.  Vous pouvez dessiner du texte de cette manière en utilisant la méthode surchargée <xref:System.Drawing.Graphics.DrawString%2A> de la classe <xref:System.Drawing.Graphics> qui utilise un paramètre <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF>.  La méthode <xref:System.Drawing.Graphics.DrawString%2A> exige également <xref:System.Drawing.Brush> et <xref:System.Drawing.Font>  
  
 Vous pouvez également utiliser la méthode surchargée <xref:System.Windows.Forms.TextRenderer.DrawText%2A> de <xref:System.Windows.Forms.TextRenderer> qui prend un <xref:System.Drawing.Point>.  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> requiert également un <xref:System.Drawing.Color> et un <xref:System.Drawing.Font>.  
  
 L'illustration suivante affiche la sortie d'un texte dessiné à un point spécifié à l'aide de la méthode surchargée <xref:System.Drawing.Graphics.DrawString%2A>.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### Pour dessiner une ligne de texte avec GDI\+  
  
1.  Utilisez la méthode <xref:System.Drawing.Graphics.DrawString%2A>, en passant le texte que vous voulez, <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, et <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### Pour dessiner une ligne de texte avec GDI  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.TextRenderer.DrawText%2A>, en passant le texte voulu, <xref:System.Drawing.Point>, <xref:System.Drawing.Font> et <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## Compilation du code  
 Les exemples précédents nécessitent :  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Comment : écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [Comment : construire des familles de polices et des polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)   
 [Comment : écrire du texte renvoyé à la ligne dans un rectangle](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)