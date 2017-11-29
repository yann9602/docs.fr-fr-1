---
title: Vue d'ensemble des transformations
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd4e0f65d404e70f441cf2918fd6c50e08ebec79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="transforms-overview"></a>Vue d'ensemble des transformations
Cette rubrique explique comment utiliser le [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> classes pour faire pivoter, mettre à l’échelle, déplacer (Translation) et incliner <xref:System.Windows.FrameworkElement> objets.  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Qu’est qu’une transformation ?  
 A <xref:System.Windows.Media.Transform> définit comment mapper, ou transformer, des points d’un espace de coordonnées à un autre espace de coordonnées. Ce mappage est décrit par une transformation <xref:System.Windows.Media.Matrix>, qui est une collection de trois lignes avec trois colonnes de <xref:System.Double> valeurs.  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] utilise des matrices de type row-major. Les vecteurs sont exprimés en lignes de vecteurs et non en colonnes de vecteurs.  
  
 Le tableau suivant montre la structure d’une matrice [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="a-2-d-transformation-matrix"></a>Une matrice de transformation en 2D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Valeur par défaut : 1,0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Valeur par défaut : 0,0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Valeur par défaut : 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Valeur par défaut : 1,0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Valeur par défaut : 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Valeur par défaut : 0,0|1.0|  
  
 En modifiant les valeurs de la matrice, vous pouvez faire pivoter, mettre à l’échelle, incliner et déplacer (translater) un objet. Par exemple, si vous modifiez la valeur de la première colonne de la troisième ligne (le <xref:System.Windows.Media.Matrix.OffsetX%2A> valeur) à 100, vous pouvez l’utiliser pour déplacer un objet 100 unités sur l’axe des abscisses. Si vous remplacez la valeur de la case située à l’intersection de la deuxième colonne et de la deuxième par 3, vous pouvez étirer un objet à trois fois sa hauteur actuelle. Si vous modifiez les deux valeurs comme indiqué ci-dessus, vous déplacez l’objet de 100 unités sur l’axe X et multipliez sa hauteur par 3. Comme [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ne prend en charge que les transformations affines, les valeurs de la colonne de droite sont toujours égales à 0, 0, 1.  
  
 Bien que [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] vous permet de manipuler directement des valeurs de matrice, il fournit également plusieurs <xref:System.Windows.Media.Transform> classes qui vous permettent de transformer un objet sans connaître la configuration de la structure sous-jacente de la matrice. Par exemple, le <xref:System.Windows.Media.ScaleTransform> classe vous permet de mettre à l’échelle d’un objet en définissant ses <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriétés, plutôt que de manipuler une matrice de transformation. De même, la <xref:System.Windows.Media.RotateTransform> classe vous permet de faire pivoter un objet en définissant simplement son <xref:System.Windows.Media.RotateTransform.Angle%2A> propriété.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Classes de transformation  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]fournit les éléments suivants [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> classes pour les opérations de transformation courantes :  
  
|Classe|Description|Exemple|Illustration|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Fait pivoter un élément spécifié <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Faire pivoter un objet](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![Illustration de rotation](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Met à l’échelle un élément par le <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> quantités.|[Mettre à l'échelle un élément](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![Illustration de mise à l’échelle](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Inclinaisons un élément par le <xref:System.Windows.Media.SkewTransform.AngleX%2A> et <xref:System.Windows.Media.SkewTransform.AngleY%2A> quantités.|[Incliner un élément](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![Illustration d’inclinaison](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Déplace (traduit) un élément par le <xref:System.Windows.Media.TranslateTransform.X%2A> et <xref:System.Windows.Media.TranslateTransform.Y%2A> quantités.|[Translater un élément](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![Illustration de translation](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Pour créer des transformations plus complexes, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] propose les deux classes suivantes :  
  
|Classe|Description|Exemple|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Regroupe plusieurs <xref:System.Windows.Media.TransformGroup> des objets dans un seul <xref:System.Windows.Media.Transform> que vous pouvez ensuite appliquer pour transformer des propriétés.|[Apply Multiple Transforms to an Object](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md) (Appliquer plusieurs transformations à un objet)|  
|<xref:System.Windows.Media.MatrixTransform>|Crée des transformations personnalisées qui ne sont pas fournies par les autres <xref:System.Windows.Media.Transform> classes. Lorsque vous utilisez un <xref:System.Windows.Media.MatrixTransform>, vous manipulez directement une matrice.|[Use a MatrixTransform to Create Custom Transforms](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md) (Utiliser la classe MatrixTransform pour créer des transformations personnalisées)|  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] permet également d’effectuer des transformations [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]. Pour plus d'informations, consultez la classe <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Propriétés des opérations de transformation courantes  
 Une méthode pour transformer un objet consiste à déclarer approprié <xref:System.Windows.Media.Transform> de type et l’appliquer à la propriété de transformation de l’objet. Les différents types d’objet ont différents types de propriété de transformation. Le tableau suivant répertorie plusieurs types [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] fréquemment utilisés et leurs propriétés de transformation.  
  
|Type|Propriétés de transformation|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Transformations et systèmes de coordonnées  
 Lorsque vous transformez un objet, vous ne transformez pas simplement l’objet, vous transformez l’espace de coordonnées dans lequel cet objet existe. Par défaut, une opération de transformation est centrée à l’origine du système de coordonnées de l’objet cible : (0,0). La seule exception est <xref:System.Windows.Media.TranslateTransform>; un <xref:System.Windows.Media.TranslateTransform> ne possède aucune propriété center pour définir l’effet de translation est la même, quelle que soit l’endroit où il est centré.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un <xref:System.Windows.Shapes.Rectangle> élément, un type de <xref:System.Windows.FrameworkElement>, de 45 degrés autour de son centre par défaut, (0, 0). L’illustration suivante montre l’effet de la rotation.  
  
 ![FrameworkElement pivoté de 45 degrés autour &#40; 0,0 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Un élément rectangle pivoté de 45 degrés autour du point (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Par défaut, l’élément pivote autour de son coin supérieur gauche, (0, 0). Le <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, et <xref:System.Windows.Media.SkewTransform> classes fournissent les propriétés CenterX et CenterY qui vous permettent de spécifier le point auquel la transformation est appliquée.  
  
 L’exemple suivant utilise également un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un <xref:System.Windows.Shapes.Rectangle> élément de 45 degrés ; Toutefois, cette fois le <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés sont définies afin que le <xref:System.Windows.Media.RotateTransform> dispose d’un centre de (25, 25). L’illustration suivante montre l’effet de la rotation.  
  
 ![Geometry pivoté de 45 degrés autour de &#40; 25, 25 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Un élément rectangle pivoté de 45 degrés autour du point (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Transformation d’un élément FrameworkElement  
 Pour appliquer des transformations à un <xref:System.Windows.FrameworkElement>, créez un <xref:System.Windows.Media.Transform> et appliquez-le à une des deux propriétés qui la <xref:System.Windows.FrameworkElement> classe fournit :  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A>-Transformation appliquée avant la passe de disposition. Une fois la transformation appliquée, le système de disposition traite la taille et la position transformées de l’élément.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A>– Une transformation qui modifie l’apparence de l’élément, mais est appliquée après la passe de disposition est terminée. À l’aide de la <xref:System.Windows.UIElement.RenderTransform%2A> propriété au lieu du <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriété, vous pouvez obtenir des gains de performance.  
  
 Quelle propriété utiliser ? En raison des avantages de performances qu’offre cette solution, vous devez utiliser le <xref:System.Windows.UIElement.RenderTransform%2A> propriété chaque fois que possible, notamment lorsque vous utilisez animée <xref:System.Windows.Media.Transform> objets. Utilisez le <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriété lors de la mise à l’échelle, la rotation ou inclinaison et vous devez le parent de l’élément pour ajuster la taille transformées de l’élément. Notez que, lorsqu’ils sont utilisés avec la <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriété <xref:System.Windows.Media.TranslateTransform> objets semblent n’ont aucun effet sur les éléments. Ceci est dû au fait que le système de disposition remet l’élément translaté dans sa position d’origine au cours de son traitement.  
  
 Pour plus d’informations sur la disposition dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consultez l’article [Layout](../../../../docs/framework/wpf/advanced/layout.md) (Le système de disposition).  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Exemple : faire pivoter un FrameworkElement de 45 degrés  
 L’exemple suivant utilise un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un bouton dans le sens de 45 degrés. Le bouton est contenu dans un <xref:System.Windows.Controls.StackPanel> qui comporte deux autres boutons.  
  
 Par défaut, un <xref:System.Windows.Media.RotateTransform> fait pivoter autour du point (0, 0). L’exemple ne spécifie pas de valeur pour le centre donc le bouton pivote autour du point (0, 0), qui se trouve dans le coin supérieur gauche. Le <xref:System.Windows.Media.RotateTransform> est appliqué à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété. L’illustration suivante montre les résultats de la transformation.  
  
 ![Bouton transformé à l’aide de RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Rotation de 45 degrés dans le sens des aiguilles d’une montre à partir du coin supérieur gauche  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 L’exemple suivant utilise également un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un bouton de 45 degrés dans le sens horaire, mais également définit le <xref:System.Windows.UIElement.RenderTransformOrigin%2A> du bouton (0,5, 0,5). La valeur de la <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriété est relative à la taille du bouton. Par conséquent, la rotation est appliquée au centre du bouton et non à partir de son coin supérieur gauche. L’illustration suivante montre les résultats de la transformation.  
  
 ![Bouton transformé autour de son centre](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Une rotation de 45 degrés dans le sens des aiguilles d’une montre autour de centre  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 L’exemple suivant utilise le <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriété au lieu du <xref:System.Windows.UIElement.RenderTransform%2A> propriété pour faire pivoter le bouton.  Ainsi, la transformation affecte la disposition du bouton, ce qui déclenche une passe entière par le système de disposition. Par conséquent, le bouton est pivoté, puis repositionné, car sa taille a changé. L’illustration suivante montre les résultats de la transformation.  
  
 ![Bouton transformé à l’aide de LayoutTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
Classe LayoutTransform utilisée pour faire pivoter le bouton  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animation de transformations  
 Parce qu’ils héritent de la <xref:System.Windows.Media.Animation.Animatable> (classe), le <xref:System.Windows.Media.Transform> classes peuvent être animés. Pour animer une <xref:System.Windows.Media.Transform>, appliquer une animation d’un type compatible à la propriété à animer.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.Animation.Storyboard> et un <xref:System.Windows.Media.Animation.DoubleAnimation> avec un <xref:System.Windows.Media.RotateTransform> pour rendre un <xref:System.Windows.Controls.Button> spin en place lorsque vous cliquez dessus.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D). Pour plus d’informations sur les animations, consultez l’article [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Fonctionnalités Freezable  
 Car il hérite de la <xref:System.Windows.Freezable> (classe), le <xref:System.Windows.Media.Transform> classe fournit plusieurs fonctionnalités spéciales : <xref:System.Windows.Media.Transform> objets peuvent être déclarés en tant que [ressources](../../../../docs/framework/wpf/advanced/xaml-resources.md), partagés entre plusieurs objets, définis en lecture seule pour améliorer performances, clonés et rendus thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par <xref:System.Windows.Freezable> , consultez la [vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Exemple de transformations 2D](http://go.microsoft.com/fwlink/?LinkID=158252)
