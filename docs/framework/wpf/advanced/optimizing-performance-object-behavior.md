---
title: "Optimisation des performances : comportement d'objets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12c4dc202ac4db2c21b0a45b61608f5c03c24ac9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-object-behavior"></a>Optimisation des performances : comportement d'objets
Une bonne compréhension du comportement intrinsèque des objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de choisir le bon compromis entre fonctionnalités et performances.  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Le fait de ne pas supprimer les gestionnaires d’événements sur les objets permet de conserver les objets actifs  
 Le délégué qu’un objet passe à son événement est une référence à cet objet. Par conséquent, les gestionnaires d’événements peuvent conserver les objets actifs plus longtemps que prévu. Quand vous nettoyez un objet inscrit pour détecter l’événement d’un objet, il est essentiel de supprimer ce délégué avant de libérer l’objet. La conservation d’objets actifs inutiles augmente l’utilisation de mémoire de l’application. Cela est particulièrement vrai quand l’objet est la racine d’une arborescence logique ou d’une arborescence de visuels.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] introduit un modèle de détecteur d’événements faibles qui peut être utile quand les relations de durée de vie d’objet entre la source et l’écouteur sont difficiles à suivre. Certains événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants utilisent ce modèle. Si vous implémentez des objets avec des événements personnalisés, ce modèle peut vous être utile. Pour plus d’informations, consultez [Modèles d’événement faible](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
 Il existe plusieurs outils, comme le profileur CLR et la visionneuse de jeux de travail, qui peuvent fournir des informations sur l’utilisation de mémoire d’un processus spécifié. Le profileur CLR inclut un nombre de vues très utiles du profil d’allocation, notamment un histogramme des types alloués, des graphiques d’allocation et d’appels, une chronologie montrant les opérations de garbage collection de diverses générations et l’état obtenu du tas managé après ces collections, ainsi qu’une arborescence des appels présentant les allocations par méthode et les chargements d’assembly. Pour plus d’informations, consultez le [Centre de développement .NET Framework](http://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Propriétés de dépendance et objets  
 En règle générale, l’accès à une propriété de dépendance d’un <xref:System.Windows.DependencyObject> n’est pas inférieure à celle de l’accès à un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriété. Même si l’on constate une légère baisse des performances lors de la définition d’une valeur de propriété, l’obtention d’une valeur est aussi rapide que l’obtention de la valeur d’une propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. La légère baisse des performances s’explique par le fait que les propriétés de dépendance prennent en charge des fonctionnalités robustes, comme la liaison de données, l’animation, l’héritage et les styles. Pour plus d’informations, consultez [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optimisations de DependencyProperty  
 Vous devez soigneusement définir les propriétés de dépendance dans votre application. Si votre <xref:System.Windows.DependencyProperty> affecte uniquement afficher les options de métadonnées de type, plutôt que d’autres options de métadonnées telles que <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, vous devez la marquer en tant que tel en substituant ses métadonnées. Pour plus d’informations sur la substitution ou l’obtention de métadonnées de propriété, consultez [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Il peut être plus efficace d’avoir un gestionnaire de changement de propriété qui invalide manuellement les passes de mesure, d’organisation et d’affichage si tous les changements de propriété n’affectent pas réellement la mesure, l’organisation et l’affichage. Par exemple, vous pouvez décider de réafficher un arrière-plan uniquement quand une valeur est supérieure à une limite définie. Dans ce cas, votre gestionnaire de changement de propriété invalide l’affichage uniquement quand la valeur dépasse la limite définie.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Rendre une propriété de dépendance héritable n’est pas gratuit  
 Par défaut, les propriétés de dépendance inscrites ne sont pas héritables. Toutefois, vous pouvez explicitement rendre une propriété héritable. Bien qu’il s’agisse d’une fonctionnalité utile, la conversion d’une propriété pour qu’elle soit héritable affecte les performances en augmentant la durée d’invalidation de la propriété.  
  
### <a name="use-registerclasshandler-carefully"></a>Utiliser RegisterClassHandler avec précaution  
 Lors de l’appel <xref:System.Windows.EventManager.RegisterClassHandler%2A> vous permet d’enregistrer l’état de votre instance, il est important de savoir que le gestionnaire est appelé sur chaque instance, ce qui peut entraîner des problèmes de performances. Utilisez uniquement <xref:System.Windows.EventManager.RegisterClassHandler%2A> lorsque votre application nécessite que vous enregistrez votre état de l’instance.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Définir la valeur par défaut d’une propriété DependencyProperty pendant l’inscription  
 Lors de la création un <xref:System.Windows.DependencyProperty> qui requiert une valeur par défaut, définissez la valeur à l’aide de métadonnées par défaut passées en tant que paramètre à la <xref:System.Windows.DependencyProperty.Register%2A> méthode de la <xref:System.Windows.DependencyProperty>. Utilisez cette technique au lieu de définir la valeur de propriété dans un constructeur ou sur chaque instance d’un élément.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Définir la valeur PropertyMetadata à l’aide du Registre  
 Lorsque vous créez un <xref:System.Windows.DependencyProperty>, vous avez la possibilité de définir la <xref:System.Windows.PropertyMetadata> à l’aide la <xref:System.Windows.DependencyProperty.Register%2A> ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> méthodes. Bien que votre objet peut avoir un constructeur statique à appeler <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, cela n’est pas la solution optimale et aura un impact sur les performances. Pour de meilleures performances, définissez la <xref:System.Windows.PropertyMetadata> lors de l’appel à <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Objets Freezable  
 A <xref:System.Windows.Freezable> est un type spécial d’objet qui a deux états : figé et non figé. Le fait de figer les objets chaque fois que cela est possible améliore les performances de votre application et réduit son jeu de travail. Pour plus d’informations, consultez [Vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Chaque <xref:System.Windows.Freezable> a un <xref:System.Windows.Freezable.Changed> événement est déclenché chaque fois qu’il change. Toutefois, les notifications de changement détériorent les performances de l’application.  
  
 Prenons l’exemple suivant dans lequel chaque <xref:System.Windows.Shapes.Rectangle> utilise le même <xref:System.Windows.Media.Brush> objet :  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un gestionnaire d’événements pour le <xref:System.Windows.Media.SolidColorBrush> l’objet <xref:System.Windows.Freezable.Changed> événement afin d’invalider la <xref:System.Windows.Shapes.Rectangle> l’objet <xref:System.Windows.Shapes.Shape.Fill%2A> propriété. Dans ce cas, chaque fois que le <xref:System.Windows.Media.SolidColorBrush> doit déclencher son <xref:System.Windows.Freezable.Changed> événement, il est nécessaire pour appeler la fonction de rappel pour chaque <xref:System.Windows.Shapes.Rectangle>— l’accumulation de ces appels de fonction de rappel impose une baisse significative des performances. Par ailleurs, l’ajout et la suppression des gestionnaires à ce stade consomment une grande part des performances, car cette opération oblige l’application à parcourir l’intégralité de la liste. Si votre scénario d’application ne change jamais le <xref:System.Windows.Media.SolidColorBrush>, vous paierez le coût de maintenance <xref:System.Windows.Freezable.Changed> gestionnaires d’événements inutilement.  
  
 Figer un <xref:System.Windows.Freezable> peut améliorer ses performances, car il n’a plus besoin d’étendre des ressources sur la gestion des notifications de modification. Le tableau ci-dessous indique la taille d’un simple <xref:System.Windows.Media.SolidColorBrush> lors de son <xref:System.Windows.Freezable.IsFrozen%2A> est définie sur `true`, par rapport à quand il n’est pas. Cela suppose que l’application d’un pinceau pour le <xref:System.Windows.Shapes.Shape.Fill%2A> propriété dix <xref:System.Windows.Shapes.Rectangle> objets.  
  
|**État**|**Taille**|  
|---------------|--------------|  
|Figé<xref:System.Windows.Media.SolidColorBrush>|212 octets|  
|Non figée<xref:System.Windows.Media.SolidColorBrush>|972 octets|  
  
 L'exemple de code suivant illustre ce concept :  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Les gestionnaires de changement sur des Freezables non figés peuvent conserver les objets actifs  
 Le délégué qu’un objet passe à un <xref:System.Windows.Freezable> l’objet <xref:System.Windows.Freezable.Changed> événement est effectivement une référence à cet objet. Par conséquent, <xref:System.Windows.Freezable.Changed> gestionnaires d’événements peuvent conserver des objets actifs plus longtemps que prévu. Lorsque vous effectuez un nettoyage d’un objet qui a inscrit pour écouter un <xref:System.Windows.Freezable> l’objet <xref:System.Windows.Freezable.Changed> événement, il est essentiel de supprimer ce délégué avant de libérer l’objet.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]raccorde également <xref:System.Windows.Freezable.Changed> événements en interne. Par exemple, toutes les propriétés de dépendance qui prennent <xref:System.Windows.Freezable> comme une valeur écoute <xref:System.Windows.Freezable.Changed> événements automatiquement. Le <xref:System.Windows.Shapes.Shape.Fill%2A> propriété, qui prend un <xref:System.Windows.Media.Brush>, illustre ce concept.  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Sur l’affectation de `myBrush` à `myRectangle.Fill`, un délégué pointant vers le <xref:System.Windows.Shapes.Rectangle> objet sera ajouté à la <xref:System.Windows.Media.SolidColorBrush> l’objet <xref:System.Windows.Freezable.Changed> événement. Cela signifie que le code suivant ne rend pas `myRect` éligible pour l’opération de garbage collection :  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Dans ce cas `myBrush` maintien `myRectangle` actif et rappelle il lorsqu’il se déclenche son <xref:System.Windows.Freezable.Changed> événement. Notez que l’assignation `myBrush` à la <xref:System.Windows.Shapes.Shape.Fill%2A> propriété d’un nouveau <xref:System.Windows.Shapes.Rectangle> ajoutera simplement un autre gestionnaire d’événements à `myBrush`.  
  
 La méthode recommandée pour nettoyer ces types d’objets consiste à supprimer la <xref:System.Windows.Media.Brush> à partir de la <xref:System.Windows.Shapes.Shape.Fill%2A> propriété, qui à son tour supprimera le <xref:System.Windows.Freezable.Changed> Gestionnaire d’événements.  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualisation de l'interface utilisateur  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit également une variante de la <xref:System.Windows.Controls.StackPanel> élément qui « virtualise » automatiquement le contenu enfant lié aux données. Dans ce contexte, le mot virtualiser fait référence à une technique par laquelle une partie des objets est généré à partir d’un plus grand nombre d’éléments de données en fonction des éléments visibles à l’écran. La génération d’un grand nombre d’éléments d’interface utilisateur, alors que seul un certain nombre de ces éléments peut figurer à l’écran à un moment donné, entraîne une utilisation intensive de la mémoire et du processeur. <xref:System.Windows.Controls.VirtualizingStackPanel>(via la fonctionnalité fournie par <xref:System.Windows.Controls.VirtualizingPanel>) calcule les éléments visibles et utilise le <xref:System.Windows.Controls.ItemContainerGenerator> à partir d’un <xref:System.Windows.Controls.ItemsControl> (tel que <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ListView>) pour créer uniquement des éléments pour les éléments visibles.  
  
 Pour optimiser les performances, des objets visuels pour ces éléments sont générés ou maintenus actifs uniquement s’ils sont visibles à l’écran. Quand ils ne sont plus dans la zone visible du contrôle, les objets visuels peuvent être supprimés. Cette virtualisation ne doit pas être confondue avec la virtualisation des données, où les objets de données ne sont pas tous présents dans la collection locale, mais diffusés selon les besoins.  
  
 Le tableau ci-dessous indique le temps écoulé, ajout et rendu 5000 <xref:System.Windows.Controls.TextBlock> éléments à un <xref:System.Windows.Controls.StackPanel> et un <xref:System.Windows.Controls.VirtualizingStackPanel>. Dans ce scénario, les mesures représentent le temps entre l’attachement d’une chaîne de texte à la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété d’un <xref:System.Windows.Controls.ItemsControl> objet au moment où les éléments du Panneau de configuration affichent la chaîne de texte.  
  
|**Panneau hôte**|**Durée d’affichage (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
