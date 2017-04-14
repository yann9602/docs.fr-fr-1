---
title: "Vue d&#39;ensemble des transformations | Microsoft Docs"
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
  - "classes de transformation 2D"
  - "classes, transformation 2D"
  - "objets FrameworkElement, faire pivoter"
  - "objets FrameworkElement, mettre à l'échelle"
  - "objets FrameworkElement, incliner"
  - "objets FrameworkElement, traduire"
  - "classes de transformation, 2D"
  - "transformations, à propos des transformations"
  - "Transformations, à propos de Transforms"
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Vue d&#39;ensemble des transformations
Cette rubrique décrit comment utiliser les classes <xref:System.Windows.Media.Transform> [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] pour faire pivoter, mettre à l'échelle, déplacer \(appliquer une translation\) et incliner des objets <xref:System.Windows.FrameworkElement>.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="whatIsATransformSection"></a>   
## Qu'est\-ce qu'une transformation ?  
 Un <xref:System.Windows.Media.Transform> définit la manière de mapper, ou transformer, des points d'un espace de coordonnées à un autre.  Ce mappage est décrit par une <xref:System.Windows.Media.Matrix> de transformation, c'est\-à\-dire une collection de trois lignes avec trois colonnes de valeurs <xref:System.Double>.  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] utilise des matrices ligne\-champ.  Les vecteurs sont exprimés sous la forme ligne\-vecteurs, et non colonne\-vecteurs.  
  
 Le tableau suivant montre la structure d'une matrice [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### Matrice de transformation 2D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Valeur par défaut : 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Valeur par défaut : 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Valeur par défaut : 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Valeur par défaut : 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Valeur par défaut : 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Valeur par défaut : 0.0|1.0|  
  
 En manipulant des valeurs de matrice, vous pouvez faire pivoter, mettre à l'échelle, incliner et déplacer \(appliquer une translation\) un objet.  Par exemple, si vous remplacez la valeur de la troisième ligne de la première colonne \(la valeur <xref:System.Windows.Media.Matrix.OffsetX%2A>\) par 100, vous pouvez l'utiliser pour déplacer un objet de 100 unités sur l'axe x.  Si vous remplacez la valeur de la deuxième ligne de la deuxième colonne par 3, vous pouvez l'utiliser pour étirer un objet à trois fois sa hauteur actuelle.  Si vous modifiez les deux valeurs, vous déplacez l'objet de 100 unités le long de l'axe X et étirez sa hauteur selon un facteur de 3.  Étant donné que [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] prend uniquement en charge les transformations affines, les valeurs dans la colonne de droite sont toujours 0, 0, 1.  
  
 Bien que [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] vous permette de manipuler directement des valeurs de matrice, il fournit également plusieurs classes <xref:System.Windows.Media.Transform> qui vous permettent de transformer un objet sans connaître la configuration de la structure de la matrice sous\-jacente.  Par exemple, la classe <xref:System.Windows.Media.ScaleTransform> vous permet de mettre un objet à l'échelle en définissant ses propriétés <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, au lieu de manipuler une matrice de transformation.  La classe <xref:System.Windows.Media.RotateTransform> vous permet également de faire pivoter un objet en définissant simplement sa propriété <xref:System.Windows.Media.RotateTransform.Angle%2A>.  
  
<a name="transformClassesSection"></a>   
## Classes de transformation  
 Pour les opérations de transformation courantes, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] fournit les classes <xref:System.Windows.Media.Transform> [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] suivantes :  
  
|Classe|Description|Exemple|Illustration|  
|------------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Fait pivoter un élément selon l'<xref:System.Windows.Media.RotateTransform.Angle%2A> spécifié.|[Faire pivoter un objet](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)||  
|<xref:System.Windows.Media.ScaleTransform>|Met à l'échelle un élément selon les valeurs <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> spécifiées.|[Mettre à l'échelle un élément](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)||  
|<xref:System.Windows.Media.SkewTransform>|Incline un élément selon les valeurs <xref:System.Windows.Media.SkewTransform.AngleX%2A> et <xref:System.Windows.Media.SkewTransform.AngleY%2A> spécifiées.|[Incliner un élément](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)||  
|<xref:System.Windows.Media.TranslateTransform>|Déplace \(applique une translation\) un élément selon les valeurs <xref:System.Windows.Media.TranslateTransform.X%2A> et <xref:System.Windows.Media.TranslateTransform.Y%2A> spécifiées.|[Traduire un élément](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)||  
  
 Pour créer des transformations plus complexes, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] fournit les deux classes suivantes :  
  
