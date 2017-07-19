---
title: "Vue d&#39;ensemble des graphismes vectoriels | Microsoft Docs"
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
  - "systèmes de coordonnées"
  - "graphiques, graphismes vectoriels"
  - "points de terminaison de fin et de début"
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Vue d&#39;ensemble des graphismes vectoriels
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dessine des lignes, des rectangles et d'autres formes sur un système de coordonnées.  Vous avez le choix entre plusieurs systèmes de coordonnées, mais dans le système de coordonnées par défaut, l'origine se trouve dans le coin supérieur gauche, l'axe des abscisses \(x\) pointe vers la droite et l'axe des ordonnées \(y\) pointe vers le bas.  Dans le système de coordonnées par défaut, l'unité de mesure est le pixel.  
  
## Blocs de construction de GDI\+  
 ![Graphique vectoriel](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.png "AboutGdip02\_Art01")  
  
 Le moniteur d'un ordinateur crée son écran d'affichage sur un tableau rectangulaire de points appelés pixels.  Le nombre de pixels à l'écran est variable d'un moniteur à un autre ; le nombre de pixels affichés par un moniteur donné peut généralement être configuré par l'utilisateur, dans une certaine mesure.  
  
 ![Graphique vectoriel](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.png "AboutGdip02\_Art02")  
  
 Lorsque vous utilisez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour dessiner une ligne, un rectangle ou une courbe, vous fournissez des informations essentielles sur l'élément à dessiner.  Par exemple, vous pouvez spécifier une ligne en fournissant deux points et spécifier un rectangle en fournissant un point, une hauteur et une largeur.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fonctionne conjointement au logiciel de pilote d'affichage pour déterminer les pixels devant être activés pour afficher la ligne, le rectangle ou la courbe.  L'illustration suivante montre les pixels activés pour afficher une ligne qui va du point \(4, 2\) au point \(12, 8\).  
  
 ![Graphique vectoriel](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.png "AboutGdip02\_Art03")  
  
 Avec le temps, certains blocs de construction se sont révélés plus utiles que d'autres pour construire des images en deux dimensions.  Voici la liste de ces blocs de construction, tous pris en charge par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] :  
  
-   Lignes  
  
-   Rectangles  
  
-   Ellipses  
  
-   Arcs  
  
-   Polygones  
  
-   Splines cardinales  
  
-   Splines de Bézier  
  
## Méthodes pour le dessin avec un objet Graphics  
 La classe <xref:System.Drawing.Graphics> dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit les méthodes suivantes pour dessiner les éléments de la liste précédente : <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> \(pour les splines cardinales\) et <xref:System.Drawing.Graphics.DrawBezier%2A>.  Chacune de ces méthodes est surchargée, c'est\-à\-dire qu'elle prend en charge plusieurs listes de paramètres différentes.  Par exemple, une variante de la méthode <xref:System.Drawing.Graphics.DrawLine%2A> reçoit un objet <xref:System.Drawing.Pen> et quatre entiers, tandis qu'une autre variante de la méthode <xref:System.Drawing.Graphics.DrawLine%2A> reçoit un objet <xref:System.Drawing.Pen> et deux objets <xref:System.Drawing.Point>.  
  
 Les méthodes permettant de dessiner des lignes, des rectangles et des splines de Bézier sont associées à des méthodes au pluriel qui dessinent plusieurs éléments en un seul appel : <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A> et <xref:System.Drawing.Graphics.DrawBeziers%2A>.  La méthode <xref:System.Drawing.Graphics.DrawCurve%2A> est également associée à une autre méthode, <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, qui ferme une courbe en reliant ses points de début et de fin.  
  
 Toutes les méthodes de dessin de la classe <xref:System.Drawing.Graphics> fonctionnent en collaboration avec un objet <xref:System.Drawing.Pen>.  Quoi que vous dessiniez, vous devez créer au moins deux objets : un objet <xref:System.Drawing.Graphics> et un objet <xref:System.Drawing.Pen>.  L'objet <xref:System.Drawing.Pen> contient les attributs de l'élément à dessiner \(épaisseur et couleur de la ligne, par exemple\).  L'objet <xref:System.Drawing.Pen> est passé à la méthode de dessin en tant qu'argument.  Par exemple, une variante de la méthode <xref:System.Drawing.Graphics.DrawLine%2A> reçoit un objet <xref:System.Drawing.Pen> et quatre entiers comme le montre l'exemple suivant, pour dessiner un rectangle de largeur 100 et de hauteur 50 à partir d'un coin supérieur gauche situé en \(20, 10\) :  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## Voir aussi  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)