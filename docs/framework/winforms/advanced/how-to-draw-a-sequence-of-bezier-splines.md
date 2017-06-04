---
title: "Comment&#160;: dessiner une s&#233;quence de splines de B&#233;zier | Microsoft Docs"
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
  - "splines de Bézier, dessiner la séquence de"
  - "splines, dessiner une spline de Bézier"
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: dessiner une s&#233;quence de splines de B&#233;zier
La méthode <xref:System.Drawing.Graphics.DrawBeziers%2A> de la classe <xref:System.Drawing.Graphics> peut s'utiliser pour dessiner une succession de splines de Bézier reliées l'une à l'autre.  
  
## Exemple  
 L'exemple suivant dessine une courbe formée de deux splines de Bézier reliées.  Le point de terminaison de la première spline de Bézier constitue le point de départ de la seconde.  
  
 L'illustration suivante présente les splines reliées et les sept points.  
  
 ![Spline de Bézier](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Splines de Bézier dans GDI\+](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)   
 [Génération et dessin de courbes](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)