---
title: "Vue d&#39;ensemble des transformations du pinceau | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pinceaux, propriétés de transformation"
  - "propriétés, transformation"
  - "propriétés de transformation de pinceaux"
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble des transformations du pinceau
La classe Brush fournit deux propriétés de transformation : <xref:System.Windows.Media.Brush.Transform%2A> et <xref:System.Windows.Media.Brush.RelativeTransform%2A>.  Les propriétés permettent de faire pivoter, d'incliner, de mettre à l'échelle et de traduire le contenu d'un pinceau.  Cette rubrique décrit les différences entre ces deux propriétés et illustre leur utilisation par des exemples.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## Composants requis  
 Pour comprendre cette rubrique, vous devez bien connaître les fonctionnalités du pinceau que vous transformez .  Pour <xref:System.Windows.Media.LinearGradientBrush> et <xref:System.Windows.Media.RadialGradientBrush>, consultez [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  Pour <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush>, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  Vous devez également être familiarisé avec les transformations 2D décrites dans la rubrique [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## Différences entre les propriétés Transform et RelativeTransform  
 Quand vous appliquez une transformation à la propriété <xref:System.Windows.Media.Brush.Transform%2A> d'un pinceau, vous devez connaître la taille de la zone peinte si vous voulez transformer le contenu du pinceau autour de son centre.  Supposons que la zone peinte mesure 200 [pixels indépendant du périphérique](GTMT) en largeur 150 en hauteur.  Si vous utilisez <xref:System.Windows.Media.RotateTransform> pour faire pivoter la sortie du pinceau sur 45 degrés autour de son centre, vous devez attribuer à <xref:System.Windows.Media.RotateTransform> un, <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 100 et un <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 75.  
  
 Quand vous appliquez une transformation à la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A> d'un pinceau, cette transformation est appliquée au pinceau avant que sa sortie ne soit mappée à la zone peinte.  La liste suivante décrit l'ordre dans lequel le contenu d'un pinceau est traité et transformé.  
  
1.  Traiter le contenu d'un pinceau.  Pour <xref:System.Windows.Media.GradientBrush>, cela signifie la détermination d'une zone de dégradé.  Pour <xref:System.Windows.Media.TileBrush>, <xref:System.Windows.Media.TileBrush.Viewbox%2A> est mappé au <xref:System.Windows.Media.TileBrush.Viewport%2A>.  Cela devient la sortie du pinceau.  
  
2.  Projetez la sortie du pinceau sur le rectangle de transformation 1 x 1.  
  
3.  Appliquez la <xref:System.Windows.Media.Brush.RelativeTransform%2A> du pinceau, le cas échéant.  
  
4.  Projetez la sortie transformée sur la zone à peindre.  
  
5.  Appliquez la <xref:System.Windows.Media.Transform> du pinceau, le cas échéant.  
  
 Dans la mesure où <xref:System.Windows.Media.Brush.RelativeTransform%2A> est appliquée alors que la sortie du pinceau est mappée à un rectangle 1 x 1, les valeurs d'offset et du centre de transformation apparaissent comme étant relatives.  Par exemple, si vous utilisez <xref:System.Windows.Media.RotateTransform> pour faire pivoter la sortie du pinceau sur 45 degrés autour de son centre, vous devez attribuer à <xref:System.Windows.Media.RotateTransform> un <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 0,5 et un <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 0,5.  
  
 L'illustration suivante montre la sortie de plusieurs pinceaux qui ont été pivotés sur 45 degrés à l'aide des propriétés <xref:System.Windows.Media.Brush.RelativeTransform%2A> et <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Propriétés RelativeTransform et Transform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm\_brushrelativetransform\_transform\_small")  
  
<a name="relativetransformandtilebrush"></a>   
## Utilisation de RelativeTransform avec TileBrush  
 Dans la mesure où le pinceau mosaïque est plus complexe que les autres pinceaux, le fait d'appliquer une <xref:System.Windows.Media.Brush.RelativeTransform%2A> à ce type de pinceau peut donner lieu à des résultats inattendus.  Prenons l'exemple de l'image suivante.  
  
 ![Image source](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.png "graphicsmm\_reltransform\_1\_original\_image")  
  
 L'exemple suivant utilise <xref:System.Windows.Media.ImageBrush> pour peindre une zone rectangulaire avec l'image précédente.  Il applique une <xref:System.Windows.Media.RotateTransform> à la propriété <xref:System.Windows.Media.ImageBrush> de l'objet <xref:System.Windows.Media.Brush.RelativeTransform%2A>, et affecte à sa propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> la valeur <xref:System.Windows.Media.Stretch>, qui doit préserver les proportions de l'image quand elle est étirée de façon à remplir complètement le rectangle.  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Cet exemple produit la sortie suivante :  
  
 ![Sortie transformée](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm\_reltransform\_6\_output")  
  
 Notez que l'image est formée, alors même que la <xref:System.Windows.Media.TileBrush.Stretch%2A> du pinceau avait la valeur <xref:System.Windows.Media.Stretch>.  C'est parce que la transformation relative est appliquée après que la <xref:System.Windows.Media.TileBrush.Viewbox%2A> du pinceau est mappée à son <xref:System.Windows.Media.TileBrush.Viewport%2A>.  La liste suivante décrit chaque étape du processus :  
  
1.  Projetez le contenu du pinceau \(<xref:System.Windows.Media.TileBrush.Viewbox%2A>\) sur sa mosaïque de base \(<xref:System.Windows.Media.TileBrush.Viewport%2A>\) en utilisant le paramètre <xref:System.Windows.Media.TileBrush.Stretch%2A> du pinceau.  
  
     ![Étirement de la fenêtre pour adapter à la fenêtre d'affichage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm\_reltransform\_2\_viewbox\_to\_viewport")  
  
2.  Projetez la mosaïque de base sur le rectangle de transformation 1 x 1.  
  
     ![Mappage de la fenêtre d'affichage et du rectangle de transformation](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm\_reltransform\_3\_output\_to\_transform")  
  
3.  Appliquez la <xref:System.Windows.Media.RotateTransform>.  
  
     ![Application de la transformation relative](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm\_reltransform\_4\_transform\_rotate")  
  
4.  Projetez la mosaïque de base transformée sur la zone à peindre.  
  
     ![Projection du pinceau transformé sur la zone de sortie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm\_reltransform\_5\_transform\_to\_output")  
  
<a name="rotateexample"></a>   
## Exemple : Rotation de ImageBrush sur 45 degrés  
 L'exemple suivant applique un <xref:System.Windows.Media.RotateTransform> à la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A> d'une <xref:System.Windows.Media.ImageBrush>.  Les propriétés <xref:System.Windows.Media.RotateTransform> et <xref:System.Windows.Media.RotateTransform.CenterX%2A> d'un objet <xref:System.Windows.Media.RotateTransform.CenterY%2A> ont toutes deux la valeur 0,5, les coordonnées relatives du point central de ce contenu.  Par conséquent, le contenu du pinceau pivote par rapport à son centre.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 L'exemple suivant applique également un <xref:System.Windows.Media.RotateTransform> à un <xref:System.Windows.Media.ImageBrush> ; toutefois, cet exemple utilise la propriété <xref:System.Windows.Media.Brush.Transform%2A> au lieu de la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A>.  Pour faire pivoter le pinceau par rapport à son centre, des coordonnées absolues doivent être affectées aux propriétés <xref:System.Windows.Media.RotateTransform> et <xref:System.Windows.Media.RotateTransform.CenterX%2A> de l'objet <xref:System.Windows.Media.RotateTransform.CenterY%2A>.  Étant donné que le pinceau peint un rectangle de 175 par 90 pixels, le point central du rectangle est \(87,5 ; 45\).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 L'illustration suivante montre le pinceau sans transformation, avec la transformation appliquée à la propriété <xref:System.Windows.Media.Brush.RelativeTransform%2A>, et à la propriété <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Paramètres de Brush RelativeTransform et Transform](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk\_graphicsmm\_transformandrelativetransform")  
  
 Cet exemple est extrait d'un exemple plus complet.  Pour obtenir l'exemple complet, consultez [Pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).  Pour plus d'informations sur les pinceaux, consultez [Vue d'ensemble des pinceaux WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Brush.Transform%2A>   
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>   
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.Brush>   
 [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)