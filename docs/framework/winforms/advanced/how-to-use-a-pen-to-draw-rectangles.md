---
title: "Comment&#160;: utiliser un stylet pour dessiner des rectangles | Microsoft Docs"
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
  - "stylets, dessiner des rectangles"
  - "rectangles, dessiner"
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: utiliser un stylet pour dessiner des rectangles
Pour dessiner des rectangles, il vous faut un objet <xref:System.Drawing.Graphics> et un objet <xref:System.Drawing.Pen>.  L'objet <xref:System.Drawing.Graphics> fournit la méthode <xref:System.Drawing.Graphics.DrawRectangle%2A> et l'objet <xref:System.Drawing.Pen> stocke les fonctionnalités de la ligne, telles que la couleur et la largeur.  
  
## Exemple  
 L'exemple suivant dessine un rectangle dont le coin supérieur gauche se trouve à \(10, 10\).  Le rectangle a une largeur de 100 et une hauteur de 50.  Le deuxième argument passé au constructeur <xref:System.Drawing.Pen.%23ctor%2A> indique que la largeur du stylet est de 5 pixels.  
  
 Lorsque le rectangle est dessiné, le stylet est centré sur la limite du rectangle.  Comme la largeur du stylet est de 5, les côtés du rectangle sont dessinés avec une largeur de 5 pixels : 1 pixel est dessiné sur la limite proprement dite, 2 pixels à l'intérieur et 2 pixels à l'extérieur.  Pour plus d'informations sur l'alignement du stylet, consultez [Comment : définir la largeur et l'alignement du stylet](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).  
  
 L'illustration suivante montre le rectangle résultant.  Les lignes discontinues montrent où le rectangle aurait été dessiné si la largeur du stylet avait été d'un pixel.  La vue agrandie du coin supérieur gauche du rectangle montre que les lignes noires épaisses sont centrées sur ces lignes discontinues.  
  
 ![Stylets](../../../../docs/framework/winforms/advanced/media/pens1.png "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)