---
title: "Optimisation des performances&#160;: contr&#244;les | Microsoft Docs"
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
  - "recyclage de conteneurs"
  - "contrôles (WPF), améliorer les performances"
  - "virtualisation de l'interface utilisateur"
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Optimisation des performances&#160;: contr&#244;les
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] comporte de nombreux composants d'interface utilisateur communs utilisés dans la plupart des applications Windows.  Cette rubrique présente des techniques qui permettent d'améliorer les performances de votre interface utilisateur.  
  
   
  
<a name="Displaying"></a>   
## Affichage de grands groupes de données  
 Les contrôles WPF, tels que <xref:System.Windows.Controls.ListView> et <xref:System.Windows.Controls.ComboBox>, permettent d'afficher des listes d'éléments dans une application.  Si la liste à afficher est longue, les performances de l'application risquent de s'en trouver affectées.  Cela s'explique par le fait que le système de disposition standard crée un conteneur de disposition pour chaque élément associé au contrôle de liste, puis calcule la taille et la position de sa disposition.  En règle générale, vous n'avez pas à afficher tous les éléments simultanément ; au lieu de cela, vous en affichez un sous\-ensemble et l'utilisateur fait défiler la liste.  Dans ce cas, le recours à la *virtualisation* de l'interface utilisateur est justifiée : la génération du conteneur d'élément et le calcul de la disposition qui y est associée pour un élément sont différés jusqu'à ce que cet élément soit visible.  
  
 La virtualisation de l'interface utilisateur est un aspect important des contrôles de liste.  La virtualisation de l'interface utilisateur ne doit pas être confondue avec la virtualisation des données.  La virtualisation de l'interface utilisateur stocke uniquement les éléments visibles dans la mémoire ; dans un scénario de liaison de données, elle stocke l'intégralité de la structure de données dans la mémoire.  En revanche, la virtualisation des données stocke uniquement les éléments de données qui sont visibles à l'écran dans la mémoire.  
  
 Par défaut, la virtualisation d'interface utilisateur est activée pour les contrôles <xref:System.Windows.Controls.ListView> et <xref:System.Windows.Controls.ListBox> lorsque leurs éléments de liste sont liés aux données.  La virtualisation <xref:System.Windows.Controls.TreeView> peut être activée en affectant à la propriété jointe <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> la valeur `true`.  Pour activer la virtualisation de l'interface utilisateur des contrôles personnalisés qui dérivent d'<xref:System.Windows.Controls.ItemsControl> ou de contrôles d'élément existants qui utilisent la classe <xref:System.Windows.Controls.StackPanel>, telle que <xref:System.Windows.Controls.ComboBox>, vous pouvez affecter à <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> la valeur <xref:System.Windows.Controls.VirtualizingStackPanel> et affecter à <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> la valeur `true`.  Vous risquez malheureusement de désactiver la virtualisation de l'interface utilisateur de ces contrôles sans vous en rendre compte.  La liste des conditions qui désactivent la virtualisation de l'interface utilisateur est la suivante.  
  
-   Les conteneurs d'élément sont directement ajoutés à <xref:System.Windows.Controls.ItemsControl>.  Par exemple, si une application ajoute explicitement des objets <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListBox> ne virtualise pas les objets <xref:System.Windows.Controls.ListBoxItem>.  
  
-   Les conteneurs d'élément figurant dans <xref:System.Windows.Controls.ItemsControl> sont de types différents.  Par exemple, un <xref:System.Windows.Controls.Menu> qui utilise des objets <xref:System.Windows.Controls.Separator> ne peut pas implémenter le recyclage de conteneurs, car <xref:System.Windows.Controls.Menu> contient des objets de type <xref:System.Windows.Controls.Separator> et <xref:System.Windows.Controls.MenuItem>.  
  
-   Affectation à <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> de la valeur `false`.  
  
-   Affectation à <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> de la valeur `false`.  
  
 Une considération importante lorsque vous virtualisez les conteneurs d'élément est si vous avez des informations d'état supplémentaires associées à un conteneur d'élément qui appartient à l'élément.  Si tel est le cas, vous devez enregistrer ces informations d'état supplémentaires.  Par exemple, vous pouvez avoir un élément contenu dans un contrôle <xref:System.Windows.Controls.Expander> et l'état <xref:System.Windows.Controls.Expander.IsExpanded%2A> peut être lié au conteneur de l'élément, et non à l'élément lui\-même.  Lorsque le conteneur est réutilisé pour un nouvel élément, la valeur actuelle d'<xref:System.Windows.Controls.Expander.IsExpanded%2A> est utilisée pour ce nouvel élément.  L'ancien élément perd en plus la valeur <xref:System.Windows.Controls.Expander.IsExpanded%2A> correcte.  
  
 Actuellement, aucun contrôle WPF n'assure la prise en charge intégrée de la virtualisation des données.  
  
