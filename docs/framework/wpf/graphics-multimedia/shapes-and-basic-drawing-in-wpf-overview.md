---
title: Vue d'ensemble des formes et dessins de base dans WPF
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
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2912215cb8fb0090cef58e0201cc355da1f0bf19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Vue d'ensemble des formes et dessins de base dans WPF
Cette rubrique donne une vue d’ensemble de la façon de dessiner avec <xref:System.Windows.Shapes.Shape> objets. A <xref:System.Windows.Shapes.Shape> est un type de <xref:System.Windows.UIElement> qui vous permet de dessiner une forme à l’écran. Parce qu’ils sont des éléments d’interface utilisateur, <xref:System.Windows.Shapes.Shape> objets peuvent être utilisés à l’intérieur de <xref:System.Windows.Controls.Panel> la plupart des contrôles et éléments.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre plusieurs couches d’accès aux services graphiques et de rendu. À la couche supérieure, <xref:System.Windows.Shapes.Shape> les objets sont faciles à utiliser et fournissent de nombreuses fonctionnalités utiles, telles que la disposition et la participation dans le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] système des événements.  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Objets Shape  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit un certain nombre de prêt à l’emploi <xref:System.Windows.Shapes.Shape> objets.  Tous les objets de forme héritent la <xref:System.Windows.Shapes.Shape> classe. Objets de forme disponibles incluent <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, et <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape>objets partagent les propriétés communes suivantes.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: Décrit comment est peint le contour.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Décrit l’épaisseur du contour de la forme.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: Décrit comment est peint l’intérieur de la forme.  
  
