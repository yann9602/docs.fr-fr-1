---
title: "Vue d&#39;ensemble des propri&#233;t&#233;s jointes | Microsoft Docs"
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
  - "propriétés jointes (Concepteur WPF)"
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# Vue d&#39;ensemble des propri&#233;t&#233;s jointes
Une propriété jointe est un concept défini par XAML.  Elle est conçue pour être utilisée comme un type de propriété globale qui peut être défini sur tout objet.  Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les propriétés attachées sont généralement définies comme une forme spécialisée de la propriété de dépendance qui n'a pas le « wrapper » de propriété classique.  
  
   
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique part du principe que vous comprenez les propriétés de dépendance du point de vue d'un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et que vous avez lu [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Pour suivre les exemples dans cette rubrique, vous devez également maîtriser XAML et savoir écrire des applications de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
<a name="attached_properties_usage"></a>   
## Pourquoi utiliser des propriétés attachées  
 Une des finalités d'une propriété attachée est de permettre à différents éléments enfants de spécifier des valeurs uniques pour une propriété définie en fait dans un élément parent.  Une application spécifique de ce scénario est de faire en sorte que les éléments enfants informent l'élément parent sur la manière dont ils doivent être présentés dans [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  La propriété <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> en est un exemple.  La propriété <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> est créée en tant que propriété jointe car elle est conçue pour être définie sur les éléments contenus dans un <xref:System.Windows.Controls.DockPanel>, plutôt que sur le <xref:System.Windows.Controls.DockPanel> proprement dit.  La classe <xref:System.Windows.Controls.DockPanel> définit le champ statique <xref:System.Windows.DependencyProperty> nommé <xref:System.Windows.Controls.DockPanel.DockProperty>, puis fournit les méthodes <xref:System.Windows.Controls.DockPanel.GetDock%2A> et <xref:System.Windows.Controls.DockPanel.SetDock%2A> comme accesseurs publics pour la [propriété attachée](GTMT).  
  
<a name="attached_properties_xaml"></a>   
## Propriétés attachées en XAML  
 En XAML, vous définissez des propriétés jointes à l'aide de la syntaxe *FournisseurPropriétéJointe*.*NomPropriété*.  
  
 L'exemple suivant illustre la manière dont vous pouvez définir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> en XAML :  
  
 [!code-xml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 Notez que l'utilisation est quelque peu semblable à une propriété statique ; vous faites toujours référence au type <xref:System.Windows.Controls.DockPanel> qui possède et enregistre la [propriété attachée](GTMT), plutôt qu'à une instance quelconque spécifiée par nom.  
  
 En outre, étant donné qu'une propriété attachée en XAML est un attribut que vous définissez dans le balisage, seule l'opération définie est pertinente.  Vous ne pouvez pas obtenir directement une propriété en XAML, bien que des mécanismes indirects permettent de comparer des valeurs, telles que les déclencheurs dans les styles \(pour plus d'informations, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)\).  
  
### Implémentation des propriétés attachées dans WPF  
 Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], la plupart des propriétés attachées existant sur les types de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] liés à la présentation d'interface sont implémentées comme propriétés de dépendance.  les propriétés jointes sont un concept de XAML, tandis que les propriétés de dépendance sont un concept de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  Étant donné que les propriétés attachées de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sont des propriétés de dépendance, elles prennent en charge les concepts de propriété de dépendance tels que les métadonnées de propriété, et les valeurs par défaut de ces métadonnées.  
  
<a name="howused"></a>   
## Comment les propriétés attachées sont utilisées par le type propriétaire  
 Bien que les propriétés attachées puissent être définies sur tout objet, cela ne signifie pas systématiquement que leur définition produira un résultat concret ou que leur valeur sera jamais utilisée par un autre objet.  En général, les propriétés jointes sont utilisées pour que les objets provenant de diverses relations logiques ou hiérarchies de classes possibles puissent chacun communiquer des informations communes au type qui définit la propriété jointe.  Le type qui définit la propriété attachée suit en général l'un de ces modèles :  
  
-   Le type qui définit la propriété attachée est conçu pour pouvoir être l'élément parent des éléments qui définiront les valeurs de la propriété attachée.  Le type itère ensuite ses objets enfants via la logique interne au sein d'une structure d'objets arborescente, obtient les valeurs et agit sur elles.  
  
-   Le type qui définit la propriété attachée sera utilisé comme élément enfant pour divers éléments parents et modèles de contenu possibles.  
  
-   Le type qui définit la propriété attachée représente un service.  D'autres types définissent les valeurs de la propriété attachée.  Lorsque l'élément qui définit la propriété est évalué dans le contexte du service, les valeurs de la propriété attachée sont alors obtenues par le biais de la logique interne de la classe de service.  
  
### Exemple d'une propriété attachée définie par le parent  
 Le scénario le plus courant dans lequel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit une propriété attachée est lorsqu'un élément parent prend en charge une collection d'éléments enfants, et implémente également un comportement dont les caractéristiques sont signalées individuellement pour chaque élément enfant.  
  
 <xref:System.Windows.Controls.DockPanel> définit la propriété attachée <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>, et le code du niveau de classe de <xref:System.Windows.Controls.DockPanel> fait partie de la logique de rendu correspondante \(en particulier <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> et <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>\).  Une instance <xref:System.Windows.Controls.DockPanel> vérifiera toujours si l'un de ses éléments enfants immédiats a défini une valeur pour <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>.  Si tel est le cas, ces valeurs sont entrées pour la logique de rendu appliquée à l'élément enfant en question.  Les instances <xref:System.Windows.Controls.DockPanel> imbriquées traitent chacune leurs propres collections d'éléments enfants immédiates, mais ce comportement est spécifique à l'implémentation et dépend de la manière dont <xref:System.Windows.Controls.DockPanel> traite les valeurs <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>.  Il est théoriquement possible d'avoir des propriétés attachées qui influencent des éléments au\-delà du parent immédiat.  Si la propriété attachée <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> est définie sur un élément qui n'a aucun élément parent <xref:System.Windows.Controls.DockPanel> pour agir dessus, aucune erreur ou exception n'est déclenchée.  Cela signifie simplement qu'une valeur de propriété globale a été définie, mais elle n'a actuellement aucun parent <xref:System.Windows.Controls.DockPanel> susceptible de consommer les informations.  
  
<a name="attached_properties_code"></a>   
## Propriétés attachées dans le code  
 Les propriétés attachées dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n'ont pas les méthodes de "wrapper" [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typiques qui facilitent la définition\/l'obtention de l'accès.  Cela est dû au fait que la propriété attachée ne fait pas nécessairement partie de l'espace de noms [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] pour les instances dans lesquelles est définie la propriété.  Toutefois, un processeur XAML doit pouvoir définir ces valeurs lorsque XAML est analysé.  Pour prendre en charge une utilisation efficace de la propriété attachée, le type de propriétaire de la propriété attachée doit implémenter des méthodes d'accesseur dédiées dans le `Get`formulaire*PropertyName* et `Set`*PropertyName*.  Ces méthodes d'accesseur dédiées sont également utiles pour obtenir ou définir la propriété jointe dans le code.  Du point de vue du code, une propriété attachée s'apparente à un champ de stockage comportant des accesseurs de méthode au lieu d'accesseurs de propriété, et ce champ de stockage peut exister sur tout objet plutôt que devoir être défini de manière spécifique.  
  
 L'exemple suivant illustre la définition d'une propriété attachée dans le code.  Dans cet exemple, `myCheckBox` est une instance de la classe <xref:System.Windows.Controls.CheckBox>.  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 Similaire au cas XAML, si `myCheckBox` n'a pas déjà été ajouté comme un élément enfant d' `myDockPanel` par la troisième ligne de code, la quatrième ligne du code ne déclenchera pas d'exception, mais la valeur de propriété n'interagirait pas avec <xref:System.Windows.Controls.DockPanel> parent et ne ferait donc rien.  Seule une valeur <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> définie sur un élément enfant combiné à la présence d'un élément parent <xref:System.Windows.Controls.DockPanel> déclenchera un comportement effectif dans l'application rendue.  \(Dans ce cas, vous pourriez définir la propriété jointe, puis la joindre à l'arborescence.  Vous pourriez également joindre la propriété à l'arborescence puis la définir.  Le résultat est le même, quel que soit l'ordre des actions.\)  
  
<a name="attached_properties_metadata"></a>   
## Métadonnées de propriété attachée  
 Lors de l'enregistrement de la propriété, <xref:System.Windows.FrameworkPropertyMetadata> est défini pour spécifier des caractéristiques de la propriété, par exemple si la propriété affecte le rendu, les mesures, etc.  Les métadonnées d'une [propriété attachée](GTMT) sont en général identiques à celles d'une [propriété de dépendance](GTMT).  Si vous spécifiez une valeur par défaut dans une substitution des métadonnées d'une propriété attachée, cette valeur devient la valeur par défaut de la propriété attachée implicite sur les instances de la classe prioritaire.  Spécifiquement, votre valeur par défaut est signalée si un processus demande la valeur d'une propriété attachée par le biais de l'accesseur de méthode `Get` de cette propriété, en spécifiant une instance de la classe dans laquelle vous avez indiqué les métadonnées, et si la valeur de cette propriété attachée n'était autrement pas définie.  
  
 Si vous souhaitez activer l'héritage des valeurs de propriété sur une propriété, vous devez utiliser des propriétés attachées plutôt que des propriétés de dépendance non attachées.  Pour plus d'informations, consultez [Héritage de la valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="custom"></a>   
## Propriétés attachées personnalisées  
  
<a name="create_attached_properties"></a>   
### Quand créer une propriété attachée  
 Vous pouvez créer une [propriété attachée](GTMT) si un mécanisme de définition de propriété doit être disponible pour les classes autres que la classe de définition.  Le scénario le plus courant à cette fin est la mise en page.  Voici quelques exemples de propriétés de mise en page existantes : <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName> et <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=fullName>.  Le scénario activé ici implique que les éléments existant comme éléments enfants sur les éléments contrôlant la mise en page sont en mesure d'exprimer individuellement des spécifications de mise en page à leurs éléments parents de mise en page et chacun d'eux définit une valeur de propriété configurée par le parent comme une propriété attachée.  
  
 Un autre scénario illustrant l'utilisation d'une propriété attachée s'applique lorsque votre classe représente un service et vous que voulez que les classes soient en mesure d'intégrer le service avec une plus grande transparence.  
  
 Un autre scénario encore consiste à bénéficier de la prise en charge du [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] de [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], par exemple l'édition de la fenêtre **Propriétés**.  Pour plus d'informations, consultez [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Comme mentionné précédemment, vous devez enregistrer une propriété attachée si vous souhaitez utiliser l'héritage des valeurs de propriété.  
  
<a name="how_do_i_create_attached_properties"></a>   
### Comment créer une propriété attachée  
 Si votre classe définit strictement la [propriété attachée](GTMT) pour son utilisation sur d'autres types, il n'est alors pas nécessaire qu'elle dérive de <xref:System.Windows.DependencyObject>.  Mais vous devez dériver d' <xref:System.Windows.DependencyObject> si vous suivez le modèle global de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de disposer votre propriété attachée soit également une propriété de dépendance.  
  
 Définissez votre propriété jointe comme une propriété de dépendance en déclarant un champ `public` `static` `readonly` de type <xref:System.Windows.DependencyProperty>.  Vous définissez ce champ à l'aide de la valeur de retour de la méthode <xref:System.Windows.DependencyProperty.RegisterAttached%2A>.  Le nom du champ doit correspondre au nom de la propriété attachée, auquel s'ajoute la chaîne `Property`, pour suivre le modèle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] établi de dénomination des champs d'identification par rapport aux propriétés représentés.  Le fournisseur de propriétés jointes doit également fournir des méthodes statiques `Get`de*PropertyName* et `Set`de*PropertyName* comme accesseurs de la propriété attachée ; impossibilité d'effectuer cela empêchera le système de propriétés ne pourra pas utiliser votre propriété attachée.  
  
> [!NOTE]
>  Si vous omettez l'accesseur get de la propriété jointe, la liaison de données sur la propriété ne fonctionnera pas dans les outils de conception, tels que [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] et Expression Blend.  
  
#### Accesseur Get  
 La signature de `Get`l'accesseur de*PropertyName* doit être :  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   L'objet `target` peut être défini comme un type plus spécifique dans votre implémentation.  Par exemple, la méthode <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=fullName> tape le paramètre comme <xref:System.Windows.UIElement>, car la propriété attachée doit uniquement être définie sur les instances <xref:System.Windows.UIElement>.  
  
-   La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation.  Par exemple, la méthode <xref:System.Windows.Controls.DockPanel.GetDock%2A> le tape comme <xref:System.Windows.Controls.Dock>, car la valeur peut être uniquement cette énumération.  
  
#### Accesseur Set  
 La signature de `Set`l'accesseur de*PropertyName* doit être :  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   L'objet `target` peut être défini comme un type plus spécifique dans votre implémentation.  Par exemple, la méthode <xref:System.Windows.Controls.DockPanel.SetDock%2A> le tape comme <xref:System.Windows.UIElement>, car la propriété attachée doit uniquement être définie sur les instances <xref:System.Windows.UIElement>.  
  
-   L'objet `value` peut être défini comme un type plus spécifique dans votre implémentation.  Par exemple, la méthode <xref:System.Windows.Controls.DockPanel.SetDock%2A> le tape comme <xref:System.Windows.Controls.Dock>, car la valeur peut être uniquement cette énumération.  N'oubliez pas que la valeur de cette méthode est l'entrée provenant du chargeur XAML lorsqu'il rencontre votre propriété attachée dans une utilisation des propriétés attachées dans le balisage.  Cette entrée est la valeur spécifiée comme une valeur d'attribut XAML dans le balisage.  Par conséquent, la conversion de type, la sérialisation de valeur ou l'extension de balisage doit être prise en charge pour le type utilisé de sorte que le type approprié puisse être créé à partir de la valeur d'attribut \(laquelle est en fin de compte une simple chaîne\).  
  
 L'exemple suivant illustre l'inscription de propriété de dépendance \(à l'aide de la méthode d' <xref:System.Windows.DependencyProperty.RegisterAttached%2A> \), ainsi que `Get`les accesseurs de*PropertyName* et `Set`de*PropertyName* .  Dans cet exemple, le nom de la propriété attachée est `IsBubbleSource`.  Par conséquent, les accesseurs doivent être nommés `GetIsBubbleSource` et `SetIsBubbleSource`.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### Attributs des propriétés attachées  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit plusieurs [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] qui doivent fournir des informations sur les propriétés attachées aux processus de réflexion et aux utilisateurs typiques des informations de réflexion et de propriété, tels que les concepteurs.  Étant donné que les propriétés jointes ont un type de portée illimitée, les concepteurs ont besoin d'un moyen d'éviter les utilisateurs contenu avec une liste globale de toutes les propriétés attachées définies dans une implémentation particulière de technologie qui utilise XAML.  Le [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit pour les propriétés attachées peut être utilisé pour déterminer les cas où une propriété attachée donnée doit être affichée dans une fenêtre de propriétés.  Vous pouvez également envisager l'application de ces attributs à vos propres propriétés attachées personnalisées.  La finalité et la syntaxe de [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] sont décrites dans les pages de référence appropriées :  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## En savoir plus sur les propriétés attachées  
  
-   Pour plus d'informations sur la création d'une propriété attachée, consultez [Enregistrer une propriété jointe](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).  
  
-   Pour obtenir des scénarios d'usage avancés des propriétés de dépendance et des propriétés attachées, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
-   Vous pouvez également enregistrer une propriété comme une propriété attachée et comme une propriété de dépendance ; mais dans ce cas, vous exposerez encore les implémentations de "wrapper."  Dans ce cas, la propriété peut être définie soit sur cet élément, ou tout élément via la syntaxe de propriété jointe XAML.  Le scénario suivant illustre un exemple de propriété pour utilisations standard et attachée : <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.DependencyProperty>   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Enregistrer une propriété jointe](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)