---
title: Vue d'ensemble des pinceaux WPF
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
helpviewer_keywords: brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de5bcaeffb77f52b80c229cf0402c2c090e40d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-brushes-overview"></a>Vue d'ensemble des pinceaux WPF
Tous les éléments visibles sur votre écran sont visible, car il a été peint par un pinceau. Par exemple, un pinceau est utilisé pour décrire l’arrière-plan d’un bouton, le premier plan du texte et le remplissage de la forme. Cette rubrique présente les concepts de la peinture avec [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de pinceaux et fournit des exemples. Les pinceaux permettent de peindre des objets de l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aussi bien avec de simples couleurs unies qu’avec des ensembles complexes de modèles et d’images.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Peinture avec un pinceau  
 A <xref:System.Windows.Media.Brush> « peint » une zone avec sa sortie. Les différents pinceaux ont différents types de sortie. Certains peignent une zone avec une couleur unie, d’autres avec un dégradé, un motif, une image ou un dessin. L’illustration suivante montre des exemples de chacun des différents <xref:System.Windows.Media.Brush> types.  
  
 ![Types de pinceau](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Exemples de pinceau  
  
 La plupart des objets visual permettent de spécifier la façon dont ils sont peints. Le tableau suivant répertorie certains objets courants et les propriétés dont vous pouvez utiliser un <xref:System.Windows.Media.Brush>.  
  
|Classe|Propriétés de pinceau|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Les sections suivantes décrivent les différentes <xref:System.Windows.Media.Brush> types et fournissent un exemple de chaque.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Peinture avec une couleur unie  
 A <xref:System.Windows.Media.SolidColorBrush> peint une zone avec un solide <xref:System.Windows.Media.Color>. Il existe plusieurs manières de spécifier le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush>: par exemple, vous pouvez spécifier ses canaux alpha, rouge, bleu et vert ou utiliser une des couleurs prédéfinies fournis par le <xref:System.Windows.Media.Colors> classe.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.SolidColorBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Rectangle peint avec un SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.SolidColorBrush> de classe, consultez [peinture avec des couleurs unies et vue d’ensemble des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Peinture avec un dégradé linéaire  
 A <xref:System.Windows.Media.LinearGradientBrush> peint une zone avec un dégradé linéaire. Un dégradé linéaire mélange deux ou plusieurs couleurs sur une ligne, l’axe du dégradé. Vous utilisez <xref:System.Windows.Media.GradientStop> objets pour spécifier les couleurs du dégradé et leurs positions.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.LinearGradientBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Rectangle peint avec un LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.LinearGradientBrush> de classe, consultez [peinture avec des couleurs unies et vue d’ensemble des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Peinture avec un dégradé Radial  
 A <xref:System.Windows.Media.RadialGradientBrush> peint une zone avec un dégradé radial. Un dégradé radial mélange deux ou plus de couleurs sur un cercle. Comme avec la <xref:System.Windows.Media.LinearGradientBrush> (classe), vous utilisez <xref:System.Windows.Media.GradientStop> objets pour spécifier les couleurs du dégradé et leurs positions.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.RadialGradientBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un RadialGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Rectangle peint avec un RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.RadialGradientBrush> de classe, consultez [peinture avec des couleurs unies et vue d’ensemble des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Peinture avec une Image  
 Un <xref:System.Windows.Media.ImageBrush> peint une zone avec un <xref:System.Windows.Media.ImageSource>.  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.ImageBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Rectangle peint à l’aide d’une Image  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.ImageBrush> de classe, consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Peinture avec un dessin  
 A <xref:System.Windows.Media.DrawingBrush> peint une zone avec un <xref:System.Windows.Media.Drawing>. Un <xref:System.Windows.Media.Drawing> peut contenir des formes, d’images, de texte et de support.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.DrawingBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Rectangle peint avec un DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.DrawingBrush> de classe, consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Peinture avec un élément visuel  
 A <xref:System.Windows.Media.VisualBrush> peint une zone avec un <xref:System.Windows.Media.Visual> objet. Exemples d’objets visuels <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, et <xref:System.Windows.Controls.MediaElement>. A <xref:System.Windows.Media.VisualBrush> vous permet également de projeter du contenu d’une partie de votre application dans une autre zone ; il est très utile pour créer des effets de reflet et agrandir des parties de l’écran.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.VisualBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>. L’illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un VisualBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Rectangle peint avec un VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.VisualBrush> de classe, consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Peinture à l’aide de pinceaux système et prédéfinis  
 Pour plus de commodité, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] fournit un ensemble de système et pinceaux prédéfinis que vous pouvez utiliser pour peindre des objets.  
  
-   Pour obtenir la liste des pinceaux prédéfinis disponibles, consultez la <xref:System.Windows.Media.Brushes> classe. Pour obtenir un exemple montrant comment utiliser un pinceau prédéfini, consultez [peindre une zone avec une couleur unie](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md).  
  
-   Pour obtenir la liste des pinceaux système disponibles, consultez la <xref:System.Windows.SystemColors> classe. Pour obtenir un exemple, consultez [peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Fonctionnalités communes de pinceau  
 <xref:System.Windows.Media.Brush>objets fournissent une <xref:System.Windows.Media.Brush.Opacity%2A> propriété qui peut être utilisée pour rendre un pinceau totalement ou partiellement transparent. Un <xref:System.Windows.Media.Brush.Opacity%2A> la valeur 0 rend le pinceau complètement transparent, tandis qu’un <xref:System.Windows.Media.Brush.Opacity%2A> la valeur 1 indique un pinceau est complètement opaque. L’exemple suivant utilise le <xref:System.Windows.Media.Brush.Opacity%2A> propriété pour rendre un <xref:System.Windows.Media.SolidColorBrush> opaque à 25 %.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Si le pinceau contient des couleurs qui sont partiellement transparentes, la valeur d’opacité de la couleur est combinée multipliée par la valeur d’opacité du pinceau. Par exemple, si un pinceau a une valeur d’opacité de 0,5 et une couleur utilisée dans le pinceau a également une valeur d’opacité de 0,5, la couleur de sortie a une valeur d’opacité de 0,25.  
  
> [!NOTE]
>  Il est plus efficace de changer la valeur d’opacité d’un pinceau que celle pour modifier l’opacité d’un élément tout entier à l’aide de son <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> propriété.  
  
 Vous pouvez faire pivoter, mettre à l’échelle, incliner et traduire le contenu d’un pinceau à l’aide de son <xref:System.Windows.Media.Brush.Transform%2A> ou <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriétés. Pour plus d’informations, consultez [vue d’ensemble de la Transformation de pinceau](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Parce qu’ils sont <xref:System.Windows.Media.Animation.Animatable> objets <xref:System.Windows.Media.Brush> objets peuvent être animés. Pour plus d’informations, consultez [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Fonctionnalités Freezable  
 Car il hérite de la <xref:System.Windows.Freezable> (classe), le <xref:System.Windows.Media.Brush> classe propose plusieurs fonctionnalités spéciales : <xref:System.Windows.Media.Brush> objets peuvent être déclarés en tant que [ressources](../../../../docs/framework/wpf/advanced/xaml-resources.md), partagés entre plusieurs objets et clonés. En outre, toutes les le <xref:System.Windows.Media.Brush> , à l’exception des types <xref:System.Windows.Media.VisualBrush> peut être définie en lecture seule pour améliorer les performances et rendus thread-safe.  
  
 Pour plus d’informations sur les différentes fonctionnalités fournies par <xref:System.Windows.Freezable> , consultez [vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Pour plus d’informations sur la raison pour laquelle <xref:System.Windows.Media.VisualBrush> objets ne peut pas être figés, consultez la <xref:System.Windows.Media.VisualBrush> page type.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.Brushes>  
 [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Peinture avec des images, des dessins et des objets visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973)  
 [ImageBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049) (Exemple de VisualBrush)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
