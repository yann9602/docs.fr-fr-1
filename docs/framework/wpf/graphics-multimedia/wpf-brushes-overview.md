---
title: "Vue d&#39;ensemble des pinceaux WPF | Microsoft Docs"
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
  - "pinceaux, à propos des pinceaux"
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble des pinceaux WPF
Les éléments sont visibles sur votre écran car ils ont été peints avec un pinceau.  Par exemple, un pinceau est utilisé pour définir l'arrière\-plan d'un bouton, le premier plan du texte et le remplissage d'une forme.  Cette rubrique présente les concepts relatifs à la peinture avec les pinceaux [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et contient des exemples.  Les pinceaux vous permettent de peindre des objets [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] avec n'importe quoi, des couleurs simples et unies aux ensembles complexes de modèles et d'images.  
  
<a name="paintingwithbrush"></a>   
## Peinture avec un pinceau  
 Un <xref:System.Windows.Media.Brush> « peint » une zone avec sa sortie.  Les différents pinceaux ont différents types de sortie.  Certains peignent une zone avec une couleur unie, d'autres avec un dégradé, un modèle, une image ou un dessin.  L'illustration suivante montre des exemples de chaque type de <xref:System.Windows.Media.Brush>.  
  
 ![Types de pinceau](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.png "graphicsmm\_brushtypes")  
Exemples de pinceaux  
  
 La plupart des objets visuels vous permettent de spécifier la façon dont ils sont peints.  Le tableau ci\-dessous répertorie quelques propriétés et objets courants avec lesquels vous pouvez utiliser un <xref:System.Windows.Media.Brush>.  
  
|Classe|Propriétés de pinceaux|  
|------------|----------------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Les sections suivantes décrivent les différents types de <xref:System.Windows.Media.Brush> et fournissent un exemple de chaque type.  
  
<a name="paintwithsolidcolorbrush"></a>   
## Peinture avec une couleur unie  
 <xref:System.Windows.Media.SolidColorBrush> peint une zone avec un <xref:System.Windows.Media.Color> uni.  Il existe plusieurs moyens de spécifier le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d'un <xref:System.Windows.Media.SolidColorBrush> : par exemple, vous pouvez spécifier ses canaux alpha, rouge, bleu et vert ou utiliser l'une des couleurs prédéfinies comprises dans la classe <xref:System.Windows.Media.Colors>.  
  
 L'exemple suivant utilise <xref:System.Windows.Media.SolidColorBrush> pour peindre l'objet <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle>.  L'illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm\_brush\_ovw\_solidcolorbrush")  