-   Des propriétés de données pour spécifier des coordonnées et des sommets, mesurés en dip (device independent pixel).  
  
 Comme ils dérivent <xref:System.Windows.UIElement>, les objets de forme peuvent être utilisés à l’intérieur de panneaux et de la plupart des contrôles. Le <xref:System.Windows.Controls.Canvas> Panneau de configuration est un choix idéal pour créer des dessins complexes, car il prend en charge le positionnement absolu de ses objets enfants.  
  
 La <xref:System.Windows.Shapes.Line> classe vous permet de tracer une ligne entre deux points. L’exemple suivant montre plusieurs façons de spécifier les propriétés du trait et les coordonnées de la ligne.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 L’illustration suivante montre le rendu <xref:System.Windows.Shapes.Line>.  
  
 ![Illustration de la ligne](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Bien que le <xref:System.Windows.Shapes.Line> classe ne fournit pas un <xref:System.Windows.Shapes.Shape.Fill%2A> paramètre de la propriété, il n’a aucun effet, car un <xref:System.Windows.Shapes.Line> n’a aucune zone.  
  
 Une autre forme commune est le <xref:System.Windows.Shapes.Ellipse>.  Créer un <xref:System.Windows.Shapes.Ellipse> en définissant la forme <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés. Pour tracer un cercle, vous devez spécifier un <xref:System.Windows.Shapes.Ellipse> dont <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> les valeurs sont égales.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 L’illustration suivante montre un exemple de rendu <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Illustration d’une ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Utilisation des tracés et des géométries  
 La <xref:System.Windows.Shapes.Path> classe vous permet de dessiner des courbes et formes complexes. Ces courbes et formes sont décrites à l’aide de <xref:System.Windows.Media.Geometry> objets. Pour utiliser un <xref:System.Windows.Shapes.Path>, vous créez un <xref:System.Windows.Media.Geometry> et utilisez-la pour définir le <xref:System.Windows.Shapes.Path> l’objet <xref:System.Windows.Shapes.Path.Data%2A> propriété.  
  
 Il existe une multitude de <xref:System.Windows.Media.Geometry> choix d’objets. Le <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, et <xref:System.Windows.Media.EllipseGeometry> classes décrivent des formes relativement simples. Pour créer des formes plus complexes ou créer des courbes, utilisez un <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>Éléments PathGeometry et PathSegments  
 <xref:System.Windows.Media.PathGeometry>les objets sont constitués d’un ou plusieurs <xref:System.Windows.Media.PathFigure> objets ; chaque <xref:System.Windows.Media.PathFigure> représente une forme ou un autre « figure ». Chaque <xref:System.Windows.Media.PathFigure> elle-même se compose d’un ou plusieurs <xref:System.Windows.Media.PathSegment> d’objets, chacun représentant une partie connectée de l’illustration ou forme. Les types de segment sont les suivants : <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, et <xref:System.Windows.Media.ArcSegment>.  
  
 Dans l’exemple suivant, un <xref:System.Windows.Shapes.Path> est utilisé pour tracer une courbe de Bézier quadratique.  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 L’illustration suivante montre le rendu de la forme.  
  
 ![Illustration du tracé](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Pour plus d’informations sur <xref:System.Windows.Media.PathGeometry> et l’autre <xref:System.Windows.Media.Geometry> des classes, consultez le [vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>Syntaxe XAML abrégée  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez également utiliser une syntaxe abrégée spéciale pour décrire un <xref:System.Windows.Shapes.Path>. Dans l’exemple suivant, la syntaxe abrégée est utilisée pour dessiner une forme complexe.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 L’illustration suivante montre un rendu <xref:System.Windows.Shapes.Path>.  
  
 ![Illustration du tracé](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 Le <xref:System.Windows.Shapes.Path.Data%2A> chaîne d’attribut commence avec la commande « moveto », indiquée par M, qui définit le point de départ pour le chemin d’accès dans le système de coordonnées de la <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path>paramètres de données respectent la casse. Le M majuscule indique un emplacement absolu pour le nouveau point actuel. Un m minuscule indiquerait des coordonnées relatives. Le premier segment est une courbe de Bézier cubique commençant à (100,200) et se terminant à (400,175), tracée en utilisant les deux points de contrôle (100,25) et (400,350). Ce segment est indiqué par la commande C dans la <xref:System.Windows.Shapes.Path.Data%2A> chaîne d’attribut. Là encore, le C majuscule indique un tracé absolu ; le c minuscule indiquerait un tracé relatif.  
  
 Le deuxième segment commence par une commande H « lineto » horizontale absolue, qui indique une ligne tracée à partir du point de fin du sous-tracé précédent (400,175) vers un nouveau point de fin (280,175). S’agissant d’une commande « lineto » horizontale, la valeur spécifiée est un *x*-coordonner.  
  
 Pour connaître la syntaxe de chemin d’accès complet, consultez la <xref:System.Windows.Shapes.Path.Data%2A> référence et [créer une forme à l’aide de PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Peindre des formes  
 <xref:System.Windows.Media.Brush>objets sont utilisés pour peindre la forme <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.Fill%2A>. Dans l’exemple suivant, le trait et le remplissage d’un <xref:System.Windows.Shapes.Ellipse> sont spécifiés. Notez que les entrées valides pour les propriétés de pinceau peuvent être une valeur de couleur hexadécimale ou un mot clé de couleur. Pour plus d’informations sur les mots clés de couleur disponibles, consultez les propriétés de la <xref:System.Windows.Media.Colors> classe dans le <xref:System.Windows.Media> espace de noms.  
  
```  
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 L’illustration suivante montre le rendu <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Une ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Ou bien, vous pouvez utiliser la syntaxe d’élément de propriété pour créer explicitement un <xref:System.Windows.Media.SolidColorBrush> objet pour peindre la forme avec une couleur unie.  
  
```  
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 L’illustration suivante montre le rendu de la forme.  
  
 ![Illustration de SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Vous pouvez également peindre le trait ou le remplissage d’une forme avec des dégradés, des images, des motifs, etc. Pour plus d’informations, consultez la [peinture avec des couleurs unies et vue d’ensemble des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Formes étirables  
 Le <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, et <xref:System.Windows.Shapes.Rectangle> classes ont tous un <xref:System.Windows.Shapes.Shape.Stretch%2A> propriété. Cette propriété détermine comment un <xref:System.Windows.Shapes.Shape> le contenu de l’objet (la forme à dessiner) est étiré pour remplir le <xref:System.Windows.Shapes.Shape> espace de disposition de l’objet. A <xref:System.Windows.Shapes.Shape> espace de disposition de l’objet est la quantité d’espace la <xref:System.Windows.Shapes.Shape> est allouée par le système de disposition, en raison soit explicite <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> paramètre ou à cause de son <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> paramètres. Pour plus d’informations sur la mise en page dans Windows Presentation Foundation, consultez [disposition](../../../../docs/framework/wpf/advanced/layout.md) vue d’ensemble.  
  
 La propriété Stretch peut prendre les valeurs suivantes :  
  
-   <xref:System.Windows.Media.Stretch.None>: Le <xref:System.Windows.Shapes.Shape> contenu de l’objet n’est pas étendue.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Le <xref:System.Windows.Shapes.Shape> contenu de l’objet est étiré pour remplir son espace de disposition.  Les proportions ne sont pas conservées.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Le <xref:System.Windows.Shapes.Shape> contenu de l’objet est étiré autant que possible pour remplir son espace de disposition tout en conservant ses proportions d’origine.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Le <xref:System.Windows.Shapes.Shape> contenu de l’objet est étiré pour remplir complètement son espace de disposition tout en conservant ses proportions d’origine.  
  
 Notez que, lorsqu’un <xref:System.Windows.Shapes.Shape> contenu de l’objet est étiré, le <xref:System.Windows.Shapes.Shape> plan de l’objet est peint après l’étirement.  
  
 Dans l’exemple suivant, un <xref:System.Windows.Shapes.Polygon> est utilisé pour dessiner un très petit triangle de (0,0) à (0,1) à (1,1). Le <xref:System.Windows.Shapes.Polygon> l’objet <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> sont définies sur 100, et sa propriété d’étirement a la valeur de remplissage. Par conséquent, le <xref:System.Windows.Shapes.Polygon> le contenu de l’objet (triangle) est étiré pour remplir le plus grand espace.  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
...  
```  
  
<a name="transforms"></a>   
## <a name="transforming-shapes"></a>Transformer des formes  
 La <xref:System.Windows.Media.Transform> classe fournit les moyens permettant de transformer des formes dans un plan à deux dimensions.  Les différents types de transformations incluent la rotation (<xref:System.Windows.Media.RotateTransform>), l’échelle (<xref:System.Windows.Media.ScaleTransform>), l’inclinaison (<xref:System.Windows.Media.SkewTransform>) et la translation (<xref:System.Windows.Media.TranslateTransform>).  
  
 Une transformation courante à appliquer à une forme est la rotation.  Pour faire pivoter une forme, vous devez créer un <xref:System.Windows.Media.RotateTransform> et spécifiez son <xref:System.Windows.Media.RotateTransform.Angle%2A>. Un <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 fait pivoter l’élément de 45 degrés dans le sens horaire ; un angle de 90 fait pivoter l’élément de 90 degrés dans le sens horaire ; et ainsi de suite. Définir le <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> si vous souhaitez contrôler le point de rotation de l’élément sur lequel les propriétés. Ces valeurs de propriété sont exprimées dans l’espace de coordonnées de l’élément que vous êtes en train de transformer. <xref:System.Windows.Media.RotateTransform.CenterX%2A>et <xref:System.Windows.Media.RotateTransform.CenterY%2A> ont les valeurs par défaut de zéro. Enfin, appliquez le <xref:System.Windows.Media.RotateTransform> à l’élément. Si vous ne voulez pas que la transformation affecte la disposition, définissez la forme <xref:System.Windows.UIElement.RenderTransform%2A> propriété.  
  
 Dans l’exemple suivant, un <xref:System.Windows.Media.RotateTransform> est utilisé pour faire pivoter une forme de 45 degrés sur en la forme haut à gauche (0,0).  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Dans l’exemple suivant, une autre forme effectue une rotation de 45 degrés, mais cette fois-ci par rapport au point (25,50).  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 L’illustration suivante montre les résultats de l’application des deux transformations.  
  
 ![rotations de 45 degrés par rapport à différents points centraux](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Dans les exemples précédents, une transformation unique a été appliquée à chaque objet Shape. Pour appliquer plusieurs transformations à une forme (ou tout autre élément d’interface utilisateur), utilisez un <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Procédure pas à pas : ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
