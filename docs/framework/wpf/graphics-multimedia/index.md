---
title: "Graphiques et multim&#233;dia | Microsoft Docs"
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
  - "animation, fonctionnalités"
  - "fonctionnalités graphiques"
  - "média, fonctionnalités"
  - "effets sonores"
  - "effets de transition"
  - "effets de vidéo"
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# Graphiques et multim&#233;dia
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre une prise en charge du multimédia, des graphiques vectoriels, de l'animation et de la composition de contenu, simplifiant la génération d'interfaces utilisateur et de contenu pour les développeurs.  À l'aide de [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vous pouvez créer des graphiques vectoriels ou des animations complexes, et intégrer des médias à vos applications.  
  
 Cette rubrique présente les fonctionnalités de graphiques, d'animation et multimédia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui vous permettent d'ajouter des graphiques, des effets de transition, du son et des vidéos à vos applications.  
  
> [!NOTE]
>  L'utilisation de types WPF dans un service Windows est fortement déconseillée.  Si vous tentez d'utiliser des types WPF dans un service Windows, le service peut ne pas fonctionner comme prévu.  
  
   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## Nouveautés liées aux graphiques et au contenu multimédia dans WPF 4  
 Plusieurs modifications ont été apportées aux graphiques et aux animations.  
  
-   Arrondi de disposition  
  
     Lorsque le bord d'un objet tombe au milieu d'un pixel de périphérique, le système de graphique indépendant des ppp peut créer des artefacts de rendu, tels que des bords flous ou semi\-transparents.  Les versions antérieures de WPF incluaient l'accrochage des pixels pour permettre de traiter ce cas.  Silverlight 2 a introduit l'arrondi de disposition, qui est une autre manière de déplacer des éléments afin que les bords tombent sur les limites des pixels entières.  WPF prend maintenant en charge l'arrondi de disposition avec la propriété jointe <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> sur <xref:System.Windows.FrameworkElement>.  
  
-   Composition mise en cache  
  
     En utilisant les nouvelles classes <xref:System.Windows.Media.BitmapCache> et <xref:System.Windows.Media.BitmapCacheBrush>, vous pouvez mettre en cache une partie complexe de l'arborescence d'éléments visuels en tant qu'image bitmap et améliorer nettement l'heure du rendu.  L'image bitmap continue de réagir aux entrées d'utilisateur, telles que les clics de souris, et vous pouvez la peindre sur d'autres éléments comme avec n'importe quel pinceau.  
  
-   Prise en charge de Pixel Shader 3  
  
     WPF 4 repose sur la prise en charge <xref:System.Windows.Media.Effects.ShaderEffect> introduite dans WPF 3.5 SP1, qui permet aux applications d'écrire des effets à l'aide de Pixel Shader \(PS\) version 3.0.  Le modèle du nuanceur de PS 3.0 est plus sophistiqué que celui de PS 2.0 et  permet d'obtenir davantage d'effets sur le matériel pris en charge.  
  
-   Fonctions d'accélération  
  
     Vous pouvez améliorer des animations avec des fonctions d'accélération, qui vous permettent de mieux contrôler le comportement des animations.  Par exemple, vous pouvez appliquer une <xref:System.Windows.Media.Animation.ElasticEase> à une animation afin de lui conférer un comportement élastique.  Pour plus d'informations, consultez les types d'accélération dans l'espace de noms <xref:System.Windows.Media.Animation>.  
  
<a name="graphics_and_rendering"></a>   
## Graphiques et rendu  
 WPF comprend la prise en charge des graphiques 2D de haute qualité.  Cette fonctionnalité comprend des pinceaux, des géométries, des images, des formes et des transformations.  Pour plus d'informations, consultez [Graphiques](../../../../docs/framework/wpf/graphics-multimedia/graphics.md).  Le rendu des éléments graphiques est basé sur la classe <xref:System.Windows.Media.Visual>.  La structure des objets visuels à l'écran est représentée par l'arborescence d'éléments visuels.  Pour plus d'informations, consultez [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
### Formes 2D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit une bibliothèque de formes vectorielles [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] couramment utilisées, telles que des les rectangles et ellipses présentés dans l'illustration suivante.  
  
 ![Ellipses et rectangles](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.png "WPFIntroFigure4")  
  
 Ces formes [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] intrinsèques ne sont pas seulement des formes : ce sont des éléments programmables qui implémentent de nombreuses fonctionnalités que vous attendez de la plupart des contrôles communs, incluant l'entrée clavier et souris.  L'exemple suivant montre comment gérer l'événement <xref:System.Windows.UIElement.MouseUp> que vous déclenchez en cliquant sur un élément <xref:System.Windows.Shapes.Ellipse>.  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  x:Class="Window1" >  
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />  
</Window>  
```  
  
```csharp  
public partial class Window1  : Window  
{  
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)  
    {  
        MessageBox.Show("You clicked the ellipse!");  
    }  
}  
```  
  
```vb  
Partial Public Class Window1  
    Inherits Window  
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)  
        MessageBox.Show("You clicked the ellipse!")  
    End Sub  
