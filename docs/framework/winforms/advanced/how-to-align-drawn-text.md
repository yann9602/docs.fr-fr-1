---
title: "Comment&#160;: aligner le texte &#233;crit | Microsoft Docs"
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
  - "texte, aligner"
  - "Windows Forms, aligner le texte dessiné"
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: aligner le texte &#233;crit
En effectuant un dessin personnalisé, il est probable que vous souhaitiez centrer le texte dessiné sur un formulaire ou un contrôle.  Vous pouvez facilement aligner le texte dessiné avec les méthodes <xref:System.Drawing.Graphics.DrawString%2A> ou <xref:System.Windows.Forms.TextRenderer.DrawText%2A> en créant l'objet de mise en forme voulu et en définissant les indicateurs de format appropriés.  
  
### Pour dessiner un texte centré avec GDI\+ \(DrawString\)  
  
1.  Utilisez un <xref:System.Drawing.StringFormat> avec la méthode <xref:System.Drawing.Graphics.DrawString%2A> appropriée pour spécifier le texte centré.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### Pour dessiner un texte centré avec GDI \(DrawText\)  
  
1.  Utilisez l'énumération <xref:System.Windows.Forms.TextFormatFlags> pour habiller ainsi que centrer verticalement et horizontalement le texte avec la méthode <xref:System.Windows.Forms.TextRenderer.DrawText%2A> appropriée.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## Compilation du code  
 Les exemples de code précédents sont conçus pour être utilisés avec Windows Forms, et ils nécessitent <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Comment : écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [Comment : construire des familles de polices et des polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)