<a name="Container"></a>   
## Recyclage de conteneurs  
 Le *recyclage de conteneurs* optimise la virtualisation de l'interface utilisateur ajoutée au .NET Framework 3.5 SP1 pour les contrôles qui héritent d'<xref:System.Windows.Controls.ItemsControl> et peut également améliorer les performances de défilement.  Lors du remplissage d'un <xref:System.Windows.Controls.ItemsControl> qui utilise la virtualisation de l'interface utilisateur, celui\-ci crée un conteneur d'élément pour chaque élément qui défile de manière visible et détruit le conteneur d'élément de chaque élément qui défile de manière invisible.  Le *recyclage de conteneurs* permet au contrôle de réutiliser les conteneurs d'élément existants pour des éléments de données différents, de manière à éviter que les conteneurs d'élément ne soient constamment créés et détruits à mesure que l'utilisateur fait défiler <xref:System.Windows.Controls.ItemsControl>.  Vous pouvez choisir d'activer le recyclage de conteneurs en définissant la propriété jointe de <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> à <xref:System.Windows.Controls.VirtualizationMode>.  
  
 Tout <xref:System.Windows.Controls.ItemsControl> qui prend en charge la virtualisation peut utiliser le recyclage de conteneurs.  Pour obtenir un exemple d'activation du recyclage de conteneurs sur un <xref:System.Windows.Controls.ListBox>, consultez [Améliorer les performances de défilement d'un contrôle ListBox](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).  
  
<a name="Supporting"></a>   
## Prise en charge de la virtualisation bidirectionnelle  
 <xref:System.Windows.Controls.VirtualizingStackPanel> assure la prise en charge intégrée de la virtualisation de l'interface utilisateur dans un sens, soit horizontalement soit verticalement.  Pour utiliser la virtualisation bidirectionnelle pour vos contrôles, vous devez implémenter un panneau personnalisé qui étend la classe <xref:System.Windows.Controls.VirtualizingStackPanel>.  La classe <xref:System.Windows.Controls.VirtualizingStackPanel> expose des méthodes virtuelles, telles que <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A> et <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Ces méthodes virtuelles vous permettent de détecter une modification dans la partie visible d'une liste et de la gérer en conséquence.  
  
<a name="Optimizing"></a>   
## Optimisation des modèles  
 L'arborescence d'éléments visuels contient tous les éléments visuels d'une application.  Elle contient non seulement les objets directement créés, mais aussi les objets résultant d'une expansion de modèle.  Par exemple, lorsque vous créez un <xref:System.Windows.Controls.Button>, vous obtenez également des objets <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> et <xref:System.Windows.Controls.ContentPresenter> dans l'arborescence d'éléments visuels.  Si vous n'avez pas optimisé vos modèles de contrôle, vous pouvez créer de nombreux objets supplémentaires inutiles dans l'arborescence d'éléments visuels.  Pour plus d'informations sur l'arborescence d'éléments visuels, consultez [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
<a name="Deferred"></a>   
## Défilement différé  
 Par défaut, lorsque l'utilisateur fait glisser le curseur d'une barre de défilement, l'affichage du contenu est mis à jour en permanence.  Si le défilement est lent dans votre contrôle, envisagez d'utiliser le défilement différé.  Le contenu est alors uniquement mis à jour lorsque l'utilisateur arrête de faire glisser le curseur.  
  
 Pour implémenter le défilement différé, affectez à la propriété <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> la valeur `true`.  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> est une propriété jointe qui peut avoir la valeur <xref:System.Windows.Controls.ScrollViewer> et tout contrôle qui a un <xref:System.Windows.Controls.ScrollViewer> dans son modèle de contrôle.  
  
<a name="Controls"></a>   
## Contrôles implémentant des fonctionnalités de performances  
 Le tableau suivant répertorie les contrôles communs d'affichage de données et leur prise en charge de fonctionnalités de performances.  Pour plus d'informations sur l'activation de ces fonctionnalités, consultez les sections précédentes.  
  
|Contrôle|Virtualisation|Recyclage de conteneurs|Défilement différé|  
|--------------|--------------------|-----------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|Peut être activé|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.ContextMenu>|Peut être activé|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.DocumentViewer>|Non disponible|Non disponible|Peut être activé|  
|<xref:System.Windows.Controls.ListBox>|Par défaut|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.ListView>|Par défaut|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.TreeView>|Peut être activé|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.ToolBar>|Non disponible|Non disponible|Peut être activé|  
  
> [!NOTE]
>  Pour obtenir un exemple d'activation de la virtualisation et du recyclage de conteneurs sur un <xref:System.Windows.Controls.TreeView>, consultez [Améliorer les performances d'un contrôle TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md).  
  
## Voir aussi  
 [Disposition](../../../../docs/framework/wpf/advanced/layout.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Contrôles](../../../../docs/framework/wpf/controls/index.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Procédure pas à pas : mise en cache de données d'application dans une application WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)