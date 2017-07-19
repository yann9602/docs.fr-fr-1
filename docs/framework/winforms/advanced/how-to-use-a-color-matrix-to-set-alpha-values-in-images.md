---
title: "Comment&#160;: utiliser une matrice de couleurs pour d&#233;finir des valeurs alpha dans des images | Microsoft Docs"
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
  - "bitmaps (Windows Forms), utiliser les matrices des couleurs pour les semi-transparents"
  - "images (Windows Forms), utiliser les matrices des couleurs pour les semi-transparents"
  - "matrices, valeurs alpha"
  - "transparence, matrices des couleurs"
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: utiliser une matrice de couleurs pour d&#233;finir des valeurs alpha dans des images
La classe <xref:System.Drawing.Bitmap> \(qui hérite de la classe <xref:System.Drawing.Image>\) et la classe <xref:System.Drawing.Imaging.ImageAttributes> fournissent les fonctionnalités d'obtention et de définition de valeurs de pixels.  Vous pouvez utiliser la classe <xref:System.Drawing.Imaging.ImageAttributes> pour modifier les valeurs alpha de toute une image ou vous pouvez appeler la méthode <xref:System.Drawing.Bitmap.SetPixel%2A> de la classe <xref:System.Drawing.Bitmap> pour modifier des valeurs de pixel individuelles.  
  
## Exemple  
 La classe <xref:System.Drawing.Imaging.ImageAttributes> comporte plusieurs propriétés que vous pouvez utiliser pour modifier les images pendant le rendu.  Dans l'exemple suivant, un objet <xref:System.Drawing.Imaging.ImageAttributes> est employé pour définir toutes les valeurs alpha à 80 pour cent de la valeur d'origine.  Cela est effectué en initialisant une matrice de couleurs et en définissant la valeur de dimensionnement alpha dans la matrice à 0,8.  L'adresse de la matrice couleur est passée à la méthode <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> de l'objet <xref:System.Drawing.Imaging.ImageAttributes> et l'objet <xref:System.Drawing.Imaging.ImageAttributes> est passé à la méthode <xref:System.Drawing.Graphics.DrawString%2A> de l'objet <xref:System.Drawing.Graphics>.  
  
 Pendant le rendu, les valeurs alpha dans la bitmap sont converties à 80 pour cent de leur valeur d'origine.  Cela donne une image fondue à l'arrière\-plan.  Comme le montre l'illustration suivante, l'image bitmap semble transparente ; vous pouvez voir la ligne noire unie à travers.  
  
 ![Fusion alpha utilisant une matrice](../../../../docs/framework/winforms/advanced/media/image2.png "image2")  
  
 Là où l'image se trouve au\-dessus de la partie blanche de l'arrière\-plan, l'image a été fondue à la couleur blanche.  Là où l'image traverse la ligne noire, l'image se fond à la couleur noire.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Fusion alpha de lignes et de remplissages](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)