---
title: "Optimisation des performances : contrôles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1b414aee19082196ab242706c7730c031cf3a76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-controls"></a>Optimisation des performances : contrôles
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] intègre de nombreux composants d’interface utilisateur communs qui sont utilisés dans la plupart des applications Windows. Cette rubrique présente des techniques destinées à améliorer les performances de votre interface utilisateur.  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>Affichage de jeux de données volumineux  
 Contrôles WPF, tels que les <xref:System.Windows.Controls.ListView> et <xref:System.Windows.Controls.ComboBox> sont utilisées pour afficher des listes d’éléments dans une application. Si la liste à afficher est longue, les performances de l’application risquent de s’en être affectées. Cela s’explique par le fait que le système de disposition standard crée un conteneur de disposition pour chaque élément associé au contrôle de liste, puis calcule la taille et la position de sa disposition. En règle générale, vous n’avez pas besoin d’afficher tous les éléments en même temps ; il suffit en effet de n’en afficher qu’une partie et l’utilisateur parcourt la liste. Dans ce cas, il est judicieux d’utiliser la *virtualisation* de l’interface utilisateur : la génération du conteneur d’élément et le calcul de disposition associé d’un élément sont alors différés jusqu’à ce que cet élément soit visible.  
  
 La virtualisation de l’interface utilisateur est un aspect important des contrôles de liste. Il ne faut pas confondre la virtualisation de l’interface utilisateur et la virtualisation des données. La virtualisation de l’interface utilisateur ne stocke en mémoire que les éléments visibles, mais dans un scénario de liaison de données, elle stocke en mémoire l’ensemble de la structure de données. En revanche, dans le cas de la virtualisation des données, seuls sont stockées en mémoire les éléments de données qui sont visibles à l’écran.  
  
 Par défaut, la virtualisation de l’interface utilisateur est activée pour le <xref:System.Windows.Controls.ListView> et <xref:System.Windows.Controls.ListBox> contrôle lorsque leurs éléments de liste sont liés aux données. <xref:System.Windows.Controls.TreeView>la virtualisation peut être activée en définissant le <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> --> `IsVirtualizing` propriété attachée `true`. Si vous souhaitez activer la virtualisation de l’interface utilisateur pour les contrôles personnalisés qui dérivent de <xref:System.Windows.Controls.ItemsControl> ou les contrôles d’élément existants qui utilisent la <xref:System.Windows.Controls.StackPanel> class, telle que <xref:System.Windows.Controls.ComboBox>, vous pouvez définir le <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> à <xref:System.Windows.Controls.VirtualizingStackPanel> et définissez <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> à `true`. Vous risquez malheureusement de désactiver la virtualisation de l’interface utilisateur pour ces contrôles sans vous en rendre compte. Voici la liste des situations qui entraînent la désactivation de la virtualisation de l’interface utilisateur :  
  
-   Conteneurs d’éléments sont ajoutés directement à la <xref:System.Windows.Controls.ItemsControl>. Par exemple, si une application ajoute explicitement <xref:System.Windows.Controls.ListBoxItem> des objets sur un <xref:System.Windows.Controls.ListBox>, le <xref:System.Windows.Controls.ListBox> n’a pas été virtualiser le <xref:System.Windows.Controls.ListBoxItem> objets.  
  
-   Élément des conteneurs dans le <xref:System.Windows.Controls.ItemsControl> sont de types différents. Par exemple, un <xref:System.Windows.Controls.Menu> qui utilise <xref:System.Windows.Controls.Separator> objets ne peut pas implémenter le recyclage de conteneurs, car le <xref:System.Windows.Controls.Menu> contient des objets de type <xref:System.Windows.Controls.Separator> et <xref:System.Windows.Controls.MenuItem>.  
  
-   Paramètre <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> à `false`.  
  
