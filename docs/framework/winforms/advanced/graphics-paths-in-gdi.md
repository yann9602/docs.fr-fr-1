---
title: "Trac&#233;s graphiques dans GDI+ | Microsoft Docs"
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
  - "dessiner, chemins d'accès"
  - "GDI+, dessiner des chemins d'accès"
  - "graphiques, chemins d'accès"
  - "chemins d'accès, dessiner"
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Trac&#233;s graphiques dans GDI+
Les tracés sont formés de combinaisons de lignes, de rectangles et de courbes simples.  Dans la rubrique [Vue d'ensemble des graphismes vectoriels](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md), nous avons vu que les blocs de construction de base suivants étaient les plus utiles pour dessiner des images :  
  
-   Lignes  
  
-   Rectangles  
  
-   Ellipses  
  
-   Arcs  
  
-   Polygones  
  
-   Splines cardinales  
  
-   Splines de Bézier  
  
 Dans GDI\+, l'objet <xref:System.Drawing.Drawing2D.GraphicsPath> permet de réunir dans une entité unique une séquence de tels blocs.  La séquence entière de lignes, rectangles, polygones et courbes peut ensuite être dessinée à l'aide d'un seul appel à la méthode <xref:System.Drawing.Graphics.DrawPath%2A> de la classe <xref:System.Drawing.Graphics>.  L'illustration suivante représente un tracé créé en combinant une ligne, un arc, une spline de Bézier et une spline cardinale.  
  
 ![Chemin d'accès](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.png "Aboutgdip02\_art14")  
  
## Utilisation d'un tracé  
 La classe <xref:System.Drawing.Drawing2D.GraphicsPath> fournit les méthodes suivantes pour créer une séquence d'éléments à dessiner : <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> \(pour les splines cardinales\) et <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.  Chacune de ces méthodes est surchargée, c'est\-à\-dire qu'elle prend en charge plusieurs listes de paramètres différentes.  Par exemple, une variante de la méthode <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> reçoit quatre entiers, tandis qu'une autre variante de la méthode <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> reçoit deux objets <xref:System.Drawing.Point>.  
  
 Les méthodes permettant d'ajouter des lignes, des rectangles et des splines de Bézier à un tracé sont associées à des méthodes au pluriel qui ajoutent plusieurs éléments au tracé en un seul appel : <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A> et <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.  Par ailleurs, les méthodes <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> et <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> sont également associées à d'autres méthodes, à savoir <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> et <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, qui ajoutent une courbe fermée ou un secteur au tracé.  
  
 Pour dessiner un tracé, il vous faut un objet <xref:System.Drawing.Graphics>, un objet <xref:System.Drawing.Pen> et un objet <xref:System.Drawing.Drawing2D.GraphicsPath>.  L'objet <xref:System.Drawing.Graphics> fournit la méthode <xref:System.Drawing.Graphics.DrawPath%2A> et l'objet <xref:System.Drawing.Pen> stocke des attributs \(largeur et couleur notamment\) de la ligne utilisée pour représenter le tracé.  L'objet <xref:System.Drawing.Drawing2D.GraphicsPath> stocke la séquence de lignes et de courbes qui constitue le tracé.  L'objet <xref:System.Drawing.Pen> et l'objet <xref:System.Drawing.Drawing2D.GraphicsPath> sont passés en tant qu'arguments à la méthode <xref:System.Drawing.Graphics.DrawPath%2A>.  L'exemple suivant dessine un tracé constitué d'une ligne, d'une ellipse et d'une spline de Bézier :  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 L'illustration suivante représente ce tracé.  
  
 ![Chemin d'accès](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.png "Aboutgdip02\_art15")  
  
 Outre des lignes, des rectangles et des courbes, vous pouvez ajouter d'autres tracés à un tracé.  Vous pouvez ainsi combiner des tracés existants pour former des tracés plus complexes et de plus grande taille.  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 Vous pouvez ajouter deux autres éléments à un tracé : des chaînes et des secteurs.  Un secteur est une portion de l'intérieur d'une ellipse.  L'exemple suivant crée un tracé constitué d'un arc, d'une spline cardinale et d'un secteur.  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 L'illustration suivante représente ce tracé.  Notez qu'un tracé n'est pas obligatoirement constitué d'éléments liés ; l'arc, la spline cardinale, la chaîne et le secteur sont séparés.  
  
 ![Chemins d'accès](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.png "Aboutgdip02\_Art16")  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 <xref:System.Drawing.Point?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [Génération et dessin de tracés](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)