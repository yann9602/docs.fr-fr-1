---
title: "Courbes ouvertes et ferm&#233;es dans GDI+ | Microsoft Docs"
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
  - "courbes"
  - "courbes, dessiner"
  - "courbes, remplir"
  - "GDI+, courbes"
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Courbes ouvertes et ferm&#233;es dans GDI+
L'illustration suivante représente deux courbes dont l'une est ouverte et l'autre fermée.  
  
 ![Courbes ouvertes et fermées](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.png "Aboutgdip02\_art24")  
  
## Interface managée pour les courbes  
 Les courbes fermées ont un intérieur qui peut être rempli à l'aide d'un pinceau.  La classe <xref:System.Drawing.Graphics> de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit les méthodes suivantes pour le remplissage de formes fermées et de courbes : <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A> et <xref:System.Drawing.Graphics.FillRegion%2A>.  Lorsque vous appelez une de ces méthodes, vous devez lui passer un type de pinceau précis \(<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush> ou <xref:System.Drawing.Drawing2D.PathGradientBrush>\) en tant qu'argument.  
  
 La méthode <xref:System.Drawing.Graphics.FillPie%2A> est associée à la méthode <xref:System.Drawing.Graphics.DrawArc%2A>.  De même que la méthode <xref:System.Drawing.Graphics.DrawArc%2A> dessine une partie du contour d'une ellipse, la méthode <xref:System.Drawing.Graphics.FillPie%2A> remplit une portion de l'intérieur d'une ellipse.  L'exemple suivant dessine un arc et remplit la portion correspondante de l'intérieur de l'ellipse :  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 L'illustration suivante représente l'arc et le secteur rempli.  
  
 ![Courbes ouvertes et fermées](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.png "Aboutgdip02\_art25")  
  
 La méthode <xref:System.Drawing.Graphics.FillClosedCurve%2A> est associée à la méthode <xref:System.Drawing.Graphics.DrawClosedCurve%2A>.  Ces deux méthodes ferment automatiquement la courbe en reliant le point de départ et le point d'arrivée.  L'exemple suivant dessine une courbe qui passe par les points \(0, 0\), \(60, 20\) et \(40, 50\).  Ensuite, la courbe est fermée automatiquement par liaison du point \(40, 50\) au point de départ \(0, 0\) et l'intérieur est rempli à l'aide d'une couleur unie.  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 La méthode <xref:System.Drawing.Graphics.FillPath%2A> remplit l'intérieur des différents éléments d'un tracé.  Si un tracé comprend un élément qui ne forme pas une courbe fermée ou une forme, la méthode <xref:System.Drawing.Graphics.FillPath%2A> ferme automatiquement cet élément et le remplit.  L'exemple suivant dessine et remplit un tracé constitué d'un arc, d'une spline cardinale, d'une chaîne et d'un secteur.  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 L'illustration suivante représente ce tracé avec et sans le remplissage uni.  Notez que la méthode <xref:System.Drawing.Graphics.DrawPath%2A> ne remplit pas le texte de la chaîne mais l'encadre.  La méthode qui permet de peindre l'intérieur des caractères de la chaîne est <xref:System.Drawing.Graphics.FillPath%2A>.  
  
 ![Chaîne dans un tracé](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.png "Aboutgdip02\_art26")  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Point?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [Génération et dessin de tracés](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)