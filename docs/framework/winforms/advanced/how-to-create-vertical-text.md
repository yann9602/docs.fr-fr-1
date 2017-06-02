---
title: "Comment&#160;: cr&#233;er du texte vertical | Microsoft Docs"
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
  - "chaînes (Windows Forms), dessiner verticalement"
  - "texte (Windows Forms), dessiner verticalement"
  - "texte vertical, dessiner"
  - "Windows Forms, dessiner du texte vertical"
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er du texte vertical
Vous pouvez utiliser un objet <xref:System.Drawing.StringFormat> pour spécifier que le texte doit être dessiné verticalement et non horizontalement.  
  
## Exemple  
 L'exemple suivant assigne la valeur <xref:System.Drawing.StringFormatFlags> à la propriété <xref:System.Drawing.StringFormat.FormatFlags%2A> d'un objet <xref:System.Drawing.StringFormat>.  Cet objet <xref:System.Drawing.StringFormat> est passé à la méthode <xref:System.Drawing.Graphics.DrawString%2A> de la classe <xref:System.Drawing.Graphics>.  La valeur <xref:System.Drawing.StringFormatFlags> est un membre de l'énumération <xref:System.Drawing.StringFormatFlags>.  
  
 L'illustration suivante montre le texte vertical.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## Compilation du code  
  
-   L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e` , qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Comment : écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)