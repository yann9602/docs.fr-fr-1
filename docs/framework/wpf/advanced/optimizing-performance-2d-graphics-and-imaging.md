---
title: "Optimisation des performances&#160;: graphiques 2D et acquisition d&#39;images | Microsoft Docs"
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
  - "graphiques 2D"
  - "dessiner, optimiser les performances"
  - "graphiques, performances"
  - "images, optimiser les performances"
  - "images, optimiser les performances"
  - "formes, optimiser les performances"
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Optimisation des performances&#160;: graphiques 2D et acquisition d&#39;images
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une large gamme de fonctionnalités graphiques 2D et d'acquisition d'images qui peuvent être optimisées pour répondre aux spécifications de votre application.  Cette rubrique fournit des informations sur l'optimisation des performances dans ces domaines.  
  
   
  
<a name="Drawing_and_Shapes"></a>   
## Dessin et formes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les objets <xref:System.Windows.Media.Drawing> et <xref:System.Windows.Shapes.Shape> pour représenter du contenu graphique dessiné.  Cependant, les objets <xref:System.Windows.Media.Drawing> sont des constructions plus simples que les objets <xref:System.Windows.Shapes.Shape> et présentent de meilleures caractéristiques de performances.  
  
 <xref:System.Windows.Shapes.Shape> vous permet de dessiner une forme graphique à l'écran.  Puisqu'ils sont dérivés de la classe <xref:System.Windows.FrameworkElement>, les objets <xref:System.Windows.Shapes.Shape> peuvent être utilisés à l'intérieur des panneaux et de la plupart des contrôles.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre plusieurs couches d'accès aux services graphiques et de rendu.  Au niveau de la couche supérieure, les objets, <xref:System.Windows.Shapes.Shape> sont faciles à utiliser et offrent de nombreuses fonctionnalités utiles, telles que la disposition et la gestion d'événements.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit plusieurs objets de forme prêts à l'emploi.  Tous les objets de forme héritent de la classe <xref:System.Windows.Shapes.Shape>.  Parmi les objets de forme disponibles figurent <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline> et <xref:System.Windows.Shapes.Rectangle>.  
  
 Les objets <xref:System.Windows.Media.Drawing>, en revanche, ne dérivent pas de la classe <xref:System.Windows.FrameworkElement> et fournissent une implémentation allégée du rendu des formes, des images et du texte.  
  
 Il existe quatre types d'objets <xref:System.Windows.Media.Drawing> :  
  
-   <xref:System.Windows.Media.GeometryDrawing> Dessine une forme.  
  
-   <xref:System.Windows.Media.ImageDrawing> Dessine une image.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> Dessine du texte.  
  
-   <xref:System.Windows.Media.DrawingGroup> Dessine d'autres dessins.  Utilisez un groupe de dessins pour combiner d'autres dessins en un seul dessin composite.  
  
 L'objet <xref:System.Windows.Media.GeometryDrawing> est utilisé pour afficher du contenu géométrique.  La classe <xref:System.Windows.Media.Geometry> et les classes concrètes qui en dérivent, telles que <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry> et <xref:System.Windows.Media.PathGeometry>, fournissent une solution pour le rendu des graphiques 2D ainsi que la prise en charge des tests d'atteinte et du détourage.  Les objets géométriques peuvent être utilisés pour définir la zone d'un contrôle, par exemple, ou pour définir la zone de détourage à appliquer à une image.  Les objets géométriques peuvent constituer des zones simples, telles que des rectangles et des cercles, ou des zones composites créées à partir d'au moins deux objets géométriques.  Il est possible de créer des zones géométriques plus complexes en combinant des objets dérivés de <xref:System.Windows.Media.PathSegment>, tels que <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment> et <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 En apparence, les classes <xref:System.Windows.Media.Geometry> et <xref:System.Windows.Shapes.Shape> sont assez semblables.  Elles sont toutes deux utilisées pour le rendu des graphiques 2D et elles ont toutes deux des classes concrètes semblables qui dérivent d'elles, par exemple <xref:System.Windows.Media.EllipseGeometry> et <xref:System.Windows.Shapes.Ellipse>.  Toutefois, il existe des différences importantes entre ces deux ensembles de classes.  À l'une d'elles, la classe <xref:System.Windows.Media.Geometry>, il manque une partie des fonctionnalités de la classe <xref:System.Windows.Shapes.Shape>, telle que la possibilité de dessiner elle\-même.  Pour dessiner un objet géométrique, une autre classe telle que DrawingContext, Drawing ou Path \(il est important de noter que Path est une forme\) doit être utilisée pour effectuer l'opération de dessin.  Les propriétés de rendu telles que le remplissage, le trait et l'épaisseur du trait sont dans la classe qui dessine l'objet géométrique, puisqu'un objet de forme contient ces propriétés.  Une façon de se représenter à l'esprit cette différence est de considérer qu'un objet géométrique définit une zone, par exemple un cercle, tandis qu'un objet de forme définit une zone, définit son remplissage et son contour, et participe au système de disposition.  
  
 Puisque les objets <xref:System.Windows.Shapes.Shape> dérivent de la classe <xref:System.Windows.FrameworkElement>, leur utilisation peut engendrer une plus grande consommation de mémoire de votre application.  Si vous n'avez réellement pas besoin des fonctionnalités de <xref:System.Windows.FrameworkElement> pour votre contenu graphique, envisagez l'utilisation des objets <xref:System.Windows.Media.Drawing> allégés.  
  
 Pour plus d'informations sur les objets <xref:System.Windows.Media.Drawing>, consultez [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## Objets StreamGeometry  
 L'objet <xref:System.Windows.Media.StreamGeometry> est une alternative légère à <xref:System.Windows.Media.PathGeometry> pour la création de formes géométriques.  Utilisez <xref:System.Windows.Media.StreamGeometry> lorsque vous avez besoin de décrire une géométrie complexe.  <xref:System.Windows.Media.StreamGeometry> est optimisé pour gérer de nombreux objets <xref:System.Windows.Media.PathGeometry> et fonctionne mieux en comparaison à l'utilisation de nombreux objets <xref:System.Windows.Media.PathGeometry> individuels.  
  
 L'exemple suivant utilise la syntaxe d'attribut pour créer un <xref:System.Windows.Media.StreamGeometry> triangulaire en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Pour plus d'informations sur les objets <xref:System.Windows.Media.StreamGeometry>, consultez [Créer une forme à l'aide d'un StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## Objets DrawingVisual  
 L'objet <xref:System.Windows.Media.DrawingVisual> est une classe de dessin légère utilisée pour le rendu des formes, des images ou du texte.  Cette classe est considérée comme légère parce qu'elle ne fournit pas la disposition ou la gestion d'événements, ce qui améliore ses performances.  Pour cette raison, les objets de ce type sont idéaux pour les arrière\-plans et les images clipart.  Pour plus d'informations, consultez [Utilisation d'objets DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## Images  
 L'acquisition d'images de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apporte une amélioration importante par rapport aux fonctionnalités des images des versions précédentes de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  Les fonctionnalités liées aux images, telles que l'affichage de bitmap ou l'utilisation d'une image sur un contrôle commun, étaient principalement prises en charge par l'interface de programmation d'application \(API\) Microsoft Windows Graphics Device Interface \(GDI\) ou Microsoft Windows GDI\+.  Ces API proposaient des fonctionnalités de base pour la création d'images, mais étaient dépourvues de fonctionnalités telles que la prise en charge de l'extensibilité de codec et des images haute fidélité.  Les API de création d'images de WPF ont été refondues pour résoudre les problèmes de GDI et GDI\+, et fournissent un nouvel ensemble d'API pour afficher et utiliser des images dans vos applications.  
  
 Lorsque vous utilisez des images, tenez compte des recommandations suivantes pour obtenir de meilleures performances :  
  
-   Si votre application requiert l'affichage d'images miniatures, envisagez la création d'une version de taille réduite de l'image.  Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] charge votre image et la décode dans sa taille maximale.  Si vous voulez seulement une version miniature de l'image, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] décode inutilement l'image dans sa taille maximale et la réduit ensuite à sa taille miniature.  Afin d'éviter ce traitement inutile, vous pouvez soit demander à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de décoder l'image en taille miniature, soit demander à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de charger une image de taille miniature.  
  
