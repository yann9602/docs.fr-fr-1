---
title: Vue d'ensemble de Geometry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a10e74342141f8ef6664cc424552dc173d9b0f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="geometry-overview"></a>Vue d'ensemble de Geometry
Cette vue d’ensemble décrit comment utiliser le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> classes pour décrire les formes. Cette rubrique compare également les différences entre <xref:System.Windows.Media.Geometry> objets et <xref:System.Windows.Shapes.Shape> éléments.  
  
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Qu’est-ce qu’une géométrie ?  
 Le <xref:System.Windows.Media.Geometry> classe et les classes qui dérivent, telles que <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, et <xref:System.Windows.Media.CombinedGeometry>, vous permettent de décrire la géométrie d’une forme 2D. Ces descriptions géométriques ont de nombreuses utilisations, telles que la définition d’une forme à peindre à l’écran ou la définition d’un test de positionnement et de zones de découpage. Vous pouvez également utiliser une géométrie pour définir un tracé d’animation.  
  
 <xref:System.Windows.Media.Geometry>objets peuvent être simples, tels que des rectangles et des cercles ou composites, créés à partir de deux ou plusieurs objets de géométrie.  Les géométries plus complexes peuvent être créées à l’aide de la <xref:System.Windows.Media.PathGeometry> et <xref:System.Windows.Media.StreamGeometry> classes, qui vous permettent de décrire des arcs et des courbes.  
  
 Car un <xref:System.Windows.Media.Geometry> est un type de <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> objets fournissent plusieurs fonctionnalités spéciales : ils peuvent être déclarés en tant que [ressources](../../../../docs/framework/wpf/advanced/xaml-resources.md), partagés entre plusieurs objets, définis en lecture seule pour améliorer les performances, clonés, et rendus thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par <xref:System.Windows.Freezable> , consultez la [vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Géométries et Formes  
 Le <xref:System.Windows.Media.Geometry> et <xref:System.Windows.Shapes.Shape> classes apparemment similaires en ce qu’elles décrivent les formes 2D (comparer <xref:System.Windows.Media.EllipseGeometry> et <xref:System.Windows.Shapes.Ellipse> par exemple), mais il existe des différences importantes.  
  
 Pour un, le <xref:System.Windows.Media.Geometry> hérite de la classe le <xref:System.Windows.Freezable> classe lors de la <xref:System.Windows.Shapes.Shape> hérite de la classe <xref:System.Windows.FrameworkElement>. Étant donné que ce sont des éléments, <xref:System.Windows.Shapes.Shape> objets peuvent se rendre et participer au système de disposition, tandis que <xref:System.Windows.Media.Geometry> aux objets.  
  
 Bien que <xref:System.Windows.Shapes.Shape> objets sont plus facilement utilisables que <xref:System.Windows.Media.Geometry> objets <xref:System.Windows.Media.Geometry> objets sont plus souple. Pendant un <xref:System.Windows.Shapes.Shape> objet utilisé pour afficher les graphiques 2D, un <xref:System.Windows.Media.Geometry> objet peut être utilisé pour définir la région géométrique pour les graphiques 2D, définir une région pour le découpage ou définir une région pour le test de positionnement, par exemple.  
  
### <a name="the-path-shape"></a>La forme Tracé  
 Un <xref:System.Windows.Shapes.Shape>, le <xref:System.Windows.Shapes.Path> classe utilise en fait un <xref:System.Windows.Media.Geometry> pour décrire son contenu. En définissant le <xref:System.Windows.Shapes.Path.Data%2A> propriété de la <xref:System.Windows.Shapes.Path> avec un <xref:System.Windows.Media.Geometry> et en définissant son <xref:System.Windows.Shapes.Shape.Fill%2A> et <xref:System.Windows.Shapes.Shape.Stroke%2A> propriétés, vous pouvez effectuer le rendu un <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Propriétés courantes qui acceptent une géométrie  
 Dans les sections précédentes, il était indiqué que les objets géométriques peuvent être utilisés avec d’autres objets pour diverses raisons, telles que le dessin de formes, l’animation et le découpage. Le tableau suivant répertorie plusieurs classes qui ont des propriétés qui acceptent un <xref:System.Windows.Media.Geometry> objet.  
  
|Type|Propriété|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Types de géométrie simples  
 La classe de base pour toutes les géométries est la classe abstraite <xref:System.Windows.Media.Geometry>.  Les classes qui dérivent de la <xref:System.Windows.Media.Geometry> classe peut être groupé en gros en trois catégories : géométries simples, géométries de tracés et géométries composites.  
  
 Classes de géométrie simple incluent <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, et <xref:System.Windows.Media.EllipseGeometry> et sont utilisés pour créer des formes géométriques de base, telles que des lignes, des rectangles et des cercles.  
  
-   A <xref:System.Windows.Media.LineGeometry> est défini en spécifiant le point de départ de la ligne et le point de terminaison.  
  
-   A <xref:System.Windows.Media.RectangleGeometry> est défini avec un <xref:System.Windows.Rect> structure qui spécifie sa position relative et sa hauteur et sa largeur. Vous pouvez créer un rectangle arrondi en définissant le <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> et <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> propriétés.  
  
-   Un <xref:System.Windows.Media.EllipseGeometry> est définie par un point central, un rayon x et un rayon y.  Les exemples suivants montrent comment créer des géométries simples pour le rendu et le découpage.  
  
 Ces mêmes formes, ainsi que des formes plus complexes, peuvent être créés en utilisant un <xref:System.Windows.Media.PathGeometry> ou en combinant des objets géométriques ensemble, mais ces classes fournissent un moyen plus simple de générer ces formes géométriques de base.  
  
 L’exemple suivant montre comment créer et restituer un <xref:System.Windows.Media.LineGeometry>.  Comme indiqué précédemment, un <xref:System.Windows.Media.Geometry> objet ne peut pas se dessiner lui-même, par conséquent, l’exemple utilise un <xref:System.Windows.Shapes.Path> forme pour restituer la ligne.  Car une ligne n’a pas de zone, définition de la <xref:System.Windows.Shapes.Shape.Fill%2A> propriété de la <xref:System.Windows.Shapes.Path> n’a aucun effet ; au lieu de cela, uniquement le <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriétés sont spécifiées. L’illustration suivante montre la sortie de l’exemple.  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Une LineGeometry tracée de (10,20) à (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 L’exemple suivant montre comment créer et restituer un <xref:System.Windows.Media.EllipseGeometry>.  Les jeux d’exemples le <xref:System.Windows.Media.EllipseGeometry.Center%2A> de la <xref:System.Windows.Media.EllipseGeometry> est définie sur le point de `50,50` et le rayon x et le rayon y sont définis sur `50`, ce qui crée un cercle avec un diamètre de 100.  L’intérieur de l’ellipse est peint en affectant une valeur à la propriété de remplissage de l’élément chemin d’accès, dans ce cas <xref:System.Windows.Media.Brushes.Gold%2A>. L’illustration suivante montre la sortie de l’exemple.  
  
 ![EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Une EllipseGeometry dessinée à (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 L’exemple suivant montre comment créer et restituer un <xref:System.Windows.Media.RectangleGeometry>.  La position et les dimensions du rectangle sont définies par un <xref:System.Windows.Rect> structure. La position est définie sur `50,50` et la hauteur et la largeur sont définies sur `25`, ce qui crée un carré. L’illustration suivante montre la sortie de l’exemple.  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Une RectangleGeometry dessinée à 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 L’exemple suivant montre comment utiliser une <xref:System.Windows.Media.EllipseGeometry> en tant que la zone de découpage pour une image.  Un <xref:System.Windows.Controls.Image> objet est défini avec un <xref:System.Windows.FrameworkElement.Width%2A> de 200 et un <xref:System.Windows.FrameworkElement.Height%2A> de 150.  Un <xref:System.Windows.Media.EllipseGeometry> avec un <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> valeur de 100, une <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> valeur de 75 et un <xref:System.Windows.Media.EllipseGeometry.Center%2A> de 100,75 a la valeur la <xref:System.Windows.UIElement.Clip%2A> propriété de l’image.  Seule la partie de l’image qui se trouve dans la zone de l’ellipse s’affiche. L’illustration suivante montre la sortie de l’exemple.  
  
 ![Une Image avec et sans écrêtage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Une EllipseGeometry utilisée pour découper une commande Image  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Géométries de tracés  
 Le <xref:System.Windows.Media.PathGeometry> classe et son équivalent léger, la <xref:System.Windows.Media.StreamGeometry> de classe, de fournir les moyens permettant de décrire plusieurs illustrations complexes composées d’arcs, de courbes et de lignes.  
  
 Au cœur d’un <xref:System.Windows.Media.PathGeometry> est une collection de <xref:System.Windows.Media.PathFigure> objets, ce nom, car chaque illustration décrit une forme discrète dans le <xref:System.Windows.Media.PathGeometry>. Chaque <xref:System.Windows.Media.PathFigure> elle-même se compose d’un ou plusieurs <xref:System.Windows.Media.PathSegment> objets, qui décrivent chacune un segment de l’illustration.  
  
 Il existe un grand nombre de segments.  
  
|Type de segment|Description|Exemple|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Crée un arc elliptique entre deux points.|[Créer un arc elliptique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Crée une courbe de Bézier cubique entre deux points.|[Créer une courbe de Bézier cubique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Crée une ligne entre deux points.|[Créer un LineSegment dans une PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Crée une série de courbes de Bézier cubiques.|Consultez le <xref:System.Windows.Media.PolyBezierSegment> page type.|  
|<xref:System.Windows.Media.PolyLineSegment>|Crée une série de lignes.|Consultez le <xref:System.Windows.Media.PolyLineSegment> page type.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Crée une série de courbes de Bézier quadratiques.|Consultez le <xref:System.Windows.Media.PolyQuadraticBezierSegment> page.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Crée une courbe de Bézier quadratique.|[Créer une courbe de Bézier quadratique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).|  
  
 Les segments d’un <xref:System.Windows.Media.PathFigure> sont combinés en une forme géométrique unique avec le point de terminaison de chaque segment comme point de départ du segment suivant. Le <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriété d’un <xref:System.Windows.Media.PathFigure> Spécifie le point à partir de laquelle le premier segment est dessiné. Chaque segment suivant démarre au point de fin du segment précédent. Par exemple, une ligne verticale de `10,50` à `10,150` peut être défini en définissant le <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriété `10,50` et la création d’un <xref:System.Windows.Media.LineSegment> avec un <xref:System.Windows.Media.LineSegment.Point%2A> définition de la propriété de `10,150`.  
  
 L’exemple suivant crée un simple <xref:System.Windows.Media.PathGeometry> constitué d’un seul <xref:System.Windows.Media.PathFigure> avec un <xref:System.Windows.Media.LineSegment> et affiche à l’aide d’un <xref:System.Windows.Shapes.Path> élément. Le <xref:System.Windows.Media.PathFigure> l’objet <xref:System.Windows.Media.PathFigure.StartPoint%2A> a la valeur `10,20` et un <xref:System.Windows.Media.LineSegment> est défini avec un point de terminaison `100,130`. L’illustration suivante montre le <xref:System.Windows.Media.PathGeometry> créé par cet exemple.  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Une PathGeometry contenant un seul LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Il est intéressant de comparer cet exemple avec le précédent <xref:System.Windows.Media.LineGeometry> exemple.  La syntaxe utilisée pour un <xref:System.Windows.Media.PathGeometry> est beaucoup plus longue que celle utilisée pour un simple <xref:System.Windows.Media.LineGeometry>, et il peut être plus judicieux d’utiliser le <xref:System.Windows.Media.LineGeometry> classe dans ce cas, mais la syntaxe détaillée de la <xref:System.Windows.Media.PathGeometry> permet extrêmement élaborées et complexes régions géométriques.  
  
 Les géométries plus complexes peuvent être créées à l’aide d’une combinaison de <xref:System.Windows.Media.PathSegment> objets.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.BezierSegment>, un <xref:System.Windows.Media.LineSegment>et un <xref:System.Windows.Media.ArcSegment> pour créer une forme. L’exemple crée d’abord une courbe de Bézier cubique en définissant quatre points : un point de départ, qui est le point de terminaison du segment précédent, un point de terminaison (<xref:System.Windows.Media.BezierSegment.Point3%2A>), et deux points de contrôle (<xref:System.Windows.Media.BezierSegment.Point1%2A> et <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Les deux points de contrôle d’une courbe de Bézier cubique se comportent comme des aimants qui attirent vers eux des parties de ce qui devrait normalement être une ligne droite, produisant ainsi une courbe. Le premier point de contrôle, <xref:System.Windows.Media.BezierSegment.Point1%2A>, affecte le début partie de la courbe ; le deuxième point de contrôle, <xref:System.Windows.Media.BezierSegment.Point2%2A>, affecte la portion de fin de la courbe.  
  
 L’exemple ajoute ensuite un <xref:System.Windows.Media.LineSegment>, qui est dessiné entre le point de terminaison de l’exemple précédent <xref:System.Windows.Media.BezierSegment> qui précédait au point spécifié par son <xref:System.Windows.Media.LineSegment> propriété.  
  
 L’exemple ajoute ensuite un <xref:System.Windows.Media.ArcSegment>, qui est dessiné à partir du point de fin de l’exemple précédent <xref:System.Windows.Media.LineSegment> au point spécifié par son <xref:System.Windows.Media.ArcSegment.Point%2A> propriété. L’exemple spécifie également rayons de l’arc x et y-(<xref:System.Windows.Media.ArcSegment.Size%2A>), un angle de rotation (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), un indicateur qui indique la taille l’angle de l’arc résultant doit être (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) et une valeur indiquant la direction dans laquelle l’arc est dessiné (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). L’illustration suivante montre la forme créée par cet exemple.  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Les géométries encore plus complexes peuvent être créées en utilisant plusieurs <xref:System.Windows.Media.PathFigure> objets au sein d’un <xref:System.Windows.Media.PathGeometry>.  
  
 L’exemple suivant crée un <xref:System.Windows.Media.PathGeometry> avec deux <xref:System.Windows.Media.PathFigure> objets, chacun d’eux contient plusieurs <xref:System.Windows.Media.PathSegment> objets.  Le <xref:System.Windows.Media.PathFigure> à partir de l’exemple ci-dessus et un <xref:System.Windows.Media.PathFigure> avec un <xref:System.Windows.Media.PolyLineSegment> et <xref:System.Windows.Media.QuadraticBezierSegment> sont utilisés.  A <xref:System.Windows.Media.PolyLineSegment> est défini avec un tableau de points et les <xref:System.Windows.Media.QuadraticBezierSegment> est défini avec un point de contrôle et un point de terminaison. L’illustration suivante montre la forme créée par cet exemple.  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry avec plusieurs figures  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Comme le <xref:System.Windows.Media.PathGeometry> (classe), un <xref:System.Windows.Media.StreamGeometry> définit une forme géométrique complexe pouvant contenir des courbes, des arcs et des lignes. Contrairement à un <xref:System.Windows.Media.PathGeometry>, le contenu d’un <xref:System.Windows.Media.StreamGeometry> ne prennent pas en charge la liaison de données, les animations ni les modifications. Utilisez un <xref:System.Windows.Media.StreamGeometry> lorsque vous devez décrire une géométrie complexe, mais ne souhaitez pas que la surcharge de prendre en charge la liaison de données, les animations ni les modifications. En raison de son efficacité, la <xref:System.Windows.Media.StreamGeometry> classe est un bon choix pour décrire des ornements.  
  
 Pour obtenir un exemple, consultez [Créer une forme à l’aide d’une StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Syntaxe XAML pour les tracés  
 Le <xref:System.Windows.Media.PathGeometry> et <xref:System.Windows.Media.StreamGeometry> types prennent en charge un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] à l’aide d’une série spéciale de déplacement de syntaxe d’attribut et les commandes de dessin. Pour plus d’informations, consultez [Syntaxe XAML pour les tracés](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Géométries composites  
 Objets de géométrie composite peuvent être créés à l’aide un <xref:System.Windows.Media.GeometryGroup>, un <xref:System.Windows.Media.CombinedGeometry>, ou en appelant la méthode statique <xref:System.Windows.Media.Geometry> méthode <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
-   Le <xref:System.Windows.Media.CombinedGeometry> objet et la <xref:System.Windows.Media.Geometry.Combine%2A> méthode effectue une opération booléenne pour combiner la zone définie par deux géométries. <xref:System.Windows.Media.Geometry>les objets qui n’ont aucune zone sont ignorés. Seuls deux <xref:System.Windows.Media.Geometry> objets peuvent être combinés (bien que ces deux géométries peuvent également être composites).  
  
-   Le <xref:System.Windows.Media.GeometryGroup> classe crée un amalgame de la <xref:System.Windows.Media.Geometry> objets qu’il contient sans combiner leur zone. Un nombre quelconque de <xref:System.Windows.Media.Geometry> objets peuvent être ajoutés à un <xref:System.Windows.Media.GeometryGroup>. Pour obtenir un exemple, consultez [Créer une forme composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md).  
  
 Comme ils n’effectuent pas une opération d’association, à l’aide <xref:System.Windows.Media.GeometryGroup> objets apporte des avantages de performances sur de <xref:System.Windows.Media.CombinedGeometry> objets ou <xref:System.Windows.Media.Geometry.Combine%2A> (méthode).  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Géométries combinées  
 La section précédente a mentionné le <xref:System.Windows.Media.CombinedGeometry> objet et la <xref:System.Windows.Media.Geometry.Combine%2A> méthode combiner l’aire définie par les géométries qu’ils contiennent. Le <xref:System.Windows.Media.GeometryCombineMode> énumération spécifie la manière dont les géométries sont combinées. Les valeurs possibles pour le <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> propriété sont : <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, et <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 Dans l’exemple suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode combiné de Union.  Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Résultats du mode d’association Union](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 Dans l’exemple suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode combiné de <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Résultats du mode d’association Xor](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Pour obtenir des exemples supplémentaires, consultez [Créer une forme composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md) et [Créer une géométrie combinée](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Fonctionnalités Freezable  
 Car il hérite de la <xref:System.Windows.Freezable> (classe), le <xref:System.Windows.Media.Geometry> classe fournit plusieurs fonctionnalités spéciales : <xref:System.Windows.Media.Geometry> objets peuvent être déclarés en tant que [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md), partagés entre plusieurs objets, définis en lecture seule pour améliorer performances, clonés et rendus thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par <xref:System.Windows.Freezable> , consultez la [vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Autres fonctionnalités de géométrie  
 La <xref:System.Windows.Media.Geometry> classe fournit également des méthodes utilitaires utiles, telles que les éléments suivants :  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A>-Obtient la zone de la <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A>-Détermine si la géométrie contient une autre <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A>-Détermine si le trait d’un <xref:System.Windows.Media.Geometry> contient un point spécifié.  
  
 Consultez la <xref:System.Windows.Media.Geometry> classe pour une liste complète de ses méthodes.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Geometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Syntaxe XAML pour les tracés](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d’ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Vue d’ensemble des objets de dessin](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
