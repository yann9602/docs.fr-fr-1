---
title: "Vue d&#39;ensemble de la cr&#233;ation de contr&#244;les | Microsoft Docs"
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
  - "création de contrôles (vue d'ensemble)"
  - "contrôles, création (vue d'ensemble)"
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# Vue d&#39;ensemble de la cr&#233;ation de contr&#244;les
L'extensibilité du modèle de contrôle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] réduit considérablement le besoin de créer un contrôle.  Toutefois, vous serez parfois amené à devoir créer un contrôle personnalisé dans certains cas.  Cette rubrique traite des fonctionnalités qui limitent votre besoin de créer un contrôle personnalisé et des différents modèles de création de contrôle dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Cette rubrique montre également comment créer un nouveau contrôle.  
  
   
  
<a name="when_to_write_a_new_control"></a>   
## Alternatives à l'écriture d'un nouveau contrôle  
 Historiquement, si vous souhaitiez obtenir une expérience personnalisée à partir d'un contrôle existant, vous étiez limité à la modification des propriétés standards du contrôle, telles que la couleur d'arrière\-plan, la largeur de bordure et la taille de police.  Si vous souhaitiez étendre l'apparence ou le comportement d'un contrôle au\-delà de ces paramètres prédéfinis, vous deviez créer un contrôle, généralement via l'héritage d'un contrôle existant et la substitution de la méthode responsable du dessin du contrôle.  Bien que ce soit toujours possible, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de personnaliser des contrôles existants en utilisant son modèle, ses styles, ses modèles et ses déclencheurs au contenu riche.  La liste suivante propose des exemples d'utilisation de ces fonctionnalités pour créer des expériences personnalisées et cohérentes sans devoir créer un contrôle.  
  
