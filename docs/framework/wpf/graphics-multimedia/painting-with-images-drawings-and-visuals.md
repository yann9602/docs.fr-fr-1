---
title: "Peinture avec des objets d&#39;image, de dessin et visuels | Microsoft Docs"
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
  - "pinceaux, peindre avec des dessins"
  - "pinceaux, peindre avec des images"
  - "pinceaux, peindre avec des objets visuels"
  - "peindre avec des objets visuels"
  - "peindre, avec des dessins"
  - "peindre, avec des images"
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# Peinture avec des objets d&#39;image, de dessin et visuels
Cette rubrique explique comment utiliser les objets <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> pour peindre une zone avec une image, un <xref:System.Windows.Media.Drawing> ou un <xref:System.Windows.Media.Visual>.  
  
   
  
<a name="prereqs"></a>   
## Composants requis  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les différents types de pinceaux que propose [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et leurs fonctionnalités de base.  Pour une introduction, consultez [Vue d'ensemble des pinceaux WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
<a name="image"></a>   
## Peindre une zone avec une image  
 Un <xref:System.Windows.Media.ImageBrush> peint une zone avec une <xref:System.Windows.Media.ImageSource>.  Le type d'<xref:System.Windows.Media.ImageSource> le plus courant à utiliser avec un <xref:System.Windows.Media.ImageBrush> est une <xref:System.Windows.Media.Imaging.BitmapImage>, qui décrit un graphique bitmap.  Vous pouvez utiliser une <xref:System.Windows.Media.DrawingImage> pour peindre à l'aide d'un objet <xref:System.Windows.Media.Drawing>, mais il est plus simple d'utiliser un <xref:System.Windows.Media.DrawingBrush>.  Pour plus d'informations sur les objets <xref:System.Windows.Media.ImageSource>, consultez [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
 Pour peindre avec un <xref:System.Windows.Media.ImageBrush>, créez une <xref:System.Windows.Media.Imaging.BitmapImage> et utilisez\-la pour charger un contenu de bitmap.  Ensuite, utilisez <xref:System.Windows.Media.Imaging.BitmapImage> pour définir la propriété <xref:System.Windows.Media.ImageBrush.ImageSource%2A> du <xref:System.Windows.Media.ImageBrush>.  Enfin, appliquez le <xref:System.Windows.Media.ImageBrush> à l'objet que vous voulez peindre.  En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez également définir la propriété <xref:System.Windows.Media.ImageBrush.ImageSource%2A> du <xref:System.Windows.Media.ImageBrush> selon le chemin d'accès de l'image à charger.  
  
 Comme tous les objets <xref:System.Windows.Media.Brush>, un <xref:System.Windows.Media.ImageBrush> peut être utilisé pour peindre des objets tels que des formes, des panneaux, des contrôles et du texte.  L'illustration suivante indique divers effets pouvant être accomplis avec un <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemples de sortie ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.png "wcpsdk\_mmgraphics\_imagebrushexamples")  