-   Décodez toujours l'image dans la taille désirée et non pas dans la taille par défaut.  Comme mentionné ci\-dessus, demandez à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de décoder votre image dans la taille désirée et non pas dans la taille par défaut.  Vous réduirez non seulement le jeu de travail de votre application, mais son exécution sera également plus rapide.  
  
-   Si possible, combinez les images en une seule image, comme un extrait de film composé de plusieurs images.  
  
-   Pour plus d'informations, consultez [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### BitmapScalingMode  
 Lors de l'animation de l'échelle d'une bitmap, l'algorithme de rééchantillonnage d'image haute qualité par défaut peut parfois consommer assez de ressources système pour provoquer une dégradation de la fréquence d'images, causant en pratique l'interruption des animations.  En affectant à la propriété <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> de l'objet <xref:System.Windows.Media.RenderOptions> la valeur <xref:System.Windows.Media.BitmapScalingMode>, vous pouvez créer une animation plus lisse lors de la mise à l'échelle d'une bitmap.  Le mode <xref:System.Windows.Media.BitmapScalingMode> indique au moteur de rendu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de basculer d'un algorithme optimisé pour la qualité à un algorithme optimisé pour la vitesse lorsqu'il traite des images.  
  
 L'exemple suivant indique comment définir le <xref:System.Windows.Media.BitmapScalingMode> d'un objet image.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### CachingHint  
 Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne met pas en cache le contenu rendu des objets <xref:System.Windows.Media.TileBrush>, tels que <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>.  Dans les scénarios statiques où ni le contenu ni l'utilisation du <xref:System.Windows.Media.TileBrush> dans la scène ne changent, cela a du sens, puisqu'il conserve la mémoire vidéo.  Cela a moins de sens lorsqu'un <xref:System.Windows.Media.TileBrush> avec du contenu statique est utilisé de façon non\-statique ; par exemple lorsqu'un <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> statique est mappé à la surface d'un objet 3D pivotant.  Le comportement par défaut de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est de restituer à nouveau le contenu entier du <xref:System.Windows.Media.DrawingBrush> ou du <xref:System.Windows.Media.VisualBrush> pour chaque trame, même si le contenu est invariable.  
  
 En définissant la propriété <xref:System.Windows.Media.RenderOptions.CachingHint%2A> de l'objet <xref:System.Windows.Media.RenderOptions> à <xref:System.Windows.Media.CachingHint>, vous pouvez augmenter les performances en utilisant des versions mises en cache des objets de pinceau en mosaïque.  
  
 Les valeurs de propriété <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> et <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> sont des valeurs de taille relative qui déterminent le moment où l'objet <xref:System.Windows.Media.TileBrush> doit être régénéré en raison de modifications dans l'échelle.  Par exemple, en affectant la valeur 2.0 à la propriété <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>, le cache pour <xref:System.Windows.Media.TileBrush> n'a besoin d'être régénéré que lorsque sa taille dépasse deux fois la taille du cache actuel.  
  
 L'exemple suivant montre comment utiliser l'option d'optimisation de mise en cache pour un <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Comportement d'objets](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)   
 [Conseils et astuces sur les animations](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)