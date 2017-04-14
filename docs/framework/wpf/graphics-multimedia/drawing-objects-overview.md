---
title: "Vue d&#39;ensemble des objets Drawing | Microsoft Docs"
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
  - "Dessiner des objets"
  - "objets DrawingGroup"
  - "dessins, à propos des dessins"
  - "objets GeometryDrawing"
  - "objets GlyphRunDrawing"
  - "objets ImageDrawing"
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Vue d&#39;ensemble des objets Drawing
Cette rubrique présente les objets <xref:System.Windows.Media.Drawing> et décrit comment les utiliser pour dessiner efficacement des formes, des images, du texte et des médis.  Utilisez les objets <xref:System.Windows.Media.Drawing> lorsque vous créez des images clipart, dessinez avec un <xref:System.Windows.Media.DrawingBrush> ou utilisez les objets <xref:System.Windows.Media.Visual>.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="whatisadrawingsection"></a>   
## Qu'est\-ce qu'un objet Drawing ?  
 Un objet <xref:System.Windows.Media.Drawing> décrit un contenu visible, tel qu'une forme, une image, une vidéo ou une ligne de texte.  Il existe différents types d'objets Drawing pour les types différents de contenu.  La liste qui suit répertorie les différents types d'objets Drawing.  
  
-   <xref:System.Windows.Media.GeometryDrawing> – Dessine une forme.  
  
-   <xref:System.Windows.Media.ImageDrawing> – Dessine une image.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – Dessine du texte.  
  
-   <xref:System.Windows.Media.VideoDrawing> – Lit un fichier audio ou vidéo.  
  
-   <xref:System.Windows.Media.DrawingGroup> – Dessine d'autres dessins.  Utilisez un groupe de dessins pour combiner d'autres dessins en un seul dessin composite.  
  
 Les objets <xref:System.Windows.Media.Drawing> sont polyvalents. Il existe de nombreuses façons d'utiliser un objet <xref:System.Windows.Media.Drawing>.  
  
-   Vous pouvez l'afficher comme une image à l'aide d'un contrôle <xref:System.Windows.Media.DrawingImage> et d'un contrôle <xref:System.Windows.Controls.Image>.  
  
-   Vous pouvez l'utiliser avec un <xref:System.Windows.Media.DrawingBrush> pour peindre un objet, tel que l'<xref:System.Windows.Controls.Page.Background%2A> d'une <xref:System.Windows.Controls.Page>.  
  
-   Vous pouvez l'utiliser pour décrire l'apparence d'un <xref:System.Windows.Media.DrawingVisual>.  
  
