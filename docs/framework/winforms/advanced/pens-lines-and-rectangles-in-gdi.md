---
title: "Stylets, lignes et rectangles dans GDI+ | Microsoft Docs"
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
  - "dessiner, lignes"
  - "dessiner, rectangles"
  - "exemples (Windows Forms), tracer des lignes et des formes"
  - "exemples (Windows Forms), GDI+"
  - "exemples (Windows Forms), stylets"
  - "GDI+, lignes"
  - "GDI+, stylets"
  - "GDI+, rectangles"
  - "lignes"
  - "lignes, en pointillés"
  - "rectangles"
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Stylets, lignes et rectangles dans GDI+
Pour dessiner des lignes à l'aide de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous devez créer un objet <xref:System.Drawing.Graphics> ainsi qu'un objet <xref:System.Drawing.Pen>.  L'objet <xref:System.Drawing.Graphics> fournit les méthodes qui effectuent réellement le dessin et l'objet <xref:System.Drawing.Pen> stocke des attributs, tels que la couleur, la largeur et le style de ligne.  
  
## Dessin d'une ligne  
 Pour dessiner une ligne, appelez la méthode <xref:System.Drawing.Graphics.DrawLine%2A> de l'objet <xref:System.Drawing.Graphics>.  L'objet <xref:System.Drawing.Pen> est passé à la méthode <xref:System.Drawing.Graphics.DrawLine%2A> en tant qu'argument.  L'exemple suivant dessine une ligne qui va du point \(4, 2\) au point \(12, 6\) :  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> est une méthode surchargée de la classe <xref:System.Drawing.Graphics> ; vous pouvez donc lui fournir des arguments de diverses manières.  Par exemple, vous pouvez construire deux objets <xref:System.Drawing.Point> et les passer en tant qu'arguments à la méthode <xref:System.Drawing.Graphics.DrawLine%2A> :  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## Construction d'un stylet  
 Vous pouvez spécifier certains attributs lorsque vous construisez un objet <xref:System.Drawing.Pen>.  Par exemple, un constructeur `Pen` vous permet de spécifier la couleur et la largeur.  L'exemple suivant dessine une ligne bleue de largeur 2 qui va du point \(0, 0\) au point \(60, 30\) :  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## Lignes en pointillés et embouts de ligne  
 L'objet <xref:System.Drawing.Pen> expose également des propriétés, telles que <xref:System.Drawing.Pen.DashStyle%2A>, que vous pouvez utiliser pour spécifier des caractéristiques de la ligne.  L'exemple suivant dessine une ligne en pointillés qui va du point \(100, 50\) au point \(300, 80\) :  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Vous pouvez utiliser les propriétés de l'objet <xref:System.Drawing.Pen> pour définir beaucoup d'autres attributs de la ligne.  Les propriétés <xref:System.Drawing.Pen.StartCap%2A> et <xref:System.Drawing.Pen.EndCap%2A> spécifient l'aspect des extrémités de la ligne, lesquelles peuvent être à deux dimensions \(flat\), carrées, arrondies, triangulaires ou de forme personnalisée.  La propriété <xref:System.Drawing.Pen.LineJoin%2A> permet de spécifier si les lignes reliées entre elles forment une jointure à angle aigu, en biseau, arrondie ou découpée.  L'illustration suivante présente des lignes avec différents styles d'extrémité et de jointure.  
  
 ![Lignes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.png "Aboutgdip02\_art04")  
  
## Dessin d'un rectangle  
 Le dessin de rectangles avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est similaire au dessin de lignes.  Pour dessiner un rectangle, il vous faut un objet <xref:System.Drawing.Graphics> et un objet <xref:System.Drawing.Pen>.  L'objet <xref:System.Drawing.Graphics> fournit une méthode <xref:System.Drawing.Graphics.DrawRectangle%2A> et l'objet <xref:System.Drawing.Pen> stocke des attributs, tels que la largeur et la couleur de ligne.  L'objet <xref:System.Drawing.Pen> est passé à la méthode <xref:System.Drawing.Graphics.DrawRectangle%2A> en tant qu'argument.  L'exemple suivant dessine un rectangle de largeur 80 et de hauteur 40 à partir du coin supérieur gauche situé en \(100, 50\) :  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> est une méthode surchargée de la classe <xref:System.Drawing.Graphics> ; vous pouvez donc lui fournir des arguments de diverses manières.  Par exemple, vous pouvez construire un objet <xref:System.Drawing.Rectangle> et le passer en tant qu'argument à la méthode <xref:System.Drawing.Graphics.DrawRectangle%2A> :  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 Un objet <xref:System.Drawing.Rectangle> comprend des méthodes et des propriétés permettant de manipuler et de collecter les informations qui le décrivent.  Par exemple, les méthodes <xref:System.Drawing.Rectangle.Inflate%2A> et <xref:System.Drawing.Rectangle.Offset%2A> modifient la taille et la position du rectangle.  La méthode <xref:System.Drawing.Rectangle.IntersectsWith%2A> vous indique si le rectangle coupe un rectangle donné et la méthode <xref:System.Drawing.Rectangle.Contains%2A> indique si un point donné se trouve dans le rectangle.  
  
## Voir aussi  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Rectangle?displayProperty=fullName>   
 [Comment : créer un objet Pen](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [Comment : dessiner une ligne dans un Windows Form](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)   
 [Comment : dessiner une forme avec contour](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)