Rectangle peint à l'aide de SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Pour plus d'informations sur la classe <xref:System.Windows.Media.SolidColorBrush>, consultez [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## Peinture avec un dégradé linéaire  
 <xref:System.Windows.Media.LinearGradientBrush> peint une zone avec un dégradé linéaire.  Un dégradé linéaire mélange deux couleurs, ou plus, sur une ligne, l'axe de dégradé.  Vous utilisez les objets <xref:System.Windows.Media.GradientStop> pour spécifier les couleurs du dégradé et leurs positions.  
  
 L'exemple suivant utilise <xref:System.Windows.Media.LinearGradientBrush> pour peindre l'objet <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle>.  L'illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.png "graphicsmm\_brush\_ovw\_lineargradientbrush")  
Rectangle peint à l'aide de LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Pour plus d'informations sur la classe <xref:System.Windows.Media.LinearGradientBrush>, consultez [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## Peinture avec un dégradé radial  
 <xref:System.Windows.Media.RadialGradientBrush> peint une zone avec un dégradé radial.  Un dégradé radial mélange deux couleurs, ou plus, sur un cercle.  Comme avec la classe <xref:System.Windows.Media.LinearGradientBrush>, vous utilisez les objets <xref:System.Windows.Media.GradientStop> pour spécifier les couleurs du dégradé et leurs positions.  
  
 L'exemple suivant utilise <xref:System.Windows.Media.RadialGradientBrush> pour peindre l'objet <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle>.  L'illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un RadialGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.png "graphicsmm\_brush\_ovw\_radialgradientbrush")  
Rectangle peint à l'aide de RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Pour plus d'informations sur la classe <xref:System.Windows.Media.RadialGradientBrush>, consultez [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## Peinture avec une image  
 <xref:System.Windows.Media.ImageBrush> peint une zone avec <xref:System.Windows.Media.ImageSource>.  
  
 L'exemple suivant utilise <xref:System.Windows.Media.ImageBrush> pour peindre l'objet <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle>.  L'illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.png "graphicsmm\_brush\_ovw\_imagebrush")  
Rectangle peint à l'aide d'une image  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Pour plus d'informations sur la classe <xref:System.Windows.Media.ImageBrush>, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## Peinture avec un dessin  
 <xref:System.Windows.Media.DrawingBrush> peint une zone avec un <xref:System.Windows.Media.Drawing>.  Un <xref:System.Windows.Media.Drawing> peut contenir des formes, des images, du texte et des médias.  
  
 L'exemple suivant utilise <xref:System.Windows.Media.DrawingBrush> pour peindre l'objet <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle>.  L'illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.png "graphicsmm\_brush\_ovw\_drawingbrush")  
Rectangle peint à l'aide de DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Pour plus d'informations sur la classe <xref:System.Windows.Media.DrawingBrush>, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## Peinture avec un visuel  
 <xref:System.Windows.Media.VisualBrush> peint une zone avec un objet <xref:System.Windows.Media.Visual>.  Voici quelques exemples d'objets visuels : <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page> et <xref:System.Windows.Controls.MediaElement>.  <xref:System.Windows.Media.VisualBrush> vous permet également de projeter du contenu d'une partie de votre application vers une autre zone, ce qui est très utile pour créer des effets de reflet et agrandir des zones de l'écran.  
  
 L'exemple suivant utilise <xref:System.Windows.Media.VisualBrush> pour peindre l'objet <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle>.  L'illustration suivante montre le rectangle peint.  
  
 ![Rectangle peint avec un VisualBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.png "graphicsmm\_brush\_ovw\_visualbrush")  
Rectangle peint à l'aide de VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Pour plus d'informations sur la classe <xref:System.Windows.Media.VisualBrush>, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## Peinture à l'aide des pinceaux système et prédéfinis  
 Pour des raisons pratiques, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] possède un ensemble de pinceaux système et pinceaux prédéfinis que vous pouvez utiliser pour peindre des objets.  
  
-   Pour obtenir la liste des pinceaux prédéfinis disponibles, consultez la classe <xref:System.Windows.Media.Brushes>.  Pour obtenir un exemple d'utilisation d'un pinceau prédéfini, consultez [Peindre une zone avec une couleur unie](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md).  
  
-   Pour obtenir la liste des pinceaux système disponibles, consultez la classe <xref:System.Windows.SystemColors>.  Pour obtenir un exemple, consultez [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## Fonctions communes des pinceaux  
 Les objets <xref:System.Windows.Media.Brush> ont une propriété <xref:System.Windows.Media.Brush.Opacity%2A> qui peut être utilisée pour rendre un pinceau totalement ou partiellement transparent.  Une valeur <xref:System.Windows.Media.Brush.Opacity%2A> de 0 rend le pinceau complètement transparent, tandis qu'une valeur <xref:System.Windows.Media.Brush.Opacity%2A> de 1 indique que le pinceau est complètement opaque.  L'exemple suivant utilise la propriété <xref:System.Windows.Media.Brush.Opacity%2A> pour rendre <xref:System.Windows.Media.SolidColorBrush> opaque à 25 %.  
  
 [!code-xml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Si le pinceau contient des couleurs qui sont partiellement transparentes, la valeur d'opacité de la couleur est multipliée par la valeur d'opacité du pinceau.  Par exemple, si un pinceau a une valeur d'opacité de 0,5 et que la couleur utilisée dans le pinceau a également une valeur d'opacité de 0,5, la couleur de sortie a une valeur d'opacité de 0,25.  
  
> [!NOTE]
>  Il est plus facile de changer la valeur d'opacité d'un pinceau que celle d'un élément complet par l'intermédiaire de sa propriété <xref:System.Windows.UIElement.Opacity%2A?displayProperty=fullName>.  
  
 Vous pouvez faire pivoter, incliner, mettre à l'échelle et traduire le contenu d'un pinceau en utilisant ses propriétés <xref:System.Windows.Media.Brush.Transform%2A> ou <xref:System.Windows.Media.Brush.RelativeTransform%2A>.  Pour plus d'informations, consultez [Vue d'ensemble des transformations du pinceau](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Puisqu'ils sont des objets <xref:System.Windows.Media.Animation.Animatable>, les objets <xref:System.Windows.Media.Brush> peuvent être animés.  Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
### Fonctionnalités Freezable  
 Comme elle hérite de la classe <xref:System.Windows.Freezable>, la classe <xref:System.Windows.Media.Brush> fournit plusieurs fonctionnalités spéciales : les objets <xref:System.Windows.Media.Brush> peuvent être déclarés comme [ressources](../../../../docs/framework/wpf/advanced/xaml-resources.md), partagés entre plusieurs objets et clonés.  En outre, tous les types <xref:System.Windows.Media.Brush>, à l'exception de <xref:System.Windows.Media.VisualBrush>, peuvent être mis en lecture seule pour améliorer les performances et rendus thread\-safe.  
  
 Pour plus d'informations sur les différentes fonctionnalités fournies par les objets <xref:System.Windows.Freezable>, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Pour plus d'informations sur la raison pour laquelle les objets <xref:System.Windows.Media.VisualBrush> ne peuvent pas être figés, consultez la page <xref:System.Windows.Media.VisualBrush>.  
  
## Voir aussi  
 <xref:System.Windows.Media.Brush>   
 <xref:System.Windows.Media.Brushes>   
 [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [Brushes, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159973)   
 [ImageBrush, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160005)   
 [VisualBrush, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160049)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)