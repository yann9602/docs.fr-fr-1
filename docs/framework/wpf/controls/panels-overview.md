---
title: "Vue d&#39;ensemble de Panel | Microsoft Docs"
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
  - "contrôles, Volet"
  - "Panel (contrôle) (WPF), à propos du contrôle Panel"
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
caps.latest.revision: 48
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 45
---
# Vue d&#39;ensemble de Panel
Les éléments <xref:System.Windows.Controls.Panel> sont des composants qui contrôlent le rendu des éléments : leurs taille et dimensions, leur position et la disposition de leur contenu enfant.  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un nombre d'éléments <xref:System.Windows.Controls.Panel> prédéfinis ainsi que la possibilité de construire des éléments <xref:System.Windows.Controls.Panel> personnalisés.  
  
 Cette rubrique contient les sections suivantes.  
  
-   [La classe Panel](#Panels_view_from_10000_feet)  
  
-   [Membres communs aux éléments Panel](#Panels_declared_members)  
  
-   [Éléments Panel dérivés](#Panels_derived_elements)  
  
-   [Panneaux d'interface utilisateur](#Panels_main_UI_elements)  
  
-   [Éléments Panel imbriqués](#Panels_nested_panel_elements)  
  
-   [Éléments Panel personnalisés](#Panels_custom_panel_elements)  
  
-   [Prise en charge de la localisation\/globalisation](#Panels_global_localization)  
  
-   [Rubriques connexes](#seeAlsoToggle)  
  
<a name="Panels_view_from_10000_feet"></a>   
## La classe Panel  
 <xref:System.Windows.Controls.Panel> est la classe de base pour tous les éléments qui offrent une prise en charge de la disposition dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Les éléments <xref:System.Windows.Controls.Panel> sont utilisés pour positionner et organiser les éléments en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comprend une suite complète d'implémentations de panneaux dérivés permettant de nombreuses dispositions complexes.  Ces classes dérivées exposent des propriétés et des méthodes qui permettent d'implémenter la plupart des scénarios d'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  Les développeurs qui ne parviennent pas à trouver le comportement de disposition d'enfants qui répond à leur besoin peuvent créer de nouvelles dispositions en remplaçant les méthodes <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> et <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  Pour plus d'informations sur les comportements de dispositions personnalisés, consultez [Éléments Panel personnalisés](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## Membres communs aux éléments Panel  
 Tous les éléments <xref:System.Windows.Controls.Panel> prennent en charge les propriétés de dimensionnement et de positionnement de base définies par <xref:System.Windows.FrameworkElement>, telles que <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> et <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  Pour plus d'informations sur les propriétés de positionnement définies par <xref:System.Windows.FrameworkElement>, consultez [Vue d'ensemble de l'alignement, des marges et du remplissage](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel> expose des propriétés supplémentaires qui sont d'une importance primordiale pour comprendre et utiliser la disposition.  La propriété <xref:System.Windows.Controls.Panel.Background%2A> est utilisée pour remplir la zone entre les limites d'un élément Panel dérivé avec un <xref:System.Windows.Media.Brush>.  <xref:System.Windows.Controls.Panel.Children%2A> représente la collection enfant d'éléments dont  <xref:System.Windows.Controls.Panel> est composé.  <xref:System.Windows.Controls.Panel.InternalChildren%2A> représente le contenu de la collection <xref:System.Windows.Controls.Panel.Children%2A> plus les membres générés par la liaison de données.  Tous deux consistent en une <xref:System.Windows.Controls.UIElementCollection> d'éléments enfants hébergés dans le <xref:System.Windows.Controls.Panel> parent.  
  
 Le Panel expose également une propriété <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName> jointe qui peut être utilisée pour effectuer un ordre superposé dans un <xref:System.Windows.Controls.Panel> dérivé.  Les membres d'une collection de <xref:System.Windows.Controls.Panel.Children%2A> d'un panneau dont la valeur <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName> est supérieure apparaissent en face de ceux dont la valeur <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName> est inférieure.  Ceci est particulièrement utile pour les panneaux tels que <xref:System.Windows.Controls.Canvas> et <xref:System.Windows.Controls.Grid> qui permettent à des enfants de partager le même espace de coordonnées.  
  
 <xref:System.Windows.Controls.Panel> définit également la méthode <xref:System.Windows.Controls.Panel.OnRender%2A>, qui peut être utilisée pour remplacer le comportement de présentation par défaut de <xref:System.Windows.Controls.Panel>.  
  
#### Propriétés jointes  
 Les éléments Panel dérivés utilisent très souvent des [propriétés jointes](GTMT).  Une propriété jointe est une forme spécialisée de [propriété de dépendance](GTMT) qui ne possède pas le « wrapper » de propriété classique du [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)].  Les propriétés jointes ont une syntaxe spécialisée en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], ce qui est montré dans plusieurs des exemples suivants.  
  
 L'un des objectifs d'une propriété jointe est de permettre à des éléments enfants de stocker des valeurs uniques d'une propriété qui est réellement définie par un élément parent.  Une application de cette fonctionnalité est que les éléments enfants informent le parent sur la manière dont ils souhaitent être présentés dans l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], ce qui est extrêmement utile pour la disposition d'application.  Pour plus d'informations, consultez [Vue d'ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## Éléments Panel dérivés  
 De nombreux objets dérivent de <xref:System.Windows.Controls.Panel>, mais ils ne sont pas tous destinés à être utilisés comme des fournisseurs de disposition racine.  Il existe six classes Panel définies \(<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel> et <xref:System.Windows.Controls.WrapPanel>\) qui sont conçues spécifiquement pour créer une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'application.  
  
 Chaque élément Panel encapsule sa propre fonctionnalité particulière, comme le montre le tableau suivant.  
  
|Nom de l'élément|Panneau UI ?|Description|  
|----------------------|------------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Oui|Définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants par leurs coordonnées relatives à la zone du <xref:System.Windows.Controls.Canvas>.|  
|<xref:System.Windows.Controls.DockPanel>|Oui|Définit une zone dans laquelle vous pouvez réorganiser des éléments enfants soit horizontalement soit verticalement, les uns par rapport aux autres.|  
|<xref:System.Windows.Controls.Grid>|Oui|Définit une grille flexible qui se compose de colonnes et de lignes.  Les éléments enfants de <xref:System.Windows.Controls.Grid> peuvent être positionnés avec précision à l'aide de la propriété <xref:System.Windows.FrameworkElement.Margin%2A>.|  
|<xref:System.Windows.Controls.StackPanel>|Oui|Réorganise des éléments enfants sur une seule ligne pouvant être orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Non|Gère la disposition de boutons d'onglet dans un <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Non|Réorganise le contenu dans un contrôle <xref:System.Windows.Controls.ToolBar>.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Non|<xref:System.Windows.Controls.Primitives.UniformGrid> est utilisé pour réorganiser des enfants dans une grille dont les cellules sont toutes de même taille.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Non|Fournit une classe de base pour des panneaux qui peuvent « virtualiser » leur collection d'enfants.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Oui|Réorganise et virtualise le contenu sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.WrapPanel>|Oui|<xref:System.Windows.Controls.WrapPanel> positionne les éléments enfants selon un ordre séquentiel de gauche à droite, en envoyant le contenu à la ligne suivante, à l'extrémité de la zone conteneur.  L'ordre séquentiel ultérieur est établi de haut en bas ou de droite à gauche, en fonction de la valeur de la propriété <xref:System.Windows.Controls.WrapPanel.Orientation%2A>.|  
  
<a name="Panels_main_UI_elements"></a>   
## Panneaux d'interface utilisateur  
 Il existe six classes Panel disponibles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui sont optimisées pour prendre en charge des scénarios d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] : <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel> et <xref:System.Windows.Controls.WrapPanel>.  Ces éléments Panel sont faciles à utiliser, polyvalents et suffisamment extensibles pour la plupart des applications.  
  
 Chaque élément <xref:System.Windows.Controls.Panel> dérivé traite différemment les contraintes liées au dimensionnement.  En comprenant comment <xref:System.Windows.Controls.Panel> gère les contraintes, soit dans le sens horizontal soit dans le sens vertical, il est plus facile de prévoir la disposition.  
  
|**Nom du panneau**|**Dimension x**|**Dimension y**|  
|------------------------|---------------------|---------------------|  
|<xref:System.Windows.Controls.Canvas>|Limité au contenu|Limité au contenu|  
|<xref:System.Windows.Controls.DockPanel>|Limité|Limité|  
|<xref:System.Windows.Controls.StackPanel> \(orientation verticale\)|Limité|Limité au contenu|  
|<xref:System.Windows.Controls.StackPanel> \(orientation horizontale\)|Limité au contenu|Limité|  
|<xref:System.Windows.Controls.Grid>|Limité|Limité, sauf dans les cas où <xref:System.Windows.GridUnitType> s'applique aux lignes et aux colonnes|  
|<xref:System.Windows.Controls.WrapPanel>|Limité au contenu|Limité au contenu|  
  
 Des descriptions plus détaillées ainsi que des exemples d'utilisation de chacun de ces éléments sont fournis ci\-dessous.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### Canvas  
 L'élément <xref:System.Windows.Controls.Canvas> permet de positionner du contenu en fonction des coordonnées absolues *x* et *y*.  Les éléments peuvent être dessinés dans un emplacement unique, ou, si des éléments occupent les mêmes coordonnées, l'ordre dans lequel ces éléments sont dessinés est déterminé par l'ordre dans lequel ils apparaissent dans le balisage.  
  
 <xref:System.Windows.Controls.Canvas> est le <xref:System.Windows.Controls.Panel> qui fournit la prise en charge de la disposition la plus souple.  Les propriétés Height et Width sont utilisées pour définir la zone de dessin, et des coordonnées absolues par rapport à la zone du <xref:System.Windows.Controls.Canvas> parent sont assignées aux éléments qui sont à l'intérieur de cette zone.  Quatre propriétés jointes, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=fullName>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=fullName>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=fullName> et <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=fullName>, permettent de bien contrôler le placement des objets à l'intérieur d'un <xref:System.Windows.Controls.Canvas>, donnant ainsi la possibilité au développeur de positionner et de réorganiser les éléments avec précision sur l'écran.  
  
#### ClipToBound dans une zone de dessin  
 <xref:System.Windows.Controls.Canvas> peut positionner des éléments enfants à n'importe quelle position sur l'écran, même à des coordonnées qui sont en dehors de ses propres <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> définies.  De plus, <xref:System.Windows.Controls.Canvas> n'est pas affecté par la taille de ses enfants.  Il en résulte qu'un élément enfant a la possibilité de recouvrir d'autres éléments situés en dehors du rectangle englobant du <xref:System.Windows.Controls.Canvas> parent.  Le comportement par défaut de <xref:System.Windows.Controls.Canvas> est de permettre à des enfants d'être dessinés en dehors des limites du <xref:System.Windows.Controls.Canvas> parent.  Si ce comportement n'est pas souhaité; il est possible d'affecter `true` à la propriété <xref:System.Windows.UIElement.ClipToBounds%2A>.  <xref:System.Windows.Controls.Canvas> est détouré à sa taille.  <xref:System.Windows.Controls.Canvas> est le seul élément de disposition qui autorise des enfants à être dessiné à l'extérieur de ses limites.  
  
 Ce comportement est illustré graphiquement dans [Comparaison des propriétés Width, exemple](http://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### Définition et utilisation de Canvas  
 <xref:System.Windows.Controls.Canvas> peut être instancié en utilisant simplement [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou du code.  L'exemple suivant montre comment utiliser <xref:System.Windows.Controls.Canvas> pour positionner du contenu de façon absolue.  Ce code génère trois carrés de 100 pixels de côté.  Le premier carré est rouge et la position de son angle supérieur gauche \(*x, y*\) est spécifiée sous la forme \(0, 0\).  Le deuxième carré est vert et la position de son angle supérieur gauche est \(100, 100\), juste en dessous et à droite du premier carré.  Le troisième carré est bleu, et la position de son angle supérieur gauche est \(50, 50\), il recouvre ainsi le quadrant inférieur droit du premier carré et le quadrant supérieur gauche du deuxième.  Le troisième carré étant placé en dernier, il semble se trouver au\-dessus des deux autres, c'est\-à\-dire que les parties qui se chevauchent prennent la couleur du troisième carré.  
  
 [!code-csharp[CanvasOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xml[CanvasOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 L'application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à ce qui suit.  
  
 ![Élément Canevas classique.](../../../../docs/framework/wpf/controls/media/panel-intro-canvas.png "panel\_intro\_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### DockPanel  
 L'élément <xref:System.Windows.Controls.DockPanel> utilise la propriété jointe <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> comme jeu dans les éléments de contenu enfants pour positionner le contenu le long des bords d'un conteneur.  Lorsque <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> a la valeur <xref:System.Windows.Controls.Dock> ou <xref:System.Windows.Controls.Dock>, il positionne les éléments enfants au\-dessus ou en dessous les uns des autres.  Lorsque <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> a la valeur  <xref:System.Windows.Controls.Dock> ou <xref:System.Windows.Controls.Dock>, il positionne les éléments enfants à gauche ou à droite l'un de l'autre.  La propriété <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> détermine la position du dernier élément ajouté en tant qu'enfant de <xref:System.Windows.Controls.DockPanel>.  
  
 Vous pouvez utiliser <xref:System.Windows.Controls.DockPanel> pour positionner un groupe de contrôles connexes, tel qu'un ensemble de boutons.  Vous pouvez également l'utiliser pour créer une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] « en panneaux », semblable à celle de [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### Dimensionnement relatif au contenu  
 Si ses propriétés <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> ne sont pas spécifiées, <xref:System.Windows.Controls.DockPanel> se dimensionne par rapport à son contenu.  Sa taille peut augmenter ou diminuer pour s'adapter à celle de ses éléments enfants.  Cependant, lorsque ces propriétés sont spécifiées et qu'il n'y a plus de place pour l'élément enfant spécifié suivant, <xref:System.Windows.Controls.DockPanel> n'affiche pas cet élément enfant ou les éléments enfants ultérieurs, et ne mesure pas les éléments enfants ultérieurs.  
  
#### LastChildFill  
 Par défaut, le dernier enfant d'un élément <xref:System.Windows.Controls.DockPanel> « remplira » l'espace non alloué restant.  Si ce comportement n'est pas souhaité, affectez `false` à la propriété <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>.  
  
#### Définition et utilisation de DockPanel  
 L'exemple suivant montre comment partitionner l'espace à l'aide de <xref:System.Windows.Controls.DockPanel>.  Cinq éléments <xref:System.Windows.Controls.Border> sont ajoutés en tant qu'enfants d'un <xref:System.Windows.Controls.DockPanel> parent.  Chacun d'eux utilise une différente propriété de positionnement de <xref:System.Windows.Controls.DockPanel> afin de partitionner l'espace.  Le dernier élément « remplit » l'espace non alloué restant.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 L'application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à ce qui suit.  
  
 ![Scénario DockPanel classique.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.png "panel\_intro\_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### Grille  
 L'élément <xref:System.Windows.Controls.Grid> réunit les fonctionnalités d'un positionnement absolu et d'un contrôle de données tabulaires.  Un <xref:System.Windows.Controls.Grid> permet de positionner et mettre en forme les éléments.  <xref:System.Windows.Controls.Grid> permet de définir des regroupements de colonnes et de lignes flexibles et fournit même un mécanisme pour partager des informations de redimensionnement entre plusieurs éléments <xref:System.Windows.Controls.Grid>.  
  
#### En quoi Grid est différent de Table ?  
 <xref:System.Windows.Documents.Table> et <xref:System.Windows.Controls.Grid> partagent des fonctionnalités communes, mais chacun d'eux est plus adapté à des scénarios différents.  <xref:System.Windows.Documents.Table> est conçu pour être utilisé au sein d'un contenu de flux \(consultez [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md) pour plus d'informations sur le contenu de flux\).  Les grilles fonctionnent de manière optimale dans les formulaires \(en général n'importe où en dehors d'un contenu de flux\).  Dans un <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> prend en charge les comportements de contenu tels que la pagination, la gestion du rendu des colonnes et la sélection de contenu, tandis que <xref:System.Windows.Controls.Grid> ne le fait pas.  <xref:System.Windows.Controls.Grid> fonctionne en revanche de manière optimale en dehors d'un <xref:System.Windows.Documents.FlowDocument> pour de nombreuses raisons, dont le fait que <xref:System.Windows.Controls.Grid> ajoute des éléments basés sur un index de ligne et de colonne, alors que <xref:System.Windows.Documents.Table> ne le fait pas.  L'élément <xref:System.Windows.Controls.Grid> permet la superposition de contenu enfant, où plusieurs éléments peuvent exister dans une même « cellule ». <xref:System.Windows.Documents.Table> ne prend pas en charge la superposition.  Les éléments enfants d'un <xref:System.Windows.Controls.Grid> peuvent être positionnés de manière absolue par rapport à la zone de leurs limites de « cellule ».  <xref:System.Windows.Documents.Table> ne prend pas en charge cette fonctionnalité.  Enfin, <xref:System.Windows.Controls.Grid> est un élément plus léger que <xref:System.Windows.Documents.Table>.  
  
#### Comportement de dimensionnement de colonnes et de lignes  
 Les colonnes et les lignes définies dans un élément <xref:System.Windows.Controls.Grid> peuvent tirer parti du dimensionnement <xref:System.Windows.GridUnitType> pour distribuer proportionnellement l'espace restant.  Si <xref:System.Windows.GridUnitType> est sélectionné comme hauteur ou largeur d'une ligne ou d'une colonne, cette colonne ou cette ligne reçoit une proportion pondérée de l'espace disponible restant.  Par opposition, <xref:System.Windows.GridUnitType> distribue l'espace de façon égale selon la taille du contenu de la colonne ou de la ligne.  Cette valeur est exprimée sous la forme `*` ou `2*` lorsque vous utilisez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Dans le premier cas, la ligne ou la colonne reçoit une fois l'espace disponible, dans le second cas, elle le reçoit deux fois, et ainsi de suite.  En combinant cette technique de répartition proportionnelle de l'espace avec une valeur <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et  <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> de `Stretch`, il est possible de partitionner l'espace de disposition en pourcentage de l'espace d'écran.  <xref:System.Windows.Controls.Grid> est le seul panneau de disposition qui peut distribuer l'espace de cette manière.  
  
#### Définition et utilisation de Grid  
 L'exemple suivant montre comment générer une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à celle de la boîte de dialogue Exécuter du menu Démarrer de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 L'application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à ce qui suit.  
  
 ![Élément de grille classique.](../../../../docs/framework/wpf/controls/media/avalon-run-dialog.png "avalon\_run\_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### StackPanel  
 <xref:System.Windows.Controls.StackPanel> vous permet d'« empiler » des éléments dans un sens assigné.  La direction de la pile par défaut est dans le sens vertical.  La propriété <xref:System.Windows.Controls.StackPanel.Orientation%2A> peut être utilisée pour contrôler le flux du contenu.  
  
#### StackPanel et DockPanel  
 Bien que <xref:System.Windows.Controls.DockPanel> puisse aussi « empiler » des éléments enfants, <xref:System.Windows.Controls.DockPanel> et <xref:System.Windows.Controls.StackPanel> ne produisent pas des résultats analogues dans certains scénarios d'usage.  Par exemple, l'ordre des éléments enfants peut affecter leur taille dans un <xref:System.Windows.Controls.DockPanel> mais pas dans un <xref:System.Windows.Controls.StackPanel>.  En effet, <xref:System.Windows.Controls.StackPanel> mesure dans le sens de l'empilement jusqu'à <xref:System.Double.PositiveInfinity>, tandis que <xref:System.Windows.Controls.DockPanel> mesure uniquement la taille disponible.  
  
 L'exemple suivant illustre ces différences clés.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 La différence de comportement du rendu est illustrée sur cette image.  
  
 ![Capture d'écran : StackPanel et DockPanel](../../../../docs/framework/wpf/controls/media/layout-smiley-stackpanel.png "layout\_smiley\_stackpanel")  
  
#### Définition et utilisation de StackPanel  
 L'exemple suivant montre comment utiliser <xref:System.Windows.Controls.StackPanel> pour créer un ensemble de boutons positionnés dans le sens vertical.  Pour définir le positionnement horizontal, affectez <xref:System.Windows.Controls.Orientation> à la propriété <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
 [!code-csharp[StackPanel_ovw2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 L'application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à ce qui suit.  
  
 ![Élément StackPanel classique.](../../../../docs/framework/wpf/controls/media/panel-intro-stackpanel.png "panel\_intro\_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également une variante de l'élément <xref:System.Windows.Controls.StackPanel> qui « virtualise » automatiquement du contenu enfant lié aux données.  Dans ce contexte, le mot « virtualiser » fait référence à une technique par laquelle un sous\-ensemble d'éléments  est généré à partir d'un plus grand nombre d'éléments de données, sur la base des éléments qui sont visibles sur l'écran.  Générer un grand nombre d'éléments de l'interface utilisateur, alors que seuls un certain nombre d'entre eux peuvent être visibles sur l'écran à un moment donné, provoque une utilisation intensive de la mémoire et du processeur.  <xref:System.Windows.Controls.VirtualizingStackPanel> \(via la fonctionnalité fournie par <xref:System.Windows.Controls.VirtualizingPanel>\) calcule les éléments visibles et utilise <xref:System.Windows.Controls.ItemContainerGenerator> à partir d'un <xref:System.Windows.Controls.ItemsControl> \(tel que <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ListView>\) pour créer uniquement des éléments pour des éléments visibles.  
  
 L'élément <xref:System.Windows.Controls.VirtualizingStackPanel> est automatiquement défini comme l'hôte d'éléments pour des contrôles tels que <xref:System.Windows.Controls.ListBox>.  Lors de l'hébergement d'une collection liée aux données, le contenu est automatiquement virtualisé, tant qu'il est situé dans les limites d'un <xref:System.Windows.Controls.ScrollViewer>.  Ceci améliore sensiblement les performances quand de nombreux enfants sont hébergés.  
  
 L'exemple suivant montre comment utiliser <xref:System.Windows.Controls.VirtualizingStackPanel> comme un hôte d'éléments.  La [propriété jointe](GTMT) <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> doit être `true` \(par défaut\) pour que la virtualisation ait lieu.  
  
 [!code-xml[VirtualizingStackPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> est utilisé pour positionner des éléments enfants selon un ordre séquentiel de gauche à droite, en envoyant le contenu à la ligne suivante lorsqu'il atteint l'extrémité de son conteneur parent.  Le contenu peut être orienté horizontalement ou verticalement.  <xref:System.Windows.Controls.WrapPanel> est utile pour les scénarios d'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] simples.  Il peut aussi être utilisé pour appliquer un dimensionnement uniforme à tous ses éléments enfants.  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Controls.WrapPanel> pour afficher des contrôles <xref:System.Windows.Controls.Button> qui retournent automatiquement à la ligne quand ils atteignent l'extrémité de leur conteneur.  
  
 [!code-cpp[WrapPanel_Intro#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xml[WrapPanel_Intro#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 L'application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à ce qui suit.  
  
 ![Élément WrapPanel classique.](../../../../docs/framework/wpf/controls/media/wrappanel-element.png "WrapPanel\_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## Éléments Panel imbriqués  
 Les éléments <xref:System.Windows.Controls.Panel> peuvent être imbriqués à l'intérieur les uns des autres afin de produire des dispositions complexes.  Ceci peut s'avérer très utile dans des situations où un <xref:System.Windows.Controls.Panel> est idéal pour une partie d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], mais peut ne pas répondre aux besoins d'une autre partie de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Le nombre d'imbrications que votre application peut prendre en charge est illimité ; cependant, il est généralement préférable de limiter votre application uniquement aux panneaux qui sont réellement nécessaires pour la disposition souhaitée.  Dans de nombreux cas, un élément <xref:System.Windows.Controls.Grid> peut être utilisé à la place des panneaux imbriqués, du fait de sa souplesse en tant que conteneur de disposition.  Cela peut accroître les performances de votre application en laissant les éléments inutiles en dehors de l'arborescence.  
  
 L'exemple suivant montre comment créer une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui tire profit d'éléments imbriqués <xref:System.Windows.Controls.Panel> pour réaliser une disposition spécifique.  Dans ce cas particulier, un élément <xref:System.Windows.Controls.DockPanel> est utilisé pour fournir la structure de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], et des éléments <xref:System.Windows.Controls.StackPanel> imbriqués, un contrôle <xref:System.Windows.Controls.Grid> et un <xref:System.Windows.Controls.Canvas> sont utilisés pour positionner avec précision  des éléments enfants dans le <xref:System.Windows.Controls.DockPanel> parent.  
  
 [!code-csharp[Nested_Panels#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 L'application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à ce qui suit.  
  
 ![Interface utilisateur bénéficiant de volets imbriqués.](../../../../docs/framework/wpf/controls/media/nested-panels.png "nested\_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## Éléments Panel personnalisés  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un ensemble de contrôles de disposition souples, mais il est également possible de réaliser des comportements de disposition personnalisés en substituant les méthodes <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> et <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  Il est possible d'effectuer un dimensionnement et un positionnement personnalisés en définissant de nouveaux comportements de disposition dans ces méthodes override.  
  
 De même, des comportements de disposition personnalisés basés sur des classes dérivées \(telles que <xref:System.Windows.Controls.Canvas> ou <xref:System.Windows.Controls.Grid>\) peuvent être définis en substituant leurs méthodes <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> et <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  
  
 L'exemple de code suivant montre comment créer un élément <xref:System.Windows.Controls.Panel> personnalisé.  Ce nouveau <xref:System.Windows.Controls.Panel> défini en tant que `PlotPanel` prend en charge le positionnement des éléments enfants via l'utilisation de coordonnées *x* et *y* codées en dur.  Dans cet exemple, un élément <xref:System.Windows.Shapes.Rectangle> \(non affiché\) est positionné au point de coordonnées 50 \(*x*\), et 50 \(*y*\).  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Pour voir une implémentation de panneau personnalisé plus complexe, consultez [Créer un panneau d'habillage du contenu personnalisé, exemple](http://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## Prise en charge de la localisation\/globalisation  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge un nombre de fonctionnalités qui facilitent la création d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] localisable.  
  
 Tous les éléments Panel prennent en charge en mode natif la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A>, qui peut être utilisée pour réorienter dynamiquement du contenu selon les paramètres régionaux de l'utilisateur ou les paramètres de langue.  Pour plus d'informations, consultez <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 La propriété <xref:System.Windows.Window.SizeToContent%2A> fournit un mécanisme qui permet aux développeurs d'applications d'anticiper les besoins d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] localisée.  En utilisant la valeur <xref:System.Windows.SizeToContent> de cette propriété, une <xref:System.Windows.Window> parent est toujours dimensionnée dynamiquement afin de s'adapter à son contenu et n'est pas soumise à des restrictions artificielles de sa hauteur et de sa largeur.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid> et <xref:System.Windows.Controls.StackPanel> sont tous des choix adéquats pour une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]localisable.  <xref:System.Windows.Controls.Canvas> n'est pas un choix approprié, car il positionne le contenu de façon absolue, le rendant difficile à localiser.  
  
 Pour plus d'informations sur la création d'applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec des [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] localisables, consultez [Vue d'ensemble de l'utilisation de la disposition automatique](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md).  
  
## Voir aussi  
 [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)   
 [Galerie de dispositions WPF, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160054)   
 [Disposition](../../../../docs/framework/wpf/advanced/layout.md)   
 [Galerie de contrôles WPF, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160053)   
 [Vue d'ensemble de l'alignement, des marges et du remplissage](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)   
 [Créer un panneau d'habillage du contenu personnalisé, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159979)   
 [Vue d'ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)   
 [Vue d'ensemble de l'utilisation de la disposition automatique](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)