-   Vous pouvez l'utiliser pour énumérer le contenu d'un <xref:System.Windows.Media.Visual>.  
  
 WPF propose d'autres types d'objets permettant de dessiner des formes, des images, du texte et des médias.  Par exemple, vous pouvez aussi utiliser des objets <xref:System.Windows.Shapes.Shape> pour dessiner des formes et le contrôle <xref:System.Windows.Controls.MediaElement> fournit un autre moyen d'ajouter un contenu vidéo à votre application.  Par conséquent, quand devez\-vous utiliser des objets <xref:System.Windows.Media.Drawing> ?  Lorsque vous pouvez sacrifier des fonctionnalités au niveau de l'infrastructure pour optimiser les performances ou lorsque vous avez besoin de fonctionnalités <xref:System.Windows.Freezable>.  Étant donné que les objets <xref:System.Windows.Media.Drawing> ne prennent pas en charge le [Disposition](../../../../docs/framework/wpf/advanced/layout.md), l'entrée et le focus, ils fournissent de meilleures performances, idéales pour la description des arrière\-plans, les images clipart, et pour le dessin de bas niveau avec les objets <xref:System.Windows.Media.Visual>.  
  
 Comme ils constituent un objet <xref:System.Windows.Freezable> type, les objets <xref:System.Windows.Media.Drawing> héritent de plusieurs fonctionnalités spéciales qui permettent notamment de les déclarer comme étant des [ressources](../../../../docs/framework/wpf/advanced/xaml-resources.md), partagés entre plusieurs objets, configurés en lecture seule \(afin d'améliorer les performances\), clonés ou rendus thread\-safe.  Pour plus d'informations sur les différentes fonctionnalités fournies par les objets <xref:System.Windows.Freezable>, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## Dessiner une forme  
 Pour dessiner une forme, utilisez un <xref:System.Windows.Media.GeometryDrawing>.  La propriété <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> d'un dessin géométrique décrit la forme à dessiner, la propriété <xref:System.Windows.Media.GeometryDrawing.Brush%2A> décrit comment peindre l'intérieur de la forme et la propriété <xref:System.Windows.Media.GeometryDrawing.Pen%2A> décrit comment dessiner son contour.  
  
 L'exemple suivant illustre l'utilisation d'un <xref:System.Windows.Media.GeometryDrawing> pour dessiner une forme.  La forme est décrite par un <xref:System.Windows.Media.GeometryGroup> et deux objets <xref:System.Windows.Media.EllipseGeometry>.  L'intérieur de la forme est peint avec un <xref:System.Windows.Media.LinearGradientBrush> et son contour est dessiné avec un <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 Cet exemple crée l'objet <xref:System.Windows.Media.GeometryDrawing> suivant.  
  
 ![GeometryDrawing de deux ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Pour obtenir l'exemple complet, consultez [Créer un GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md).  
  
 D'autres classes <xref:System.Windows.Media.Geometry>, telles que <xref:System.Windows.Media.PathGeometry> vous permettent de créer des formes plus complexes en créant des courbes et des arcs.  Pour plus d'informations sur les objets <xref:System.Windows.Media.Geometry>, consultez [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 Pour plus d'informations sur d'autres façons de dessiner des formes sans utiliser d'objets <xref:System.Windows.Media.Drawing>, consultez [Vue d'ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## Dessiner une image  
 Pour dessiner une image, utilisez un <xref:System.Windows.Media.ImageDrawing>.  La propriété <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> d'un objet <xref:System.Windows.Media.ImageDrawing> décrit l'image à dessiner et la propriété <xref:System.Windows.Media.ImageDrawing.Rect%2A> définit la région dans laquelle l'image est dessinée.  
  
 L'exemple suivant dessine une image dans un rectangle situé à \(75,75\), soit 100 sur 100 [pixels](GTMT).  L'illustration suivante montre l'exemple du <xref:System.Windows.Media.ImageDrawing> créé.  Une bordure grise a été ajoutée pour montrer les limites du <xref:System.Windows.Media.ImageDrawing>.  
  
 ![ImageDrawing 100 par 100 dessiné à &#40;75,75&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm\_simple\_imagedrawing\_offset")  
ImageDrawing 100 sur 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Pour plus d'informations sur les images, consultez [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
<a name="playmedia"></a>   
## Lire un média \(code uniquement\)  
  
> [!NOTE]
>  Bien que vous puissiez déclarer un <xref:System.Windows.Media.VideoDrawing> en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez uniquement charger et lire son média en utilisant le code.  Pour lire une vidéo en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], utilisez plutôt <xref:System.Windows.Controls.MediaElement>.  
  
 Pour lire un fichier audio ou vidéo, utilisez un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer>.  Il existe deux façons de charger et de lire un média.  La première consiste à utiliser un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing>, et la seconde consiste à créer votre propre <xref:System.Windows.Media.MediaTimeline> à utiliser avec <xref:System.Windows.Media.MediaPlayer> et <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Lorsque vous distribuez un média avec votre application, vous ne pouvez pas utiliser un fichier multimédia comme ressource de projet, comme vous le feriez avec une image.  Dans votre fichier projet, vous devez plutôt affecter `Content` au type de média et `PreserveNewest` ou `Always` à `CopyToOutputDirectory`.  
  
 Pour lire un média sans créer votre propre <xref:System.Windows.Media.MediaTimeline>, vous devez effectuer la procédure suivante.  
  
1.  Créez un objet <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  Utilisez la méthode <xref:System.Windows.Media.MediaPlayer.Open%2A> pour charger le fichier multimédia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  Créez un <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  Spécifiez la taille et l'emplacement où dessiner le média en définissant la propriété <xref:System.Windows.Media.VideoDrawing.Rect%2A> du <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  Définissez la propriété <xref:System.Windows.Media.VideoDrawing.Player%2A> du <xref:System.Windows.Media.VideoDrawing> avec le <xref:System.Windows.Media.MediaPlayer> que vous avez créé.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  Utilisez la méthode <xref:System.Windows.Media.MediaPlayer.Play%2A> du <xref:System.Windows.Media.MediaPlayer> pour commencer à lire le média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer> pour lire un fichier vidéo une seule fois.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour optimiser le contrôle du minutage du média, utilisez un <xref:System.Windows.Media.MediaTimeline> avec le <xref:System.Windows.Media.MediaPlayer> et des objets <xref:System.Windows.Media.VideoDrawing>.  <xref:System.Windows.Media.MediaTimeline> vous permet de spécifier si la vidéo doit se répéter.  Pour utiliser un <xref:System.Windows.Media.MediaTimeline> avec un <xref:System.Windows.Media.VideoDrawing>, vous devez effectuer la procédure suivante :  
  
1.  Déclarez le <xref:System.Windows.Media.MediaTimeline> et définissez ses comportements de minutage.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  Créez un <xref:System.Windows.Media.MediaClock> à partir d'un <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  Créez un <xref:System.Windows.Media.MediaPlayer> et utilisez le <xref:System.Windows.Media.MediaClock> pour définir sa propriété <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  Créez un <xref:System.Windows.Media.VideoDrawing> et assignez le <xref:System.Windows.Media.MediaPlayer> à la propriété <xref:System.Windows.Media.VideoDrawing.Player%2A> du <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.MediaTimeline> avec un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> pour lire un fichier vidéo à plusieurs reprises.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Notez que lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline>, vous utilisez le <xref:System.Windows.Media.Animation.ClockController> interactif retourné à partir de la propriété <xref:System.Windows.Media.Animation.Clock.Controller%2A> du <xref:System.Windows.Media.MediaClock> pour contrôler la lecture du média à la place des méthodes interactives du <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## Dessiner un texte  
 Pour dessiner un texte, utilisez un <xref:System.Windows.Media.GlyphRunDrawing> et un <xref:System.Windows.Media.GlyphRun>.  L'exemple suivant utilise un <xref:System.Windows.Media.GlyphRunDrawing> pour dessiner le texte « Hello World ».  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 Un <xref:System.Windows.Media.GlyphRun> est un objet de bas niveau prévu pour la présentation et l'impression de documents de format fixe.  Une méthode plus simple pour dessiner du texte à l'écran consiste à utiliser un <xref:System.Windows.Controls.Label> ou un <xref:System.Windows.Controls.TextBlock>.  Pour plus d'informations sur <xref:System.Windows.Media.GlyphRun>, consultez la vue d'ensemble [Introduction à l'objet GlyphRun et à l'élément Glyphs](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md).  
  
<a name="compositedrawingssection"></a>   
## Dessins composites  
 Un <xref:System.Windows.Media.DrawingGroup> vous permet de combiner plusieurs dessins en un seul dessin composite.  À l'aide d'un <xref:System.Windows.Media.DrawingGroup>, vous pouvez combiner des formes, des images et du texte en un seul objet <xref:System.Windows.Media.Drawing>.  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.DrawingGroup> pour combiner deux objets <xref:System.Windows.Media.GeometryDrawing> et un <xref:System.Windows.Media.ImageDrawing>.  Cet exemple génère la sortie suivante.  
  
 ![DrawingGroup avec plusieurs dessins](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.png "graphicsmm\_simple")  
Dessin composite  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Un <xref:System.Windows.Media.DrawingGroup> vous permet également d'appliquer des masques d'opacité, des transformations, des effets bitmap et d'autres opérations à son contenu.  Les opérations <xref:System.Windows.Media.DrawingGroup> sont appliquées dans l'ordre suivant : <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, puis <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 L'illustration suivante montre l'ordre dans lequel les opérations du <xref:System.Windows.Media.DrawingGroup> sont appliquées.  
  
 ![ordre des opérations DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm\_drawinggroup\_order")  
Ordre des opérations du DrawingGroup  
  
 Le tableau suivant décrit les propriétés que vous pouvez utiliser pour manipuler le contenu d'un objet <xref:System.Windows.Media.DrawingGroup>.  
  
|Propriété|Description|Illustration|  
|---------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Modifie l'opacité de certaines parties du contenu d'un <xref:System.Windows.Media.DrawingGroup>.  Pour obtenir un exemple, consultez [How to: Control the Opacity of a Drawing](http://msdn.microsoft.com/fr-fr/68580652-7d32-4d27-93cc-a5148cf4d5ee).||  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Modifie uniformément l'opacité du contenu d'un <xref:System.Windows.Media.DrawingGroup>.  Utilisez cette propriété pour rendre un <xref:System.Windows.Media.Drawing> entièrement ou partiellement transparent.  Pour obtenir un exemple, consultez [How to: Apply an Opacity Mask to a Drawing](http://msdn.microsoft.com/fr-fr/d77b420b-9be2-479c-a45e-82f4da30eb9f).||  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Applique un <xref:System.Windows.Media.Effects.BitmapEffect> au contenu du <xref:System.Windows.Media.DrawingGroup>.  Pour obtenir un exemple, consultez [How to: Apply a BitmapEffect to a Drawing](http://msdn.microsoft.com/fr-fr/c5b1de83-8d09-47fb-96db-5f174471f4b5).||  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Découpe le contenu d'un <xref:System.Windows.Media.DrawingGroup> dans une zone décrite à l'aide d'un <xref:System.Windows.Media.Geometry>.  Pour obtenir un exemple, consultez [How to: Clip a Drawing](http://msdn.microsoft.com/fr-fr/1f7d8a2c-c3c2-42cb-a542-e6796f9fb058).||  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Aligne les [pixels indépendants du périphérique](GTMT) sur les pixels du périphérique selon les directives spécifiées.  Cette propriété est utile pour vérifier que la restitution des graphiques très détaillés est nette sur les écrans basse résolution.  Pour obtenir un exemple, consultez [Appliquer un GuidelineSet à un dessin](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md).||  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transforme le contenu du <xref:System.Windows.Media.DrawingGroup>.  Pour obtenir un exemple, consultez [How to: Apply a Transform to a Drawing](http://msdn.microsoft.com/fr-fr/0d525f2b-682d-4d67-9660-cf46929fbabd).||  
  
<a name="usingimagedrawing"></a>   
## Afficher un dessin comme une image  
 Pour afficher un <xref:System.Windows.Media.Drawing> avec un contrôle <xref:System.Windows.Controls.Image>, utilisez un <xref:System.Windows.Media.DrawingImage> comme contrôle du <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Image.Source%2A> et affectez à la propriété <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=fullName> de l'objet <xref:System.Windows.Media.DrawingImage> le dessin que vous souhaitez afficher.  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.DrawingImage> et un contrôle <xref:System.Windows.Controls.Image> pour afficher un <xref:System.Windows.Media.GeometryDrawing>.  Cet exemple génère la sortie suivante.  
  
 ![GeometryDrawing de deux ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## Peindre un objet avec un objet Drawing  
 Un <xref:System.Windows.Media.DrawingBrush> est un type de pinceau qui peint une zone avec un objet Drawing.  Vous pouvez l'utiliser pour peindre un objet graphique avec un objet Drawing.  La propriété <xref:System.Windows.Media.Drawing> d'un <xref:System.Windows.Media.DrawingBrush> décrit son <xref:System.Windows.Media.DrawingBrush.Drawing%2A>.  Pour restituer un <xref:System.Windows.Media.Drawing> avec un <xref:System.Windows.Media.DrawingBrush>, ajoutez\-le au pinceau à l'aide de la propriété <xref:System.Windows.Media.Drawing> du pinceau et utilisez le pinceau pour peindre un objet graphique, tel qu'un contrôle ou panneau.  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.DrawingBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle> avec un modèle créé à partir d'un <xref:System.Windows.Media.GeometryDrawing>.  Cet exemple génère la sortie suivante.  
  
 ![DrawingBrush en mosaïque](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm\_drawingbrush\_geometrydrawing")  
GeometryDrawing utilisé avec un DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 La classe <xref:System.Windows.Media.DrawingBrush> fournit plusieurs options pour étier et afficher en mosaïques son contenu.  Pour plus d'informations sur <xref:System.Windows.Media.DrawingBrush>, consultez la vue d'ensemble [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="renderingwithvisualsection"></a>   
## Rendu d'un dessin avec un Visual  
 Un <xref:System.Windows.Media.DrawingVisual> est un type d'objet visuel conçu pour restituer un dessin.  Travailler directement sur la superposition visuelle est une option pour les développeurs qui souhaitent générer un environnement hautement graphique personnalisé, mais cette procédure n'est pas décrite dans cette vue d'ensemble.  Pour plus d'informations, consultez la vue d'ensemble [Utilisation d'objets DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="drawingcontextobjects"></a>   
## Objets DrawingContext  
 La classe <xref:System.Windows.Media.DrawingContext> vous permet de remplir un <xref:System.Windows.Media.Visual> ou un <xref:System.Windows.Media.Drawing> avec un contenu visuel.  Nombre d'objets graphiques de niveau inférieur utilisent un <xref:System.Windows.Media.DrawingContext> car il décrit le contenu graphique très efficacement.  
  
 Bien que les méthodes de dessin <xref:System.Windows.Media.DrawingContext> semblent être similaires aux méthodes de dessin du type <xref:System.Drawing.Graphics?displayProperty=fullName>, elles sont en réalité très différentes.  <xref:System.Windows.Media.DrawingContext> est utilisé avec un système graphique à mode conservé, tandis que le type <xref:System.Drawing.Graphics?displayProperty=fullName> est utilisé avec un système graphique à mode direct.  Lorsque vous utilisez les commandes de dessin d'un objet <xref:System.Windows.Media.DrawingContext>, vous stockez réellement un jeu d'instructions de rendu \(bien que le mécanisme de stockage exact dépende du type d'objet qui fournit le <xref:System.Windows.Media.DrawingContext>\) qui seront utilisées ultérieurement par le système graphique ; vous ne dessinez pas à l'écran en temps réel.  Pour plus d'informations sur le fonctionnement du système graphique de [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)], consultez [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 Vous n'instanciez jamais un <xref:System.Windows.Media.DrawingContext> directement ; vous pouvez toutefois acquérir un contexte de dessin de certaines méthodes, telles que <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=fullName> et <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=fullName>.  
  
<a name="enumeratevisualcontents"></a>   
## Énumérer le contenu d'un Visual  
 Outre leurs autres utilisations, les objets <xref:System.Windows.Media.Drawing> fournissent aussi un modèle d'objet pour énumérer le contenu d'un <xref:System.Windows.Media.Visual>.  
  
 L'exemple suivant utilise la méthode <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> pour récupérer la valeur <xref:System.Windows.Media.DrawingGroup> d'un <xref:System.Windows.Media.Visual> et l'énumérer.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## Voir aussi  
 <xref:System.Windows.Media.Drawing>   
 <xref:System.Windows.Media.DrawingGroup>   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [Vue d'ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)