-   Paramètre <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>--> `IsVirtualizing` à `false`.    
  
 Au moment de virtualiser des conteneurs d’éléments, il est important de déterminer si des informations d’état supplémentaire sont associées à un conteneur d’élément qui appartient à l’élément. Si tel est le cas, vous devez enregistrer l’état supplémentaire. Par exemple, vous pouvez avoir un élément contenu dans un <xref:System.Windows.Controls.Expander> contrôle et la <xref:System.Windows.Controls.Expander.IsExpanded%2A> état est lié au conteneur de l’élément et non à l’élément lui-même. Lorsque le conteneur est réutilisé pour un nouvel élément, la valeur actuelle de <xref:System.Windows.Controls.Expander.IsExpanded%2A> est utilisé pour le nouvel élément. En outre, l’ancien élément perd la bonne <xref:System.Windows.Controls.Expander.IsExpanded%2A> valeur.  
  
 Actuellement, aucun contrôle WPF n’offre une prise en charge intégrée de la virtualisation des données.  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>Recyclage de conteneurs  
 Optimise la virtualisation de l’interface utilisateur ajoutée dans le .NET Framework 3.5 SP1 pour les contrôles qui héritent de <xref:System.Windows.Controls.ItemsControl> est *recyclage de conteneurs* ce qui peut également améliorer les performances de défilement.  Lorsqu’un <xref:System.Windows.Controls.ItemsControl> que la virtualisation de l’interface utilisateur utilise est remplie, il crée un conteneur d’élément pour chaque élément qui défile dans la vue et détruit le conteneur d’élément pour chaque élément qui défile hors de l’affichage. *Recyclage de conteneurs* permet au contrôle de réutiliser les conteneurs d’éléments existants pour les différents éléments de données, afin que les conteneurs d’éléments ne sont pas constamment créés et détruits à mesure que l’utilisateur fait défiler le <xref:System.Windows.Controls.ItemsControl>. Vous pouvez choisir d’activer le recyclage en définissant le <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> propriété attachée <xref:System.Windows.Controls.VirtualizationMode.Recycling>.  
  
 N’importe quel <xref:System.Windows.Controls.ItemsControl> qui prend en charge la virtualisation peut utiliser le recyclage de conteneurs.  Pour obtenir un exemple d’activation du recyclage de conteneurs sur un <xref:System.Windows.Controls.ListBox>, consultez [améliorer les performances de défilement d’un contrôle ListBox](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>Prise en charge de la virtualisation bidirectionnelle  
 <xref:System.Windows.Controls.VirtualizingStackPanel>offre une prise en charge intégrée pour la virtualisation de l’interface utilisateur dans une direction, horizontalement ou verticalement. Si vous souhaitez utiliser la virtualisation bidirectionnelle pour vos contrôles, vous devez implémenter un panneau personnalisé qui étend la <xref:System.Windows.Controls.VirtualizingStackPanel> classe. Le <xref:System.Windows.Controls.VirtualizingStackPanel> classe expose des méthodes virtuelles telles que <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, et <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Ces méthodes virtuelles permettent de détecter une modification dans la partie visible d’une liste et de gérer en conséquence.  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>Optimisation des modèles  
 L’arborescence d’éléments visuels contient tous les éléments visuels d’une application.  Elle contient non seulement les objets directement créés, mais aussi les objets résultant d’une expansion de modèle.  Par exemple, lorsque vous créez un <xref:System.Windows.Controls.Button>, vous obtenez également <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> et <xref:System.Windows.Controls.ContentPresenter> objets dans l’arborescence d’éléments visuels.  Si vous n’avez pas optimisé vos modèles de contrôle, vous risquez de créer de nombreux objets superflus dans l’arborescence visuelle.   Pour plus d’informations sur l’arborescence d’éléments visuels, consultez [Vue d’ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>Défilement différé  
 Par défaut, quand l’utilisateur fait glisser le curseur d’une barre de défilement, l’affichage du contenu est mis à jour en permanence.  Si le défilement est lent dans votre contrôle, envisagez d’utiliser le défilement différé.  Le contenu n’est alors mis à jour qu’à partir du moment où l’utilisateur arrête de faire glisser le curseur.  
  
 Pour implémenter le défilement différé, affectez le <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> propriété `true`.  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>est une propriété jointe et peut être définie sur <xref:System.Windows.Controls.ScrollViewer> et n’importe quel contrôle ayant une <xref:System.Windows.Controls.ScrollViewer> dans son modèle de contrôle.  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>Contrôles qui implémentent des fonctionnalités de performances  
 Le tableau suivant répertorie les contrôles communs d’affichage de données et leur prise en charge des fonctionnalités de performances.  Pour plus d’informations sur l’activation de ces fonctionnalités, consultez les sections précédentes.  
  
|Contrôle|Virtualisation|Recyclage de conteneurs|Défilement différé|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|Peut être activé|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.ContextMenu>|Peut être activé|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.DocumentViewer>|Non disponible|Non disponible|Peut être activé|  
|<xref:System.Windows.Controls.ListBox>|Par défaut|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.ListView>|Par défaut|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.TreeView>|Peut être activé|Peut être activé|Peut être activé|  
|<xref:System.Windows.Controls.ToolBar>|Non disponible|Non disponible|Peut être activé|  
  
> [!NOTE]
>  Pour obtenir un exemple d’activation de la virtualisation et le recyclage de conteneurs sur un <xref:System.Windows.Controls.TreeView>, consultez [améliorer les performances d’un contrôle TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Disposition](../../../../docs/framework/wpf/advanced/layout.md)  
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Contrôles](../../../../docs/framework/wpf/controls/index.md)  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Procédure pas à pas : mise en cache de données d’application dans une application WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
