---
title: "Comment&#160;: dessiner une spline de B&#233;zier unique | Microsoft Docs"
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
  - "splines de Bézier, dessiner"
  - "dessiner, splines de Bézier"
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: dessiner une spline de B&#233;zier unique
Une spline de Bézier se définit par quatre points : un point de départ, deux points de contrôle et un point de terminaison.  
  
## Exemple  
 L'exemple suivant dessine une spline de Bézier ayant pour point de départ \(10, 100\) et pour point de terminaison \(200, 100\).  Les points de contrôle correspondent à \(100, 10\) et \(150, 150\).  
  
 L'illustration suivante représente la spline de Bézier qui en résulte avec son point de départ, ses points de contrôle et son point de terminaison.  Elle montre également la forme convexe de la spline qui constitue un polygone formé en reliant les quatre points par des lignes droites.  
  
 ![Spline de Bézier](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 <xref:System.Drawing.Graphics.DrawBezier%2A>   
 [Splines de Bézier dans GDI\+](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)   
 [Comment : dessiner une séquence de splines de Bézier](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)