Objets peints avec un ImageBrush  
  
 Par défaut, un <xref:System.Windows.Media.ImageBrush> étend son image de façon à remplir complètement la zone qui est peinte, en déformant peut\-être l'image si la zone peinte a des proportions différentes de celles de l'image.  Vous pouvez modifier ce comportement en faisant passer la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> de la valeur par défaut <xref:System.Windows.Media.Stretch> à <xref:System.Windows.Media.Stretch>, <xref:System.Windows.Media.Stretch> ou <xref:System.Windows.Media.Stretch>.  Dans la mesure où <xref:System.Windows.Media.ImageBrush> est un type de <xref:System.Windows.Media.TileBrush>, vous pouvez spécifier exactement comment un pinceau image remplit la zone de sortie et même crée des motifs.  Pour plus d'informations sur le blocage et les fonctionnalités avancées de <xref:System.Windows.Media.TileBrush>, consultez [Vue d'ensemble de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## Exemple : peindre un objet avec une image bitmap  
 L'exemple suivant utilise un <xref:System.Windows.Media.ImageBrush> pour peindre l'objet <xref:System.Windows.Controls.Panel.Background%2A> d'un <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## Peindre une zone avec un dessin \(Drawing\)  
 Un <xref:System.Windows.Media.DrawingBrush> vous permet de peindre une zone avec des formes, du texte, des images et de la vidéo.  Les formes à l'intérieur d'un pinceau de dessin peuvent elles\-mêmes être peintes avec des couleurs unies, des dégradées, des images et même un <xref:System.Windows.Media.DrawingBrush>.  L'illustration suivante montre certaines utilisations d'un <xref:System.Windows.Media.DrawingBrush>.  
  
 ![Exemples de sortie DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk\_mmgraphics\_drawingbrushexamples")  
Objets peints par un DrawingBrush  
  
 Un <xref:System.Windows.Media.DrawingBrush> peint une zone avec un objet <xref:System.Windows.Media.Drawing>.  Un objet <xref:System.Windows.Media.Drawing> décrit un contenu visible, tel qu'une forme, une image, une vidéo ou une ligne de texte.  Il existe différents types d'objets Drawing pour les types différents de contenu.  La liste qui suit répertorie les différents types d'objets Drawing.  
  
-   <xref:System.Windows.Media.GeometryDrawing> – Dessine une forme.  
  
-   <xref:System.Windows.Media.ImageDrawing> – Dessine une image.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – Dessine du texte.  
  
-   <xref:System.Windows.Media.VideoDrawing> – Lit un fichier audio ou vidéo.  
  
-   <xref:System.Windows.Media.DrawingGroup> – Dessine d'autres dessins.  Utilisez un groupe de dessins pour combiner d'autres dessins en un seul dessin composite.  
  
 Pour plus d'informations sur les objets <xref:System.Windows.Media.Drawing>, consultez [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
 À l'instar d'un <xref:System.Windows.Media.ImageBrush>, un <xref:System.Windows.Media.DrawingBrush> étend son <xref:System.Windows.Media.DrawingBrush.Drawing%2A> pour remplir sa zone de sortie.  Vous pouvez substituer ce comportement en modifiant la valeur par défaut <xref:System.Windows.Media.Stretch> de la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A>.  Pour plus d'informations, consultez la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## Exemple : peindre un objet avec un dessin  
 L'exemple suivant montre comment peindre un objet avec un dessin de trois ellipses.  Un <xref:System.Windows.Media.GeometryDrawing> permet de décrire les ellipses.  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## Peindre une zone avec un visuel  
 Le plus puissant et le plus polyvalent de tous les pinceaux, le <xref:System.Windows.Media.VisualBrush> peint une zone avec un <xref:System.Windows.Media.Visual>.  Un <xref:System.Windows.Media.Visual> est un type graphique de bas niveau qui sert d'ancêtre à de nombreux composants graphiques.  Par exemple, les classes <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement> et <xref:System.Windows.Controls.Control> correspondent à tous les types d'objets <xref:System.Windows.Media.Visual>.  En utilisant un <xref:System.Windows.Media.VisualBrush>, vous pouvez peindre des zones avec n'importe quel objet graphique [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ou presque.  
  
> [!NOTE]
>  Bien que <xref:System.Windows.Media.VisualBrush> soit un type d'objet <xref:System.Windows.Freezable>, il ne peut pas être gelé \(mis dans un état en lecture seule\) quand sa propriété <xref:System.Windows.Media.VisualBrush.Visual%2A> a une valeur autre que `null`.  
  
 Il existe deux façons de spécifier le contenu <xref:System.Windows.Media.VisualBrush.Visual%2A> d'un <xref:System.Windows.Media.VisualBrush>.  
  
-   Créez un nouveau <xref:System.Windows.Media.Visual>, puis utilisez\-le pour définir la propriété <xref:System.Windows.Media.VisualBrush.Visual%2A> du <xref:System.Windows.Media.VisualBrush>.  Pour obtenir un exemple, consultez la section [Exemple : peindre un objet avec un visuel](#examplevisualbrush1) qui suit.  
  
-   Utilisez un <xref:System.Windows.Media.Visual> existant, qui crée une image dupliquée de la cible <xref:System.Windows.Media.Visual>.  Vous pouvez alors utiliser <xref:System.Windows.Media.VisualBrush> pour créer des effets intéressants, comme la réflexion et l'agrandissement.  Pour obtenir un exemple, consultez la section Comment créer une vue sous [Exemple : créer une réflexion](#examplevisualbrush2).  
  
 Lorsque vous définissez un nouveau <xref:System.Windows.Media.VisualBrush.Visual%2A> pour un <xref:System.Windows.Media.VisualBrush> et que <xref:System.Windows.Media.Visual> est un <xref:System.Windows.UIElement> \(un panneau ou un contrôle\), le système de disposition s'exécute sur <xref:System.Windows.UIElement> et ses éléments enfants quand la propriété <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> a la valeur `true`.  Cependant, la racine <xref:System.Windows.UIElement> est essentiellement isolée du reste du système : les styles et la disposition externe ne peuvent pas franchir cette limite.  Par conséquent, vous devez explicitement spécifier la taille de la racine <xref:System.Windows.UIElement>, car son seul parent est le <xref:System.Windows.Media.VisualBrush> et ne peut donc pas se dimensionner automatiquement à la zone qui est peinte.  Pour plus d'informations sur la disposition dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consultez [Disposition](../../../../docs/framework/wpf/advanced/layout.md).  
  
 À l'instar de <xref:System.Windows.Media.ImageBrush> et de  <xref:System.Windows.Media.DrawingBrush>, un <xref:System.Windows.Media.VisualBrush> étend son contenu pour remplir sa zone de sortie.  Vous pouvez substituer ce comportement en modifiant la valeur par défaut <xref:System.Windows.Media.Stretch> de la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A>.  Pour plus d'informations, consultez la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="examplevisualbrush1"></a>   
## Exemple : peindre un objet avec un visuel  
 Dans l'exemple suivant, plusieurs contrôles et un panneau sont utilisés pour peindre un rectangle.  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## Exemple : créer une réflexion  
 L'exemple précédent a montré comment créer un nouveau <xref:System.Windows.Media.Visual> à utiliser comme arrière\-plan.  Vous pouvez également utiliser un <xref:System.Windows.Media.VisualBrush> pour afficher un effet visuel existant ; cette fonction vous permet de produire des effets visuels intéressants, tels que des réflexions et des agrandissements.  L'exemple suivant utilise un <xref:System.Windows.Media.VisualBrush> pour créer la réflexion d'une <xref:System.Windows.Controls.Border> qui contient plusieurs éléments.  L'illustration suivante montre la sortie produite par cet exemple.  
  
 ![Objet Visual réfléchi](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.png "graphicsmm\_visualbrush\_reflection\_small")  
Objet visuel réfléchi  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Pour obtenir des exemples supplémentaires qui montrent comment agrandir des parties de l'écran et créer des réflexions, consultez [VisualBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## Fonctionnalités TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush> sont des types d'objets <xref:System.Windows.Media.TileBrush>.  Les objets <xref:System.Windows.Media.TileBrush> vous permettent de bien contrôler la peinture d'une zone à l'aide d'une image, d'un dessin ou d'un visuel.  Par exemple, au lieu de simplement peindre une zone à l'aide d'une seule image étendue, vous pouvez utiliser une série de mosaïques d'images qui créent un motif.  
  
 Un <xref:System.Windows.Media.TileBrush> a trois composants essentiels : un content, des titres et la zone de sortie.  
  
 ![Composants de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk\_mmgraphics\_defaultcontentprojection2")  
Composants d'un TileBrush avec une seule mosaïque  
  
 ![Composants d'un TileBrush en mosaïque](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm\_tiledprojection")  
Composants d'un TileBrush avec plusieurs mosaïques  
  
 Pour plus d'informations sur les fonctions de disposition en mosaïque <xref:System.Windows.Media.TileBrush>, consultez [Vue d'ensemble de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.ImageBrush>   
 <xref:System.Windows.Media.DrawingBrush>   
 <xref:System.Windows.Media.VisualBrush>   
 <xref:System.Windows.Media.TileBrush>   
 [Vue d'ensemble de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)   
 [Vue d'ensemble des pinceaux WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)   
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Vue d'ensemble des masques d'opacité](../../../../docs/framework/wpf/graphics-multimedia/opacity-masks-overview.md)   
 [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [ImageBrush, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160005)   
 [VisualBrush, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160049)