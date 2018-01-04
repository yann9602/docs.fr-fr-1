---
title: "Comment : dessiner une séquence de B &#233; Splines de Bézier"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5bdd9ae29dcbb8397d2fe645e240572aad32a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Comment : dessiner une séquence de B &#233; Splines de Bézier
Vous pouvez utiliser la <xref:System.Drawing.Graphics.DrawBeziers%2A> méthode de la <xref:System.Drawing.Graphics> classe pour dessiner une séquence de splines de Bézier reliées.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant dessine une courbe qui se compose de deux splines de Bézier connectés. Le point de terminaison de la première spline de Bézier est le point de départ de la deuxième spline de Bézier.  
  
 L’illustration suivante montre les splines reliées et les sept points.  
  
 ![Spline de Bézier](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Splines de Bézier dans GDI+](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [Génération et dessin de courbes](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
