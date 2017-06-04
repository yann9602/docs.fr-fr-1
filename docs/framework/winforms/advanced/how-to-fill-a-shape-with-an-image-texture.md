---
title: "Comment&#160;: remplir une forme avec une texture d&#39;image | Microsoft Docs"
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
  - "bitmaps (Windows Forms), utiliser la texture"
  - "images (Windows Forms), utiliser avec les pinceaux"
  - "formes, remplir avec les images"
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: remplir une forme avec une texture d&#39;image
Vous pouvez remplir une forme fermée avec une texture en utilisant la classe <xref:System.Drawing.Image> et la classe <xref:System.Drawing.TextureBrush>.  
  
## Exemple  
 L'exemple suivant remplit une ellipse avec une image.  Le code construit un objet <xref:System.Drawing.Image>, puis passe l'adresse de cet objet <xref:System.Drawing.Image> comme argument à un constructeur <xref:System.Drawing.TextureBrush.%23ctor%2A>.  La troisième instruction met l'image à l'échelle et la quatrième remplit l'ellipse avec des copies répétées de l'image dimensionnée.  
  
 Dans le code suivant, la propriété <xref:System.Drawing.TextureBrush.Transform%2A> contient la transformation qui est appliquée à l'image avant qu'elle ne soit dessinée.  Supposons que l'image d'origine ait une largeur de 640 pixels et une hauteur de 480 pixels.  La transformation réduit l'image à 75×75 en définissant les valeurs de mise à l'échelle horizontale et verticale.  
  
> [!NOTE]
>  Dans l'exemple suivant, la taille de l'image est 75×75 et la taille de l'ellipse est 150×250.  Étant donné que l'image est plus petite que l'ellipse qu'elle remplit, l'ellipse est disposée en mosaïque.  Une mosaïque correspond à une répétition horizontale et verticale de l'image jusqu'à ce que la limite de la forme soit atteinte.  Pour plus d'informations sur la disposition en mosaïque, consultez [Comment : remplir une forme avec une image](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Utilisation d'un pinceau pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)