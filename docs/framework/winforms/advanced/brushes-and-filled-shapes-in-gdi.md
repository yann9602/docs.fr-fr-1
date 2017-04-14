---
title: "Pinceaux et remplissage de formes dans GDI+ | Microsoft Docs"
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
  - "pinceaux, GDI+"
  - "pinceaux, dégradé"
  - "formes remplies, GDI+"
  - "GDI+, pinceaux"
  - "GDI+, formes remplies"
  - "pinceaux à couleurs dégradées"
  - "formes, GDI+"
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Pinceaux et remplissage de formes dans GDI+
Une forme fermée \(comme un rectangle ou une ellipse\) comprend un contour et un intérieur.  Le contour est dessiné avec un stylet et l'intérieur est rempli avec un pinceau.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit plusieurs classes de pinceaux pour le remplissage des intérieurs des formes fermées : <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush> et <xref:System.Drawing.Drawing2D.PathGradientBrush>.  Toutes ces classes héritent de la classe <xref:System.Drawing.Brush>.  L'illustration suivante représente un rectangle rempli à l'aide d'un pinceau uni et une ellipse remplie à l'aide d'un pinceau à hachures.  
  
 ![Formes pleines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.png "Aboutgdip02\_art17")  
  
## Pinceaux unis  
 Pour remplir une forme fermée, vous avez besoin d'une instance de la classe <xref:System.Drawing.Graphics> et d'un objet <xref:System.Drawing.Brush>.  L'instance de la classe <xref:System.Drawing.Graphics> fournit des méthodes, telles que <xref:System.Drawing.Graphics.FillRectangle%2A> et <xref:System.Drawing.Graphics.FillEllipse%2A>, et l'objet <xref:System.Drawing.Brush> stocke des attributs de remplissage, par exemple la couleur et le motif.  <xref:System.Drawing.Brush> est passé en tant qu'argument à la méthode de remplissage.  L'exemple de code suivant montre comment remplir une ellipse avec une couleur rouge unie.  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  Dans l'exemple précédent, le pinceau est du type <xref:System.Drawing.SolidBrush> qui hérite de <xref:System.Drawing.Brush>.  
  
## Pinceaux à hachures  
 Lorsque vous remplissez une forme à l'aide d'un pinceau à hachure, vous spécifiez une couleur de premier plan, une couleur d'arrière\-plan et un style de hachures.  La couleur de premier plan est celle des hachures.  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit plus de 50 styles de hachurage. Les trois styles présentés dans l'illustration suivante sont <xref:System.Drawing.Drawing2D.HatchStyle>, <xref:System.Drawing.Drawing2D.HatchStyle> et <xref:System.Drawing.Drawing2D.HatchStyle>.  
  
 ![Formes pleines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.png "Aboutgdip02\_art18")  
  
## Pinceaux à texture  
 Un pinceau à texture vous permet de remplir une forme avec un motif stocké dans une bitmap.  Par exemple, supposez que l'image suivante soit stockée dans un fichier disque `MyTexture.bmp`.  
  
 ![Forme pleine](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.png "Aboutgdip02\_Art19")  
  
 L'exemple de code suivant montre comment remplir une ellipse en répétant l'image stockée dans `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 L'illustration suivante montre l'ellipse remplie.  
  
 ![Forme pleine](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.png "AboutGdip02\_Art20")  
  
## Pinceaux à dégradé  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit deux genres de pinceaux de dégradé : linéaire et de tracé.  Utilisez un pinceau à dégradé linéaire pour remplir une forme avec une couleur qui change graduellement à mesure que vous déplacez le pinceau \(horizontalement, verticalement ou en diagonale\) sur la forme.  L'exemple de code suivant montre comment remplir une ellipse à l'aide d'un pinceau à dégradé horizontal qui passe du bleu au vert en passant de l'extrémité gauche à l'extrémité droite de l'ellipse.  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 L'illustration suivante montre l'ellipse remplie.  
  
 ![Forme pleine](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.png "AboutGdip02\_Art21")  
  
 Un pinceau à dégradé de tracé peut être configuré pour changer de couleur en passant du centre d'une forme à son contour.  
  
 ![Forme pleine](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.png "AboutGdip02\_Art22")  
  
 Les pinceaux à dégradé de tracé offrent une grande souplesse d'utilisation.  Dans l'illustration suivante, le pinceau à dégradé utilisé pour remplir le triangle passe graduellement du rouge au centre à trois couleurs différentes en allant vers les sommets.  
  
 ![Forme pleine](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.png "AboutGdip02\_Art23")  
  
## Voir aussi  
 <xref:System.Drawing.SolidBrush?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=fullName>   
 <xref:System.Drawing.TextureBrush?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Comment : dessiner un rectangle rempli dans un Windows Form](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)   
 [Comment : dessiner une ellipse remplie dans un Windows Form](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)