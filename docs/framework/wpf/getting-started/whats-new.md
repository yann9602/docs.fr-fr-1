---
title: "Nouveautés de WPF version 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
caps.latest.revision: "55"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4dc6a35a0ff8586b91ab7d74abc182fa6002f88
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="what39s-new-in-wpf-version-45"></a>Nouveautés de WPF version 4.5
<a name="introduction"></a>Cette rubrique contient des informations sur les fonctionnalités nouvelles et améliorées dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] version 4.5.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Contrôle de ruban](#ribbon_control)  
  
-   [Amélioration des performances lors de l’affichage de grands jeux de données groupées](#grouped_virtualization)  
  
-   [Nouvelles fonctionnalités destinées au VirtualizingPanel](#VirtualizingPanel)  
  
-   [Liaison aux propriétés statiques](#static_properties)  
  
-   [Accès aux collections sur les threads sans interface utilisateur](#xthread_access)  
  
-   [Validation des données de façon synchrone et asynchrone](#INotifyDataErrorInfo)  
  
-   [Mise à jour automatique de la source d’une liaison de données](#delay)  
  
-   [Liaison aux types qui implémentent ICustomTypeProvider](#ICustomTypeProvider)  
  
-   [Récupération des informations de liaison de données à partir d’une expression de liaison](#binding_state)  
  
-   [Vérification d’un objet DataContext valide](#DisconnectedSource)  
  
-   [Repositionnement des données au fur et à mesure du changement des valeurs des données (mise en forme active)](#live_shaping)  
  
-   [Amélioration de la prise en charge pour l’établissement d’une référence faible à un événement](#weak_event_pattern)  
  
-   [Nouvelles méthodes pour la classe Dispatcher](#async)  
  
-   [Extensions de balisage pour les événements](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Contrôle de ruban  
 WPF 4.5 est fourni avec un <xref:System.Windows.Controls.Ribbon.Ribbon> contrôle qui héberge une barre d’outils Accès rapide, Menu de l’Application et des onglets.  Pour plus d’informations, consultez l’article [Vue d’ensemble du ruban](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Amélioration des performances lors de l’affichage de grands jeux de données groupées  
 La virtualisation de l’interface utilisateur survient lorsqu’un sous-ensemble d’éléments d’interface utilisateur sont générés à partir d’un plus grand nombre d’éléments de données, selon les éléments visibles à l’écran. Le <xref:System.Windows.Controls.VirtualizingPanel> définit la <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> jointe de propriété qui permet la virtualisation de l’interface utilisateur pour les données groupées.  Pour plus d’informations sur le regroupement de données, consultez Comment : trier et grouper des données à l’aide d’une vue en XAML.  Pour plus d’informations sur la virtualisation des données groupées, consultez le <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> propriété jointe.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Nouvelles fonctionnalités destinées au VirtualizingPanel  
  
1.  Vous pouvez spécifier si un <xref:System.Windows.Controls.VirtualizingPanel>, telles que la <xref:System.Windows.Controls.VirtualizingStackPanel>, affiche des éléments partiels à l’aide de la <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> propriété jointe. Si <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> a la valeur <xref:System.Windows.Controls.ScrollUnit.Item>, la <xref:System.Windows.Controls.VirtualizingPanel> affiche uniquement les éléments qui sont complètement visibles. Si <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> a la valeur <xref:System.Windows.Controls.ScrollUnit.Pixel>, le <xref:System.Windows.Controls.VirtualizingPanel> peut afficher des éléments partiellement visibles.  
  
2.  Vous pouvez spécifier la taille du cache avant et après la fenêtre d’affichage lorsque la <xref:System.Windows.Controls.VirtualizingPanel> virtualise à l’aide de la <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> propriété jointe.  Le cache est la quantité d’espace au-dessus ou au-dessous de la fenêtre d’affichage dans laquelle les éléments ne sont pas virtualisés.  L’utilisation d’un cache pour éviter de générer des éléments d’interface utilisateur à mesure qu’ils défilent peut améliorer les performances. Le cache est alimenté à un niveau de priorité inférieure afin que l’application ne cesse pas de répondre lors de l’opération. Le <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> propriété détermine l’unité de mesure utilisée par <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Liaison aux propriétés statiques  
 Vous pouvez utiliser des propriétés statiques comme source d’une liaison de données. Le moteur de liaison de données reconnaît le changement de valeur d’une propriété lors du déclenchement d’un événement statique.  Par exemple, si la classe `SomeClass` définit une propriété statique appelée `MyProperty`, `SomeClass` peut définir un événement statique déclenché lorsque la valeur de `MyProperty` varie.  L’événement statique peut utiliser une des signatures suivantes.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Notez que dans le premier cas, la classe expose un événement statique nommé *PropertyName* `Changed` qui passe <xref:System.EventArgs> au gestionnaire d’événements.  Dans le second cas, la classe expose un événement statique nommé `StaticPropertyChanged` qui passe <xref:System.ComponentModel.PropertyChangedEventArgs> au gestionnaire d’événements. Une classe qui implémente la propriété statique peut choisir de déclencher des notifications de modification de propriété à l’aide d’une des deux méthodes.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Accès aux collections sur les threads sans interface utilisateur  
 WPF permet d’accéder et de modifier des collections de données sur des threads autres que celui qui a créé la collection.  Cela permet d’utiliser un thread d’arrière-plan pour recevoir des données provenant d’une source externe, comme une base de données et afficher les données sur le thread d’interface utilisateur.  En utilisant un autre thread pour modifier la collection, l’interface utilisateur reste réactive à une interaction utilisateur.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Validation des données de façon synchrone et asynchrone  
 Le <xref:System.ComponentModel.INotifyDataErrorInfo> interface permet des classes d’entité de données implémenter des règles de validation personnalisées et exposer des résultats de la validation de manière asynchrone. Cette interface prend également en charge les objets d’erreur personnalisés, plusieurs erreurs par propriété, les erreurs d’inter-propriétés et les erreurs au niveau de l’entité.  Pour plus d'informations, consultez <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Mise à jour automatique de la source d’une liaison de données  
 Si vous utilisez une liaison de données pour mettre à jour une source de données, vous pouvez utiliser le <xref:System.Windows.Data.BindingBase.Delay%2A> propriété pour spécifier un intervalle de temps à passer après les modifications des propriétés sur la cible avant les mises à jour de la source.  Par exemple, supposons que vous ayez un <xref:System.Windows.Controls.Slider> qui a son <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> bidirectionnelle des données de propriété lié à une propriété d’un objet de données et la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> est définie sur <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  Dans cet exemple, lorsque l’utilisateur déplace le <xref:System.Windows.Controls.Slider>, les mises à jour de la source pour chaque pixel qui le <xref:System.Windows.Controls.Slider> déplace.  L’objet source doit en général, la valeur du curseur uniquement lorsque le curseur du composant <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> arrête la modification.  Pour empêcher la mise à jour de la source de trop souvent, utilisez <xref:System.Windows.Data.BindingBase.Delay%2A> pour spécifier que la source de ne doit pas être mis à jour jusqu'à ce qu’une certaine quantité de temps est écoulé après le curseur cesse de se déplacer.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Liaison aux types qui implémentent ICustomTypeProvider  
 WPF prend en charge la liaison de données aux objets qui implémentent <xref:System.Reflection.ICustomTypeProvider>, également appelées types personnalisés.  Vous pouvez utiliser des types personnalisés dans les cas suivants.  
  
1.  Comme un <xref:System.Windows.PropertyPath> dans une liaison de données. Par exemple, le <xref:System.Windows.Data.Binding.Path%2A> propriété d’un <xref:System.Windows.Data.Binding> peut faire référence à une propriété d’un type personnalisé.  
  
2.  En tant que la valeur de la <xref:System.Windows.DataTemplate.DataType%2A> propriété.  
  
3.  En tant que type qui détermine les colonnes générées automatiquement dans un <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Récupération des informations de liaison de données à partir d’une expression de liaison  
 Dans certains cas, vous risquez d’obtenir le <xref:System.Windows.Data.BindingExpression> d’un <xref:System.Windows.Data.Binding> et avez besoin d’informations sur les objets source et cible de la liaison.  De nouvelles API ont été ajoutées pour vous permettre d’obtenir l’objet source ou cible ou la propriété associée.  Lorsque vous avez une <xref:System.Windows.Data.BindingExpression>, utiliser les API suivantes pour obtenir des informations sur la cible et source.  
  
|Pour trouver cette valeur de la liaison|Utilisez cette API|  
|---------------------------------------|------------------|  
|Objet cible|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Propriété cible|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Objet source|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Propriété source|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Si le <xref:System.Windows.Data.BindingExpression> appartient à un<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Le propriétaire d’un<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Vérification d’un objet DataContext valide  
 Il existe des cas où la <xref:System.Windows.FrameworkElement.DataContext%2A> d’un conteneur d’éléments dans un <xref:System.Windows.Controls.ItemsControl> est déconnecté.  Un conteneur d’élément est l’élément d’interface utilisateur qui affiche un élément dans un <xref:System.Windows.Controls.ItemsControl>.  Lorsqu’un <xref:System.Windows.Controls.ItemsControl> données n’est lié à une collection, un conteneur d’élément est généré pour chaque élément. Dans certains cas, les conteneurs d’éléments sont supprimés de l’arborescence d’éléments visuels. Sont de deux cas classiques où un conteneur d’élément est supprimé lorsqu’un élément est supprimé de la collection sous-jacente et lorsque la virtualisation est activée sur le <xref:System.Windows.Controls.ItemsControl>. Dans ce cas, le <xref:System.Windows.FrameworkElement.DataContext%2A> propriété du conteneur d’élément est fixée à l’objet de sentinelle qui est retourné par la <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> propriété statique.  Vous devez vérifier si le <xref:System.Windows.FrameworkElement.DataContext%2A> est égal à la <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> objet avant d’accéder à la <xref:System.Windows.FrameworkElement.DataContext%2A> d’un conteneur d’élément.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Repositionnement des données au fur et à mesure du changement des valeurs des données (mise en forme active)  
 Une collection de données peut être regroupée, triée ou filtrée. WPF 4.5 permet la réorganisation des données lorsque les données sont modifiées. Par exemple, supposons qu’une application utilise un <xref:System.Windows.Controls.DataGrid> pour répertorier dans un marché boursier et des stocks sont triés par valeur de stock. Si le tri dynamique est activé sur les stocks' <xref:System.Windows.Data.CollectionView>, position d’une action dans le <xref:System.Windows.Controls.DataGrid> se déplace lorsque la valeur de l’action devient supérieure ou valeur du stock inférieur à un autre.   Pour plus d’informations, consultez le <xref:System.ComponentModel.ICollectionViewLiveShaping> interface.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Amélioration de la prise en charge pour l’établissement d’une référence faible à un événement  
 L’implémentation du modèle d’événement faible est désormais plus facile car les abonnés aux événements peuvent y participer sans avoir à implémenter d’interface supplémentaire.  Le type générique <xref:System.Windows.WeakEventManager> classe permet également aux abonnés devant être inclus dans le modèle d’événement faible si dédiée <xref:System.Windows.WeakEventManager> n’existe pas d’un événement particulier.  Pour plus d’informations, consultez [Modèles d’événement faible](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Nouvelles méthodes pour la classe Dispatcher  
 La classe Dispatcher définit de nouvelles méthodes pour les opérations synchrones et asynchrones.  Synchrones <xref:System.Windows.Threading.Dispatcher.Invoke%2A> méthode définit des surcharges qui prennent un <xref:System.Action> ou <xref:System.Func%601> paramètre. La nouvelle méthode asynchrone, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, prend également un <xref:System.Action> ou <xref:System.Func%601> comme paramètre de rappel et retourne un <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>.   Le <xref:System.Windows.Threading.DispatcherOperation> et <xref:System.Windows.Threading.DispatcherOperation%601> classes définissent un <xref:System.Threading.Tasks.Task> propriété.  Lorsque vous appelez <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, vous pouvez utiliser la `await` mot clé avec l’option le <xref:System.Windows.Threading.DispatcherOperation> ou associé <xref:System.Threading.Tasks.Task>. Si vous avez besoin d’attente de façon synchrone de la <xref:System.Threading.Tasks.Task> qui est retourné par une <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, appelez le <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> méthode d’extension. Appel de <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> entraîne un blocage si l’opération est en attente sur un thread d’appel. Pour plus d’informations sur l’utilisation d’un <xref:System.Threading.Tasks.Task> pour effectuer des opérations asynchrones, consultez [parallélisme des tâches (bibliothèque parallèle de tâches)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Extensions de balisage pour les événements  
 WPF 4.5 prend en charge les extensions de balisage pour les événements.  Bien que WPF ne définisse pas d’extension de balisage à utiliser pour les événements, des tiers sont en mesure de créer une extension de balisage qui peut être utilisée avec les événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés dans le .NET Framework](../../../../docs/framework/whats-new/index.md)