-   **Contenu riche.** De nombreux contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standard prennent en charge le contenu riche.  Par exemple, la propriété de contenu d'un <xref:System.Windows.Controls.Button> est de type <xref:System.Object>, de sorte que, théoriquement, il est possible de tout afficher sur un <xref:System.Windows.Controls.Button>.  Si vous voulez qu'un bouton affiche une image et un texte, vous pouvez ajouter une image et un <xref:System.Windows.Controls.TextBlock> à un <xref:System.Windows.Controls.StackPanel> et assigner le <xref:System.Windows.Controls.StackPanel> à la propriété <xref:System.Windows.Controls.ContentControl.Content%2A>.  Comme les contrôles peuvent afficher des éléments visuels [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des données arbitraires, il est moins souvent nécessaire de créer un contrôle ou de modifier un contrôle existant pour prendre en charge une visualisation complexe.  Pour plus d'informations sur le modèle de contenu de <xref:System.Windows.Controls.Button> et d'autres modèles de contenu dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Modèle de contenu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
-   **Styles.** Un <xref:System.Windows.Style> est une collection de valeurs qui représentent les propriétés d'un contrôle.  L'utilisation de styles vous permet de créer une représentation réutilisable de l'apparence et du comportement souhaités d'un contrôle sans écrire un nouveau contrôle.  Par exemple, supposez que vous voulez que tous vos contrôles <xref:System.Windows.Controls.TextBlock> aient une police rouge, Arial, avec une taille de police de 14.  Vous pouvez créer un style en tant que ressource et définir les propriétés appropriées en conséquence.  Chaque <xref:System.Windows.Controls.TextBlock> que vous ajoutez à votre application a alors la même apparence.  
  
-   **Modèles de données.** Un <xref:System.Windows.DataTemplate> permet de personnaliser l'affichage des données sur un contrôle.  Vous pouvez par exemple utiliser un <xref:System.Windows.DataTemplate> pour définir l'affichage des données dans une <xref:System.Windows.Controls.ListBox>.  Pour obtenir un exemple, consultez [Vue d'ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md).  En plus de personnaliser l'apparence des données, un <xref:System.Windows.DataTemplate> peut inclure des éléments d'interface, ce qui vous offre une grande flexibilité dans les interfaces utilisateur personnalisées.  Par exemple, vous pouvez créer une <xref:System.Windows.Controls.ComboBox> dans laquelle chaque élément contient une case à cocher en utilisant un <xref:System.Windows.DataTemplate>.  
  
-   **Modèles de contrôle.** De nombreux contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisent un <xref:System.Windows.Controls.ControlTemplate> pour définir la structure et l'apparence de contrôle, qui sépare l'apparence d'un contrôle de ses fonctionnalités. Vous pouvez totalement modifier l'apparence d'un contrôle en redéfinissant son <xref:System.Windows.Controls.ControlTemplate>.  Imaginons par exemple que vous souhaitiez créer un contrôle ressemblant à un feu rouge.  Ce contrôle possède une interface utilisateur et des fonctionnalités simples.  Il est constitué de trois cercles, dont un seul peut être allumé à la fois.  Après quelques instants de réflexion, vous réalisez qu'une <xref:System.Windows.Controls.RadioButton> offre la possibilité d'effectuer une sélection unique. L'apparence par défaut de la <xref:System.Windows.Controls.RadioButton> ne ressemble toutefois en rien aux voyants d'un feu rouge.  Comme la <xref:System.Windows.Controls.RadioButton> utilise un modèle de contrôle pour définir son apparence, il est facile de redéfinir ce <xref:System.Windows.Controls.ControlTemplate> pour répondre aux exigences du contrôle et utiliser des cases d'option pour créer votre feu rouge.  
  
    > [!NOTE]
    >  Bien qu'une <xref:System.Windows.Controls.RadioButton> puisse utiliser un <xref:System.Windows.DataTemplate>, ce dernier ne suffit pas dans cet exemple.  Le <xref:System.Windows.DataTemplate> définit l'apparence du contenu d'un contrôle.  Dans le cas d'une <xref:System.Windows.Controls.RadioButton>, le contenu est l'élément qui apparaît à droite du cercle qui indique si la <xref:System.Windows.Controls.RadioButton> est sélectionnée.  Dans l'exemple du feu rouge, la case d'option doit juste être un cercle capable de "s'allumer". Comme l'apparence du feu rouge est très différente de l'apparence par défaut de la <xref:System.Windows.Controls.RadioButton>, il est nécessaire de redéfinir le <xref:System.Windows.Controls.ControlTemplate>.  En général, un <xref:System.Windows.DataTemplate> est utilisé pour définir le contenu \(ou les données\) d'un contrôle et un <xref:System.Windows.Controls.ControlTemplate> pour définir sa structure.  
  
-   **Déclencheurs.** Un <xref:System.Windows.Trigger> vous permet de modifier dynamiquement l'apparence et le comportement d'un contrôle sans créer de contrôle.  Par exemple, imaginons vous ayez plusieurs contrôles <xref:System.Windows.Controls.ListBox> dans votre application et souhaitiez que les éléments de chaque <xref:System.Windows.Controls.ListBox> apparaissent en caractères gras et rouges lorsqu'ils sont sélectionnés.  Votre premier réflexe vous dicte de créer une classe qui hérite de <xref:System.Windows.Controls.ListBox> et substitue la méthode <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> pour modifier l'apparence de l'élément sélectionné. La solution idéale consiste toutefois à ajouter un déclencheur à un style de <xref:System.Windows.Controls.ListBoxItem> qui modifie l'apparence de l'élément sélectionné.  Un déclencheur vous permet de modifier les valeurs des propriétés ou de prendre des mesures sur la base de la valeur d'une propriété.  Un <xref:System.Windows.EventTrigger> vous permet de prendre des mesures lorsqu'un événement se produit.  
  
 Pour plus d'informations sur les styles, les modèles et les déclencheurs, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 En règle générale, si votre contrôle reflète les fonctionnalités d'un contrôle existant, mais que vous souhaitez qu'il ait l'air différent, vous devez d'abord vous demander s'il est possible d'utiliser une des méthodes examinées de cette section pour modifier l'apparence du contrôle existant.  
  
<a name="models_for_control_authoring"></a>   
## Modèles pour création de contrôle  
 Le modèle de contenu riche, les styles, les modèles et les déclencheurs réduisent la nécessité de créer des contrôles.  Toutefois, si vous devez créer un contrôle, il est important de comprendre les différents modèles de création de contrôle proposés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. À cet effet, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propose trois modèles généraux offrant chacun un jeu de fonctionnalités et un niveau de flexibilité différent.  Les classes de base de ces trois modèles sont <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control> et <xref:System.Windows.FrameworkElement>.  
  
### Dériver de UserControl  
 La méthode la plus simple pour créer un contrôle dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à le dériver d'un <xref:System.Windows.Controls.UserControl>.  Lorsque vous générez un contrôle qui hérite de <xref:System.Windows.Controls.UserControl>, vous ajoutez des composants existants au <xref:System.Windows.Controls.UserControl>, nommez les composants et référencez les gestionnaires d'événements dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Vous pouvez ensuite référencer les éléments nommés et définir les gestionnaires d'événements dans le code.  Ce modèle de développement ressemble fortement au modèle utilisé pour le développement d'applications dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Si la génération s'est déroulée correctement, un <xref:System.Windows.Controls.UserControl> peut tirer parti des avantages d'un contenu riche, de styles et de déclencheurs.  Toutefois, si votre contrôle hérite de <xref:System.Windows.Controls.UserControl>, les personnes qui utilisent votre contrôle ne pourront pas utiliser un <xref:System.Windows.DataTemplate> ou un <xref:System.Windows.Controls.ControlTemplate> pour personnaliser son apparence.  Il est nécessaire de dériver à partir de la classe <xref:System.Windows.Controls.Control> ou d'une de ses classes dérivées \(autre que <xref:System.Windows.Controls.UserControl>\) pour créer un contrôle personnalisé qui prend en charge des modèles.  
  
#### Avantages de dériver de UserControl  
 Vous pouvez envisager de dériver de <xref:System.Windows.Controls.UserControl> si toutes les conditions suivantes s'appliquent :  
  
-   Vous voulez créer votre contrôle de la même manière que vous générez une application.  
  
-   Votre contrôle contient uniquement des composants existants.  
  
-   Vous n'avez pas besoin de prendre en charge une personnalisation complexe.  
  
### Dériver de Control  
 Dériver de la classe <xref:System.Windows.Controls.Control> est le modèle utilisé par la plupart des contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants.  Lorsque vous créez un contrôle qui hérite de la classe <xref:System.Windows.Controls.Control>, vous définissez son apparence à l'aide de modèles.  En agissant de la sorte, vous séparez la logique opérationnelle de la représentation visuelle.  Vous pouvez également garantir le découplage de l'interface utilisateur et de la logique en utilisant des commandes et des liaisons au lieu des événements et en évitant le plus possible de référencer les éléments dans le <xref:System.Windows.Controls.ControlTemplate>.  Si l'interface utilisateur et la logique de votre contrôle sont correctement découplées, un utilisateur de votre contrôle peut redéfinir son <xref:System.Windows.Controls.ControlTemplate> pour personnaliser son apparence. Bien que la génération d'un <xref:System.Windows.Controls.Control> personnalisé ne soit pas aussi simple que la génération d'un <xref:System.Windows.Controls.UserControl>, un <xref:System.Windows.Controls.Control> personnalisé fournit plus de flexibilité.  
  
#### Avantages de dériver de Control  
 Vous pouvez envisager de dériver de <xref:System.Windows.Controls.Control> au lieu d'utiliser la classe <xref:System.Windows.Controls.UserControl> lorsqu'une ou plusieurs des conditions suivantes s'appliquent :  
  
-   Vous voulez pouvoir personnaliser l'apparence de votre contrôle via le <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Vous souhaitez que votre contrôle prenne en charge des thèmes différents.  
  
### Dériver de FrameworkElement  
 Les contrôles qui dérivent de <xref:System.Windows.Controls.UserControl> ou de <xref:System.Windows.Controls.Control> reposent sur la composition d'éléments existants.  Cette solution est acceptable dans de nombreux scénarios, car tout objet héritant de <xref:System.Windows.FrameworkElement> peut appartenir à un <xref:System.Windows.Controls.ControlTemplate>.  Dans certains cas, l'apparence d'un contrôle requiert toutefois des fonctionnalités autres que celles de la composition d'éléments simples.  Pour ces scénarios, baser un composant sur <xref:System.Windows.FrameworkElement> est le bon choix.  
  
 Il existe deux méthodes standard pour générer des composants basés sur <xref:System.Windows.FrameworkElement> : le rendu direct et la composition d'éléments personnalisés.  Le rendu direct implique de substituer la méthode <xref:System.Windows.UIElement.OnRender%2A> de <xref:System.Windows.FrameworkElement> et de fournir des opérations <xref:System.Windows.Media.DrawingContext> qui définissent explicitement les visuels du composant.  C'est la méthode utilisée par <xref:System.Windows.Controls.Image> et <xref:System.Windows.Controls.Border>.  La composition d'éléments personnalisés implique l'utilisation d'objets de type <xref:System.Windows.Media.Visual> pour composer l'apparence du composant.  Pour obtenir un exemple, consultez [Utilisation d'objets DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  <xref:System.Windows.Controls.Primitives.Track> est un exemple de contrôle dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui utilise une composition d'éléments personnalisée.  Il est également possible de combiner le rendu direct et la composition d'éléments personnalisés au sein du même contrôle.  
  
#### Avantages de dériver de FrameworkElement  
 Vous pouvez envisager de dériver de <xref:System.Windows.FrameworkElement> dans l'un des cas suivants :  
  
-   Vous souhaitez avoir un contrôle précis sur l'apparence de votre contrôle allant au\-delà des fonctionnalités proposées par la composition d'éléments simples.  
  
-   Vous souhaitez définir l'apparence de votre contrôle en définissant votre propre logique de rendu.  
  
-   Vous souhaitez composer des éléments existants de manière innovante au delà de ce qui est possible avec <xref:System.Windows.Controls.UserControl> et <xref:System.Windows.Controls.Control>.  
  
<a name="control_authoring_basics"></a>   
## Notions de base de la création de contrôle  
 Comme expliqué précédemment, l'une des fonctionnalités les plus puissantes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est la possibilité d'aller au delà de la définition de propriétés de base d'un contrôle pour modifier son apparence et son comportement, tout en n'ayant toujours pas besoin de créer un contrôle personnalisé. Les styles, la liaison de données et les fonctionnalités du déclencheur sont rendus possibles par le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et le système d'événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Les sections suivantes décrivent certaines pratiques que vous devez respecter, indépendamment du modèle que vous utilisez pour créer le contrôle personnalisé, afin que les utilisateurs de votre contrôle personnalisé puissent utiliser ces fonctionnalités comme ils le feraient pour un contrôle inclus dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### Utiliser des propriétés de dépendance  
 Dans le cas d'une propriété de dépendance, il est possible d'effectuer les opérations suivantes :  
  
-   Définir la propriété dans un style.  
  
-   Lier la propriété à une source de données.  
  
-   Utiliser une ressource dynamique en tant que valeur de la propriété.  
  
-   Animer la propriété.  
  
 Si vous voulez qu'une propriété de votre contrôle prenne en charge l'une de ces fonctionnalités, vous devez l'implémenter en tant que propriété de dépendance.  L'exemple suivant montre comment définir une propriété de dépendance appelée `Value`.  
  
-   Définissez un identificateur <xref:System.Windows.DependencyProperty> nommé `ValueProperty` en tant que champ `public` `static` `readonly`.  
  
-   Enregistre le nom de la propriété avec le système de propriétés, en appelant <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=fullName>, afin de spécifier les éléments suivants :  
  
    -   le nom de la propriété ;  
  
    -   Type de la propriété.  
  
    -   le type propriétaire de la propriété ;  
  
    -   Les métadonnées de la propriété.  Les métadonnées contiennent la valeur par défaut de la propriété, un <xref:System.Windows.CoerceValueCallback> et un <xref:System.Windows.PropertyChangedCallback>.  
  
-   Définissez une propriété de wrapper [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nommée `Value`, qui est le nom utilisé pour enregistrer la propriété de dépendance, en implémentant les accesseurs `get` et `set` de la propriété.  Notez que les accesseurs `get` et `set` appellent uniquement <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>, respectivement.  Il est conseillé de ne pas inclure de logique supplémentaire dans les accesseurs de propriétés de dépendance car les clients et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peuvent ignorer les accesseurs et appeler directement <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>.  Par exemple, lorsqu'une propriété est liée à une source de données, l'accesseur `set` de la propriété n'est pas appelé.  Au lieu d'ajouter une logique supplémentaire aux accesseurs get et set, utilisez les délégués <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback> et <xref:System.Windows.PropertyChangedCallback> pour répondre ou vérifier la valeur lorsque celle\-ci change.  Pour plus d'informations sur ces rappels, consultez [Validation et rappels de propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Définissez une méthode pour le <xref:System.Windows.CoerceValueCallback>, nommée `CoerceValue`.  `CoerceValue` garantit que `Value` est supérieur ou égal à `MinValue` et inférieur ou égal à `MaxValue`.  
  
-   Définissez une méthode pour le <xref:System.Windows.PropertyChangedCallback>, nommée `OnValueChanged`.  `OnValueChanged` crée un objet <xref:System.Windows.RoutedPropertyChangedEventArgs%601> et se prépare à déclencher l'événement routé `ValueChanged`.  Les événements routés sont examinés dans la section suivante.  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 Pour plus d'informations, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### Utiliser RoutedEvents  
 De même que les [propriétés de dépendance](GTMT) étendent la notion de propriétés [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] avec des fonctionnalités supplémentaires, les [événements routés](GTMT) étendent la notion d'événements [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] standard.  Lorsque vous créez un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il est également conseillé d'implémenter votre événement sous forme d'événement routé car un tel événement prend en charge le comportement suivant :  
  
-   Les événements peuvent être gérés sur le parent de plusieurs contrôles.  Si un événement est un événement de propagation, un parent unique de l'arborescence d'éléments peut s'abonner à l'événement.  Les auteurs d'applications peuvent ensuite utiliser un gestionnaire unique pour répondre à l'événement de plusieurs contrôles.  Par exemple, si votre contrôle fait partie de chaque élément d'une <xref:System.Windows.Controls.ListBox> \(parce qu'il est inclus dans un <xref:System.Windows.DataTemplate>\), le développeur d'applications peut définir le gestionnaire de l'événement de votre contrôle sur la <xref:System.Windows.Controls.ListBox>.  Dans ce cas, chaque fois que l'événement se produit sur un des contrôles, le gestionnaire d'événements est appelé.  
  
-   Des événements routés peuvent être utilisés dans un <xref:System.Windows.EventSetter>, ce qui permet aux développeurs d'applications de spécifier le gestionnaire d'un événement dans un style.  
  
-   Il est possible d'utiliser des événements routés dans un <xref:System.Windows.EventTrigger>, ce qui est utile pour animer des propriétés à l'aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 L'exemple suivant montre comment définir un événement routé :  
  
-   Définissez un identificateur <xref:System.Windows.RoutedEvent> nommé `ValueChangedEvent` en tant que champ `public` `static` `readonly`.  
  
-   Enregistrez l'événement routé en appelant la méthode <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=fullName>.  L'exemple spécifie les informations suivantes lorsqu'il appelle <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> :  
  
    -   Le nom de l'événement est `ValueChanged`.  
  
    -   La stratégie de routage est <xref:System.Windows.RoutingStrategy>, ce qui signifie qu'un gestionnaire d'événements sur la source \(l'objet qui déclenche l'événement\) est appelé en premier, puis que les gestionnaires d'événements sur les éléments parents de la source sont appelés dans l'ordre, en commençant par le gestionnaire d'événements sur l'élément parent le plus proche.  
  
    -   Le type du gestionnaire d'événements est <xref:System.Windows.RoutedPropertyChangedEventHandler%601>, qui est construit avec un type <xref:System.Decimal>.  
  
    -   Le type propriétaire de l'événement est `NumericUpDown`.  
  
-   Déclarez un événement public nommé `ValueChanged` et incluez des déclarations d'accesseurs d'événement.  L'exemple appelle <xref:System.Windows.UIElement.AddHandler%2A> dans la déclaration d'accesseur `add` et <xref:System.Windows.UIElement.RemoveHandler%2A> dans la déclaration d'accesseur `remove` afin d'utiliser les services d'événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Créez une méthode virtuelle protégée nommée `OnValueChanged`, qui déclenche l'événement `ValueChanged`.  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 Pour plus d'informations, consultez [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md) et [Créer un événement routé personnalisé](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
### Utilisation de la liaison  
 Pour découpler l'interface utilisateur de votre contrôle de sa logique, pensez à utiliser la liaison de données.  C'est particulièrement important si vous définissez l'apparence de votre contrôle à l'aide d'un <xref:System.Windows.Controls.ControlTemplate>.  L'utilisation de la liaison de données permet d'éviter de référencer des parties spécifiques de l'interface utilisateur au départ du code.  Il est préférable d'éviter de référencer des éléments qui se trouvent dans le <xref:System.Windows.Controls.ControlTemplate> parce que lorsque le code référence des éléments présents dans le <xref:System.Windows.Controls.ControlTemplate> et que le <xref:System.Windows.Controls.ControlTemplate> est modifié, l'élément référencé doit être inclus dans le nouveau <xref:System.Windows.Controls.ControlTemplate>.  
  
 L'exemple suivant met à jour le <xref:System.Windows.Controls.TextBlock> du contrôle `NumericUpDown`, en lui assignant un nom et référençant la zone de texte dans le code par son nom.  
  
 [!code-xml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 L'exemple suivant utilise la liaison pour faire la même chose.  
  
 [!code-xml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 Pour plus d'informations sur la liaison de données, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
### Conception pour les concepteurs  
 Pour obtenir de l'aide pour les contrôles WPF personnalisés dans [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] \(par exemple, pour modifier des propriétés avec la fenêtre Propriétés\), suivez les indications ci\-après.  Pour plus d'informations sur le développement pour [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)], consultez [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26).  
  
#### Propriétés de dépendance  
 Veillez à implémenter des assesseurs `get` et `set` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] comme décrit précédemment dans la section « Utiliser des propriétés de dépendance ». Les concepteurs peuvent utiliser le wrapper pour détecter la présence d'une propriété de dépendance, mais, à l'instar de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des clients du contrôle, ils ne sont pas tenus d'appeler les accesseurs lors de l'obtention ou de la définition de la propriété.  
  
#### Propriétés jointes  
 Vous devez implémenter des propriétés attachées sur des contrôles personnalisés à l'aide des indications suivantes :  
  
-   Préparez une <xref:System.Windows.DependencyProperty> `public` `static` `readonly` de type *NomPropriété*`Property` créé à l'aide de l'une des méthodes <xref:System.Windows.DependencyProperty.RegisterAttached%2A>.  Le nom de propriété passé à <xref:System.Windows.DependencyProperty.RegisterAttached%2A> doit correspondre *à NomPropriété*.  
  
-   Implémentez deux méthodes `public` `static` CLR nommées `Set`*NomPropriété* et `Get`*NomPropriété*.  Les deux méthodes doivent accepter une classe dérivée de <xref:System.Windows.DependencyProperty> pour leur premier argument.  La méthode `Set`*NomPropriété* accepte également un argument dont le type correspond au type de données enregistré pour la propriété.  La méthode `Get`*NomPropriété* doit retourner une valeur du même type.  Si la méthode `Set`*NomPropriété* fait défaut, la propriété est marquée en lecture seule.  
  
-   `Set` *PropertyName* et `Get`*PropertyName* doivent router directement aux méthodes <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> sur l'objet de dépendance cible, respectivement.  Les concepteurs peuvent accéder à la propriété attachée en l'appelant via le wrapper de méthode ou lançant un appel direct à l'objet de dépendance cible.  
  
 Pour plus d'informations sur les propriétés attachées, consultez [Vue d'ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
### Définir et utiliser des ressources partagées  
 Vous pouvez inclure votre contrôle dans le même assembly que votre application, ou l'intégrer dans un assembly séparé qui peut être utilisé dans plusieurs applications.  Pour la plupart, les informations abordées dans cette rubrique sont valables, quelle que soit la méthode que vous utilisez.  Toutefois, il existe une différence notable.  Lorsque vous placez un contrôle dans le même assembly qu'une application, vous êtes libre d'ajouter des ressources globales au fichier App.xaml.  Cependant, un assembly qui ne contient que des contrôles n'est associé à aucun objet <xref:System.Windows.Application> et aucun fichier App.xaml n'est donc disponible.  
  
 Lorsqu'une application recherche une ressource, elle examine trois niveaux dans l'ordre suivant :  
  
1.  Niveau de l'élément.  
  
     Le système commence par l'élément qui référence la ressource, puis il passe en revue les ressources du parent logique, et ainsi de suite, jusqu'à atteindre l'élément racine ;  
  
2.  Niveau de l'application.  
  
     Ressources définies par l'objet <xref:System.Windows.Application> ;  
  
3.  Niveau du thème.  
  
     Les dictionnaires au niveau du thème sont enregistrés dans un sous\-dossier nommé Themes.  Les fichiers contenus dans ce dossier correspondent aux thèmes.  Par exemple, vous pouvez avoir Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml, etc.  Vous pouvez également avoir un fichier nommé generic.xaml.  Lorsque le système recherche une ressource au niveau des thèmes, il la cherche en premier lieu dans le fichier spécifique au thème puis dans generic.xaml.  
  
 Lorsque votre contrôle se trouve dans un assembly distinct de l'application, vous devez placer vos ressources globales au niveau de l'élément ou du thème.  Les deux méthodes ont leurs avantages.  
  
#### Définition de ressources au niveau de l'élément  
 Vous pouvez définir des ressources partagées au niveau de l'élément en créant un dictionnaire de ressources personnalisé et en le fusionnant avec le dictionnaire de ressources de votre contrôle.  Lorsque vous utilisez cette méthode, vous pouvez donner à votre fichier de ressources le nom de votre choix, et il peut se trouver dans le même dossier que vos contrôles.  Les ressources au niveau de l'élément peuvent également utiliser des chaînes simples comme clés.  L'exemple suivant crée un fichier de ressources <xref:System.Windows.Media.LinearGradientBrush> nommé Dictionary1.xaml.  
  
 [!code-xml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 Une fois que vous avez défini votre dictionnaire, vous devez le fusionner avec le dictionnaire de ressources de votre contrôle.  Pour ce faire, vous pouvez utiliser le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code.  
  
 L'exemple suivant fusionne un dictionnaire de ressources à l'aide du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 L'inconvénient de cette approche réside dans le fait qu'un objet <xref:System.Windows.ResourceDictionary> est créé chaque fois que vous le référencez.  Par exemple, si vous avez dix contrôles personnalisés dans votre bibliothèque et fusionnez les dictionnaires de ressources partagées pour chaque contrôle en utilisant le XAML, vous créez 10 objets <xref:System.Windows.ResourceDictionary> identiques.  Vous pouvez éviter ceci en créant une classe statique qui fusionne les ressources dans le code et retourne le <xref:System.Windows.ResourceDictionary> résultant.  
  
 L'exemple de code suivant crée une classe qui retourne un <xref:System.Windows.ResourceDictionary> partagé.  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 L'exemple suivant fusionne la ressource partagée avec les ressources d'un contrôle personnalisé dans le constructeur du contrôle avant d'appeler `InitilizeComponent`.  `SharedDictionaryManager.SharedDictionary` étant une propriété statique, le <xref:System.Windows.ResourceDictionary> n'est créé qu'une seule fois.  Comme le dictionnaire de ressources a été fusionné avant l'appel de `InitializeComponent`, les ressources sont mises à la disposition du contrôle dans son fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### Définition de ressources au niveau du thème  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permet de créer des ressources pour les différents thèmes Windows.  En tant qu'auteur du contrôle, vous pouvez définir une ressource pour un thème spécifique afin de modifier l'apparence de votre contrôle selon le thème utilisé.  Par exemple, l'apparence d'un <xref:System.Windows.Controls.Button> dans le thème Windows Classic \(thème par défaut de Windows 2000\) diffère de celle d'un <xref:System.Windows.Controls.Button> avec le thème Windows Luna \(thème par défaut de Windows XP\) parce que le <xref:System.Windows.Controls.Button> utilise un <xref:System.Windows.Controls.ControlTemplate> différent pour chaque thème.  
  
 Les ressources spécifiques à un thème sont conservées dans un dictionnaire de ressources avec un nom de fichier spécifique.  Ces fichiers doivent se trouver dans un dossier nommé `Themes`, dépendant du dossier qui contient le contrôle.  Le tableau suivant répertorie les fichiers des dictionnaires de ressources et le thème associé à chaque fichier :  
  
|Nom de fichier du dictionnaire de ressources|Thème de Windows|  
|--------------------------------------------------|----------------------|  
|`Classic.xaml`|Aspect habituel de Windows 9x\/2000 sous Windows XP|  
|`Luna.NormalColor.xaml`|Thème bleu par défaut sous Windows XP|  
|`Luna.Homestead.xaml`|Thème vert olive sur Windows XP|  
|`Luna.Metallic.xaml`|Thème argent sur Windows XP|  
|`Royale.NormalColor.xaml`|Thème par défaut sous Windows XP Édition Media Center|  
|`Aero.NormalColor.xaml`|Thème par défaut sous Windows Vista|  
  
 Il n'est pas nécessaire de définir une ressource pour chaque thème.  Si une ressource n'est pas définie pour un thème spécifique, le contrôle vérifie `Classic.xaml` pour la ressource.  Si la ressource n'est pas définie dans le fichier correspondant au thème actuel ou dans `Classic.xaml`, le contrôle utilise la ressource générique, qui se trouve dans un fichier de dictionnaire de ressources nommé `generic.xaml`.  Le fichier `generic.xaml` se trouve dans le même dossier que les fichiers de dictionnaire de ressources spécifiques au thème.  Bien que `generic.xaml` ne corresponde pas à un thème spécifique de Windows, il s'agit néanmoins d'un dictionnaire au niveau du thème.  
  
 [Contrôle personnalisé NumericUpDown avec exemple de thème et de prise en charge d'UI Automation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160025) contient deux dictionnaires de ressources pour le contrôle `NumericUpDown` : l'un dans generic.xaml et l'autre dans Luna.NormalColor.xaml.  Vous pouvez exécuter l'application et basculer entre le thème Argent de Windows XP et un autre thème afin de voir la différence entre les deux modèles de contrôle.  \(Si vous travaillez sous Windows Vista, vous pouvez renommer Luna.NormalColor.xaml en Aero.NormalColor.xaml et basculer entre deux thèmes, tels que Windows Classic et le thème par défaut de Windows Vista.\)  
  
 Lorsque vous placez un <xref:System.Windows.Controls.ControlTemplate> dans l'un des fichiers de dictionnaire de ressources spécifiques au thème, vous devez créer un constructeur statique pour votre contrôle et appeler la méthode <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> de la <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, comme illustré dans l'exemple suivant.  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### Définition et référencement de clés pour les ressources de thème  
 Lorsque vous définissez une ressource au niveau de l'élément, vous pouvez assigner une chaîne comme clé et accéder à la ressource via la chaîne.  Lorsque vous définissez une ressource au niveau du thème, vous devez utiliser une <xref:System.Windows.ComponentResourceKey> comme clé.  L'exemple suivant définit une ressource dans generic.xaml.  
  
  
  
 L'exemple suivant référence la ressource en spécifiant la <xref:System.Windows.ComponentResourceKey> comme clé.  
  
  
  
##### Spécification de l'emplacement des ressources spécifiques aux thèmes  
 Pour rechercher les ressources relatives à un contrôle, l'application d'hébergement doit savoir quel l'assembly contient des ressources spécifiques au contrôle.  Pour ce faire, vous pouvez ajouter le <xref:System.Windows.ThemeInfoAttribute> à l'assembly qui contient le contrôle.  Le <xref:System.Windows.ThemeInfoAttribute> comporte une propriété <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> qui spécifie l'emplacement des ressources génériques, et une propriété <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> qui spécifie l'emplacement des ressources spécifiques au thème.  
  
 L'exemple suivant affecte aux propriétés <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> et <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> la valeur <xref:System.Windows.ResourceDictionaryLocation>, pour spécifier que les ressources génériques et spécifiques au thème se trouvent dans le même assembly que le contrôle.  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## Voir aussi  
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [URI à en\-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)   
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)