End Class  
  
```  
  
 L'illustration suivante montre la sortie pour la balise [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédente et code\-behind.  
  
 ![Fenêtre avec le texte "vous avez cliqué sur le bouton de sélection"](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Pour plus d'informations, consultez [Vue d'ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).  Pour obtenir un exemple de présentation, consultez [Éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
### Géométries 2D  
 Lorsque les formes [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit ne sont pas suffisantes, vous pouvez utiliser la prise en charge [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour les géométries et les chemins d'accès pour créer le vôtre.  L'illustration suivante montre comment vous pouvez utiliser des géométries pour créer des formes, comme un pinceau de dessin, et extraire d'autres éléments [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 ![Différentes utilisations d'un Chemin d'accès](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.png "WPFIntroFigure5")  
  
 Pour plus d'informations, consultez [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  Pour obtenir un exemple de présentation, consultez [Géométries, exemple](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
### Effets 2D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit à une bibliothèque de classes [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] que vous pouvez utiliser pour créer divers effets.  La capacité de rendu [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet de peindre des éléments d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] comportant des gradients, des bitmaps, des dessins et des vidéos, et de les manipuler en utilisant la rotation, la mise à l'échelle et l'[inclinaison](GTMT).  L'illustration suivante donne un exemple des nombreux effets que vous pouvez obtenir en utilisant des pinceaux [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 ![Illustration de différents pinceaux](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.png "WPFIntroFigure6")  
  
 Pour plus d'informations, consultez [Vue d'ensemble des pinceaux WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  Pour obtenir un exemple de présentation, consultez [Pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
<a name="rendering"></a>   
## Rendu 3D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit un jeu de capacités de rendu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] qui s'intègrent avec la prise en charge de graphiques [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour vous puissiez créer des dispositions plus intéressantes, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] et des visualisations de données.  À la fin du spectre, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vous permet de restituer des images [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] sur les surfaces des formes [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], que montre l'illustration suivante.  
  
 ![Capture d'écran : exemple Visual3D](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Pour plus d'informations, consultez [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).  Pour obtenir un exemple de présentation, consultez [Solides 3D, exemple](http://go.microsoft.com/fwlink/?LinkID=159964).  
  
<a name="animation"></a>   
## Animation  
 Utilisez les animations pour agrandir, faire bouger, faire pivoter et réaliser des fondus avec les contrôles et éléments, et pour créer des transitions de page intéressantes, etc..  En raison du fait que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vous permet d'animer la plupart des propriétés, vous pouvez non seulement animer la plupart des objets [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], mais également utiliser [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour animer les objets personnalisés que vous créez.  
  
 ![Images d'un cube animé](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  Pour obtenir un exemple de présentation, consultez [Galerie d'exemples d'animation](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
<a name="media"></a>   
## Multimédia  
 Les images, la vidéo et l'audio sont des moyens multimédia riches permettant d'acheminer des informations et des expériences utilisateur.  
  
### Images  
 Les images, qui incluent les icônes, les arrière\-plans et même une partie des animations, sont une partie principale de la plupart des applications.  Du fait que vous devez fréquemment utiliser des images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] expose la capacité de les utiliser de différentes manières.  L'illustration suivante montre juste un de ces moyens.  
  
 ![Capture d'écran : exemple de styles](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro\_EventTriggers")  
  
 Pour plus d'informations, consultez [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### Audio et vidéo  
 Une fonctionnalité principale des capacités graphique de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est de fournir la prise en charge native pour utiliser le multimédia, qui inclut la vidéo et l'audio.  L'exemple suivant indique comment insérer un lecteur multimédia dans une application.  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement> est capable de jouer à la fois vidéo et audio, et est suffisamment extensible pour autoriser la création facile de [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] personnalisés.  
  
 Pour plus d'informations, consultez [Vue d'ensemble du multimédia](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Media>   
 <xref:System.Windows.Media.Animation>   
 <xref:System.Windows.Media.Media3D>   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Vue d'ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Animation and Timing](http://msdn.microsoft.com/fr-fr/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [3\-D Graphics](http://msdn.microsoft.com/fr-fr/565c1f3c-235b-47de-b05b-3b53ed63f1b8)   
 [Multimedia](http://msdn.microsoft.com/fr-fr/44a8dcd0-80cb-4db0-a222-87cde68c2fac)