|Classe|Description|Exemple|  
|------------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Regroupe plusieurs objets <xref:System.Windows.Media.TransformGroup> en un seul <xref:System.Windows.Media.Transform>, que vous pouvez ensuite appliquer pour transformer des propriétés.|[Appliquer plusieurs transformations à un objet](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Crée des transformations personnalisées qui ne sont pas fournies par les autres classes <xref:System.Windows.Media.Transform>.  Lorsque vous utilisez un <xref:System.Windows.Media.MatrixTransform>, vous manipulez directement une matrice.|[Utiliser un MatrixTransform pour créer des transformations personnalisées](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] fournit également des transformations [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)].  Pour plus d'informations, consultez la classe <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>   
## Propriétés de transformation courantes  
 L'une des manières de transformer un objet est de déclarer le type <xref:System.Windows.Media.Transform> approprié et de l'appliquer à la propriété de transformation de l'objet.  Les différents types d'objets ont différents types de propriétés de transformation.  Le tableau suivant répertorie plusieurs types [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] et leurs propriétés de transformation les plus souvent utilisés.  
  
|Type|Propriétés de transformation|  
|----------|----------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## Transformations et systèmes de coordonnées  
 Lorsque vous transformez un objet, vous ne transformez pas uniquement l'objet, vous transformez également l'espace de coordonnées dans lequel cet objet existe.  Par défaut, une transformation est centrée à l'origine du système de coordonnées de l'objet cible : \(0,0\).  La seule exception est <xref:System.Windows.Media.TranslateTransform> ; un <xref:System.Windows.Media.TranslateTransform> n'a pas de propriétés de centre à définir parce que l'effet de translation est le même indépendamment du centre.  
  
 L'exemple suivant utilise une classe <xref:System.Windows.Media.RotateTransform> pour faire pivoter un élément <xref:System.Windows.Shapes.Rectangle> \(type d'objet <xref:System.Windows.FrameworkElement>\) de 45 degrés par rapport à son centre par défaut \(0, 0\).  L'illustration suivante présente l'effet de la rotation.  
  
 ![FrameworkElement pivoté de 45 degrés autour de &#40;0,0&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm\_FE\_rotated\_about\_upperleft\_corner")  
Élément Rectangle tourné à 45 degrés par rapport au point \(0,0\)  
  
 [!code-xml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Par défaut, l'élément pivote par rapport à son angle supérieur gauche, \(0, 0\).  Les classes <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform> et <xref:System.Windows.Media.SkewTransform> fournissent les propriétés CenterX et CenterY qui vous permettent de spécifier le point au niveau duquel la transformation est appliquée.  
  
 L'exemple suivant utilise également un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un élément <xref:System.Windows.Shapes.Rectangle> de 45 degrés ; cependant, cette fois, les propriétés <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> sont définies de sorte que le centre de <xref:System.Windows.Media.RotateTransform> ait la valeur \(25, 25\).  L'illustration suivante présente l'effet de la rotation.  
  
 ![Geometry pivoté de 45 degrés autour de &#40;25, 25&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm\_FE\_rotated\_about\_center")  
Élément Rectangle tourné à 45 degrés par rapport au point \(25,25\)  
  
 [!code-xml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## Transformation d'un FrameworkElement  
 Pour appliquer des transformations à un <xref:System.Windows.FrameworkElement>, créez un <xref:System.Windows.Media.Transform> et appliquez\-le à l'une des deux propriétés fournies par la classe <xref:System.Windows.FrameworkElement> :  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A> \- Transformation appliquée avant la passe de disposition.  Après que la transformation a été appliquée, le système de disposition traite la taille et la position transformées de l'élément.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A> \- Transformation modifiant l'apparence de l'élément mais ne s'appliquant qu'une fois la passe de disposition terminée.  En utilisant la propriété <xref:System.Windows.UIElement.RenderTransform%2A> au lieu de la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A>, vous pouvez obtenir des avantages de performance.  
  
 Quelle propriété faut\-il utiliser ?  Étant donné les avantages de performance qu'elle fournit, utilisez le plus possible la propriété <xref:System.Windows.UIElement.RenderTransform%2A>, surtout lorsque vous utilisez des objets <xref:System.Windows.Media.Transform> animés.  Utilisez la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A> pour mettre à l'échelle, faire pivoter ou incliner un élément. Pour ajuster la taille transformée de l'élément, vous aurez besoin du parent de l'élément.  Notez que, lorsqu'ils sont utilisés avec la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A>, les objets <xref:System.Windows.Media.TranslateTransform> semblent n'avoir aucun effet sur les éléments.  Cela est dû au fait que le système de disposition renvoie l'élément translaté à sa position d'origine lors de son traitement.  
  
 Pour plus d'informations sur la disposition dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consultez la vue d'ensemble [Disposition](../../../../docs/framework/wpf/advanced/layout.md).  
  
<a name="exampleRotateAnElement45degSection"></a>   
## Exemple : faire pivoter un FrameworkElement de 45 degrés  
 L'exemple suivant utilise un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un bouton de 45 degrés dans le sens horaire.  Le bouton est contenu dans un <xref:System.Windows.Controls.StackPanel> qui comporte deux autres boutons.  
  
 Par défaut, un <xref:System.Windows.Media.RotateTransform> pivote par rapport au point \(0, 0\).  Étant donné que l'exemple ne spécifie pas de valeur de centre, le bouton pivote par rapport au point \(0, 0\), qui est son angle supérieur gauche.  Le <xref:System.Windows.Media.RotateTransform> est appliqué à la propriété <xref:System.Windows.UIElement.RenderTransform%2A>.  L'illustration suivante affiche le résultat de la transformation.  
  
 ![Bouton transformé à l'aide de RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm\_RenderTransformWithDefaultCenter")  
Rotation de 45 degrés dans le sens des aiguilles d'une montre, à partir de l'angle supérieur gauche  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 L'exemple suivant utilise également un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un bouton de 45 degrés dans le sens horaire, mais il définit également le <xref:System.Windows.UIElement.RenderTransformOrigin%2A> du bouton à \(0.5, 0.5\).  La valeur de la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> est en rapport avec la taille du bouton.  Par conséquent, la rotation est appliquée au centre du bouton, plutôt qu'à l'angle supérieur gauche.  L'illustration suivante affiche le résultat de la transformation.  
  
 ![Bouton transformé autour de son centre](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm\_RenderTransformRelativeCenter")  
Rotation de 45 degrés dans le sens des aiguilles d'une montre, par rapport au centre  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 L'exemple suivant utilise la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A> au lieu de la propriété <xref:System.Windows.UIElement.RenderTransform%2A> pour faire pivoter le bouton.  Dans ce cas, la transformation affecte la disposition du bouton, ce qui déclenche une passe entière par le système de disposition.  Par conséquent, le bouton pivote, puis est repositionné car sa taille a été modifiée.  L'illustration suivante affiche le résultat de la transformation.  
  
 ![Bouton transformé à l'aide de LayoutTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm\_LayoutTransform")  
LayoutTransform utilisé pour faire pivoter le bouton  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## Animation de transformations  
 Étant donné qu'elles héritent de la classe <xref:System.Windows.Media.Animation.Animatable>, les classes <xref:System.Windows.Media.Transform> peuvent être animées.  Pour animer un <xref:System.Windows.Media.Transform>, appliquez l'animation d'un type compatible à la propriété que vous souhaitez animer.  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.Animation.Storyboard> et un <xref:System.Windows.Media.Animation.DoubleAnimation> avec un <xref:System.Windows.Media.RotateTransform> pour faire tourner un <xref:System.Windows.Controls.Button> sur place lorsque vous cliquez dessus.  
  
 [!code-xml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Pour l'exemple complet, consultez [Transformations 2D, exemple](http://go.microsoft.com/fwlink/?LinkID=158252).  Pour plus d'informations sur les animations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## Fonctionnalités Freezable  
 Comme elle hérite de la classe <xref:System.Windows.Freezable>, la classe <xref:System.Windows.Media.Transform> fournit plusieurs fonctionnalités spéciales : les objets <xref:System.Windows.Media.Transform> peuvent être déclarés comme [ressources](../../../../docs/framework/wpf/advanced/xaml-resources.md), partagés entre de nombreux objets, clonés, configurés en lecture seule pour améliorer les performances et rendus thread\-safe.  Pour plus d'informations sur les différentes fonctionnalités fournies par les objets <xref:System.Windows.Freezable>, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.Matrix>   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)   
 [Transformations 2D, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=158252)