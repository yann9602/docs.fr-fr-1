---
title: "Vue d&#39;ensemble du rendu graphique de WPF | Microsoft Docs"
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
  - "graphiques, rendu"
  - "restituer des graphiques"
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
caps.latest.revision: 51
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 48
---
# Vue d&#39;ensemble du rendu graphique de WPF
Cette rubrique propose une vue d'ensemble de la couche visuelle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Elle se concentre sur le rôle de la classe <xref:System.Windows.Media.Visual> pour la prise en charge du rendu dans le modèle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
   
  
<a name="role_of_visual_object"></a>   
## Rôle de l'objet visuel  
 La classe <xref:System.Windows.Media.Visual> est l'abstraction de base de laquelle dérive chaque objet <xref:System.Windows.FrameworkElement>.  Elle sert également de point d'entrée pour l'écriture de nouveaux contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et peut, par bien des aspects, être considérée comme le descripteur de fenêtre \(HWND\) dans le modèle d'application Win32.  
  
 L'objet <xref:System.Windows.Media.Visual> est un objet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] principal; dont le rôle est de fournir une prise en charge du rendu.  Les contrôles d'interface utilisateur, tels que <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.TextBox>, dérivent de la classe <xref:System.Windows.Media.Visual> et l'utilisent pour rendre leurs données de rendu persistantes.  L'objet <xref:System.Windows.Media.Visual> fournit une prise en charge pour :  
  
-   L'affichage de sortie : rendu du contenu de dessin sérialisé persistant d'un visuel.  
  
-   Transformations : exécution de transformations sur un objet visuel  
  
-   Le découpage : fourniture d'une prise en charge d'une zone de découpage d'un visuel.  
  
-   Le test d'atteinte : déterminer si une coordonnée ou une géométrie est contenue dans les limites d'un visuel.  
  
-   Les calculs du cadre englobant : déterminer le rectangle englobant d'un visuel.  
  
 Cependant, l'objet <xref:System.Windows.Media.Visual> n'inclut pas la prise en charge pour les fonctionnalités n'effectuant pas de rendu, telles que :  
  
-   Gestion des événements  
  
-   Disposition  
  
-   Styles  
  
-   Liaison des données  
  
-   Globalisation  
  
 <xref:System.Windows.Media.Visual> est exposé comme classe publique abstraite à partir de laquelle doivent être dérivées les classes enfants.  L'illustration suivante montre la hiérarchie des objets visuels exposés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagramme des classes dérivées de l'objet Visual](../../../../docs/framework/wpf/graphics-multimedia/media/visualclass01.png "VisualClass01")  
Hiérarchie de classe visuelle  
  
### Classe DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> est une classe de dessin légère utilisée pour le rendu des formes, des images ou du texte.  Cette classe est considérée comme légère car elle ne fournit pas la disposition ou la gestion d'événements, ce qui améliore ses performances au moment de l'exécution.  Pour cette raison, les objets de ce type sont idéaux pour les arrière\-plans et les images clipart.  Le <xref:System.Windows.Media.DrawingVisual> peut être utilisé pour créer un objet visuel personnalisé.  Pour plus d'informations, consultez [Utilisation d'objets DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
### Classe Viewport3DVisual  
 La classe <xref:System.Windows.Media.Media3D.Viewport3DVisual> fournit un pont entre les objets 2D <xref:System.Windows.Media.Visual> et <xref:System.Windows.Media.Media3D.Visual3D>.  La classe <xref:System.Windows.Media.Media3D.Visual3D> est la classe de base pour tous les éléments visuels 3D.  La classe <xref:System.Windows.Media.Media3D.Viewport3DVisual> nécessite que vous définissiez une valeur <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> et une valeur <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A>.  La caméra pour permet de visionner la scène.  La fenêtre d'affichage établit où se mappe la projection sur la surface 2D.  Pour plus d'informations sur la 3D dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).  
  
