---
title: "Vue d&#39;ensemble de l&#39;alignement, des marges et du remplissage | Microsoft Docs"
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
  - "aligner"
  - "classes, FrameworkElement"
  - "FrameworkElement (classe)"
  - "marges"
  - "marge intérieure"
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Vue d&#39;ensemble de l&#39;alignement, des marges et du remplissage
La classe <xref:System.Windows.FrameworkElement> expose plusieurs propriétés, utilisées pour positionner des éléments enfants de manière précise.  Cette rubrique présente quatre des propriétés les plus importantes : <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>.  Il est important de comprendre les effets de ces propriétés, car elles servent de base au contrôle de la position des éléments dans les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
   
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## Introduction au positionnement d'un élément  
 Il existe de nombreuses manières de positionner des éléments à l'aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Toutefois, pour obtenir une disposition parfaite, il ne suffit pas simplement de choisir le bon élément <xref:System.Windows.Controls.Panel>.  Un contrôle de positionnement précis requiert une bonne connaissance des propriétés <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>.  
  
 L'illustration suivante montre un scénario de disposition qui utilise plusieurs propriétés de positionnement.  
  
 ![Exemple de propriétés de positionnement WPF](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.png "layout\_margins\_padding\_alignment\_graphic1")  
  
 À première vue, les éléments <xref:System.Windows.Controls.Button> de cette illustration semblent placés de manière aléatoire.  Toutefois, leurs positions sont contrôlées de manière précise à l'aide d'une combinaison de marges, d'alignements et de remplissage.  
  
 L'exemple suivant décrit comment créer la disposition de l'illustration précédente.  Un élément <xref:System.Windows.Controls.Border> encapsule un <xref:System.Windows.Controls.StackPanel> parent, avec une valeur <xref:System.Windows.Controls.Border.Padding%2A> de 15 [pixels indépendants du périphérique](GTMT).  Cela explique l'étroite bande <xref:System.Windows.Media.Brushes.LightBlue%2A> qui entoure le <xref:System.Windows.Controls.StackPanel> enfant.  Les éléments enfants du <xref:System.Windows.Controls.StackPanel> sont utilisés pour illustrer chacune des différentes propriétés de positionnement détaillées dans cette rubrique.  Trois éléments <xref:System.Windows.Controls.Button> sont utilisés pour montrer les propriétés <xref:System.Windows.FrameworkElement.Margin%2A> et <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>.  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Le diagramme suivant fournit un gros plan de l'affichage des différentes propriétés de positionnement utilisées dans l'exemple précédent.  Les sections suivantes de cette rubrique décrivent plus en détail la manière d'utiliser chaque propriété de positionnement.  
  
 ![Propriétés de positionnement avec légendes d'écran](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.png "layout\_margins\_padding\_alignment\_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## Présentation des propriétés d'alignement  
 Les propriétés <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> décrivent la manière de positionner un élément enfant dans l'espace de disposition alloué d'un élément parent.  En utilisant ces propriétés ensemble, vous pouvez positionner des éléments enfants de manière précise.  Par exemple, les éléments enfants d'un <xref:System.Windows.Controls.DockPanel> peuvent spécifier quatre alignements horizontaux différents : <xref:System.Windows.HorizontalAlignment>, <xref:System.Windows.HorizontalAlignment>, <xref:System.Windows.HorizontalAlignment> ou <xref:System.Windows.HorizontalAlignment> pour remplir l'espace disponible.  Des valeurs similaires sont disponibles pour le positionnement vertical.  
  
> [!NOTE]
>  Les propriétés <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A>, définies explicitement sur un élément, ont la priorité sur la valeur de propriété <xref:System.Windows.HorizontalAlignment>.  En cas de tentative de définition d'une valeur <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> sur `Stretch`, la requête `Stretch` est ignorée.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### Propriété HorizontalAlignment  
 La propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> déclare les caractéristiques de l'alignement horizontal à appliquer aux éléments enfants.  Le tableau suivant montre toutes les valeurs possibles de la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>.  
  
|Membre|Description|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment>|Les éléments enfants sont alignés à gauche de l'espace de disposition alloué de l'élément parent.|  
|<xref:System.Windows.HorizontalAlignment>|Les éléments enfants sont alignés au centre de l'espace de disposition alloué de l'élément parent.|  
|<xref:System.Windows.HorizontalAlignment>|Les éléments enfants sont alignés à droite de l'espace de disposition alloué de l'élément parent.|  
|<xref:System.Windows.HorizontalAlignment> \(par défaut\)|Les éléments enfants sont étirés pour remplir l'espace de disposition alloué de l'élément parent.  Les valeurs <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> explicites sont prioritaires.|  
  
 L'exemple suivant indique comment appliquer la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> aux éléments <xref:System.Windows.Controls.Button>.  Chaque valeur d'attribut est présentée pour mieux illustrer les différents comportements de rendu.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Le code précédent donne une disposition semblable à l'image suivante.  Les effets de positionnement de chaque valeur <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> sont visibles dans l'illustration.  
  
 ![Exemple d'alignement horizontal](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.png "layout\_horizontal\_alignment\_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### Propriété VerticalAlignment  
 La propriété <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> décrit les caractéristiques de l'alignement vertical à appliquer aux éléments enfants.  Le tableau suivant montre toutes les valeurs possibles pour la propriété <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>.  
  
|Membre|Description|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment>|Les éléments enfants sont alignés en haut de l'espace de disposition alloué de l'élément parent.|  
|<xref:System.Windows.VerticalAlignment>|Les éléments enfants sont alignés au centre de l'espace de disposition alloué de l'élément parent.|  
|<xref:System.Windows.VerticalAlignment>|Les éléments enfants sont alignés en bas de l'espace de disposition alloué de l'élément parent.|  
|<xref:System.Windows.VerticalAlignment> \(par défaut\)|Les éléments enfants sont étirés pour remplir l'espace de disposition alloué de l'élément parent.  Les valeurs <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> explicites sont prioritaires.|  
  
 L'exemple suivant indique comment appliquer la propriété <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> aux éléments <xref:System.Windows.Controls.Button>.  Chaque valeur d'attribut est présentée pour mieux illustrer les différents comportements de rendu.  Pour les besoins de cet exemple, un élément <xref:System.Windows.Controls.Grid> avec un quadrillage visible est utilisé en tant que parent pour mieux illustrer le comportement de disposition de chaque valeur de propriété.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Le code précédent donne une disposition semblable à l'image suivante.  Les effets de positionnement de chaque valeur <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> sont visibles dans l'illustration.  
  
 ![Exemple de propriété VerticalAlignment](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.png "layout\_vertical\_alignment\_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## Présentation des propriétés de marge  
 La propriété <xref:System.Windows.FrameworkElement.Margin%2A> décrit la distance entre un élément et son enfant ou ses homologues.  Les valeurs <xref:System.Windows.FrameworkElement.Margin%2A> peuvent être uniformes, en utilisant une syntaxe telle que `Margin="20"`.  Avec cette syntaxe, un <xref:System.Windows.FrameworkElement.Margin%2A> uniforme de 20 [dip \(device independent pixels\)](GTMT) serait appliqué à l'élément.  Les valeurs <xref:System.Windows.FrameworkElement.Margin%2A> peuvent également prendre la forme de quatre valeurs distinctes, chaque valeur décrivant une marge distincte à s'appliquer à gauche, en haut, à droite et en bas \(dans cet ordre\), comme `Margin="0,10,5,25"`.  Une utilisation adéquate de la propriété <xref:System.Windows.FrameworkElement.Margin%2A> permet un excellent contrôle de la position de rendu d'un élément et de la position de rendu de ses éléments voisins et enfants.  
  
> [!NOTE]
>  Une marge non nulle applique un espace en dehors de la <xref:System.Windows.FrameworkElement.ActualWidth%2A> et de la <xref:System.Windows.FrameworkElement.ActualHeight%2A> de l'élément.  
  
 L'exemple suivant indique comment appliquer des marges uniformes autour d'un groupe d'éléments <xref:System.Windows.Controls.Button>.  Les éléments <xref:System.Windows.Controls.Button> sont espacés régulièrement avec une mémoire tampon de marge de dix pixels dans chaque direction.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 Dans de nombreux cas, une marge uniforme n'est pas appropriée.  Dans ces cas précis, l'espacement non uniforme peut être appliqué.  L'exemple suivant indique comment appliquer un espacement de marge non uniforme aux éléments enfants.  Les marges sont décrites dans cet ordre : gauche, haut, droite, bas.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## Présentation de la propriété de remplissage  
 Le remplissage est semblable à <xref:System.Windows.FrameworkElement.Margin%2A> à bien des égards.  La propriété Padding n'est exposée que sur un petit nombre de classes, principalement pour des raisons pratiques : <xref:System.Windows.Documents.Block>, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control> et <xref:System.Windows.Controls.TextBlock> sont des exemples de classes qui exposent une propriété Padding.  La propriété <xref:System.Windows.Controls.Border.Padding%2A> agrandit la taille effective d'un élément enfant selon la valeur <xref:System.Windows.Thickness> spécifiée.  
  
 L'exemple suivant indique comment appliquer <xref:System.Windows.Controls.Border.Padding%2A> à un élément <xref:System.Windows.Controls.Border> parent.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## Utilisation de l'alignement, des marges et du remplissage dans une application  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> fournissent le contrôle de positionnement nécessaire à la création d'une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] complexe.  Vous pouvez utiliser les effets de chaque propriété pour modifier le positionnement d'un élément enfant, en offrant une plus grande souplesse lors de la création d'applications dynamiques et d'expériences utilisateur.  
  
 L'exemple suivant montre chacun des concepts détaillés dans cette rubrique.  Reposant sur l'infrastructure du premier exemple présenté dans cette rubrique, cet exemple ajoute un élément <xref:System.Windows.Controls.Grid> en tant qu'enfant du <xref:System.Windows.Controls.Border> du premier exemple.  <xref:System.Windows.Controls.Border.Padding%2A> est appliqué à l'élément <xref:System.Windows.Controls.Border> parent.  Le <xref:System.Windows.Controls.Grid> est utilisé pour partitionner l'espace entre trois éléments <xref:System.Windows.Controls.StackPanel> enfants.  Les éléments <xref:System.Windows.Controls.Button> sont encore utilisés pour afficher les différents effets de <xref:System.Windows.FrameworkElement.Margin%2A> et <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>.  Des éléments <xref:System.Windows.Controls.TextBlock> sont ajoutés à chaque <xref:System.Windows.Controls.ColumnDefinition> pour mieux définir les différentes propriétés appliquées aux éléments <xref:System.Windows.Controls.Button> dans chaque colonne.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Une fois compilée, l'application précédente donne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui ressemble à l'illustration suivante.  Les effets des différentes valeurs de propriété sont évidents dans l'espacement entre les éléments. Les valeurs de propriété significatives pour les éléments de chaque colonne sont affichées dans des éléments <xref:System.Windows.Controls.TextBlock>.  
  
 ![Plusieurs propriétés de positionnement dans une application](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.png "layout\_margins\_padding\_aligment\_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## Quoi d'autre ?  
 Les propriétés de positionnement définies par la classe <xref:System.Windows.FrameworkElement> permettent un contrôle précis du positionnement de l'élément dans des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Vous disposez désormais de plusieurs techniques pour mieux positionner les éléments à l'aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Des ressources supplémentaires expliquent plus en détail la disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La rubrique [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md) contient plus de détails sur les différents éléments <xref:System.Windows.Controls.Panel>.  La rubrique [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) présente des techniques avancées qui utilisent des éléments de disposition pour positionner des composants et lier leurs actions aux sources de données.  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.Margin%2A>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Disposition](../../../../docs/framework/wpf/advanced/layout.md)   
 [Galerie de dispositions WPF, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160054)