---
title: "Comment&#160;: dessiner des splines cardinales | Microsoft Docs"
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
  - "splines cardinales, dessiner"
  - "dessiner, splines cardinales"
  - "graphiques, splines cardinales"
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: dessiner des splines cardinales
Une spline cardinale est une courbe qui passe de manière souple par un ensemble donné de points.  Pour dessiner une spline cardinale, créez un objet <xref:System.Drawing.Graphics> et passez l'adresse d'un tableau de points à la méthode <xref:System.Drawing.Graphics.DrawCurve%2A>.  
  
### Dessin d'une spline cardinale en forme de cloche  
  
-   L'exemple suivant dessine une spline cardinale en forme de cloche qui passe par cinq points définis.  L'illustration suivante montre la courbe et les cinq points.  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### Dessin d'une spline cardinale fermée  
  
-   La méthode <xref:System.Drawing.Graphics.DrawClosedCurve%2A> de la classe <xref:System.Drawing.Graphics> peut s'utiliser pour dessiner une spline cardinale fermée.  Dans ce cas, la courbe se poursuit jusqu'au dernier point de la matrice et rejoint le premier point de la matrice.  L'exemple suivant dessine une spline cardinale fermée qui passe par six points définis :  L'illustration suivante représente la spline fermée avec les six points.  
  
 ![Spline cardinale](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### Modification de la courbure d'une spline cardinale  
  
-   Pour modifier la courbure d'une spline cardinale, passez un argument de tension à la méthode <xref:System.Drawing.Graphics.DrawCurve%2A>.  L'exemple suivant dessine trois splines cardinales qui passent par un même ensemble de points.  L'illustration suivante représente les trois splines avec leur valeur de tension.  Notez que si la tension a pour valeur zéro \(0\), les points sont reliés par des lignes droites.  
  
 ![Spline cardinale](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## Compilation du code  
 Les exemples précédents sont destinés à une utilisation avec Windows Forms et nécessitent <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Génération et dessin de courbes](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)