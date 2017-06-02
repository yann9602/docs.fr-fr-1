---
title: "Ellipses et arcs dans GDI+ | Microsoft Docs"
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
  - "arcs"
  - "dessiner, arcs"
  - "dessiner, ellipses"
  - "ellipses"
  - "GDI+, arcs"
  - "GDI+, ellipses"
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Ellipses et arcs dans GDI+
Vous pouvez dessiner facilement des ellipses et des arcs à l'aide des méthodes <xref:System.Drawing.Graphics.DrawEllipse%2A> et <xref:System.Drawing.Graphics.DrawArc%2A> de la classe <xref:System.Drawing.Graphics>.  
  
## Dessin d'une ellipse  
 Pour dessiner une ellipse, vous avez besoin d'un objet <xref:System.Drawing.Graphics> et d'un objet <xref:System.Drawing.Pen>.  L'objet <xref:System.Drawing.Graphics> fournit la méthode <xref:System.Drawing.Graphics.DrawEllipse%2A> et l'objet <xref:System.Drawing.Pen> stocke des attributs \(largeur et couleur notamment\) de la ligne utilisée pour représenter l'ellipse.  L'objet <xref:System.Drawing.Pen> est passé à la méthode <xref:System.Drawing.Graphics.DrawEllipse%2A> en tant qu'argument.  Les autres arguments passés à la méthode <xref:System.Drawing.Graphics.DrawEllipse%2A> définissent le rectangle englobant de l'ellipse.  L'illustration suivante représente une ellipse et son rectangle englobant.  
  
 ![Ellipses et arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.png "Aboutgdip02\_art05")  
  
 L'exemple suivant dessine une ellipse dont le rectangle englobant présente une largeur de 80 et une hauteur de 40 à partir du coin supérieur gauche situé en \(100, 50\) :  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> est une méthode surchargée de la classe <xref:System.Drawing.Graphics> ; vous pouvez donc lui fournir des arguments de diverses manières.  Par exemple, vous pouvez construire un objet <xref:System.Drawing.Rectangle> et le passer en tant qu'argument à la méthode <xref:System.Drawing.Graphics.DrawEllipse%2A> :  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## Dessin d'un arc  
 Un arc est un segment d'ellipse.  Pour dessiner un arc, appelez la méthode <xref:System.Drawing.Graphics.DrawArc%2A> de la classe <xref:System.Drawing.Graphics>.  Les paramètres de la méthode <xref:System.Drawing.Graphics.DrawArc%2A> sont les mêmes que ceux de la méthode <xref:System.Drawing.Graphics.DrawEllipse%2A>, sauf que <xref:System.Drawing.Graphics.DrawArc%2A> nécessite un angle de départ et un angle de balayage.  L'exemple suivant dessine un arc dont l'angle de départ est de 30 degrés et l'angle de balayage de 180 degrés :  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 L'illustration suivante représente l'arc, l'ellipse et le rectangle englobant.  
  
 ![Ellipses et arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.png "Aboutgdip02\_art06")  
  
## Voir aussi  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [Comment : créer un objet Pen](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [Comment : dessiner une forme avec contour](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)