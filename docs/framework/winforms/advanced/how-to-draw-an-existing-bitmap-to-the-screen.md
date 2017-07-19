---
title: "Comment&#160;: dessiner une bitmap existante &#224; l&#39;&#233;cran | Microsoft Docs"
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
  - "bitmaps (Windows Forms), afficher dans les Windows Forms"
  - "bitmaps (Windows Forms), charger dans les applications (Windows Forms)"
  - "images (Windows Forms), afficher sur les Windows Forms"
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: dessiner une bitmap existante &#224; l&#39;&#233;cran
Vous pouvez facilement dessiner une image existante à l'écran.  Commencez par créer un objet <xref:System.Drawing.Bitmap> à l'aide du constructeur de bitmap qui prend un nom de fichier, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.  Ce constructeur accepte des images ayant différents formats de fichiers \(BMP, GIF, JPEG, PNG et TIFF, par exemple\).  Une fois que vous avez créé l'objet <xref:System.Drawing.Bitmap>, passez cet objet <xref:System.Drawing.Bitmap> à la méthode <xref:System.Drawing.Graphics.DrawImage%2A> d'un objet <xref:System.Drawing.Graphics>.  
  
## Exemple  
 Cet exemple crée un objet <xref:System.Drawing.Bitmap> à partir d'un fichier JPEG, puis dessine la bitmap en positionnant son coin supérieur gauche à \(60, 10\).  
  
 L'illustration suivante montre la bitmap dessinée à l'emplacement spécifié.  
  
 ![Position de l'image](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)