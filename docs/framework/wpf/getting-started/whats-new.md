---
title: "Nouveaut&#233;s de WPF version&#160;4.5 | Microsoft Docs"
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
  - "Windows Presentation Foundation, nouveautés"
  - "WPF, nouveautés"
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
caps.latest.revision: 55
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 55
---
# Nouveaut&#233;s de WPF version&#160;4.5
<a name="introduction"></a> Cette rubrique contient les informations sur les fonctionnalités nouvelles et améliorées dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], version 4.5.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Contrôle du ruban](#ribbon_control)  
  
-   [Performances améliorées en affichant de grands groupes de données groupées](#grouped_virtualization)  
  
-   [Nouvelles fonctionnalités pour le VirtualizingPanel](#VirtualizingPanel)  
  
-   [Lier aux propriétés statiques](#static_properties)  
  
-   [Collections de accès sur les threads non interface utilisateur](#xthread_access)  
  
-   [De façon synchrone et de façon asynchrone la validation des données](#INotifyDataErrorInfo)  
  
-   [Mettre à jour automatiquement la source d'une liaison de données](#delay)  
  
-   [Lier aux types qui implémentent ICustomTypeProvider](#ICustomTypeProvider)  
  
-   [Les informations de liaison de récupération des données d'une expression de liaison](#binding_state)  
  
-   [Vérification un objet valide du DataContext](#DisconnectedSource)  
  
-   [En repositionnant les données sous forme de valeurs de données modifiez \(façonner actif\)](#live_shaping)  
  
-   [Prise en charge améliorée pour établir une référence faible à un événement](#weak_event_pattern)  
  
-   [Nouvelles méthodes de la classe de répartiteur](#async)  
  
-   [Extensions de balisage pour les événements](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## Contrôle du ruban  
 Les fourni pour WPF 4,5 avec <xref:System.Windows.Controls.Ribbon.Ribbon> contrôle qui héberge une Barre d'outils Accès rapide, un menu application, les onglets et.  Pour plus d’informations, voir [Vue d'ensemble du ruban](../Topic/Ribbon%20Overview.md).  
  
<a name="grouped_virtualization"></a>   
## Performances améliorées en affichant de grands groupes de données groupées  
 La virtualisation de l'interface utilisateur se produit lorsqu'un sous\-ensemble d'éléments de l'interface utilisateur \(UI\) est généré à partir d'un plus grand nombre d'éléments de données selon lequel les éléments sont visibles à l'écran.  <xref:System.Windows.Controls.VirtualizingPanel> définit la propriété attachée d' <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> qui active la virtualisation de l'interface utilisateur pour les données groupées.  Pour plus d'informations sur les données de regroupement, consultez procédure : Tri et données du groupe utilisation d'une vue en XAML.  Pour plus d'informations sur virtualiser les données groupées, consultez la propriété attachée d' <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> .  
  
<a name="VirtualizingPanel"></a>   
## Nouvelles fonctionnalités pour le VirtualizingPanel  
  
1.  Vous pouvez spécifier si <xref:System.Windows.Controls.VirtualizingPanel>, tel qu' <xref:System.Windows.Controls.VirtualizingStackPanel>, affiche les éléments partiel à l'aide de la propriété attachée d' <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> .  Si <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> a la valeur <xref:System.Windows.Controls.ScrollUnit>, <xref:System.Windows.Controls.VirtualizingPanel> affiche uniquement les éléments qui sont intégralement visibles.  Si <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> a la valeur <xref:System.Windows.Controls.ScrollUnit>, <xref:System.Windows.Controls.VirtualizingPanel> peut afficher les éléments partiellement visibles.  
  
2.  Vous pouvez spécifier la taille du cache avant et après la fenêtre d'affichage lorsque <xref:System.Windows.Controls.VirtualizingPanel> virtualise à l'aide de la propriété attachée d' <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> .  Le cache est la quantité d'espace au\-dessus ou en\-dessous de la fenêtre d'affichage dans lequel les éléments ne sont pas virtualisés.  À l'aide d'un cache éviter de générer des éléments d'interface utilisateur tels qu'ils sont l'objet d'un défilement dans l'affichage peut améliorer les performances.  Le cache est rempli à une priorité plus faible afin que l'application ne soit pas répond pas pendant l'exécution.  La propriété d' <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=fullName> détermine l'unité de mesure utilisée par <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=fullName>.  
  
<a name="static_properties"></a>   
## Lier aux propriétés statiques  
 Vous pouvez utiliser les propriétés statiques comme source d'une liaison de données.  Le moteur de liaison de données identifie lorsque la valeur de propriété change si un événement statique est déclenché.  Par exemple, si la classe `SomeClass` définit une propriété statique appelée `MyProperty`, `SomeClass` peut définir un événement statique qui est déclenché lorsque la valeur d' `MyProperty` change.  l'événement statique peut utiliser l'un ou l'autre des signatures suivantes.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Notez que dans le premier cas, le expose un événement de classe statique nommé *PropertyName*`Changed` qui passe <xref:System.EventArgs> au gestionnaire d'événements.  Dans le deuxième cas, la classe expose un événement statique nommé `StaticPropertyChanged` qui passe <xref:System.ComponentModel.PropertyChangedEventArgs> au gestionnaire d'événements.  Une classe qui implémente la propriété statique peut choisir de déclenchement de notifications de modifications de propriétés à l'aide de l'un ou l'autre de méthode.  
  
<a name="xthread_access"></a>   
## Collections de accès sur les threads non interface utilisateur  
 WPF vous permet d'accéder et modifier à des collections de données sur des threads autres que celui qui a créé la collection.  Cela vous permet d'utiliser un thread d'arrière\-plan pour recevoir les données d'une source externe, telle qu'une base de données, et affiche les données sur le thread d'interface utilisateur.  À l'aide d'un autre thread pour modifier la collection, votre interface utilisateur reste sensible à l'intervention de l'utilisateur.  
  
<a name="INotifyDataErrorInfo"></a>   
## De façon synchrone et de façon asynchrone la validation des données  
 L'interface d' <xref:System.ComponentModel.INotifyDataErrorInfo> permet aux classes d'entité de données d'implémenter des règles de validation personnalisées et d'exposer les résultats de la validation de façon asynchrone.  Cette interface prend également en charge les objets personnalisés d'erreur, plusieurs erreurs par propriété, les erreurs entre propriété, et les erreurs d'entité\- niveau.  Pour plus d’informations, consultez <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## Mettre à jour automatiquement la source d'une liaison de données  
 Si vous utilisez une liaison de données pour mettre à jour une source de données, vous pouvez utiliser la propriété d' <xref:System.Windows.Data.BindingBase.Delay%2A> pour spécifier une durée à exécuter lorsque la propriété change sur la cible avant que les mises à jour de la source.  Par exemple, supposez que vous avez <xref:System.Windows.Controls.Slider> qui possède sa limite bidirectionnelle de données de propriété d' <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> à une propriété d'un objet de données et la propriété d' <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> a la valeur <xref:System.Windows.Data.UpdateSourceTrigger>.  Dans cet exemple, lorsque l'utilisateur déplace <xref:System.Windows.Controls.Slider>, les mises à jour de la source de chaque pixel qu' <xref:System.Windows.Controls.Slider> déplace.  L'objet source requiert généralement de la valeur du curseur uniquement lorsque <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> du curseur arrête de modifier.  Pour empêcher mettre à jour la source trop souvent, utilisez <xref:System.Windows.Data.BindingBase.Delay%2A> de spécifier que la source ne doit pas être mise à jour jusqu'à ce que les exécutions de temps après curseur de défilement cesse de se déplacer.  
  
<a name="ICustomTypeProvider"></a>   
## Lier aux types qui implémentent ICustomTypeProvider  
 WPF prend en charge la liaison de données aux objets qui implémentent <xref:System.Reflection.ICustomTypeProvider>, également appelés types personnalisés.  Vous pouvez utiliser personnalisé dans les cas suivants.  
  
1.  Comme <xref:System.Windows.PropertyPath> dans la liaison de données.  Par exemple, la propriété d' <xref:System.Windows.Data.Binding.Path%2A> d' <xref:System.Windows.Data.Binding> peut référencer une propriété d'un type personnalisé.  
  
2.  Comme valeur de la propriété d' <xref:System.Windows.DataTemplate.DataType%2A> .  
  
3.  Comme type qui détermine les colonnes générées automatiquement dans <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## Les informations de liaison de récupération des données d'une expression de liaison  
 Dans certains cas, vous pouvez obtenir <xref:System.Windows.Data.BindingExpression> d' <xref:System.Windows.Data.Binding> et avoir besoin d'informations sur la source et des objets cibles de liaison.  De nouvelles API ont été ajoutées pour vous permettre d'obtenir la source ou l'objet cible ou la propriété associée.  Lorsque vous avez <xref:System.Windows.Data.BindingExpression>, utilisez les API suivantes pour obtenir des informations sur la cible et la source.  
  
|Pour rechercher la valeur de la liaison|Utilisez cette API|  
|---------------------------------------------|------------------------|  
|l'objet cible|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=fullName>|  
|La propriété cible|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=fullName>|  
|l'objet source|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=fullName>|  
|La propriété source|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=fullName>|  
|Si <xref:System.Windows.Data.BindingExpression> appartient à <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=fullName>|  
|Le propriétaire d' <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## Vérification un objet valide du DataContext  
 Dans certains cas où <xref:System.Windows.FrameworkElement.DataContext%2A> d'un conteneur d'élément dans <xref:System.Windows.Controls.ItemsControl> est déconnecté.  Un conteneur d'élément est l'élément d'interface utilisateur qui affiche un élément dans <xref:System.Windows.Controls.ItemsControl>.  Lorsque <xref:System.Windows.Controls.ItemsControl> est lié aux données à une collection, un conteneur d'élément est généré pour chaque élément.  Dans certains cas, les conteneurs d'élément sont supprimés de l'arborescence d'éléments visuels.  Deux cas typiques où un conteneur d'élément est supprimé sont lorsqu'un élément est supprimé de la collection sous\-jacente et lorsque la virtualisation est activée sur <xref:System.Windows.Controls.ItemsControl>.  Dans ces cas, la propriété d' <xref:System.Windows.FrameworkElement.DataContext%2A> du conteneur d'élément sera placée à l'objet de sentinelle retourné par la propriété statique d' <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=fullName> .  Vous devez vérifier si <xref:System.Windows.FrameworkElement.DataContext%2A> est égal à l'objet d' <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> avant d'accéder à <xref:System.Windows.FrameworkElement.DataContext%2A> d'un conteneur d'élément.  
  
<a name="live_shaping"></a>   
## En repositionnant les données sous forme de valeurs de données modifiez \(façonner actif\)  
 Une collection de données peut être regroupés, triée, ou filtré.  WPF 4,5 permet aux données d'être organisées lorsque les données sont modifiées.  Par exemple, supposons qu'une application utilise <xref:System.Windows.Controls.DataGrid> pour répertorier les actions sur un marché boursier et les actions sont triées par valeur stock.  Si le tri actif est activé sur <xref:System.Windows.Data.CollectionView>des actions, la position des actions dans <xref:System.Windows.Controls.DataGrid> place lorsque la valeur des actions est supérieure ou inférieure à la valeur des autres actions.  Pour plus d'informations, consultez l'interface <xref:System.ComponentModel.ICollectionViewLiveShaping>.  
  
<a name="weak_event_pattern"></a>   
## Prise en charge améliorée pour établir une référence faible à un événement  
 Implémenter le modèle d'événement faible est maintenant plus facile car les abonnés aux événements peuvent participer à lui sans implémenter une interface supplémentaire.  La classe générique d' <xref:System.Windows.WeakEventManager> permet également aux abonnés de participer au modèle d'événement faible si <xref:System.Windows.WeakEventManager> dédié n'existe pour un événement.  Pour plus d’informations, consultez [Modèles d'événement faible](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## Nouvelles méthodes de la classe de répartiteur  
 La classe de répartiteur définit de nouvelles méthodes pour synchrone et les opérations asynchrones.  La méthode synchrone d' <xref:System.Windows.Threading.Dispatcher.Invoke%2A> définit des surcharges qui acceptent un paramètre d' <xref:System.Action> ou d' <xref:System.Func%601> .  La nouvelle méthode asynchrone, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, prend également <xref:System.Action> ou <xref:System.Func%601> comme paramètre de rappel et retourne <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>.  Les classes d' <xref:System.Windows.Threading.DispatcherOperation> et d' <xref:System.Windows.Threading.DispatcherOperation%601> définissent une propriété d' <xref:System.Threading.Tasks.Task> .  Lorsque vous appelez <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, vous pouvez utiliser le mot clé d' `await` avec <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Threading.Tasks.Task>associé.  Si vous devez attendre de façon synchrone <xref:System.Threading.Tasks.Task> retourné par <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, appelez la méthode d'extension d' <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> .  Appeler <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName> entraîne un interblocage si l'opération est mise en file d'attente sur un thread appelant.  Pour plus d'informations sur l'utilisation <xref:System.Threading.Tasks.Task> pour exécuter des opérations asynchrones, consultez [Parallélisme des tâches \(bibliothèque parallèle de tâches\)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## Extensions de balisage pour les événements  
 Extensions de balisage de charge WPF 4,5 pour les événements.  Lorsque WPF ne définit pas d'extension de balisage à utiliser pour les événements, des tiers peuvent créer une extension de balisage qui peut être utilisée avec des événements.  
  
## Voir aussi  
 [Nouveautés dans le .NET Framework](../../../../docs/framework/whats-new/index.md)