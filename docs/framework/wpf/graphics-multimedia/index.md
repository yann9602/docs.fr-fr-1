---
title: "Graphiques et multimédia | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-4.6
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- media, features
- video effects
- sound effects
- animation, features
- graphics features
- transition effects
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: ea78944133412f43075d8d094cd5fa93685299f9
ms.lasthandoff: 04/08/2017

---
# <a name="graphics-and-multimedia"></a>Graphiques et multimédia
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prend en charge le contenu multimédia, les graphiques vectoriels, l’animation et la composition de contenu, ce qui permet aux développeurs de créer facilement des interfaces utilisateur et du contenu intéressants. À l’aide de [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vous pouvez créer des graphiques vectoriels ou des animations complexes et intégrer du contenu multimédia à vos applications.  
  
 Cette rubrique présente les fonctionnalités graphiques, d’animation et multimédia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qui vous permettent d’ajouter des graphiques, des effets de transition, du son et de la vidéo à vos applications.  
  
> [!NOTE]
>  L’utilisation de types WPF dans un service Windows est fortement déconseillée. Si vous tentez d’utiliser des types WPF dans un service Windows, celui-ci risque de ne pas fonctionner comme prévu.   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Nouveautés Graphiques et multimédia dans WPF 4  
 Plusieurs modifications ont été apportées aux graphiques et aux animations.  
  
-   Arrondi de disposition  
  
     Lorsque le bord d’un objet se trouve au milieu d’un dispositif de pixel, le système de graphiques indépendant des PPP peut créer des artefacts de rendu, tels que des bords flous ou semi-transparents. Les versions précédentes de WPF incluaient l’accrochage pixel pour aider à gérer ce cas. L’arrondi de position, introduit dans Silverlight 2, est une autre façon de déplacer des éléments afin que les bords tombent sur les limites de pixels entières. WPF prend désormais en charge l’arrondi de disposition avec la propriété jointe <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> sur <xref:System.Windows.FrameworkElement>.  
  
-   Composition en cache  
  
     À l’aide des nouvelles classes <xref:System.Windows.Media.BitmapCache> et <xref:System.Windows.Media.BitmapCacheBrush>, vous pouvez mettre en cache une partie complexe de l’arborescence visuelle en tant que bitmap et améliorer considérablement le temps de rendu. L’image bitmap reste réactive aux actions de l’utilisateur, comme des clics de souris, et vous pouvez la peindre sur d’autres éléments comme n’importe quel pinceau.  
  
-   Prise en charge du Nuanceur de pixels 3  
  
     WPF 4 repose sur la prise en charge de <xref:System.Windows.Media.Effects.ShaderEffect> introduite dans WPF 3.5 SP1 en permettant aux applications d’écrire des effets à l’aide du Nuanceur de pixels (PS) version 3.0. Le modèle du nuanceur PS 3.0 est plus sophistiqué que le modèle PS 2.0, pour davantage d’effets sur le matériel pris en charge.  
  
-   Fonctions d'accélération  
  
     Vous pouvez améliorer les animations avec les fonctions d’accélération, qui vous donnent un contrôle supplémentaire sur le comportement des animations. Par exemple, vous pouvez appliquer une <xref:System.Windows.Media.Animation.ElasticEase> à une animation afin de donner l’animation un comportement élastique. Pour plus d’informations, consultez les types d’accélération dans l’espace de noms <xref:System.Windows.Media.Animation>.  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a>Graphiques et rendu  
 WPF inclut la prise en charge des graphiques 2D de haute qualité. La fonctionnalité inclut des pinceaux, des géométries, des images, des formes et des transformations. Pour plus d’informations, consultez [Graphiques](../../../../docs/framework/wpf/graphics-multimedia/graphics.md). Le rendu des éléments graphiques est basé sur la classe <xref:System.Windows.Media.Visual>. La structure des objets visuels à l’écran est décrite par l’arborescence visuelle. Pour plus d’informations, consultez [Vue d’ensemble du rendu graphique WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
### <a name="2-d-shapes"></a>Formes 2D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit une bibliothèque de formes [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] vectorielles courantes, telles que les rectangles et ellipses présentés dans l’illustration suivante.  
  
 ![Ellipses et rectangles](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Ces formes [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] intrinsèques ne sont pas seulement des formes : ce sont des éléments programmables qui implémentent un grand nombre des fonctionnalités que vous attendez des contrôles les plus courants, notamment la saisie avec le clavier et la souris. L’exemple suivant montre comment gérer l’événement <xref:System.Windows.UIElement.MouseUp> déclenché en cliquant sur un élément <xref:System.Windows.Shapes.Ellipse>.  
  
```xaml  
\<Window  
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
  
 L’illustration suivante montre la sortie de l’exemple de balisage et code-behind [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.  
  
 ![Fenêtre avec le texte « vous avez cliqué sur l’ellipse &#33;»](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Pour plus d’informations, consultez [Vue d’ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md). Pour obtenir un exemple d’introduction, consultez [Exemples d’éléments de forme](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
### <a name="2-d-geometries"></a>Géométries 2D  
 Si les formes [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] fournies par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ne sont pas suffisantes, vous pouvez utiliser la prise en charge des géométries et des tracés par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour créer vos propres formes. L’illustration suivante montre comment vous pouvez utiliser les géométries pour créer des formes, comme un pinceau de dessin, et pour détourer d’autres éléments [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 ![Différentes utilisations d’un chemin](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Pour plus d’informations, consultez [Vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md). Pour obtenir un exemple d’introduction, consultez [Exemples de géométries](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
### <a name="2-d-effects"></a>Effets 2D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit une bibliothèque de classes [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] que vous pouvez utiliser pour créer une variété d’effets. La fonction de rendu [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet de peindre des éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] possédant des dégradés, des bitmaps, des dessins et des vidéos ; et de les manipuler à l’aide de la rotation, la mise à l’échelle et l’inclinaison. L’illustration suivante donne un exemple des nombreux effets que vous pouvez obtenir en utilisant les pinceaux [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 ![Illustration de différents pinceaux](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Pour plus d’informations, consultez [Vue d’ensemble des pinceaux WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md). Pour obtenir un exemple d’introduction, consultez [Exemples de pinceaux](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a>Rendu 3D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit un ensemble de fonctionnalités de rendu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] qui s’intègrent à la prise en charge des graphiques [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] afin de créer des dispositions plus intéressantes, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] et la visualisation de données. À une extrémité du spectre, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vous permet d’effectuer un rendu des images [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] sur les surfaces des formes [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], ce que montre l’illustration suivante.  
  
 ![Capture d’écran : exemple Visual3D](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Pour plus d’informations, consultez [Vue d’ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md). Pour obtenir un exemple d’introduction, consultez [Exemples de solides 3D](http://go.microsoft.com/fwlink/?LinkID=159964).  
  
<a name="animation"></a>   
## <a name="animation"></a>Animation  
 Utilisez l’animation pour agrandir, faire bouger, faire pivoter et réaliser des fondus avec les contrôles et les éléments pour créer des transitions de page intéressantes, et plus encore. Étant donné que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vous permet d’animer la plupart des propriétés, vous pouvez non seulement animer la plupart des objets [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], mais vous pouvez également utiliser [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour animer des objets personnalisés que vous créez.  
  
 ![Images d’un cube animé](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Pour plus d’informations, consultez [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Pour obtenir un exemple, consultez [Galerie d’exemples d’animation](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
<a name="media"></a>   
## <a name="media"></a>Médias  
 Les images, la vidéo et l’audio constituent des méthodes multimédia riches de transférer des informations et des expériences utilisateur.  
  
### <a name="images"></a>Images  
 Les images, comprenant les icônes, les arrière-plans et même des parties des animations, sont une composante essentielle de la plupart des applications. Étant donné que vous devez fréquemment utiliser des images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] expose la possibilité de les utiliser de plusieurs façons. L’illustration suivante montre l’une de ces façons.  
  
 ![Capture d’écran : exemple de styles](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
 Pour plus d’informations, consultez [Vue d’ensemble de la création d’images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="video-and-audio"></a>Audio et vidéo  
 Une fonctionnalité principale des capacités graphiques de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est de fournir la prise en charge native pour l’utilisation de contenu multimédia, qui inclut la vidéo et l’audio. L’exemple suivant montre comment insérer un lecteur multimédia dans une application.  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement> est capable de lire la vidéo et l’audio et est suffisamment extensible pour autoriser la création facile de [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] personnalisées.  
  
 Pour plus d'informations, consultez [Vue d’ensemble du multimédia](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media>   
 <xref:System.Windows.Media.Animation>   
 <xref:System.Windows.Media.Media3D>   
 [Graphiques 2D et acquisition d’images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Vue d’ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [Peinture avec des objets d’image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Animation et minutage](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [Graphiques 3D](http://msdn.microsoft.com/en-us/565c1f3c-235b-47de-b05b-3b53ed63f1b8)   
 [Multimédia](http://msdn.microsoft.com/en-us/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
