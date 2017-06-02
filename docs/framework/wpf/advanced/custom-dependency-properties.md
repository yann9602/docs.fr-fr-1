---
title: "Propri&#233;t&#233;s de d&#233;pendance personnalis&#233;es | Microsoft Docs"
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
  - "propriétés de dépendance personnalisées"
  - "propriétés de dépendance, personnalisé"
  - "implémenter, wrappers"
  - "métadonnées, pour des propriétés"
  - "propriétés, métadonnées"
  - "propriétés, inscrire"
  - "inscrire des propriétés"
  - "wrappers, implémenter"
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Propri&#233;t&#233;s de d&#233;pendance personnalis&#233;es
Cette rubrique décrit les situations dans lesquelles les développeurs d'applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et auteurs de composants doivent créer une [propriété de dépendance](GTMT) personnalisée et elle explique les étapes d'implémentation et les options d'implémentation qui peuvent améliorer les performances, l'utilisation ou la souplesse de la propriété.  
  
   
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous maîtrisez les propriétés de dépendance du point de vue d'un consommateur de propriétés de dépendance existantes dans les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et que vous avez lu la rubrique [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Pour pouvoir suivre les exemples dans cette rubrique, vous devez également maîtriser le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et savoir écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="whatis"></a>   
## Qu'est\-ce qu'une propriété de dépendance ?  
 Vous pouvez activer une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] pour prendre en charge le style, la liaison de données, l'héritage, les animations et les valeurs par défaut en l'implémentant sous la forme d'une [propriété de dépendance](GTMT).  Les propriétés de dépendance sont des propriétés enregistrées avec le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en appelant la méthode <xref:System.Windows.DependencyProperty.Register%2A> \(ou <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>\), et qui sont stockées par un champ d'identificateur <xref:System.Windows.DependencyProperty>.  Les propriétés de dépendance peuvent être utilisées uniquement par les types <xref:System.Windows.DependencyObject>, mais <xref:System.Windows.DependencyObject> elles se trouvent dans un niveau supérieur de la hiérarchie des classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], et la majorité des classes disponibles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut donc prendre en charge des propriétés de dépendance.  Pour plus d'informations sur les propriétés de dépendance et certains termes et conventions utilisés pour les décrire dans ce [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="example_dp"></a>   
