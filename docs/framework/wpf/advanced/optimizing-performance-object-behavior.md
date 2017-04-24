---
title: "Optimisation des performances&#160;: comportement d&#39;objets | Microsoft Docs"
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
  - "propriétés de dépendance, performances"
  - "gestionnaires d'événements (WPF)"
  - "objets Freezable, performances"
  - "considérations sur les performances des objets"
  - "virtualisation de l'interface utilisateur"
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Optimisation des performances&#160;: comportement d&#39;objets
Le fait de bien comprendre le comportement intrinsèque des objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous aidera à effectuer les bons compromis entre fonctionnalités et performances.  
  
   
  
<a name="Not_Removing_Event_Handlers"></a>   
## Le fait de ne pas supprimer les gestionnaires d'événements sur des objets peut conserver des objets actifs  
 Le délégué qu'un objet passe à son événement est effectivement une référence à cet objet.  Par conséquent, les gestionnaires d'événements peuvent conserver des objets actifs plus longtemps que prévu.  Lorsque vous effectuez un nettoyage d'un objet qui s'est inscrit pour se mettre à l'écoute de l'événement d'un objet, il est essentiel de supprimer ce délégué avant de libérer l'objet.  Le fait de conserver des objets inutiles en activité augmente l'utilisation de la mémoire de l'application.  Ceci est particulièrement vrai lorsque l'objet est la racine d'une [arborescence logique](GTMT) ou d'une [arborescence visuelle](GTMT).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] introduit un modèle d'écouteur d'événements faible pour les événements qui peut être utile dans les situations où les relations de durée de vie des objets entre la source et l'écouteur sont difficiles à suivre.  Certains événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants utilisent ce modèle.  Si vous implémentez des objets avec des événements personnalisés, vous trouverez peut\-être ce modèle pratique.  Pour plus d'informations, consultez [Modèles d'événement faible](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
 Il existe plusieurs outils, par exemple le profileur CLR et la visionneuse de jeu de travail \(Working Set Viewer\), qui peuvent fournir des informations sur l'utilisation de la mémoire d'un processus spécifié.  Le profileur CLR inclut un certain nombre de vues très utiles concernant le profil d'allocation, notamment un histogramme des types alloués, des graphiques d'allocation et d'appels, une chronologie montrant les opérations de garbage collection de diverses générations et l'état obtenu en résultat du tas managé après ces collections, ainsi qu'une arborescence d'appels illustrant les allocations par méthode et les chargements d'assemblys.  Pour plus d'informations, consultez [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## Propriétés de dépendance et objets  
 En général, l'accès à une [propriété de dépendance](GTMT) d'un <xref:System.Windows.DependencyObject> n'est pas plus lent que celui d'une propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  S'il y a une baisse de performances liée à la définition d'une valeur de propriété, l'obtention d'une valeur est aussi rapide que l'obtention de la valeur d'une propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  En compensation de la légère baisse des performances, les [propriétés de dépendance](GTMT) prennent en charge de puissantes fonctionnalités, comme la liaison des données, l'animation, l'héritage et les styles.  Pour plus d'informations, consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
### Optimisations de DependencyProperty  
 Vous devez définir les [propriétés de dépendance](GTMT) dans votre application très attentivement.  Si votre <xref:System.Windows.DependencyProperty> affecte uniquement des options de métadonnées de type rendu, et non pas les autres options de métadonnées telles que <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, vous devez l'indiquer en substituant ses métadonnées.  Pour plus d'informations sur la substitution ou l'obtention de métadonnées de propriétés, consultez [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Il peut être plus efficace d'avoir un gestionnaire de changement de propriétés qui invalide les passes de mesure, d'organisation et de rendu manuellement, sinon tous les changements de propriétés affecteront en fait les options de mesure, d'organisation et de rendu.  Par exemple, vous pouvez décider de réafficher un arrière\-plan uniquement quand une valeur est supérieure à une limite définie.  Dans ce cas, votre gestionnaire de changements de propriétés risque d'invalider uniquement le rendu quand la valeur dépasse la limite définie.  
  
### Rendre une DependencyProperty héritable n'est pas gratuit  
 Par défaut, les [propriétés de dépendance](GTMT) sont non héritables.  Cependant, vous pouvez rendre explicitement héritable toute propriété.  S'il s'agit d'une fonction utile, la conversion d'une propriété pour la rendre héritable a un impact sur les performances car cela augmente la durée d'invalidation de la propriété.  
  
### Utiliser attentivement RegisterClassHandler  
 Si le fait d'appeler <xref:System.Windows.EventManager.RegisterClassHandler%2A> vous permet d'enregistrer l'état de votre instance, il est important de savoir que le gestionnaire est appelé sur chaque instance, ce qui peut générer des problèmes de performance.  Utilisez <xref:System.Windows.EventManager.RegisterClassHandler%2A> uniquement quand votre application exige l'enregistrement de votre état d'instance.  
  
### Définir la valeur par défaut d'une DependencyProperty pendant l'enregistrement  
 Lorsque vous créez une <xref:System.Windows.DependencyProperty> qui nécessite une valeur par défaut, définissez la valeur à l'aide des métadonnées par défaut passées en tant que paramètres à la méthode <xref:System.Windows.DependencyProperty.Register%2A> de la <xref:System.Windows.DependencyProperty>.  Utilisez cette technique au lieu de définir la valeur de la propriété dans un constructeur ou sur chaque instance d'un élément.  
  
### Définir la valeur de PropertyMetadata à l'aide du Registre  
 Lorsque vous créez une <xref:System.Windows.DependencyProperty>, vous avez la possibilité de définir la <xref:System.Windows.PropertyMetadata> en utilisant les méthodes <xref:System.Windows.DependencyProperty.Register%2A> ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.  Bien que votre objet puisse avoir un constructeur statique pour appeler <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, ceci n'est pas la solution optimale et aura un impact sur les performances.  Pour optimiser les performances, définissez <xref:System.Windows.PropertyMetadata> pendant l'appel à <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## Objets Freezable  
 Un <xref:System.Windows.Freezable> est un type d'objet spécial qui possède deux états : figé et non figé.  Le fait de figer les objets chaque fois que possible améliore les performances de votre application et réduit son jeu de travail.  Pour plus d'informations, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Chaque <xref:System.Windows.Freezable> possède un événement <xref:System.Windows.Freezable.Changed> qui est généré à chaque changement.  Cependant, les notifications de changement sont coûteuses en termes de performances de l'application.  
  
 Examinez l'exemple suivant dans lequel chaque <xref:System.Windows.Shapes.Rectangle> utilise le même objet <xref:System.Windows.Media.Brush> :  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un gestionnaire d'événements pour l'événement <xref:System.Windows.Freezable.Changed> de l'objet <xref:System.Windows.Media.SolidColorBrush> afin d'invalider la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de l'objet <xref:System.Windows.Shapes.Rectangle>.  Dans ce cas, chaque fois que le <xref:System.Windows.Media.SolidColorBrush> doit déclencher son événement <xref:System.Windows.Freezable.Changed>,  il doit appeler la fonction de rappel pour chaque <xref:System.Windows.Shapes.Rectangle>— l'accumulation de ces appels de fonctions de rappel impose une sensible baisse de performances.  En plus, il est bon en terme de performances d'ajouter et de supprimer des gestionnaires à ce stade dans la mesure où l'application aurait à parcourir toute la liste pour le faire.  Si votre scénario d'application ne change jamais <xref:System.Windows.Media.SolidColorBrush>, vous paierez le coût du maintien de gestionnaires d'événements non nécessaires <xref:System.Windows.Freezable.Changed>.  
  
 Le fait de figer un objet <xref:System.Windows.Freezable> peut améliorer sa performance, car il n'a plus besoin d'étendre des ressources pour maintenir des notifications de changement.  Le tableau ci\-dessous montre la taille d'un simple <xref:System.Windows.Media.SolidColorBrush> quand sa propriété <xref:System.Windows.Freezable.IsFrozen%2A> a la valeur `true`, par rapport à quand elle ne l'a pas.  Cela suppose l'application d'un pinceau à la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de dix objets <xref:System.Windows.Shapes.Rectangle>.  
  
|**État**|**Taille**|  
|--------------|----------------|  
|Figé <xref:System.Windows.Media.SolidColorBrush>|212 octets|  
|Non figé <xref:System.Windows.Media.SolidColorBrush>|972 octets|  
  
 L'exemple de code suivant illustre ce concept :  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### Les gestionnaires modifiés sur des Freezables non figés peuvent conserver des objets actifs  
 Le délégué qu'un objet passe à un événement <xref:System.Windows.Freezable.Changed> d'un objet <xref:System.Windows.Freezable> est effectivement une référence à cet objet.  Par conséquent, les gestionnaires d'événements <xref:System.Windows.Freezable.Changed> peuvent conserver des objets actifs plus longtemps que prévu.  Lorsque vous effectuez un nettoyage d'un objet qui s'est inscrit pour se mettre à l'écoute de l'événement <xref:System.Windows.Freezable> d'un objet <xref:System.Windows.Freezable.Changed>, il est essentiel de supprimer ce délégué avant de libérer l'objet.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] connecte également les événements <xref:System.Windows.Freezable.Changed> en interne.  Par exemple, toutes les [propriétés de dépendance](GTMT) qui prennent <xref:System.Windows.Freezable> en tant que valeur écouteront automatiquement les événements <xref:System.Windows.Freezable.Changed>.  La propriété <xref:System.Windows.Shapes.Shape.Fill%2A>, qui prend un <xref:System.Windows.Media.Brush>, illustre ce concept.  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Lors de l'affectation de `myBrush` à `myRectangle.Fill`, un délégué pointant en arrière vers l'objet <xref:System.Windows.Shapes.Rectangle> sera ajouté à l'événement <xref:System.Windows.Freezable.Changed> de l'objet <xref:System.Windows.Media.SolidColorBrush>.  Cela signifie que le fait de suivre le code ne qualifie pas en fait `myRect` pour une opération de garbage collection :  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Dans ce cas `myBrush` maintien `myRectangle` actif et le rappellera lorsqu'il déclenchera son événement <xref:System.Windows.Freezable.Changed>.  Le fait d'affecter `myBrush` à la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> d'un nouveau <xref:System.Windows.Shapes.Rectangle> ne fera qu'ajouter un gestionnaire d'événements à `myBrush`.  
  
 La méthode recommandée pour nettoyer ces types d'objets est de supprimer le <xref:System.Windows.Media.Brush> de la propriété <xref:System.Windows.Shapes.Shape.Fill%2A>, qui à son tour supprimera le gestionnaire d'événements <xref:System.Windows.Freezable.Changed>.  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## Virtualisation de l'interface utilisateur  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également une variante de l'élément <xref:System.Windows.Controls.StackPanel> qui « virtualise » automatiquement du contenu enfant lié aux données.  Dans ce contexte, le mot « virtualiser » fait référence à une technique par laquelle un sous\-ensemble d'objets est généré à partir d'un plus grand nombre d'éléments de données, sur la base des éléments qui sont visibles à l'écran.  Générer un grand nombre d'éléments de l'interface utilisateur, alors que seuls un certain nombre d'entre eux peuvent être visibles sur l'écran à un moment donné, provoque une utilisation intensive de la mémoire et du processeur.  <xref:System.Windows.Controls.VirtualizingStackPanel> \(via la fonctionnalité fournie par <xref:System.Windows.Controls.VirtualizingPanel>\) calcule les éléments visibles et utilise <xref:System.Windows.Controls.ItemContainerGenerator> à partir d'un <xref:System.Windows.Controls.ItemsControl> \(tel que <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ListView>\) pour créer uniquement des éléments pour des éléments visibles.  
  
 En guise d'optimisation de performances, les objets visuels pour ces éléments sont uniquement générés ou maintenus actifs s'ils sont visibles à l'écran.  Quand ils ne sont plus dans la zone visualisable du contrôle, les objets visuels peuvent être supprimés.  Cette situation ne doit pas confondue avec la virtualisation des données, où les objets de données ne sont pas du tout présents dans la collection locale – mais plutôt transmis selon les besoins.  
  
 Le tableau ci\-dessous montre le temps passé à ajouter et à afficher les 5 000 éléments <xref:System.Windows.Controls.TextBlock> pour un <xref:System.Windows.Controls.StackPanel> et un <xref:System.Windows.Controls.VirtualizingStackPanel>.  Dans ce scénario, les mesures représentent le temps entre l'attachement d'une chaîne texte à la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> d'un objet <xref:System.Windows.Controls.ItemsControl> au moment où les éléments du panneau affichent la chaîne de texte.  
  
|**Panneau hôte**|**Restituer l'heure \(ms\)**|  
|----------------------|----------------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)