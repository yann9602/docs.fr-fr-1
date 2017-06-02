---
title: "Disposition | Microsoft Docs"
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
  - "contrôles (WPF), système de disposition"
  - "système de disposition (WPF)"
  - "système de disposition WPF"
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# Disposition
Cette rubrique décrit le système de disposition [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Comprendre comment et quand les calculs de disposition se produisent est essentiel pour la création d'interfaces utilisateur dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Zones englobantes d'élément](#LayoutSystem_BoundingBox)  
  
-   [Système de disposition](#LayoutSystem_Overview)  
  
-   [Mesure et réorganisation d'enfants](#LayoutSystem_Measure_Arrange)  
  
-   [Comportements des éléments de volet et de disposition personnalisée](#LayoutSystem_PanelsCustom)  
  
-   [Considérations relatives aux performances de la disposition](#LayoutSystem_Performance)  
  
-   [Rendu d'une précision inférieure au pixel et arrondi de disposition](#LayoutSystem_LayoutRounding)  
  
-   [Quoi d'autre ?](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## Zones englobantes d'élément  
 Lorsque la disposition est considérée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il est important de comprendre le cadre englobant qui entoure tous les éléments.  Chaque <xref:System.Windows.FrameworkElement> consommé par le système de disposition peut être considéré comme un rectangle emboîté dans la disposition.  La classe <xref:System.Windows.Controls.Primitives.LayoutInformation> retourne les limites de l'allocation de disposition d'un élément, ou emplacement.  La taille du rectangle est déterminée par l'espace disponible à l'écran, la taille de toutes les contraintes, les propriétés spécifiques à la disposition \(marge et marge intérieure, par exemple\) et le comportement individuel de l'élément <xref:System.Windows.Controls.Panel> parent.  En traitant ces données, le système de disposition est en mesure de calculer la position de tous les enfants d'un <xref:System.Windows.Controls.Panel> particulier.  Il est important de se souvenir que les caractéristiques de dimensionnement définies sur l'élément parent, tel qu'une <xref:System.Windows.Controls.Border>\) affectent ses enfants.  
  
 Voici une illustration.  
  
 ![Grille classique, sans cadre englobant superposé.](../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 Cette disposition peut être accomplie à l'aide du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] suivant.  
  
 [!code-xml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Un élément <xref:System.Windows.Controls.TextBlock> unique est hébergé dans un <xref:System.Windows.Controls.Grid>.  Tandis que le texte remplit uniquement l'angle supérieur gauche de la première colonne, l'espace alloué pour le <xref:System.Windows.Controls.TextBlock> est réellement beaucoup plus grand.  Le cadre englobant de tout <xref:System.Windows.FrameworkElement> peut être extrait à l'aide de la méthode <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>.  L'illustration suivante montre le cadre englobant pour l'élément <xref:System.Windows.Controls.TextBlock>.  
  
 ![Le cadre englobant du TextBlock est maintenant visible.](../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 Comme indiqué par le rectangle jaune, l'espace alloué pour l'élément <xref:System.Windows.Controls.TextBlock> est réellement beaucoup plus grand qu'il apparaît.  Comme des éléments supplémentaires sont ajoutés au <xref:System.Windows.Controls.Grid>, cette allocation pourrait réduire ou se développer, selon le type et la taille des éléments ajoutés.  
  
 L'emplacement de disposition du <xref:System.Windows.Controls.TextBlock> est traduit dans un <xref:System.Windows.Shapes.Path> à l'aide de la méthode <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>.  Cette technique peut être utile pour l'affichage du cadre englobant d'un élément.  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## Système de disposition  
 Dans sa forme la plus simple, la disposition est un système récursif qui conduit au dimensionnement, au positionnement et au dessin d'un élément.  Plus spécifiquement, la disposition décrit le processus de mesure et de réorganisation des membres de la collection <xref:System.Windows.Controls.Panel.Children%2A> d'un élément <xref:System.Windows.Controls.Panel>.  La disposition est un processus intensif.  Plus grande est la collection <xref:System.Windows.Controls.Panel.Children%2A>, plus important sera le nombre de calculs qui doivent être faits.  Il est également possible de définir une complexité en fonction du comportement de disposition défini par l'élément <xref:System.Windows.Controls.Panel> qui possède la collection.  Un <xref:System.Windows.Controls.Panel> relativement simple, tel que <xref:System.Windows.Controls.Canvas>, peut avoir de bien meilleures performances qu'un <xref:System.Windows.Controls.Panel> plus complexe, tel que <xref:System.Windows.Controls.Grid>.  
  
 Chaque fois qu'un <xref:System.Windows.UIElement> enfant modifie sa position, il a la possibilité de déclencher une nouvelle passe via le système de disposition.  Il est par conséquent important de comprendre les événements qui peuvent appeler le système de disposition, car un appel inutile risque d'altérer les performances de l'application.  Les éléments suivants décrivent le processus qui se produit lorsque le système de disposition est appelé.  
  
1.  Un <xref:System.Windows.UIElement> enfant commence le processus de disposition par la mesure de ses propriétés principales.  
  
2.  Les propriétés de dimensionnement définies sur <xref:System.Windows.FrameworkElement> sont évaluées, telles que <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3.  La logique spécifique <xref:System.Windows.Controls.Panel> est appliquée, telle que le sens <xref:System.Windows.Controls.Dock> ou l'empilement <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4.  Le contenu est réorganisé une fois que tous les enfants ont été mesurés.  
  
5.  La collection <xref:System.Windows.Controls.Panel.Children%2A> est dessinée à l'écran.  
  
6.  Le processus est encore appelé si des <xref:System.Windows.Controls.Panel.Children%2A> supplémentaires sont ajoutés à la collection, un <xref:System.Windows.FrameworkElement.LayoutTransform%2A> est appliqué, ou la méthode <xref:System.Windows.UIElement.UpdateLayout%2A> est appelée.  
  
 Ce processus et la manière de l'appeler sont définis de façon plus détaillée dans les sections suivantes.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## Mesure et réorganisation d'enfants  
 Le système de disposition complète deux passes pour chaque membre de la collection <xref:System.Windows.Controls.Panel.Children%2A>, une passe de mesure et une passe de réorganisation.  Chaque <xref:System.Windows.Controls.Panel> enfant fournit ses propres méthodes <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> pour accomplir son propre comportement de disposition spécifique.  
  
 Pendant la phase de mesure, chaque membre de la collection <xref:System.Windows.Controls.Panel.Children%2A> est évalué.  Le processus commence par un appel à la méthode <xref:System.Windows.UIElement.Measure%2A>.  Cette méthode est appelée dans l'implémentation de l'élément <xref:System.Windows.Controls.Panel> parent et n'a pas à être explicitement appelée pour que la disposition se produise.  
  
 En premier lieu, les propriétés de taille natives de <xref:System.Windows.UIElement> sont évaluées, telles que <xref:System.Windows.UIElement.Clip%2A> et <xref:System.Windows.UIElement.Visibility%2A>.  Cela génère une valeur nommée `constraintSize` passée à <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Deuxièmement, les propriétés d'infrastructure définies sur <xref:System.Windows.FrameworkElement> sont traitées, ce qui affecte la valeur de `constraintSize`.  Ces propriétés décrivent généralement les caractéristiques de dimensionnement du <xref:System.Windows.UIElement> sous\-jacent, \(<xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> et <xref:System.Windows.FrameworkElement.Style%2A>, par exemple\).  Chacune de ces propriétés peut modifier l'espace nécessaire à l'affichage de l'élément.  Puis <xref:System.Windows.FrameworkElement.MeasureOverride%2A> est appelé avec `constraintSize` comme un paramètre.  
  
> [!NOTE]
>  Il existe une différence entre les propriétés de <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A> et <xref:System.Windows.FrameworkElement.ActualWidth%2A>.  Par exemple, la propriété <xref:System.Windows.FrameworkElement.ActualHeight%2A> est une valeur calculée en fonction d'autres entrées de hauteur et le système de disposition.  La valeur est définie par le système de disposition lui\-même, selon une passe de rendu réel, et peut par conséquent rester légèrement en retrait de la valeur définie des propriétés, telle que <xref:System.Windows.FrameworkElement.Height%2A>, qui est la base de la modification d'entrée.  
>   
>  Du fait que <xref:System.Windows.FrameworkElement.ActualHeight%2A> est une valeur calculée, vous devez savoir que des modifications multiples ou incrémentielles signalées peuvent se produire sur cette valeur résultant de différentes opérations par le système de disposition.  Le système de disposition peut calculer l'espace de mesure requis pour les éléments enfants, les contraintes par l'élément parent, et ainsi de suite.  
  
 L'objectif ultime de la phase de mesure est pour l'enfant de déterminer sa <xref:System.Windows.UIElement.DesiredSize%2A>, qui se produit pendant l'appel de <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  La valeur <xref:System.Windows.UIElement.DesiredSize%2A> est stockée par <xref:System.Windows.UIElement.Measure%2A> pour une utilisation pendant la passe de réorganisation du contenu.  
  
 La passe de réorganisation du contenu commence par un appel à la méthode <xref:System.Windows.UIElement.Arrange%2A>.  Pendant la passe de réorganisation, l'élément <xref:System.Windows.Controls.Panel> parent génère un rectangle qui représente les limites de l'enfant.  Cette valeur est passée à la méthode <xref:System.Windows.FrameworkElement.ArrangeCore%2A> pour traitement.  
  
 La méthode <xref:System.Windows.FrameworkElement.ArrangeCore%2A> évalue la <xref:System.Windows.UIElement.DesiredSize%2A> de l'enfant et évalue toutes marges supplémentaires qui peuvent affecter la taille rendue de l'élément.  <xref:System.Windows.FrameworkElement.ArrangeCore%2A> génère une `arrangeSize`, qui est passée à la méthode <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> du <xref:System.Windows.Controls.Panel> en tant que paramètre.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> génère la `finalSize` de l'enfant.  Enfin, la méthode <xref:System.Windows.FrameworkElement.ArrangeCore%2A> effectue une dernière évaluation des propriétés de décalage, telles que la marge et l'alignement, par exemple\) et place l'enfant dans son emplacement de disposition.  L'enfant n'a pas besoin de remplir intégralement l'espace alloué \(et souvent ne le remplit pas\).  Le contrôle est alors retourné au <xref:System.Windows.Controls.Panel> parent, et le processus de disposition est complet.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## Comportements des éléments de volet et de disposition personnalisée  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut un groupe d'éléments qui dérivent de <xref:System.Windows.Controls.Panel>.  Ces éléments <xref:System.Windows.Controls.Panel> permettent de nombreuses dispositions complexes.  Par exemple, l'empilement d'éléments peut être facilement accompli à l'aide de l'élément <xref:System.Windows.Controls.StackPanel>, tandis que les dispositions de flux plus complexes et libres sont possible à l'aide d'un <xref:System.Windows.Controls.Canvas>.  
  
 Le tableau suivant récapitule les éléments de disposition <xref:System.Windows.Controls.Panel> disponibles.  
  
|Nom du volet|Description|  
|------------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants par leurs coordonnées relatives à la zone du <xref:System.Windows.Controls.Canvas>.|  
|<xref:System.Windows.Controls.DockPanel>|Définit une zone dans laquelle vous pouvez réorganiser des éléments enfants soit horizontalement soit verticalement, les uns par rapport aux autres.|  
|<xref:System.Windows.Controls.Grid>|Définit une grille flexible qui se compose de colonnes et des lignes.|  
|<xref:System.Windows.Controls.StackPanel>|Réorganise des éléments enfants sur une seule ligne pouvant être orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Fournit une infrastructure pour les éléments <xref:System.Windows.Controls.Panel> qui virtualisent leur collection de données enfants.  Il s'agit d'une classe abstraite.|  
|<xref:System.Windows.Controls.WrapPanel>|Positionne de gauche à droite des éléments enfants dans une position séquentielle, en arrêtant le contenu à la ligne suivante au bord de la zone conteneur.  Le classement continue ensuite séquentiellement de haut en bas ou de droite à gauche, selon la valeur de la propriété <xref:System.Windows.Controls.WrapPanel.Orientation%2A>.|  
  
 Pour les applications qui requièrent une disposition qui ne peut utiliser aucun des éléments <xref:System.Windows.Controls.Panel> prédéfinis, les comportements de disposition personnalisée peuvent être obtenus en héritant de <xref:System.Windows.Controls.Panel> et en substituant les méthodes <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.  Pour obtenir un exemple, consultez [Panneau radial personnalisé, exemple](http://go.microsoft.com/fwlink/?LinkID=159982).  
  
<a name="LayoutSystem_Performance"></a>   
## Considérations relatives aux performances de la disposition  
 La disposition est un processus récursif.  Chaque élément enfant dans une collection <xref:System.Windows.Controls.Panel.Children%2A> est traité pendant chaque appel du système de disposition.  Par conséquent, le déclenchement du système de disposition doit être évité lorsque ce n'est pas nécessaire.  Les considérations suivantes peuvent vous aider à accomplir de meilleures performances.  
  
-   Identifiez les modifications de valeurs de propriétés qui forceront une mise à jour récursive par le système de disposition.  
  
     Les propriétés de dépendance dont les valeurs peuvent entraîner l'initialisation du système de disposition sont marquées avec des indicateurs publics.  <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> et <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> fournissent des indices utiles sur les modifications de valeurs de propriétés qui forceront une mise à jour récursive par le système de disposition.  En général, toute propriété qui peut affecter la taille du cadre englobant d'un élément doit avoir un indicateur <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> ayant pour valeur true.  Pour plus d'informations, consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
-   Lorsque cela est possible, utilisez un <xref:System.Windows.UIElement.RenderTransform%2A> au lieu d'un <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     Une <xref:System.Windows.FrameworkElement.LayoutTransform%2A> peut être une méthode très utile pour affecter le contenu d'un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  Toutefois, si l'effet de la transformation ne doit pas avoir d'impact sur la position d'autres éléments, il vaut mieux utiliser à la place un <xref:System.Windows.UIElement.RenderTransform%2A>, parce que <xref:System.Windows.UIElement.RenderTransform%2A> n'appelle pas le système de disposition.  <xref:System.Windows.FrameworkElement.LayoutTransform%2A> applique sa transformation et force une mise à jour de la disposition récursive dont il faut tenir compte pour la nouvelle position de l'élément affecté.  
  
-   Évitez les appels inutiles à <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     La méthode <xref:System.Windows.UIElement.UpdateLayout%2A> force une mise à jour de la disposition récursive et n'est pas souvent nécessaire.  À moins d'être sûr qu'une mise à jour complète est obligatoire, reposez\-vous sur le système de disposition pour appeler cette méthode à votre place.  
  
-   Lorsque vous utilisez une grande collection <xref:System.Windows.Controls.Panel.Children%2A>, envisagez d'utiliser un <xref:System.Windows.Controls.VirtualizingStackPanel> au lieu d'un <xref:System.Windows.Controls.StackPanel> normal.  
  
     En virtualisant la collection enfant, le <xref:System.Windows.Controls.VirtualizingStackPanel> garde uniquement en mémoire les objets qui sont actuellement dans la [fenêtre d'affichage](GTMT) du parent.  En conséquence, les performances sont considérablement améliorées dans la plupart des scénarios.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## Rendu d'une précision inférieure au pixel et arrondi de disposition  
 Le système graphique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise des unités indépendantes du périphérique pour garantir l'indépendance vis\-à\-vis du périphérique et de la résolution.  Chaque pixel indépendant du périphérique s'ajuste automatiquement sur le paramètre [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] du système.  Cela fournit aux applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la mise à l'échelle appropriée pour différents paramètres [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] et rend l'application capable de prendre automatiquement en compte le paramètre [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)].  
  
 Cependant, cette indépendance [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] peut générer un rendu irrégulier des bords en raison de l'anticrénelage.  Ces artefacts, apparaissant généralement avec des bords flous ou semi\-transparents, peuvent se produire lorsque l'emplacement d'un bord tombe au milieu d'un pixel de périphérique au lieu d'être entre des pixels de périphériques.  Le système de disposition offre un moyen de réglage avec l'arrondi de disposition.  L'arrondi de disposition est l'endroit où le système de disposition arrondit des valeurs en pixels non intégrales pendant la passe de disposition.  
  
 L'arrondi de disposition est désactivé par défaut.  Pour permettre l'arrondi de disposition, affectez à la propriété <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> la valeur `true` sur tout <xref:System.Windows.FrameworkElement>.  Étant donné qu'il s'agit d'une propriété de dépendance, la valeur sera propagée à tous les enfants dans l'arborescence d'éléments visuels.  Pour permettre l'arrondi de disposition pour l'interface utilisateur entière, affectez au conteneur racine <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> la valeur `true`.  Pour obtenir un exemple, consultez <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.  
  
<a name="LayoutSystem_whatsnext"></a>   
## Quoi d'autre ?  
 Comprendre comment les éléments sont mesurés et organisés est la première étape dans la connaissance de la disposition.  Pour plus d'informations sur les éléments <xref:System.Windows.Controls.Panel> disponibles, consultez [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md).  Pour mieux comprendre les différentes propriétés de positionnement qui peuvent affecter la disposition, consultez [Vue d'ensemble de l'alignement, des marges et du remplissage](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md).  Pour obtenir un exemple d'un élément <xref:System.Windows.Controls.Panel> personnalisé, consultez [Panneau radial personnalisé, exemple](http://go.microsoft.com/fwlink/?LinkID=159982) Lorsque vous êtes prêt à tout réunir dans une application légère, consultez [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.UIElement>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Vue d'ensemble de l'alignement, des marges et du remplissage](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)