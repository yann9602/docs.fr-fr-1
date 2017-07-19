---
title: "Vue d&#39;ensemble de l&#39;utilisation de la disposition automatique | Microsoft Docs"
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
  - "disposition automatique"
  - "disposition, automatique"
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Vue d&#39;ensemble de l&#39;utilisation de la disposition automatique
Cette rubrique présente des instructions pour les développeurs sur la manière d'écrire des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] avec des [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] localisables.  Dans le passé, la localisation d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pouvait prendre beaucoup de temps.  Chaque langue dans laquelle était adaptée l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nécessitait un réglage pixel par pixel.  Aujourd'hui, grâce à une conception et des normes de code adaptées, il est possible de construire les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] afin que les traducteurs aient moins de redimensionnement et de repositionnement à effectuer.  L'approche consistant à écrire des applications qui sont plus faciles à redimensionner et à repositionner est appelée disposition automatique et peut être obtenue en utilisant la conception de l'application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Cette rubrique contient les sections suivantes.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [Avantages de l'utilisation de la disposition automatique](#advantages_of_autolayout)  
  
-   [Disposition automatique et contrôles](#autolayout_controls)  
  
-   [Disposition automatique et normes de codage](#autolayout_coding)  
  
-   [Disposition automatique et grilles](#autolay_grids)  
  
-   [Disposition automatique et grilles en utilisant la propriété IsSharedSizeScope](#autolay_grids_issharedsizescope)  
  
-   [Rubriques connexes](#seeAlsoToggle)  
  
<a name="advantages_of_autolayout"></a>   
## Avantages de l'utilisation de la disposition automatique  
 Du fait de la puissance et de la flexibilité du système de présentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il offre la possibilité de disposer des éléments dans une application qui peuvent être ajustés pour répondre aux exigences de différentes langues.  La liste suivante souligne quelques\-uns des avantages de la disposition automatique.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] s'affiche correctement dans n'importe quelle langue.  
  
-   Réduit le besoin de réajuster la position et la taille des contrôles une fois le texte traduit.  
  
-   Réduit le besoin de réajuster la taille de la fenêtre.  
  
-   La disposition de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est restituée correctement dans n'importe quelle langue.  
  
-   La localisation peut se trouver réduite à sa plus simple expression, à savoir la traduction d'une chaîne.  
  
<a name="autolayout_controls"></a>   
## Disposition automatique et contrôles  
 La disposition automatique permet à une application d'ajuster automatiquement la taille d'un contrôle.  Par exemple, un contrôle peut changer pour accommoder la longueur d'une chaîne.  Cette possibilité permet aux traducteurs de traduire la chaîne, sans devoir redimensionner le contrôle pour que le texte traduit s'ajuste.  L'exemple suivant crée un bouton avec un contenu en anglais.  
  
 [!code-xml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 Dans l'exemple, votre seule tâche consiste à changer le texte pour que le bouton soit en français.  Par exemple :  
  
 [!code-xml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Le graphique suivant illustre la sortie des exemples de code.  
  
 ![Même bouton avec le texte dans différentes langues](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Bouton redimensionnable automatiquement  
  
<a name="autolayout_coding"></a>   
## Disposition automatique et normes de codage  
 L'utilisation de l'approche basée sur la disposition automatique nécessite un jeu de normes de conception de code standard et de règles pour créer une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] entièrement localisable.  Les indications suivantes vont simplifier le codage de votre disposition automatique.  
  
|Normes de codage|Description|  
|----------------------|-----------------|  
|N'utilisez pas de positions absolues.|-   N'utilisez pas <xref:System.Windows.Controls.Canvas> car il positionne les éléments de manière absolue.<br />-   Utilisez <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> et <xref:System.Windows.Controls.Grid> pour positionner les contrôles.<br />-   Pour obtenir des explications sur les divers types de panneaux, consultez [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md).|  
|Ne définissez pas de fenêtre à taille fixe.|-   Utilisez <xref:System.Windows.Window.SizeToContent%2A>.<br />-   Par exemple :<br /><br /> [!code-xml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]|  
|Ajoutez un <xref:System.Windows.FrameworkElement.FlowDirection%2A>|<ul><li>Ajoutez une <xref:System.Windows.FrameworkElement.FlowDirection%2A> à l'élément racine de votre application.</li><li>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un moyen pratique de prendre en charge les dispositions horizontales, bidirectionnelles et verticales.  Dans l'infrastructure de présentation, la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> peut être utilisée pour définir la disposition.  Les modèles de sens du déroulement sont les suivants :<br /><br /> <ul><li><xref:System.Windows.FlowDirection> \(LrTb\) : disposition horizontale pour les langues latines, d'Asie orientale, etc.</li><li><xref:System.Windows.FlowDirection> \(RlTb\) : disposition bidirectionnelle pour l'arabe, l'hébreu, etc.</li></ul></li></ul>|  
|Utilisez des polices composites au lieu des polices physiques.|<ul><li>Avec les polices composites, il n'est pas nécessaire de traduire la propriété <xref:System.Windows.Controls.Control.FontFamily%2A>.</li><li>Les développeurs peuvent utiliser l'une des polices suivantes ou créer la leur.<br /><br /> <ul><li>Interface utilisateur globale</li><li>San Serif globale</li><li>Serif globale</li></ul></li></ul>|  
|Ajoutez xml:lang.|-   Ajoutez l'attribut `xml:lang` dans l'élément racine de votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], par exemple `xml:lang="en-US"` pour une application en anglais<br />-   Étant donné que les polices composites utilisent `xml:lang` pour déterminer la police à utiliser, définissez cette propriété pour qu'elle prenne en charge les scénarios multilingues.|  
  
<a name="autolay_grids"></a>   
## Disposition automatique et grilles  
 L'élément <xref:System.Windows.Controls.Grid> est utile pour la disposition automatique car il permet au développeur de positionner les éléments.  Un contrôle <xref:System.Windows.Controls.Grid> est en mesure de répartir l'espace disponible entre ses éléments enfants, à l'aide d'une disposition de ligne et de colonne.  Les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] peuvent étendre plusieurs cellules, il est également possible d'avoir des grilles imbriquées.  Les grilles sont utiles car elles vous permettent de créer et de positionner une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] complexe.  L'exemple suivant illustre l'utilisation d'une grille pour positionner des boutons et du texte.  Remarquez que la valeur définie pour la hauteur et la largeur des cellules est <xref:System.Windows.GridUnitType>, c'est\-à\-dire que la cellule qui contient le bouton imagé s'adapte à cette image.  
  
 [!code-xml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Le graphique suivant montre la grille produite par le code précédent.  
  
 ![Exemple de grille](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob\_grid")  
Grille  
  
<a name="autolay_grids_issharedsizescope"></a>   
## Disposition automatique et grilles en utilisant la propriété IsSharedSizeScope  
 Un élément <xref:System.Windows.Controls.Grid> est utile dans les applications localisables pour créer des contrôles qui s'ajustent en fonction de leur contenu.  Cependant, il arrive que vous souhaitiez que les contrôles conservent une taille particulière quel que soit le contenu.  Par exemple, pour les boutons « OK », « Annuler » et « Parcourir », vous n'avez probablement pas besoin que les boutons d'adaptent à la taille du contenu.  Dans ce cas, la propriété jointe <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=fullName> s'avère utile pour partager le même dimensionnement entre plusieurs éléments de grille.  L'exemple suivant montre comment partager les données de dimensionnement des colonnes et des lignes entre plusieurs éléments <xref:System.Windows.Controls.Grid>.  
  
 [!code-xml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Remarque** Pour obtenir le code complet, consultez [Partager des propriétés de dimensionnement entre grilles](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md).  
  
## Voir aussi  
 [Globalisation pour WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)   
 [Utiliser la disposition automatique pour créer un bouton](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)   
 [Utiliser une grille pour la disposition automatique](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)