### Classe ContainerVisual  
 La classe <xref:System.Windows.Media.ContainerVisual> est utilisée comme un conteneur pour une collection d'objets <xref:System.Windows.Media.Visual>.  La classe <xref:System.Windows.Media.DrawingVisual> dérive de la classe <xref:System.Windows.Media.ContainerVisual>, lui permettant de contenir une collection d'objets visuels.  
  
### Dessin de contenu dans des objets visuels  
 Un objet <xref:System.Windows.Media.Visual> stocke ses données de rendu en tant que **liste d'instructions graphiques vectorielles**.  Chaque élément de la liste d'instructions représente un groupe de données graphiques bas niveau et de ressources associées dans un format sérialisé.  Il existe quatre types de données de rendu différents pouvant contenir du contenu de dessin.  
  
|Type de contenu de dessin|Description|  
|-------------------------------|-----------------|  
|Graphiques vectoriels|Représente des données graphiques vectorielles et toute information de <xref:System.Windows.Media.Brush> et de <xref:System.Windows.Media.Pen> associée.|  
|Image|Représente une image dans une région définie par un <xref:System.Windows.Rect>.|  
|Glyphe|Représente un dessin qui restitue un <xref:System.Windows.Media.GlyphRun>, qui est une séquence de glyphes provenant d'une ressource de police spécifiée.  Voici comment est représenté le texte.|  
|Vidéo|Représente un dessin qui restitue de la vidéo.|  
  
 Le <xref:System.Windows.Media.DrawingContext> vous permet de remplir un <xref:System.Windows.Media.Visual> avec un contenu visuel.  Lorsque vous utilisez les commandes de dessin d'un objet <xref:System.Windows.Media.DrawingContext>, vous stockez réellement un groupe de données de rendu qui seront utilisées ultérieurement par le système graphique ; vous ne dessinez pas à l'écran en temps réel.  
  
 Lorsque vous créez un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tel qu'un <xref:System.Windows.Controls.Button>, le contrôle génère implicitement les données de rendu pour se dessiner.  Par exemple, le paramétrage de la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> du <xref:System.Windows.Controls.Button> entraîne le contrôle à stocker une représentation de rendu d'un glyphe.  
  
 Un <xref:System.Windows.Media.Visual> décrit son contenu comme un ou plusieurs  objets <xref:System.Windows.Media.Drawing> contenus dans un <xref:System.Windows.Media.DrawingGroup>.  Un <xref:System.Windows.Media.DrawingGroup> décrit également des masques d'opacité, des transformations, des effets bitmap et d'autres opérations appliquées à son contenu.  Les opérations <xref:System.Windows.Media.DrawingGroup> sont appliquées dans l'ordre suivant lorsque le contenu est restitué : <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, puis <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 L'illustration suivante montre l'ordre dans lequel les opérations du <xref:System.Windows.Media.DrawingGroup> sont appliquées pendant la séquence de rendu.  
  
 ![ordre des opérations DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm\_drawinggroup\_order")  
Ordre des opérations du DrawingGroup  
  
 Pour plus d'informations, consultez [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
#### Dessin de contenu sur la couche visuelle  
 Vous n'instanciez jamais un <xref:System.Windows.Media.DrawingContext> directement ; vous pouvez toutefois acquérir un contexte de dessin de certaines méthodes, telles que <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=fullName> et <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=fullName>.  L'exemple suivant récupère un <xref:System.Windows.Media.DrawingContext> d'un <xref:System.Windows.Media.DrawingVisual> et l'utilise pour dessiner un rectangle.  
  
 [!code-csharp[drawingvisualsample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### Énumération d'un dessin de contenu sur la couche visuelle  
 Outre leurs autres utilisations, les objets <xref:System.Windows.Media.Drawing> fournissent aussi un modèle d'objet pour énumérer le contenu d'un <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
>  Lorsque vous énumérez le contenu d'un visuel, vous récupérez des objets <xref:System.Windows.Media.Drawing>, et non pas la représentation sous\-jacente des données rendues comme liste d'instructions graphiques vectorielles.  
  
 L'exemple suivant utilise la méthode <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> pour récupérer la valeur <xref:System.Windows.Media.DrawingGroup> d'un <xref:System.Windows.Media.Visual> et l'énumérer.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## Comment les objets visuels sont utilisés pour générer des contrôles  
 De nombreux objets dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont composés d'autres objets visuels, ce qui signifie qu'ils peuvent contenir diverses hiérarchies d'objets descendants.  De nombreux éléments de l'interface utilisateur dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tels que les contrôles, sont composés de plusieurs objets visuels représentant différents types d'éléments de rendu.  Par exemple, le contrôle <xref:System.Windows.Controls.Button> peut contenir plusieurs autres objets, y compris <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter> et <xref:System.Windows.Controls.TextBlock>.  
  
 Le code suivant montre un contrôle <xref:System.Windows.Controls.Button> défini dans une balise.  
  
 [!code-xml[VisualsOverview#VisualsOverviewSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Si vous deviez énumérer les objets visuels qui constituent le contrôle <xref:System.Windows.Controls.Button> par défaut, vous trouveriez la hiérarchie d'objets visuels illustrée ci\-dessous :  
  
 ![Diagramme de la hiérarchie de l'arborescence d'éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview03.png "VisualLayerOverview03")  
Diagramme d'une hiérarchie d'arborescence d'éléments visuels  
  
 Le contrôle <xref:System.Windows.Controls.Button> contient un élément <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, qui à son tour, contient un élément <xref:System.Windows.Controls.ContentPresenter>.  L'élément <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> est responsable du dessin de la bordure et de l'arrière\-plan pour le <xref:System.Windows.Controls.Button>.  L'élément <xref:System.Windows.Controls.ContentPresenter> est responsable de l'affichage du contenu du <xref:System.Windows.Controls.Button>.  Dans ce cas, puisque vous affichez le texte, l'élément <xref:System.Windows.Controls.ContentPresenter> contient un élément <xref:System.Windows.Controls.TextBlock>.  Le fait que le contrôle <xref:System.Windows.Controls.Button> utilise un <xref:System.Windows.Controls.ContentPresenter> signifie que le contenu peut être représenté par d'autres éléments, comme une <xref:System.Windows.Controls.Image> ou une géométrie, comme une <xref:System.Windows.Media.EllipseGeometry>.  
  
### Modèles de contrôle  
 La clé de l'expansion d'un contrôle dans une hiérarchie de contrôles est le <xref:System.Windows.Controls.ControlTemplate>.  Un modèle de contrôle spécifie la hiérarchie visuelle par défaut pour un contrôle.  Lorsque vous référencez explicitement un contrôle, vous référencez implicitement sa hiérarchie visuelle.  Vous pouvez substituer les valeurs par défaut pour un modèle de contrôle afin de créer une apparence visuelle personnalisée pour un contrôle.  Par exemple, vous pourriez modifier la valeur de couleur d'arrière\-plan du contrôle <xref:System.Windows.Controls.Button> afin qu'il utilise une valeur de couleur de dégradé linéaire à la place d'une valeur de couleur unie.  Pour plus d'informations, consultez [Styles et modèles Button](../../../../docs/framework/wpf/controls/button-styles-and-templates.md).  
  
 Un élément d'interface utilisateur, comme un contrôle <xref:System.Windows.Controls.Button>, contient plusieurs listes d'instructions graphiques vectorielles qui décrivent la définition de rendu complète d'un contrôle.  Le code suivant montre un contrôle <xref:System.Windows.Controls.Button> défini dans une balise.  
  
 [!code-xml[VisualsOverview#VisualsOverviewSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Si vous deviez énumérer les objets visuels et les listes d'instructions graphiques vectorielles qui constituent le contrôle <xref:System.Windows.Controls.Button>, vous trouveriez la hiérarchie d'objets visuels illustrée ci\-dessous :  
  
 ![Diagramme de l'arborescence d'éléments visuels et des données de rendu](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview04.png "VisualLayerOverview04")  
Diagramme d'une arborescence d'éléments visuels et d'éléments de rendu  
  
 Le contrôle <xref:System.Windows.Controls.Button> contient un élément <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, qui à son tour, contient un élément <xref:System.Windows.Controls.ContentPresenter>.  L'élément <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> est responsable du dessin de tous les éléments graphiques discrets qui composent la bordure et l'arrière\-plan d'un bouton.  L'élément <xref:System.Windows.Controls.ContentPresenter> est responsable de l'affichage du contenu du <xref:System.Windows.Controls.Button>.  Dans ce cas, puisque vous affichez une image, l'élément <xref:System.Windows.Controls.ContentPresenter> contient un élément <xref:System.Windows.Controls.Image>.  
  
 Plusieurs points sont à noter concernant la hiérarchie d'objets visuels et de listes d'instructions graphiques vectorielles :  
  
-   L'ordre de la hiérarchie représente l'ordre de rendu des informations de dessin.  Depuis l'élément visuel racine, les éléments enfants sont parcourus de gauche à droite et de haut en bas.  Si un élément comporte des éléments enfants, ils sont parcourus avant les éléments frères.  
  
-   Les éléments de nœuds non terminaux dans la hiérarchie, comme un <xref:System.Windows.Controls.ContentPresenter>, sont utilisés pour contenir les éléments enfants ; ils ne contiennent pas de listes d'instructions.  
  
-   Si un élément visuel contient à la fois une liste d'instructions graphiques vectorielles et des enfants visuels, la liste d'instructions de l'élément visuel parent est restitué avant les dessins dans n'importe quel objet visuel enfant.  
  
-   Les éléments dans la liste d'instructions graphiques vectorielles sont restituées de gauche à droite.  
  
<a name="visual_tree"></a>   
## Arborescence d'éléments visuels  
 L'arborescence d'éléments visuels contient tous les éléments visuels utilisés dans l'interface graphique d'une application.  Comme un élément visuel contient des informations de dessin persistantes, vous pouvez considérer l'arborescence d'éléments visuels comme étant un graphique de scène contenant toutes les informations rendues nécessaires pour composer la sortie vers le périphérique d'affichage.  Cette arborescence est l'accumulation de tous les éléments visuels créés directement par l'application, par code ou dans une balise.  L'arborescence d'éléments visuels contient tous les éléments visuels créés par l'expansion d'éléments du modèle tels que les contrôles et les objets de données.  
  
 Le code suivant montre un élément <xref:System.Windows.Controls.StackPanel> défini dans une balise.  
  
 [!code-xml[VisualsOverview#VisualsOverviewSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Si vous deviez énumérer les objets visuels qui constituent l'élément <xref:System.Windows.Controls.StackPanel> dans l'exemple de balise, vous trouveriez la hiérarchie d'objets visuels illustrée ci\-dessous :  
  
 ![Diagramme de la hiérarchie de l'arborescence d'éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview05.png "VisualLayerOverview05")  
Diagramme d'une hiérarchie d'arborescence d'éléments visuels  
  
### Ordre de rendu  
 L'arborescence d'éléments visuels détermine l'ordre de rendu d'objets visuels et de dessin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  L'ordre de parcours démarre avec le visuel racine qui est le nœud le plus élevé dans l'arborescence d'éléments visuels.  Les enfants du visuel racine sont ensuite parcourus de gauche à droite.  Si un visuel a des enfants, ces derniers sont parcourus avant les visuels frères.  Cela signifie que le contenu d'un visuel enfant est rendu devant le propre contenu du visuel.  
  
 ![Diagramme de l'ordre de rendu de l'arborescence d'éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview06.png "VisualLayerOverview06")  
Diagramme de l'ordre de rendu d'une arborescence d'éléments visuels  
  
### Visuel racine  
 Le **visuel racine** est l'élément le plus élevé dans une hiérarchie d'arborescence d'éléments visuels.  Dans la plupart des applications, la classe de base de l'élément racine est <xref:System.Windows.Window> ou <xref:System.Windows.Navigation.NavigationWindow>.  Cependant, si vous hébergez des objets visuels dans une application Win32, le visuel racine est le visuel le plus élevé que vous hébergez dans la fenêtre Win32.  Pour plus d'informations, consultez [Didacticiel : hébergement d'objets visuels dans une application Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### Relations avec l'arborescence logique  
 L'arborescence logique dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] représente les éléments d'une application au moment de l'exécution.  Bien que vous ne manipulez pas directement l'arborescence, cette vue de l'application est pratique pour comprendre l'héritage de propriété et le routage d'événement.  Contrairement à l'arborescence d'éléments visuels, l'arborescence logique peut représenter des objets de données non visuels, tels que <xref:System.Windows.Documents.ListItem>.  Dans de nombreux cas, l'arborescence logique se mappe très étroitement aux définitions de balise d'une application.  Le code suivant montre un élément <xref:System.Windows.Controls.DockPanel> défini dans une balise.  
  
 [!code-xml[VisualsOverview#VisualsOverviewSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Si vous deviez énumérer les objets logiques qui constituent l'élément <xref:System.Windows.Controls.DockPanel> dans l'exemple de balise, vous trouveriez la hiérarchie d'objets logiques illustrée ci\-dessous :  
  
 ![Diagramme de l'arborescence](../../../../docs/framework/wpf/graphics-multimedia/media/tree1-wcp.png "Tree1\_wcp")  
Diagramme d'une arborescence logique  
  
 L'arborescence d'éléments visuels et l'arborescence logique sont synchronisées avec le jeu actuel d'éléments d'application, reflétant tout ajout, suppression ou modification d'éléments.  Toutefois, les arborescences présentent différentes vues de l'application.  Contrairement à l'arborescence d'éléments visuels, l'arborescence logique ne développe pas l'élément d'un contrôle <xref:System.Windows.Controls.ContentPresenter>.  Cela signifie qu'il existe une correspondance directe un\-à\-un entre une arborescence logique et une arborescence d'éléments visuels pour le même ensemble d'objets.  En réalité, l'appel de la méthode **LogicalTreeHelper** de l'objet <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> et la méthode **VisualTreeHelper** de l'objet <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> à l'aide du même élément comme paramètre génère des résultats différents.  
  
 Pour plus d'informations sur l'arborescence logique, consultez [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
### Affichage de l'arborescence d'éléments visuels à l'aide de XamlPad  
 L'outil XamlPad de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre une option d'affichage et d'exploration de l'arborescence d'éléments visuels qui correspond au contenu [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] actuellement défini.  Cliquez sur le bouton **Afficher l'arborescence d'éléments visuels** dans la barre de menus pour afficher l'arborescence d'éléments visuels.  L'exemple suivant montre le développement du contenu [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] en nœuds de l'arborescence d'éléments visuels dans le volet **Explorateur d'arborescence d'éléments visuels** de XamlPad :  
  
 ![Volet Explorateur de l'arborescence d'éléments visuels dans XamlPad](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview08.png "VisualLayerOverview08")  
Volet Explorateur de l'arborescence d'éléments visuels dans XamlPad  
  
 Notez la manière dont chaque contrôle <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.Button> affiche une hiérarchie d'objet visuel distincte dans le volet **Explorateur de l'arborescence d'éléments visuels** de XamlPad.  Cela tient au fait que les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possèdent un <xref:System.Windows.Controls.ControlTemplate> qui contient l'arborescence d'éléments visuels de ce contrôle.  Lorsque vous référencez explicitement un contrôle, vous référencez implicitement sa hiérarchie visuelle.  
  
### Profilage des performances visuelles  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une suite d'outils de profilage des performances qui vous permettent d'analyser le comportement au moment de l'exécution de votre application et de déterminer les types d'optimisations des performances que vous pouvez appliquer.  La suite d'outils Visual Profiler fournit une vue graphique détaillée des données de performance en mappant directement sur l'arborescence d'éléments visuels de l'application.  Dans cette capture d'écran, la section **Utilisation de l'UC** de Visual Profiler donne un descriptif précis de l'utilisation d'un objet des services [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], comme le rendu et la mise en page.  
  
 ![Sortie du Générateur de profils Visual](../../../../docs/framework/wpf/graphics-multimedia/media/wpfperf-visualprofiler-04.png "WPFPerf\_VisualProfiler\_04")  
Sortie d'affichage de Visual Profiler  
  
<a name="visual_rendering_behavior"></a>   
## Comportement de rendu visuel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] présente plusieurs fonctionnalités qui affectent le comportement de rendu d'objets visuels : graphiques en mode Conservation, graphiques vectoriels et graphiques indépendants du périphérique.  
  
### Graphiques en mode Conservation  
 Une des clés pour comprendre le rôle d'un objet visuel est de comprendre la différence entre les systèmes graphiques en **mode Exécution** et en **mode Conservation**.  Une application Win32 standard à base de GDI ou GDI\+ utilise un système de graphiques en mode Exécution.  Cela signifie que c'est la responsabilité de l'application de repeindre la portion de la zone client qui est invalidée, en raison d'une action telle qu'un redimensionnement de fenêtre, ou la modification de l'apparence visuelle d'un objet.  
  
 ![Diagramme de la séquence de rendu Win32](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview01.png "VisualLayerOverview01")  
Diagramme d'une séquence de rendu Win32  
  
 Par opposition, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise un système de mode Exécution.  Cela signifie que les objets d'application qui ont une apparence visuelle définissent un ensemble de données de dessin sérialisées.  Une fois que les données de dessin sont définies, le système est ensuite responsable de la réponse à toutes les demandes de peintures pour restituer les objets d'application.  Même au moment de l'exécution, vous pouvez modifier ou créer des objets d'application, et toujours compter sur le système pour répondre aux demandes de peinture.  La puissance d'un système de graphiques en mode Conservation réside dans le fait que les informations de dessin sont toujours persistantes dans un état sérialisé par l'application, mais que la responsabilité du rendu est laissée au système.  Le diagramme suivant illustre comment l'application se repose sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour répondre aux demandes de peinture.  
  
 ![Diagramme de la séquence de rendu WPF](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview02.png "VisualLayerOverview02")  
Diagramme d'une séquence de rendu WPF  
  
#### Redessinage intelligent  
 L'un des principaux avantages de l'utilisation de graphiques en mode Conservation réside dans le fait que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut optimiser efficacement ce qui doit être redessiné dans l'application.  Même si vous avez une scène complexe avec différents niveaux d'opacité, vous n'avez généralement pas besoin d'écrire un code spécial dans ce but pour optimiser le redessinage.  Faites la comparaison avec la programmation Win32 dans laquelle vous pouvez passer beaucoup de temps à optimiser votre application en minimisant la quantité de redessinage dans la région mise à jour.  Consultez [Redessinage dans la région mise à jour](_win32_Redrawing_in_the_Update_Region) pour un exemple du type de complexité impliquée dans l'optimisation du redessinage dans les applications Win32.  
  
### Graphiques vectoriels  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise les **graphiques vectoriels** comme format de rendu de données.  Les graphiques vectoriels, qui comprennent les Scalable Vector Graphics \(SVG\), les métafichiers Windows \(.wmf\) et les polices TrueType, stockent les données de rendu et les transmettent comme liste d'instructions décrivant comment recréer une image à l'aide de primitives graphiques.  Par exemple, les polices TrueType sont des polices vectorielles qui décrivent un ensemble de lignes, de courbes et de commandes, plutôt qu'un tableau de pixels.  L'un des avantages principaux des graphiques vectoriels est la possibilité de mettre à l'échelle dans n'importe quelle taille et résolution.  
  
 Contrairement aux graphiques vectoriels, les graphiques de bitmap stockent les données de rendu comme une représentation d'une image pixel par pixel, rendue au préalable pour une résolution spécifique.  L'une des différences clé entre les formats graphiques de bitmap et vectoriels est la fidélité par rapport à l'image source d'origine.  Par exemple, lorsque la taille d'une image source est modifiée, les systèmes de graphiques de bitmap étirent l'image, alors que les systèmes de graphiques vectoriels mettent l'image à l'échelle, préservant la fidélité de l'image.  
  
 L'illustration suivante montre une image source redimensionnée selon un facteur de 300 %.  Remarquez les distorsions qui apparaissent lorsque l'image source est étirée comme une image graphique bitmap plutôt que mise à l'échelle comme une image de graphique vectoriel.  
  
 ![Différences entre graphiques raster et vectoriels](../../../../docs/framework/wpf/graphics-multimedia/media/vectorgraphics01.png "VectorGraphics01")  
Différences entre les graphiques raster et vectoriels  
  
 La balise suivante montre deux éléments <xref:System.Windows.Shapes.Path> définis.  Le deuxième élément utilise un <xref:System.Windows.Media.ScaleTransform> pour redimensionner les instructions de dessin du premier élément de 300 %.  Notez que les instructions de dessin dans les éléments <xref:System.Windows.Shapes.Path> restent inchangées.  
  
 [!code-xml[VectorGraphicsSnippets#VectorGraphicsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### À propos des graphiques indépendants du périphérique et de la résolution  
 Il existe deux facteurs système qui déterminent la taille du texte et des graphiques sur votre résolution d'écran et PPP.  La résolution décrit le nombre de pixels qui apparaissent à l'écran.  Plus la résolution est élevée, plus les pixels sont petits, donnant l'impression de graphiques et de texte plus petits.  Un graphique affiché sur un écran défini en 1024 x 768 apparaîtra beaucoup plus petit quand la résolution change en 1600 x 1200.  
  
 L'autre paramètre système, PPP, décrit la taille d'un pouce d'écran en pixels.  La plupart des systèmes [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ont un PPP de 96, ce qui signifie qu'un pouce d'écran fait 96 pixels.  L'augmentation du paramètre PPP augmente le pouce d'écran et inversement.  Cela signifie qu'un pouce d'écran n'a pas la même taille qu'un pouce réel sur la plupart des système.  En augmentant le PPP, les graphiques et le texte reconnaissant PPP apparaissent plus grands car vous avez augmenté la taille du pouce d'écran.  L'augmentation du PPP peut faciliter la lecture du texte, principalement dans les résolutions élevées.  
  
 Toutes les applications ne reconnaissent pas PPP : certaines utilisent les pixels matériels comme unité principale de mesure, la modification du PPP système n'a aucun effet sur ces applications.  De nombreuses autres applications utilisent des unités reconnaissant PPP pour décrire les tailles de police, mais utilisent les pixels pour décrire tout le reste.  Si le PPP est trop petit ou trop grand, cela peut entraîner des problèmes de disposition pour ces applications, car le texte des applications se met à l'échelle avec le paramètre PPP du système, mais pas l'interface utilisateur de l'application.  Ce problème a été résolu pour les applications développées à l'aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la mise à l'échelle automatique en utilisant le pixel indépendant du périphérique comme unité principale de mesure, au lieu des pixels matériels ; les graphiques et le texte se mettent correctement à l'échelle sans travail supplémentaire de la part du développeur de l'application.  L'illustration suivante montre un exemple d'affichage de texte et de graphiques [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à différents paramètres PPP.  
  
 ![Graphique et texte avec différents paramètres PPP](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-dpi-setting-examples.png "graphicsmm\_dpi\_setting\_examples")  
Graphiques et texte à différents paramètres PPP  
  
<a name="visualtreehelper_class"></a>   
## Classe VisualTreeHelper  
 La classe <xref:System.Windows.Media.VisualTreeHelper> est une classe d'aide statique qui fournit une fonction de bas niveau pour la programmation au niveau de l'objet visuel, ce qui peut s'avérer utile dans certains scénarios spécifiques, comme le développement de contrôles personnalisés haute performance.  Dans la plupart des cas, les objets d'infrastructure [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du niveau le plus élevé, tels que <xref:System.Windows.Controls.Canvas> et <xref:System.Windows.Controls.TextBlock>, offrent une plus grande flexibilité et facilité d'utilisation.  
  
### Test d'atteinte  
 La classe <xref:System.Windows.Media.VisualTreeHelper> fournit des méthodes de test d'atteinte sur objets visuels lorsque la prise en charge de test d'atteinte par défaut ne correspond pas à vos besoins.  Vous pouvez utiliser les méthodes <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> dans la classe <xref:System.Windows.Media.VisualTreeHelper> pour déterminer si une géométrie ou une valeur de point de coordonnée se trouve dans les limites d'un objet donné, tel qu'un contrôle ou élément graphique.  Par exemple, vous pouvez utiliser le test d'atteinte pour déterminer si un clic de la souris dans le rectangle englobant d'un objet se situe dans la géométrie d'un cercle. Vous pouvez également choisir de remplacer l'implémentation par défaut du test d'atteinte pour effectuer vos propres calculs de test d'atteinte.  
  
 Pour plus d'informations sur les tests d'atteinte, consultez [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
### Énumération de l'arborescence d'éléments visuels  
 La classe <xref:System.Windows.Media.VisualTreeHelper> fournit une fonctionnalité pour énumérer les membres d'une arborescence d'éléments visuels.  Pour récupérer un parent, appelez la méthode <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A>.  Pour récupérer un enfant ou un descendant direct d'un objet visuel, appelez la méthode <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A>.  Cette méthode retourne un <xref:System.Windows.Media.Visual> enfant du parent à l'index spécifié.  
  
 L'exemple suivant montre comment énumérer tous les descendants d'un objet visuel, une technique utile si vous voulez sérialiser toutes les informations de rendu d'une hiérarchie d'objets visuels.  
  
 [!code-csharp[VisualsOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Dans la plupart des cas, l'arborescence logique est une représentation des éléments plus utile dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Bien que vous ne modifiez pas directement l'arborescence logique, cette vue de l'application est pratique pour comprendre l'héritage de propriété et le routage d'événement.  Contrairement à l'arborescence d'éléments visuels, l'arborescence logique peut représenter des objets de données non visuels, tels que <xref:System.Windows.Documents.ListItem>.  Pour plus d'informations sur l'arborescence logique, consultez [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 La classe <xref:System.Windows.Media.VisualTreeHelper> fournit des méthodes permettant de retourner les rectangles englobants d'objets visuels.  Vous pouvez retourner le rectangle englobant d'un objet visuel en appelant <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>.  Vous pouvez retourner le rectangle englobant de tous les descendants d'un objet visuel, y compris l'objet visuel même, en appelant <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>.  Le code suivant montre comment vous pourriez calculer le rectangle englobant d'un objet visuel et de tous ses descendants.  
  
 [!code-csharp[VisualsOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## Voir aussi  
 <xref:System.Windows.Media.Visual>   
 <xref:System.Windows.Media.VisualTreeHelper>   
 <xref:System.Windows.Media.DrawingVisual>   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [Utilisation d'objets DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)   
 [Didacticiel : hébergement d'objets visuels dans une application Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)   
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)