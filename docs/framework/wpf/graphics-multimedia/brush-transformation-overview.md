---
title: Vue d'ensemble des transformations du pinceau
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
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b57c5ee36c9ed9c89fc8ca1bfb7ea265c2460c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="brush-transformation-overview"></a>Vue d'ensemble des transformations du pinceau
La classe Brush fournit deux propriétés de transformation : <xref:System.Windows.Media.Brush.Transform%2A> et <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Les propriétés vous permettent de faire pivoter, mettre à l’échelle, incliner et effectuer la translation du contenu d’un pinceau. Cette rubrique décrit les différences entre ces deux propriétés et fournit des exemples de leur utilisation.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Pour comprendre cette rubrique, vous devez comprendre les fonctionnalités du pinceau que vous transformez. Pour <xref:System.Windows.Media.LinearGradientBrush> et <xref:System.Windows.Media.RadialGradientBrush>, consultez la [peinture avec des couleurs unies et vue d’ensemble des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Pour <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ou <xref:System.Windows.Media.VisualBrush>, consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md). Vous devez également être familiarisé avec les transformations 2D décrites dans la [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Différences entre les propriétés Transform et RelativeTransform  
 Lorsque vous appliquez une transformation à un pinceau <xref:System.Windows.Media.Brush.Transform%2A> propriété, vous devez connaître la taille de la zone peinte si vous voulez transformer le contenu du pinceau autour de son centre. Supposons que la zone peinte fasse 200 dip (pixels indépendants de l’appareil) de large et 150 de hauteur.  Si vous avez utilisé un <xref:System.Windows.Media.RotateTransform> pour faire pivoter le pinceau de sortie de 45 degrés autour de son centre, vous devez attribuer le <xref:System.Windows.Media.RotateTransform> un <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 100 et une <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 75.  
  
 Lorsque vous appliquez une transformation à un pinceau <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété, cette transformation est appliquée au pinceau avant que sa sortie est mappée à la zone peinte. La liste suivante décrit l’ordre dans lequel le contenu d’un pinceau est traité et transformé.  
  
1.  Traitez le contenu du pinceau. Pour un <xref:System.Windows.Media.GradientBrush>, cela signifie que la détermination de la zone de dégradé. Pour un <xref:System.Windows.Media.TileBrush>, le <xref:System.Windows.Media.TileBrush.Viewbox%2A> est mappé à la <xref:System.Windows.Media.TileBrush.Viewport%2A>. Cela devient la sortie du pinceau.  
  
2.  Projetez la sortie du pinceau sur le rectangle de transformation 1 x 1.  
  
3.  Appliquer le pinceau <xref:System.Windows.Media.Brush.RelativeTransform%2A>, le cas échéant.  
  
4.  Projetez la sortie transformée sur la zone à peindre.  
  
5.  Appliquer le pinceau <xref:System.Windows.Media.Transform>, le cas échéant.  
  
 Étant donné que le <xref:System.Windows.Media.Brush.RelativeTransform%2A> est appliqué lors de la sortie du pinceau est mappée à un rectangle 1 x 1, centre de transformation et de valeurs de décalage semblent être relatif. Par exemple, si vous avez utilisé un <xref:System.Windows.Media.RotateTransform> pour faire pivoter le pinceau de sortie de 45 degrés autour de son centre, vous devez attribuer le <xref:System.Windows.Media.RotateTransform> un <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 0,5 et un <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 0,5.  
  
 L’illustration suivante montre la sortie de plusieurs pinceaux qui ont été pivoté de 45 degrés à l’aide de la <xref:System.Windows.Media.Brush.RelativeTransform%2A> et <xref:System.Windows.Media.Brush.Transform%2A> propriétés.  
  
 ![Propriétés RelativeTransform et Transform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Utilisation de RelativeTransform avec TileBrush  
 Pinceaux de mosaïque étant plus complexe que les autres pinceaux, appliquer un <xref:System.Windows.Media.Brush.RelativeTransform%2A> à un peut produire des résultats inattendus. Par exemple, prenons l’image suivante.  
  
 ![L’image source](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.ImageBrush> pour peindre une zone rectangulaire avec l’image précédente. Elle s’applique une <xref:System.Windows.Media.RotateTransform> à la <xref:System.Windows.Media.ImageBrush> l’objet <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété et définit ses <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété <xref:System.Windows.Media.Stretch.UniformToFill>, qui doivent conserver les proportions de l’image lorsqu’il est étiré pour remplir complètement le rectangle.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Cet exemple génère la sortie suivante :  
  
 ![La sortie transformée](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Notez que l’image est formée, même si le pinceau <xref:System.Windows.Media.TileBrush.Stretch%2A> a été défini sur <xref:System.Windows.Media.Stretch.UniformToFill>. C’est parce que la transformation relative est appliquée après du pinceau <xref:System.Windows.Media.TileBrush.Viewbox%2A> est mappé à son <xref:System.Windows.Media.TileBrush.Viewport%2A>. La liste suivante décrit chaque étape du processus :  
  
1.  Le contenu du pinceau de projet (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) sur sa mosaïque de base (<xref:System.Windows.Media.TileBrush.Viewport%2A>) à l’aide du pinceau <xref:System.Windows.Media.TileBrush.Stretch%2A> paramètre.  
  
     ![Étirement de la Viewbox pour correspondre à la fenêtre d’affichage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  Projetez la mosaïque de base sur le rectangle de transformation 1 x 1.  
  
     ![Mappage de la fenêtre d'affichage et du rectangle de transformation](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  Appliquer le <xref:System.Windows.Media.RotateTransform>.  
  
     ![Application de la transformation relative](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  Projetez la mosaïque de base transformée sur la zone à peindre.  
  
     ![Projection du pinceau transformé sur la zone de sortie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Exemple : Rotation d’un ImageBrush de 45 degrés  
 L’exemple suivant applique un <xref:System.Windows.Media.RotateTransform> à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété d’un <xref:System.Windows.Media.ImageBrush>. Le <xref:System.Windows.Media.RotateTransform> l’objet <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés ont la valeur 0,5, les coordonnées relatives du point central du contenu. Par conséquent, le contenu du pinceau pivote autour de son centre.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 L’exemple suivant s’applique également une <xref:System.Windows.Media.RotateTransform> à un <xref:System.Windows.Media.ImageBrush>, mais utilise le <xref:System.Windows.Media.Brush.Transform%2A> propriété au lieu du <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété. Pour faire pivoter le pinceau autour de son centre, le <xref:System.Windows.Media.RotateTransform> l’objet <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> doit être définie sur des coordonnées absolues. Le rectangle peint par le pinceau étant de 175 pixels par 90, son point central est (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 L’illustration suivante montre le pinceau sans transformation, avec la transformation appliquée à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété et avec la transformation appliquée à la <xref:System.Windows.Media.Brush.Transform%2A> propriété.  
  
 ![Paramètres de Brush RelativeTransform et Transform](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Cet exemple fait partie d’un exemple plus complet. Pour l’exemple complet, consultez [Exemples de pinceaux](http://go.microsoft.com/fwlink/?LinkID=159973). Pour plus d’informations sur les pinceaux, consultez la [Vue d'ensemble des pinceaux WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Brush.Transform%2A>  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Brush>  
 [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Peinture avec des images, des dessins et des objets visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Vue d’ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