## Exemples de propriétés de dépendance  
 Les exemples des propriétés de dépendance implémentés dans les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] incluent la propriété <xref:System.Windows.Controls.Control.Background%2A>, la propriété <xref:System.Windows.FrameworkElement.Width%2A> et la propriété <xref:System.Windows.Controls.TextBox.Text%2A>, entre autres.  Chaque propriété de dépendance exposée par une classe a un champ statique public correspondant de type <xref:System.Windows.DependencyProperty> exposé dans cette même classe. Il s'agit de l'identificateur de la propriété de dépendance.  L'identificateur est nommé à l'aide d'une convention : nom de la [propriété de dépendance](GTMT) avec la chaîne `Property` qui lui est ajoutée.  Par exemple, le champ d'identificateur <xref:System.Windows.DependencyProperty> correspondant pour la propriété <xref:System.Windows.Controls.Control.Background%2A> est <xref:System.Windows.Controls.Control.BackgroundProperty>.  L'identificateur stocke les informations sur la [propriété de dépendance](GTMT) telle qu'elle a été enregistrée et l'identificateur est ensuite utilisé dans d'autres opérations impliquant la [propriété](GTMT), tel que l'appel <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
 Comme indiqué dans [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md), toutes les propriétés de dépendance dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \(sauf la plupart des [propriétés jointes](GTMT)\) sont également des propriétés [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] du fait de l'implémentation de « wrappers ».  Par conséquent, vous pouvez obtenir des propriétés de dépendance ou en définir en appelant des accesseurs [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] qui définissent les wrappers de la même manière que vous utiliseriez d'autres propriétés [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  En tant que consommateur de propriétés de dépendance établies, vous n'utilisez généralement pas les méthodes <xref:System.Windows.DependencyObject><xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>, qui sont le point de connexion au système de propriétés sous\-jacent.  L'implémentation existante des propriétés [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] aura plutôt déjà appelée <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> dans les implémentations de wrappers `get` et `set` de la propriété, à l'aide du champ d'identificateur de manière appropriée.  Si vous implémentez une propriété de dépendance personnalisée vous\-même, vous définirez le wrapper d'une manière similaire.  
  
<a name="backing_with_dp"></a>   
## Quand implémenter une propriété de dépendance ?  
 Lorsque vous implémentez une propriété dans une classe, si la classe dérive de <xref:System.Windows.DependencyObject>, vous avez la possibilité de stocker la propriété avec un identificateur <xref:System.Windows.DependencyProperty> et donc de la convertir en propriété de dépendance.  Convertir la propriété en propriété de dépendance n'est pas toujours nécessaire ou approprié ; cela dépend de vos besoins.  Quelquefois, la technique type consistant à stocker la propriété avec un champ privé est adéquate.  Toutefois, vous devez implémenter la propriété sous la forme d'une [propriété de dépendance](GTMT) chaque fois que vous souhaitez que votre propriété prenne en charge une ou plusieurs des fonctions [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivantes :  
  
-   Vous souhaitez que votre propriété soit définissable dans un style.  Pour plus d'informations, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
-   Vous souhaitez que votre propriété prenne en charge la liaison de données.  Pour plus d'informations sur les propriétés de dépendance de liaison de données, consultez [Lier les propriétés de deux contrôles](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).  
  
-   Vous souhaitez que votre propriété soit définissable avec une référence à une ressource dynamique.  Pour plus d'informations, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Vous souhaitez hériter automatiquement d'une valeur de propriété d'un élément parent dans l'arborescence d'éléments.  Dans ce cas, inscrivez la propriété avec la méthode <xref:System.Windows.DependencyProperty.RegisterAttached%2A>, même si vous créez également un wrapper de propriété pour l'accès [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  Pour plus d'informations, consultez [Héritage de la valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Vous souhaitez que votre propriété puisse être animée.  Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Vous souhaitez que le système de propriétés signale la modification de la valeur précédente de la propriété par des actions prises par le système de propriétés, l'environnement ou l'utilisateur ou en lisant et en utilisant des styles.  En utilisant des métadonnées de propriété, votre propriété peut spécifier une méthode de rappel qui sera appelée chaque fois que le système de propriétés détermine que la valeur de la propriété a été modifiée définitivement.  Un concept connexe est la contrainte de valeur de propriété.  Pour plus d'informations, consultez [Validation et rappels de propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Vous souhaitez utiliser des conventions de métadonnées établies qui sont également utilisées par des processus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], comme pour signaler si la modification de la valeur d'une propriété implique que le système de disposition recompose les effets visuels d'un élément.  Ou bien, vous souhaitez pouvoir utiliser des substitutions de métadonnées afin que les classes dérivées puissent modifier des caractéristiques basées sur les métadonnées, telles que la valeur par défaut.  
  
-   Vous souhaitez que les propriétés d'un contrôle personnalisé bénéficient de la prise en charge du [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] de [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], telle que l'édition de la fenêtre **Propriétés**.  Pour plus d'informations, consultez [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Lorsque vous examinez ces scénarios, vous devez également déterminer si vous pouvez accomplir votre scénario en substituant les métadonnées d'une [propriété de dépendance](GTMT) existante, plutôt qu'implémenter une toute nouvelle propriété.  L'intérêt d'une substitution de métadonnées dépend de votre scénario et de la similarité du scénario par rapport à l'implémentation dans les propriétés de dépendance et les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existantes.  Pour plus d'informations sur la substitution des métadonnées dans les propriétés existantes, consultez [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="checklist"></a>   
## Liste de contrôle pour définir une propriété de dépendance  
 La définition d'une propriété de dépendance repose sur quatre concepts distincts.  Ces concepts ne sont pas des étapes procédurales nécessairement strictes, car certains d'entre eux finissent pas être combinés dans des lignes uniques du code dans l'implémentation :  
  
-   \(Facultatif\) Créez les métadonnées de la propriété de dépendance.  
  
-   Inscrivez le nom de propriété avec le système de propriétés en spécifiant un type de propriétaire et le type de la valeur de la propriété.  Spécifiez également les métadonnées de propriété, si elles sont utilisées.  
  
-   Définissez un identificateur <xref:System.Windows.DependencyProperty> sous la forme d'un champ `public``static``readonly` dans le type de propriétaire.  
  
-   Définissez une propriété de « wrapper » [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dont le nom correspond au nom de la propriété de dépendance.  Implémentez les accesseurs `get` et `set` de la propriété de « wrapper » [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] pour que la connexion à la propriété de dépendance qui la stocke ait lieu.  
  
<a name="registering"></a>   
### Inscription de la propriété avec le système de propriétés.  
 Pour que votre propriété soit une [propriété de dépendance](GTMT), vous devez inscrire cette propriété dans une table gérée par le système de propriétés et lui donner un identificateur unique utilisé comme qualificateur pour les opérations de système de propriétés ultérieures.  Ces opérations peuvent être des opérations internes ou votre propre code qui appelle le système de propriétés [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].  Pour inscrire la propriété, vous appelez la méthode <xref:System.Windows.DependencyProperty.Register%2A> dans le corps de votre classe \(à l'intérieur de la classe, mais en dehors de toutes les définitions de membres\).  Le champ d'identificateur est également fourni par l'appel de méthode <xref:System.Windows.DependencyProperty.Register%2A>, comme valeur de retour.  L'appel <xref:System.Windows.DependencyProperty.Register%2A> est effectué en dehors des autres définitions de membres, car vous utilisez cette valeur de retour pour assigner et créer un champ `public` `static` `readonly` de type <xref:System.Windows.DependencyProperty> dans le cadre de votre classe.  Ce champ devient l'identificateur de votre propriété de dépendance.  
  
 [!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
 [!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]  
  
<a name="nameconventions"></a>   
### Conventions d'attribution de nom des propriétés de dépendance  
 Il existe des conventions d'attribution de noms propres aux propriétés de dépendance, que vous devez respecter dans tous les cas, sauf dans des cas exceptionnels.  
  
 La propriété de dépendance elle\-même aura un nom de base, "AquariumGraphic" comme dans cet exemple, donné comme premier paramètre de <xref:System.Windows.DependencyProperty.Register%2A>.  Ce nom doit être unique dans chaque type d'inscription.  Les propriétés de dépendance héritées à travers des types de base sont considérées faire déjà partie du type d'inscription ; les noms des propriétés héritées ne peuvent plus être inscrits.  Toutefois, il existe une technique pour ajouter une classe comme propriétaire d'une propriété de dépendance, même lorsque cette propriété de dépendance n'est pas héritée. Pour plus d'informations, consultez [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Lorsque vous créez le champ d'identificateur, nommez ce champ en utilisant le nom de la propriété que vous avez inscrit et le suffixe `Property`.  Ce champ est votre identificateur pour la propriété de dépendance, et il sera utilisé ultérieurement comme une entrée pour les appels <xref:System.Windows.DependencyObject.SetValue%2A> et <xref:System.Windows.DependencyObject.GetValue%2A> que vous ferez dans les wrappers, par tout autre accès de code à la propriété par votre propre code, par un accès de code externe que vous autorisez, par le système de propriétés et éventuellement par les processeurs [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
> [!NOTE]
>  La définition de la propriété de dépendance dans le corps de classe est l'implémentation type, mais vous pouvez également définir une propriété de dépendance dans le constructeur statique de classe.  Cette approche peut avoir un sens si vous avez besoin de plusieurs lignes de code pour initialiser la propriété de dépendance.  
  
<a name="wrapper1"></a>   
### Implémentation du "wrapper"  
 Votre implémentation de wrapper doit appeler <xref:System.Windows.DependencyObject.GetValue%2A> dans l'implémentation `get`, et <xref:System.Windows.DependencyObject.SetValue%2A> dans l'implémentation `set` \(l'appel d'inscription d'origine et le champ sont indiqués ici également pour plus de clarté\).  
  
 Dans tous les cas, sauf dans des cas exceptionnels, vos implémentations de wrapper doivent exécuter uniquement les actions <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>, respectivement.  La raison est expliquée dans la rubrique [Propriétés de dépendance et chargement XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
 Toutes les propriétés de dépendance publiques fournies dans les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisent ce modèle simple d'implémentation de wrapper ; la complexité majeure relative au fonctionnement des propriétés de dépendance est soit inhérente au comportement du système de propriétés soit implémentée via d'autres concepts, tels que la contrainte ou les rappels de modification de propriété via des métadonnées de propriété.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
 Là encore, par convention, le nom de la propriété de wrapper doit correspondre au nom choisi et au premier paramètre de l'appel <xref:System.Windows.DependencyProperty.Register%2A> qui a inscrit la propriété.  Si votre propriété ne suit pas la convention, les utilisations possibles ne sont pas pour autant impossibles, mais vous serez confrontés à différents problèmes :  
  
-   Certains aspects de styles et modèles ne fonctionneront pas.  
  
-   La plupart des outils et concepteurs doivent utiliser les conventions d'affectation de noms pour sérialiser correctement le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou fournir l'assistance d'environnement concepteur au niveau de chaque propriété.  
  
-   L'implémentation actuelle du chargeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignore complètement les wrappers, et elle utilise la convention d'affectation de noms lors du traitement des valeurs d'attributs.  Pour plus d'informations, consultez [Propriétés de dépendance et chargement XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
<a name="metadata"></a>   
### Métadonnées de propriété d'une nouvelle propriété de dépendance  
 Lorsque vous inscrivez une propriété de dépendance, l'inscription via le système de propriétés crée un objet de métadonnées qui stocke des caractéristiques de la propriété.  La plupart de ces caractéristiques ont des valeurs par défaut définies si la propriété est inscrite avec les signatures simples <xref:System.Windows.DependencyProperty.Register%2A>.  D'autres signatures <xref:System.Windows.DependencyProperty.Register%2A> permettent de spécifier les métadonnées appropriées lorsque vous inscrivez la propriété.  Les métadonnées les plus courantes des propriétés de dépendance sont celles auxquelles vous affectez une valeur par défaut qui est appliquée dans les nouvelles instances qui utilisent la propriété.  
  
 Si vous créez une propriété de dépendance qui existe dans une classe dérivée <xref:System.Windows.FrameworkElement>, vous pouvez utiliser la classe de métadonnées <xref:System.Windows.FrameworkPropertyMetadata> plus spécialisée au lieu de la classe <xref:System.Windows.PropertyMetadata> de base.  Le constructeur de la classe <xref:System.Windows.FrameworkPropertyMetadata> a plusieurs signatures où vous pouvez spécifier différentes caractéristiques de métadonnées dans une combinaison.  Si vous souhaitez spécifier la valeur par défaut uniquement, utilisez la signature qui utilise un seul paramètre de type <xref:System.Object>.  Passez ce paramètre d'objet sous la forme d'une valeur par défaut pour votre propriété \(la valeur par défaut fournie doit correspondre au type que vous avez fourni comme paramètre `propertyType` dans l'appel <xref:System.Windows.DependencyProperty.Register%2A>\).  
  
 Pour <xref:System.Windows.FrameworkPropertyMetadata>, vous pouvez également spécifier des indicateurs d'option de métadonnées pour votre propriété.  Ces indicateurs sont convertis en propriétés discrètes dans les métadonnées de propriété après l'inscription et ils sont utilisés pour communiquer certaines instructions conditionnelles à d'autres processus, tels que le moteur de présentation.  
  
#### Définition des indicateurs de métadonnées appropriés  
  
-   Si votre propriété \(ou les modifications de sa valeur\) affecte l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], et notamment, la manière dont le système de disposition doit dimensionner ou rendre l'élément dans une page, définissez un ou plusieurs des indicateurs suivants : <xref:System.Windows.FrameworkPropertyMetadataOptions>, <xref:System.Windows.FrameworkPropertyMetadataOptions>, <xref:System.Windows.FrameworkPropertyMetadataOptions>.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> indique qu'une modification de cette propriété requiert une modification de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] indiquant où l'objet conteneur peut nécessiter plus ou moins d'espace dans le parent.  Par exemple, la propriété "Width" doit avoir cet indicateur.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> indique qu'une modification de cette propriété implique de modifier le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rendu qui ne nécessite pas de modifier l'espace dédié, mais qui indique que le positionnement dans l'espace a changé.  Par exemple, la propriété "Alignment" doit avoir cet indicateur.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> indique qu'une autre modification a eu lieu et qu'elle n'affecte pas la présentation et la mesure, mais qu'un autre rendu est nécessaire.  Un exemple serait une propriété qui modifie une couleur d'un élément existant, tel que " Background".  
  
    -   Ces indicateurs sont souvent utilisés comme protocole dans les métadonnées de vos propres implémentations de substitution de système de propriétés ou les rappels de présentation.  Par exemple, vous pouvez avoir un rappel <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> qui appelle <xref:System.Windows.UIElement.InvalidateArrange%2A> si une propriété de l'instance signale une modification de valeur et dont <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> a la valeur `true` dans ses métadonnées.  
  
-   Certaines propriétés peuvent affecter les caractéristiques de rendu de l'élément parent conteneur, au\-dessus et au\-delà des modifications de la taille requise mentionnées ci\-dessus.  Un exemple est la propriété <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> utilisée dans le modèle du document du flux où les modifications de la propriété peuvent changer l'ensemble du rendu du document dynamique qui contient le paragraphe.  Utilisez <xref:System.Windows.FrameworkPropertyMetadataOptions> ou <xref:System.Windows.FrameworkPropertyMetadataOptions> pour identifier des cas semblables dans vos propres propriétés.  
  
-   Par défaut, les propriétés de dépendance prennent en charge la liaison de données.  Vous pouvez désactiver la liaison de données lorsqu'elle n'est pas nécessaire ou lorsque les performances de la liaison de données pour un objet volumineux posent un problème.  
  
-   Par défaut, la liaison de données <xref:System.Windows.Data.Binding.Mode%2A> des propriétés de dépendance est <xref:System.Windows.Data.BindingMode>.  Vous pouvez toujours modifier la liaison pour la définir en fonction de chaque instance de liaison <xref:System.Windows.Data.BindingMode>. Pour plus d'informations, consultez [Spécifier le sens de la liaison](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md).  Mais en tant que créateur de propriété de dépendance, vous pouvez demander à la propriété d'utiliser le mode de liaison <xref:System.Windows.Data.BindingMode> par défaut.  Un exemple de propriété de dépendance existante est <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=fullName> ; dans le scénario de cette propriété, la logique de définition <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> et la composition <xref:System.Windows.Controls.MenuItem> interagissent avec le style de thème par défaut.  La logique de propriété <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> utilise en mode natif la liaison de données pour gérer l'état de la propriété en fonction des autres propriétés d'état et des appels de méthodes.  Une autre propriété qui lie <xref:System.Windows.Data.BindingMode> par défaut est, par exemple, <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName>.  
  
-   Vous pouvez également activer l'héritage de propriété dans une propriété de dépendance personnalisée en définissant l'indicateur <xref:System.Windows.FrameworkPropertyMetadataOptions>.  L'héritage des propriétés est utile pour un scénario dans lequel les éléments parents et les éléments enfants ont une propriété commune, et où il est logique que les éléments enfants aient la même valeur de propriété que celle définie par le parent.  Un exemple de propriété pouvant être héritée est <xref:System.Windows.FrameworkElement.DataContext%2A> ; elle est utilisée pour les opérations de liaison pour implémenter l'important scénario maître\/détail pour la présentation des données.  En permettant à <xref:System.Windows.FrameworkElement.DataContext%2A> d'être hérité, tous les éléments enfants héritent également de ce contexte de données.  Du fait de l'héritage de valeur de propriété, vous pouvez spécifier un contexte de données à la racine de la page ou de l'application et vous n'avez pas besoin de le respécifier pour les liaisons dans tous les éléments enfants possibles.  <xref:System.Windows.FrameworkElement.DataContext%2A> est également un bon exemple pour illustrer que l'héritage remplace la valeur par défaut, mais il peut toujours être défini localement dans un élément enfant. Pour plus d'informations, consultez [Utiliser le modèle maître\/détail avec des données hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  L'héritage de valeur de propriété peut affecter les performances. Par conséquent, utilisez\-le avec précaution. Pour plus d'informations consultez [Héritage de la valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Définissez l'indicateur <xref:System.Windows.FrameworkPropertyMetadataOptions> pour signaler si votre propriété de dépendance doit être détectée ou utilisée par les services de journalisation de navigation.  Un exemple est la propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> ; tout élément sélectionné dans un contrôle de sélection doit être rendu persistant lorsque l'historique de journalisation fait l'objet d'une navigation.  
  
<a name="RODP"></a>   
## Propriétés de dépendance en lecture seule  
 Vous pouvez définir une propriété de dépendance qui est en lecture seule.  Toutefois, les scénarios dans lesquels vous pouvez définir votre propriété en lecture seule sont quelque peu différents, à l'instar de la procédure utilisée pour les inscrire avec le système de propriétés et exposer l'identificateur.  Pour plus d'informations, consultez [Propriétés de dépendance en lecture seule](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
<a name="CTDP"></a>   
## Propriétés de dépendance de type collection  
 Les propriétés de dépendance de type collection demandent de tenir compte d'autres problèmes d'implémentation.  Pour plus d'informations, consultez [Propriétés de dépendance de type collection](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md).  
  
<a name="SecurityC"></a>   
## Considérations relatives à la sécurité des propriétés de dépendance  
 Les propriétés de dépendance doivent être déclarées comme propriétés publiques.  Les champs d'identificateur de propriété de dépendance doivent être déclarés comme champs statiques publics.  Même si vous essayez de déclarer d'autres niveaux d'accès \(tel que protégés\), une propriété de dépendance reste toujours accessible via l'identificateur en association avec le système de propriétés [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].  Même un champ d'identificateur protégé est potentiellement accessible du fait des rapports de métadonnées et de la détermination de valeur [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] qui font partie du système de propriétés, tel que <xref:System.Windows.LocalValueEnumerator>.  Pour plus d'informations, consultez [Sécurité de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
<a name="DPCtor"></a>   
## Propriétés de dépendance et constructeurs de classe  
 La programmation du code managé est régie par un principe général \(souvent appliqué par des outils d'analyse du code, tels que FxCop\) qui implique que les constructeurs de classe ne doivent pas appeler des méthodes virtuelles.  Ceci s'explique par le fait que les constructeurs peuvent être appelés comme initialisation de base d'un constructeur de classe dérivée, et l'entrée de la méthode virtuelle via le constructeur peut avoir lieu à un état d'initialisation incomplet de l'instance d'objet en construction.  Lorsque vous dérivez une classe d'une classe qui dérive déjà de <xref:System.Windows.DependencyObject>, tenez compte du fait que le système de propriétés lui\-même appelle et expose des méthodes virtuelles en interne.  Ces méthodes virtuelles font partie des services de système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La substitution des méthodes permet aux classes dérivées de participer à la détermination de valeur.  Pour éviter des problèmes potentiels au niveau de l'initialisation du runtime, vous ne devez pas définir de valeurs de propriété de dépendance dans les constructeurs de classes, à moins que vous suiviez un modèle de constructeur très spécifique.  Pour plus d'informations, consultez [Modèles de constructeur sécurisé pour DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md).  
  
## Voir aussi  
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [Propriétés de dépendance de type collection](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)   
 [Sécurité de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-security.md)   
 [Propriétés de dépendance et chargement XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)   
 [Modèles de constructeur sécurisé pour DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)