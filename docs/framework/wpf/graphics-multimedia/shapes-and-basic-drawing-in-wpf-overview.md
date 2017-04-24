---
title: "Vue d&#39;ensemble des formes et dessins de base dans WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dessin de base"
  - "objets Shape"
  - "formes, à propos des formes"
  - "dessin de vecteurs, vue d'ensemble"
  - "vecteurs, dessiner"
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Vue d&#39;ensemble des formes et dessins de base dans WPF
Cette rubrique donne une vue d'ensemble de la façon de dessiner avec les objets <xref:System.Windows.Shapes.Shape>.  Un <xref:System.Windows.Shapes.Shape> est un type de <xref:System.Windows.UIElement> qui vous permet de dessiner une forme à l'écran.  Du fait qu'il s'agit d'éléments d'interface graphique, les objets <xref:System.Windows.Shapes.Shape> peuvent être utilisés à l'intérieur d'éléments <xref:System.Windows.Controls.Panel> et de la plupart des contrôles.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre plusieurs couches d'accès aux services graphiques et de rendu.  À la couche supérieure, les objets <xref:System.Windows.Shapes.Shape> sont faciles à utiliser et fournissent de nombreuses fonctionnalités utiles, telles que la disposition et la participation dans le système d'événement [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
   
  
<a name="shapes"></a>   
## Objets de forme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit plusieurs objets <xref:System.Windows.Shapes.Shape> prêt à l'emploi.  Tous les objets de forme héritent de la classe <xref:System.Windows.Shapes.Shape>.  Les objets de forme disponibles incluent <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, et <xref:System.Windows.Shapes.Rectangle>. Les objets <xref:System.Windows.Shapes.Shape> partagent les propriétés communes suivantes.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A> : décrit comment le plan de la forme est peint.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> : décrit l'épaisseur du plan de la forme.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A> : décrit la manière dont l'intérieur de la forme est peint.  
  
-   Propriétés de données pour spécifier des coordonnées et des sommets, mesurés en [pixels indépendants du périphérique](GTMT).  
  
 Du fait qu'ils dérivent de <xref:System.Windows.UIElement>, les objets de forme peuvent être utilisés à l'intérieur de panneaux et de la plupart des contrôles.  Le panneau <xref:System.Windows.Controls.Canvas> est un choix particulièrement judicieux pour créer des dessins complexes, car il prend en charge le positionnement absolu de ses objets enfants.  
  
 La classe <xref:System.Windows.Shapes.Line> vous permet de dessiner une ligne entre deux points.  L'exemple suivant affiche plusieurs méthodes pour spécifier des coordonnées de ligne et des propriétés de trait.  
  
 [!code-xml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 L'image suivante affiche le rendu de <xref:System.Windows.Shapes.Line>.  
  
 ![Illustration d'une ligne](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.png "shape\_ovw\_line2")  
  
 Bien que la classe <xref:System.Windows.Shapes.Line> fournisse une propriété <xref:System.Windows.Shapes.Shape.Fill%2A>, sa définition n'a aucun effet car un <xref:System.Windows.Shapes.Line> n'a aucune zone.  
  
 Une autre forme commune est l'<xref:System.Windows.Shapes.Ellipse>.  Créez une <xref:System.Windows.Shapes.Ellipse> en définissant les propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de la forme.  Pour dessiner un cercle, spécifiez une <xref:System.Windows.Shapes.Ellipse> dont les valeurs <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> sont identiques.  
  
 [!code-xml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 L'image suivant montre un exemple de rendu de <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Illustration d'une ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape\_ovw\_ellipse2")  
  
<a name="paths"></a>   
## Utilisation des chemins d'accès et des géométries  
 La classe <xref:System.Windows.Shapes.Path> vous permet de dessiner des courbes et des formes complexes.  Ces courbes et formes sont décrites en utilisant des objets <xref:System.Windows.Media.Geometry>.  Pour utiliser un <xref:System.Windows.Shapes.Path>, vous créez une <xref:System.Windows.Media.Geometry> et l'utilisez pour définir la propriété <xref:System.Windows.Shapes.Path.Data%2A> de l'objet <xref:System.Windows.Shapes.Path>.  
  
 Le choix d'objets <xref:System.Windows.Media.Geometry> est varié.  Les classes <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>et <xref:System.Windows.Media.EllipseGeometry> décrivent des formes relativement simples.  Pour créer plus de formes complexes ou créer des courbes, utilisez une <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### PathGeometry et PathSegments  
 Les objets <xref:System.Windows.Media.PathGeometry> sont composés d'un ou plusieurs objets <xref:System.Windows.Media.PathFigure>; chaque <xref:System.Windows.Media.PathFigure> représentant une "illustration" ou forme différente.  Chaque <xref:System.Windows.Media.PathFigure> est elle\-même composée d'un ou plusieurs objets <xref:System.Windows.Media.PathSegment>, chacun représentant une partie connectée de l'illustration ou forme.  Les types de segment sont les suivants : <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>et <xref:System.Windows.Media.ArcSegment>.  
  
 Dans l'exemple suivant, un <xref:System.Windows.Shapes.Path> est utilisé pour dessiner une courbe de Bézier quadratique.  
  
 [!code-xml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 L'image suivant affiche la forme rendue.  
  
 ![Illustration d'un chemin d'accès](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.png "shape\_ovw\_path2")  
  
 Pour plus d'informations sur <xref:System.Windows.Media.PathGeometry> et les autres classes <xref:System.Windows.Media.Geometry>, consultez [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### Syntaxe XAML abrégée  
 En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser également une syntaxe abrégée spéciale pour décrire un <xref:System.Windows.Shapes.Path>.  Dans l'exemple suivant, la syntaxe abrégée est utilisée pour dessiner une forme complexe.  
  
```xaml  
<Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 L'image suivante affiche le rendu de <xref:System.Windows.Shapes.Path>.  
  
 ![Illustration d'un chemin d'accès](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.png "shape\_ovw\_path")  
  
 La chaîne d'attribut <xref:System.Windows.Shapes.Path.Data%2A> commence par la commande « move to », indiquée par M, qui définit le point de départ du tracé dans le système de coordonnées du <xref:System.Windows.Controls.Canvas>.  Les paramètres de données <xref:System.Windows.Shapes.Path> respectent la casse.  Le M majuscule indique un emplacement absolu pour le nouveau point actuel.  Un m minuscule indiquerait des coordonnées relatives.  Le premier segment est une [courbe de Bézier](GTMT) cubique qui commence à \(100,200\) et se termine à \(400,175\). Elle est représentée à l'aide des deux points de contrôle \(100,25\) et \(400,350\).  Ce segment est indiqué par la commande C dans la chaîne d'attribut <xref:System.Windows.Shapes.Path.Data%2A>.  Encore une fois, le C majuscule indique un chemin d'accès absolu ; le c minuscule indiquerait un chemin d'accès relatif.  
  
 Le deuxième segment commence par une commande « lineto » horizontale absolue indiquée par H, qui spécifie une ligne dessinée entre le point de terminaison du sous\-tracé précédent \(400,175\) et un nouveau point de terminaison \(280,175\).  Étant donné qu'il s'agit d'une commande « lineto » horizontale, la valeur spécifiée est une coordonnée *d'abscisse*.  
  
 Pour la syntaxe de chemin d'accès complet, consultez la référence <xref:System.Windows.Shapes.Path.Data%2A> et [Créer une forme à l'aide d'un PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## Peindre des formes  
 Les objets <xref:System.Windows.Media.Brush> sont utilisés pour peindre les <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.Fill%2A> d'une forme.  Dans l'exemple suivant, le trait et le remplissage d'une <xref:System.Windows.Shapes.Ellipse> sont indiqués.  Notez que l'entrée valide pour les propriétés de pinceau peuvent être un mot clé ou une valeur de couleur hexadécimale.  Pour plus d'informations sur les mots clés de couleur disponibles, consultez les propriétés de la classe <xref:System.Windows.Media.Colors> dans l'espace de noms <xref:System.Windows.Media>.  
  
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
  
 L'image suivante affiche le rendu de <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.png "shape\_ovw\_ellipsefill")  
  
 Vous pouvez également utiliser la syntaxe d'élément de propriété pour créer explicitement un objet <xref:System.Windows.Media.SolidColorBrush> pour peindre la forme avec une couleur unie.  
  
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
  
 L'illustration suivante montre la forme rendue.  
  
 ![Illustration de SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.png "shape\_ovw\_solidcolorbrush")  
  
 Vous pouvez également peindre le trait d'une forme ou la remplir avec des dégradés, des images, des modèles, etc.  Pour plus d'informations, consultez [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## Formes étirables  
 Les classes <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline> et <xref:System.Windows.Shapes.Rectangle> ont toutes une propriété <xref:System.Windows.Shapes.Shape.Stretch%2A>.  Cette propriété détermine comment le contenu d'un objet <xref:System.Windows.Shapes.Shape> \(la forme à dessiner\) est étiré pour remplir l'espace de disposition de l'objet <xref:System.Windows.Shapes.Shape>.  L'espace de disposition d'un objet <xref:System.Windows.Shapes.Shape> est la quantité d'espace alloué à la <xref:System.Windows.Shapes.Shape> par le système de disposition, à cause d'un paramètre explicite <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>, ou à cause de ses paramètres <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>.  Pour plus d'informations sur la disposition dans Windows Presentation Foundation, consultez la vue d'ensemble [Disposition](../../../../docs/framework/wpf/advanced/layout.md).  
  
 La propriété Stretch peut prendre l'une des valeurs  suivantes :  
  
-   <xref:System.Windows.Media.Stretch> : le contenu de l'objet <xref:System.Windows.Shapes.Shape> n'est pas étiré.  
  
-   <xref:System.Windows.Media.Stretch> : le contenu de l'objet <xref:System.Windows.Shapes.Shape> est étiré pour remplir son espace de disposition.  Les proportions ne sont pas conservées.  
  
-   <xref:System.Windows.Media.Stretch> : le contenu de l'objet <xref:System.Windows.Shapes.Shape> est étiré autant que possible pour remplir son espace de disposition tout en conservant ses proportions d'origine.  
  
-   <xref:System.Windows.Media.Stretch> : le contenu de l'objet <xref:System.Windows.Shapes.Shape> est étiré pour remplir complètement son espace de disposition tout en conservant ses proportions d'origine.  
  
 Notez que lorsque le contenu d'un objet <xref:System.Windows.Shapes.Shape> est étiré, le plan de l'objet <xref:System.Windows.Shapes.Shape> est peint après l'étirement.  
  
 Dans l'exemple suivant, un <xref:System.Windows.Shapes.Polygon> est utilisé pour dessiner un très petit triangle de \(0,0\) à \(0,1\) à \(1,1\).  Les valeurs de l'objet <xref:System.Windows.Shapes.Polygon> \(<xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>\) sont définies sur 100, et sa propriété d'étirement a la valeur Remplissage.  En conséquence, le contenu de l'objet <xref:System.Windows.Shapes.Polygon> \(le triangle\) est étiré pour remplir le plus grand espace.  
  
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
## Transformation de formes  
 La classe <xref:System.Windows.Media.Transform> fournit le moyen de transformer des formes en plans à deux dimensions.  Les différents types de transformations incluent la rotation \(<xref:System.Windows.Media.RotateTransform>\), l'échelle \(<xref:System.Windows.Media.ScaleTransform>\), l'inclinaison \(<xref:System.Windows.Media.SkewTransform>\) et la translation \(<xref:System.Windows.Media.TranslateTransform>\).  
  
 Une transformation commune à s'appliquer à une forme est une rotation.  Pour faire pivoter une forme, créez une <xref:System.Windows.Media.RotateTransform> et spécifiez son <xref:System.Windows.Media.RotateTransform.Angle%2A>.  Un <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 fait pivoter l'élément de 45 degrés dans le sens des aiguilles d'une montre; un angle de 90 fait pivoter l'élément de 90 degrés dans le sens des aiguilles d'une montre; et ainsi de suite.  Définissez les propriétés <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> si vous souhaitez contrôler le point à partir duquel l'élément est pivoté.  Ces valeurs de propriété sont exprimées dans l'espace de coordonnées de l'élément en cours de transformation.  <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> possèdent la valeur par défaut zéro.  Enfin, appliquez la <xref:System.Windows.Media.RotateTransform> à l'élément.  Si vous ne souhaitez pas que la transformation affecte la disposition, définissez la propriété <xref:System.Windows.UIElement.RenderTransform%2A> de la forme.  
  
 Dans l'exemple suivant, une <xref:System.Windows.Media.RotateTransform> est utilisée pour faire pivoter une forme de 45 degrés à partir du coin supérieur gauche de la forme \(0,0\).  
  
 [!code-xml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Dans l'exemple suivant, une autre forme est pivotée de 45 degrés, mais cette fois\-ci, elle est pivotée à partir du point \(25,50\).  
  
 [!code-xml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 L'illustration suivante montre les résultats de l'application des deux transformations.  
  
 ![Rotations de 45 degrés avec différents points centraux](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.png "wcpsdk\_graphicsmm\_rotatetransform45degrees")  
  
 Dans les exemples précédents, une transformation unique a été appliquée à chaque objet de forme.  Pour appliquer plusieurs transformations à une forme \(ou tout autre élément d'interface\), utilisez un <xref:System.Windows.Media.TransformGroup>.  
  
## Voir aussi  
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)