---
title: Ellipses et arcs dans GDI+
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
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ebeae1d076a0ebcf36d52dee1af0c0ad5f04fdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ellipses-and-arcs-in-gdi"></a>Ellipses et arcs dans GDI+
Vous pouvez facilement dessiner des ellipses et arcs à l’aide de la <xref:System.Drawing.Graphics.DrawEllipse%2A> et <xref:System.Drawing.Graphics.DrawArc%2A> méthodes de la <xref:System.Drawing.Graphics> classe.  
  
## <a name="drawing-an-ellipse"></a>Dessiner une Ellipse  
 Pour dessiner une ellipse, vous avez besoin une <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet. Le <xref:System.Drawing.Graphics> objet fournit les <xref:System.Drawing.Graphics.DrawEllipse%2A> (méthode) et le <xref:System.Drawing.Pen> objet stocke des attributs, tels que la largeur et la couleur, de la ligne utilisée pour représenter l’ellipse. Le <xref:System.Drawing.Pen> objet est passé en tant qu’arguments à la <xref:System.Drawing.Graphics.DrawEllipse%2A> (méthode). Les autres arguments passés à la <xref:System.Drawing.Graphics.DrawEllipse%2A> méthode définissent le rectangle englobant de l’ellipse. L’illustration suivante montre une ellipse, ainsi que son rectangle englobant.  
  
 ![Ellipses et arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 L’exemple suivant dessine une ellipse ; le rectangle englobant d’une largeur de 80, une hauteur de 40 et un coin supérieur gauche de (100, 50) :  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>est une méthode surchargée de la <xref:System.Drawing.Graphics> classe, il y a plusieurs façons, vous pouvez lui fournir avec des arguments. Par exemple, vous pouvez construire un <xref:System.Drawing.Rectangle> et passer le <xref:System.Drawing.Rectangle> à la <xref:System.Drawing.Graphics.DrawEllipse%2A> méthode en tant qu’argument :  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>Dessin d’un Arc  
 Un arc est une partie d’une ellipse. Pour dessiner un arc, appelez le <xref:System.Drawing.Graphics.DrawArc%2A> méthode de la <xref:System.Drawing.Graphics> classe. Les paramètres de la <xref:System.Drawing.Graphics.DrawArc%2A> méthode sont les mêmes que les paramètres de la <xref:System.Drawing.Graphics.DrawEllipse%2A> (méthode), à ceci près que <xref:System.Drawing.Graphics.DrawArc%2A> nécessite un angle de départ et un angle de balayage. L’exemple suivant dessine un arc avec un angle de départ de 30 degrés et l’angle de balayage de 180 degrés :  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 L’illustration suivante montre l’arc, l’ellipse et le rectangle englobant.  
  
 ![Ellipses et arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Guide pratique pour créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Guide pratique pour créer un stylet](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Guide pratique pour dessiner une forme avec contour](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
