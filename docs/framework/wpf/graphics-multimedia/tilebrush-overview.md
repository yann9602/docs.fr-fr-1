---
title: Vue d'ensemble de TileBrush
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
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d5e9fa36ddeda0c724eeb0bb46a64d0ba36c99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tilebrush-overview"></a>Vue d'ensemble de TileBrush
<xref:System.Windows.Media.TileBrush>objets vous permettent de contrôler la peinture d’une zone avec une image, précisément <xref:System.Windows.Media.Drawing>, ou <xref:System.Windows.Media.Visual>. Cette rubrique explique comment utiliser <xref:System.Windows.Media.TileBrush> fonctionnalités pour mieux contrôler la façon un <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ou <xref:System.Windows.Media.VisualBrush> peint une zone.  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a>Prérequis  
 Pour comprendre cette rubrique, il est utile de comprendre comment utiliser les fonctionnalités de base de la <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ou <xref:System.Windows.Media.VisualBrush> classe. Pour une introduction à ces types, consultez le [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>Peindre une zone avec des mosaïques  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, sont <xref:System.Windows.Media.VisualBrush> sont des types de <xref:System.Windows.Media.TileBrush> objets. Les pinceaux mosaïque vous permettent de bien contrôler le remplissage d’une zone avec une image, un dessin ou un objet visuel. Par exemple, au lieu de simplement peindre une zone avec une seule image étendue, vous pouvez peindre une zone avec une série de mosaïques d’image qui créent un motif.  
  
 Peindre une zone avec un pinceau mosaïque implique trois composants : un contenu, une mosaïque de base et une zone de sortie.  
  
 ![Composants de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Composants d’un TileBrush avec une seule mosaïque  
  
 ![Composants de TileBrush en mosaïque](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Composants d’un TileBrush avec un TileMode de mosaïque  
  
 La zone de sortie est la zone de peinture, telle que la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Ellipse> ou le <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button>. Les sections suivantes décrivent les deux autres composants d’un <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>Contenu de pinceau  
 Il existe trois types différents de <xref:System.Windows.Media.TileBrush> et chaque peint avec un autre type de contenu.  
  
-   Si le pinceau est un <xref:System.Windows.Media.ImageBrush>, ce contenu est une image de la <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriété spécifie le contenu de la <xref:System.Windows.Media.ImageBrush>.  
  
-   Si le pinceau est un <xref:System.Windows.Media.DrawingBrush>, ce contenu est un dessin. Le <xref:System.Windows.Media.DrawingBrush.Drawing%2A> propriété spécifie le contenu de la <xref:System.Windows.Media.DrawingBrush>.  
  
-   Si le pinceau est un <xref:System.Windows.Media.VisualBrush>, ce contenu est un élément visuel. Le <xref:System.Windows.Media.VisualBrush.Visual%2A> propriété spécifie le contenu de la <xref:System.Windows.Media.VisualBrush>.  
  
 Vous pouvez spécifier la position et les dimensions de <xref:System.Windows.Media.TileBrush> contenu à l’aide de la <xref:System.Windows.Media.TileBrush.Viewbox%2A> propriété, bien qu’il soit courant de conserver le <xref:System.Windows.Media.TileBrush.Viewbox%2A> défini à sa valeur par défaut. Par défaut, le <xref:System.Windows.Media.TileBrush.Viewbox%2A> est configuré pour englober intégralement le contenu du pinceau. Pour plus d’informations sur la configuration de la <xref:System.Windows.Controls.Viewbox>, consultez le <xref:System.Windows.Controls.Viewbox> page de propriétés.  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>La mosaïque de base  
 A <xref:System.Windows.Media.TileBrush> projette son contenu sur une mosaïque de base. Le <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété détermine comment <xref:System.Windows.Media.TileBrush> contenu est étiré pour remplir la mosaïque de base. Le <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété accepte les valeurs suivantes, définies par le <xref:System.Windows.Media.Stretch> énumération :  
  
-   <xref:System.Windows.Media.Stretch.None>: Le contenu du pinceau n’est pas étiré pour remplir la mosaïque.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Le contenu du pinceau est ajusté en fonction de la vignette. Étant donné que la hauteur et la largeur du contenu sont mis à l’échelle indépendamment, les proportions d’origine du contenu risquent de ne pas être conservées. Autrement dit, le contenu du pinceau peut être déformé pour remplir complètement la mosaïque de sortie.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Le contenu du pinceau est mis à l’échelle afin qu’elle s’adapte parfaitement au sein de la vignette. Les proportions du contenu sont conservées.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Le contenu du pinceau est mis à l’échelle afin qu’il remplisse complètement la zone de sortie tout en conservant les proportions d’origine du contenu.  
  
 L’image suivante illustre les différentes <xref:System.Windows.Media.TileBrush.Stretch%2A> paramètres.  
  
 ![Différents paramètres d’étirement TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 Dans l’exemple suivant, le contenu d’un <xref:System.Windows.Media.ImageBrush> est définie afin qu’il ne s’étire pas pour remplir la zone de sortie.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Par défaut, un <xref:System.Windows.Media.TileBrush> génère une seule mosaïque (la mosaïque de base) et étire cette mosaïque pour remplir complètement la zone de sortie. Vous pouvez modifier la taille et la position de la mosaïque de base en définissant le <xref:System.Windows.Media.TileBrush.Viewport%2A> et <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriétés.  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>Taille de la mosaïque de base  
 Le <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété détermine la taille et la position de la mosaïque de base et le <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriété détermine si le <xref:System.Windows.Media.TileBrush.Viewport%2A> est spécifié à l’aide de coordonnées absolues ou relatives. Si les coordonnées sont relatives, elles sont relatives à la taille de la zone de sortie. Le point (0,0) représente le coin supérieur gauche de la zone de sortie et (1,1) représente le coin inférieur droit de la zone de sortie. Pour spécifier que le <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété utilise des coordonnées absolues, définissez la <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriété <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 L’illustration suivante montre la différence de sortie entre un <xref:System.Windows.Media.TileBrush> relative ou absolue <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>. Notez que chaque illustration représente un motif en mosaïque ; la section suivante décrit comment spécifier un tel motif.  
  
 ![Unités de fenêtre d'affichage absolues et relatives](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 Dans l’exemple suivant, une image est utilisée pour créer une mosaïque ayant une largeur et une hauteur de 50 %. La mosaïque de base se trouve au point (0,0) de la zone de sortie.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 L’exemple suivant définit les vignettes d’un <xref:System.Windows.Media.ImageBrush> à 25 par 25 pixels indépendants du périphérique. Étant donné que la <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> sont absolu, le <xref:System.Windows.Media.ImageBrush> vignettes sont toujours 25 par 25 pixels, quelle que soit la taille de la zone qui est peinte.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>Comportement des mosaïques  
 A <xref:System.Windows.Media.TileBrush> génère un modèle en mosaïque lorsque sa mosaïque de base ne remplit pas entièrement la zone de sortie et un mode de mosaïque autre <xref:System.Windows.Media.TileMode.None> est spécifié. Lorsque mosaïque un pinceau ne remplit pas entièrement la zone de sortie, son <xref:System.Windows.Media.TileBrush.TileMode%2A> propriété spécifie si la mosaïque de base doit être dupliquée pour remplir la zone de sortie et, dans ce cas, comment la mosaïque de base doit être dupliqué. Le <xref:System.Windows.Media.TileBrush.TileMode%2A> propriété accepte les valeurs suivantes, définies par le <xref:System.Windows.Media.TileMode> énumération :  
  
-   <xref:System.Windows.Media.TileMode.None>: Seule la mosaïque de base est dessinée.  
  
-   <xref:System.Windows.Media.TileMode.Tile>: La mosaïque de base est dessinée et la zone restante est remplie en répétant la mosaïque de base telles que le bord droit d’une mosaïque est adjacent sur le bord gauche de la suivante et de la même façon et du bas.  
  
-   <xref:System.Windows.Media.TileMode.FlipX>: Identique à <xref:System.Windows.Media.TileMode.Tile>, mais les autres colonnes de mosaïques sont retournées horizontalement.  
  
-   <xref:System.Windows.Media.TileMode.FlipY>: Identique à <xref:System.Windows.Media.TileMode.Tile>, mais une ligne de mosaïques est retournée verticalement.  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>: Une combinaison de <xref:System.Windows.Media.TileMode.FlipX> et <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Les images suivantes illustrent les différents modes de mosaïque.  
  
 ![Different paramètres TileMode du TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 Dans l’exemple suivant, une image est utilisée pour peindre un rectangle de 100 pixels de large et 100 pixels de haut. En définissant le pinceau <xref:System.Windows.Media.TileBrush.Viewport%2A> a été défini à 0,0,0.25,0.25, la mosaïque de base du pinceau est effectuée à 1/4 de la zone de sortie. Le pinceau <xref:System.Windows.Media.TileBrush.TileMode%2A> a la valeur <xref:System.Windows.Media.TileMode.FlipXY>. afin qu’il remplisse le rectangle de lignes de mosaïques.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [Peinture avec des images, des dessins et des objets visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [ImageBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049) (Exemple de VisualBrush)
