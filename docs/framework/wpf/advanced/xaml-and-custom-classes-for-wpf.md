---
title: "XAML et classes personnalis&#233;es pour WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "classes, classes personnalisées en XAML"
  - "classes personnalisées en XAML"
  - "XAML, classes personnalisées"
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# XAML et classes personnalis&#233;es pour WPF
XAML tel qu'il est implémenté dans des infrastructures de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] prend en charge la capacité de définir une classe ou une structure personnalisée dans tout langage de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , puis d'accéder à cette classe à l'aide de le balisage XAML.  Vous pouvez utiliser un mélange de types définis [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et de vos types personnalisés dans le même fichier de balisage, généralement en mappant les types personnalisés à un préfixe d'espace de noms XAML.  Cette rubrique décrit les spécifications qu'une classe personnalisée doit satisfaire pour être utilisable en tant qu'élément XAML.  
  
   
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## Classes personnalisées dans les applications ou les assemblys  
 Les classes personnalisées utilisées en XAML peuvent être définies de deux façons : dans le code\-behind ou un autre code qui génère l'application principal de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , ou comme classe dans un assembly séparé, tel qu'un fichier exécutable ou une DLL utilisé comme bibliothèque de classes.  Chacune de ces approches a des avantages et des inconvénients.  
  
-   La création d'une bibliothèque de classes offre l'avantage de pouvoir partager des classes personnalisées dans un grand nombre d'applications différentes.  Une bibliothèque séparée simplifie également des problèmes de versioning des applications pour contrôler, et la création d'une classe où l'utilisation de classe est telle qu'un élément racine dans une page XAML.  
  
-   La définition des classes personnalisées dans l'application présente un avantage : cette technique est relativement légère et réduit les problèmes liés au déploiement et au test rencontrés lorsque vous introduisez des assemblys séparés au\-delà du fichier exécutable d'application principal.  
  
-   S'il est défini dans un même assembly ou dans un assembly différent, les classes personnalisées doivent être mappées entre l'espace de noms CLR et l'espace de noms XML pour pouvoir être utilisées en XAML en tant qu'éléments.  Consultez [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## Spécifications d'une classe personnalisée comme élément XAML  
 Pour pouvoir instancier la classe comme un élément d'objet, la classe doit répondre aux conditions suivantes :  
  
-   La classe personnalisée doit être publique et prendre en charge un constructeur public par défaut \(sans paramètre\).  \(Consultez la section suivante pour prendre connaissance des remarques sur les structures.\)  
  
-   Votre classe personnalisée ne doit pas être une classe imbriquée.  Les classes imbriquées et le « point » dans leur syntaxe générale d'utilisation du CLR interfèrent avec d'autres fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et\/ou XAML, telles que les propriétés jointes.  
  
 Outre l'activation de la syntaxe d'élément objet, votre définition d'objet permet d'activer également la syntaxe d'élément de propriété pour les autres propriétés publiques qui considèrent cet objet comme le type valeur.  Cela s'explique par le fait que l'objet peut être désormais instancié comme élément d'objet et qu'il peut remplir la valeur d'élément de propriété d'une telle propriété.  
  
### Structures  
 Les structures que vous définissez en tant que types personnalisés peuvent toujours être construites en XAML dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Cela est dû au fait que les compilateurs de [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] créent implicitement un constructeur par défaut pour une structure qui initialise toutes les valeurs de propriété par défaut.  Dans certains cas, le comportement de construction par défaut et\/ou l'utilisation d'éléments objet pour une structure ne sont pas souhaitables.  Cela peut provenir du fait que la structure est destinée à remplir des valeurs et à fonctionner du point de vue conceptuel comme une union, où les valeurs contenues peuvent avoir des interprétations mutuellement exclusives et, dans ce cas, aucune de ses propriétés n'est définissable.  Un exemple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d'une telle structure est <xref:System.Windows.GridLength>.  En général, de telles structures doivent implémenter un convertisseur de type de telle sorte que les valeurs puissent être exprimées dans le formulaire d'attribut, à l'aide de conventions de chaîne qui créent les interprétations ou les modes différents des valeurs de la structure.  La structure doit également exposer un comportement semblable pour la construction de code via un constructeur non défini par défaut.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## Spécifications des propriétés d'une classe personnalisée comme attributs XAML  
 Les propriétés doivent référencer un type par valeur \(tel qu'une primitive\) ou utiliser une classe pour le type qui a, par défaut, un constructeur ou un convertisseur de type dédié auquel un processeur XAML peut accéder.  Dans l'implémentation XAML CLR, les processeurs XAML recherchent de tels convertisseurs via la prise en charge native pour les primitives de langage, ou via l'application de <xref:System.ComponentModel.TypeConverterAttribute> à un type ou un membre pour stocker les définitions de type  
  
 La propriété peut également faire référence à un type de classe abstraite ou une interface.  Dans le cas des classes ou des interfaces abstraites, l'attente pour l'analyse XAML est la suivante : la valeur de propriété doit être remplie avec les instances de classe pratiques qui implémentent l'interface, ou les instances de types qui dérivent de la classe abstraite.  
  
 Les propriétés peuvent être déclarées sur une classe abstraite, mais peuvent être définies uniquement sur les classes pratiques qui dérivent de la classe abstraite.  En effet, la création de l'élément objet pour la classe requiert un constructeur public par défaut sur la classe.  
  
### Syntaxe d'attribut activée par TypeConverter  
 Si vous fournissez un convertisseur de type attribué dédié au niveau de la classe, la conversion de type appliquée active la syntaxe d'attribut d'une propriété qui doit instancier ce type.  Un convertisseur de type n'active pas l'utilisation d'élément objet du type ; seule la présence d'un constructeur par défaut pour ce type active l'utilisation d'élément objet.  Par conséquent, les propriétés qui sont activées par un convertisseur de type sont généralement inutilisables dans la syntaxe de la propriété, sauf si le type lui\-même prend également en charge la syntaxe d'élément objet.  Il existe néanmoins une exception dans la mesure où vous pouvez définir une syntaxe d'élément de propriété et que l'élément de propriété peut contenir une chaîne.  Cette utilisation est vraiment essentiellement équivalente à une utilisation de syntaxe d'attribut ; une telle utilisation n'est pas courante, sauf s'il est nécessaire de traiter plus efficacement les espaces de la valeur d'attribut.  L'exemple suivant montre une utilisation d'élément de propriété qui utilise une chaîne et l'équivalent de l'utilisation de l'attribut :  
  
 [!code-xml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Des exemples de propriétés pour lesquelles la syntaxe d'attribut mais la syntaxe d'élément de propriété qui contient un élément objet est autorisée par XAML sont différentes propriétés qui prennent le type d' <xref:System.Windows.Input.Cursor> .  La classe <xref:System.Windows.Input.Cursor> a un convertisseur de type <xref:System.Windows.Input.CursorConverter> dédié, mais elle n'expose pas un constructeur par défaut. Par conséquent, la propriété <xref:System.Windows.FrameworkElement.Cursor%2A> peut être définie uniquement via la syntaxe d'attribut bien que le type <xref:System.Windows.Input.Cursor> réel soit un type référence.  
  
### Convertisseurs de type en fonction de la propriété  
 La propriété elle\-même peut déclarer également un convertisseur de type au niveau de la propriété.  Cela active un "mini langage" qui instancie des objets du type de la propriété inline en traitant les valeurs de chaîne entrantes de l'attribut comme entrée pour une opération <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> basé sur le type approprié.  En général cela permet de fournir un accesseur pratique, et non pas uniquement pour pouvoir définir une propriété en XAML.  Toutefois, il est également possible d'utiliser des convertisseurs de type pour les attributs pour lesquels vous voulez utiliser des types [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] existants qui ne fournissent pas un constructeur par défaut ni un convertisseur de type attribué.  les exemples de l'API de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont certaines propriétés qui prennent le type d' <xref:System.Globalization.CultureInfo> .  Dans ce cas, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a utilisé le type existant de[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]<xref:System.Globalization.CultureInfo> pour améliorer les scénarios de compatibilité et de migration utilisés dans les versions antérieures des infrastructures, mais le type d' <xref:System.Globalization.CultureInfo> ne prenait pas en charge les constructeurs ou conversion de type nécessaires de sécurité pour pouvoir l'utiliser comme valeur de propriété XAML directement.  
  
 Chaque fois que vous exposez une propriété qui a une utilisation XAML, en particulier si vous êtes auteur de contrôle, vous devez absolument envisager de stocker cette propriété avec une propriété de dépendance.  C'est particulièrement vrai si vous utilisez l'implémentation existante de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] du processeur XAML, car vous pouvez améliorer les performances à l'aide de la prise en charge d' <xref:System.Windows.DependencyProperty> .  Une propriété de dépendance exposera des fonctionnalités du système de propriétés pour votre propriété que les utilisateurs attendent pour une propriété accessible XAML.  Cela inclut des fonctions, telles que l'animation, la liaison de données et le support de style.  Pour plus d'informations, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) et [Propriétés de dépendance et chargement XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
### Écriture et attribution d'un convertisseur de type  
 Vous devrez parfois écrire une classe dérivée <xref:System.ComponentModel.TypeConverter> personnalisée afin de fournir la conversion de type pour votre type de propriété.  Pour savoir comment dériver une classe et créer un convertisseur de type qui prend en charge les utilisations XAML, ainsi qu'appliquer <xref:System.ComponentModel.TypeConverterAttribute>, consultez [TypeConverters et XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## Spécifications de la syntaxe d'attribut de gestionnaire d'événements XAML sur les événements d'une classe personnalisée  
 Pour pouvoir utiliser un événement comme événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], l'événement doit être exposé comme un événement public dans une classe qui prend en charge un constructeur par défaut, ou dans une classe abstraite où l'événement est accessible dans des classes dérivées.  Pour pouvoir l'utiliser aisément comme événement [routé](GTMT), votre événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] doit implémenter les méthodes implicites `add` et `remove`, qui ajoutent et suppriment des gestionnaires pour la signature d'événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et envoient ces gestionnaires aux méthodes <xref:System.Windows.UIElement.AddHandler%2A> et <xref:System.Windows.UIElement.RemoveHandler%2A>.  Ces méthodes ajoutent ou suppriment les gestionnaires dans le magasin des gestionnaires d'événements routés dans l'instance auquel l'événement est joint.  
  
> [!NOTE]
>  Il est possible d'inscrire directement des gestionnaires d'événements routés à l'aide de <xref:System.Windows.UIElement.AddHandler%2A>, et de ne pas définir délibérément un événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] qui expose l'[événement routé](GTMT).  Cela n'est généralement pas recommandé parce que l'événement ne vérifie pas la syntaxe d'attribut XAML pour joindre des gestionnaires, et votre classe résultante offrira une vue XAML moins transparente des fonctions de ce type.  
  
<a name="Collection_Properties"></a>   
## Écriture de propriétés de collection  
 Les propriétés qui prennent un type de collection ont une syntaxe XAML qui vous permet de spécifier les objets ajoutés à la collection.  Cette syntaxe a deux fonctions notables.  
  
-   L'objet qui est l'objet de collection ne doit pas être spécifié dans la syntaxe d'élément objet.  La présence de ce type de collection est implicite chaque fois que vous spécifiez une propriété dans XAML qui prend un type de collection.  
  
-   Les éléments enfants de la propriété de collection dans le balisage sont traités pour devenir membres de la collection.  Normalement, l'accès du code aux membres d'une collection est effectué via des méthodes de liste\/dictionnaire, telles que `Add` ou via un indexeur.  Mais la syntaxe XAML ne prend pas en charge les méthodes ou les indexeurs \(exception : XAML 2009 peut prendre en charge les méthodes, en utilisant XAML 2009 restreint les utilisations possibles WPF ; consultez [Fonctionnalités de langage XAML 2009](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)\).  Les collections sont à l'évidence une spécification très courante pour générer une arborescence d'éléments, et vous devez utiliser une méthode pour remplir ces collections dans XAML déclaratif.  Par conséquent, les éléments enfants d'une propriété de collection sont traités en les ajoutant à la collection qui est la valeur de type de propriété de collection.  
  
 L'implémentation des services XAML.NET Framework et donc le processeur XAML WPF utilise la définition suivante dans le cadre d'une propriété de collection.  Le type de la propriété doit implémenter l'un des éléments suivants :  
  
-   Implémente <xref:System.Collections.IList>.  
  
-   Implémente <xref:System.Collections.IDictionary> ou l'équivalent générique \(<xref:System.Collections.Generic.IDictionary%602>\).  
  
-   Dérive d' <xref:System.Array> \(pour plus d'informations sur les tableaux en XAML, consultez [x:Array, extension de balisage](../../../../docs/framework/xaml-services/x-array-markup-extension.md).\)  
  
-   Implémente <xref:System.Windows.Markup.IAddChild> \(une interface définie par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]\).  
  
 Chacun de ces types dans le CLR a une méthode d' `Add` , qui est utilisée par le processeur XAML pour ajouter des éléments à la collection sous\-jacente lors de le graphique d'objet.  
  
> [!NOTE]
>  `List` les interfaces génériques et d' `Dictionary` \(<xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IDictionary%602>\) ne sont pas pris en charge pour la détection de collection par le processeur XAML de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Toutefois, vous pouvez utiliser la classe <xref:System.Collections.Generic.List%601> comme classe de base, parce qu'elle implémente <xref:System.Collections.IList> directement, ou <xref:System.Collections.Generic.Dictionary%602> comme classe de base, parce qu'elle implémente <xref:System.Collections.IDictionary> directement.  
  
 Lorsque vous déclarez une propriété qui prend une collection, vérifiez la manière dont la valeur de propriété est initialisée dans les nouvelles instances du type.  Si vous n'implémentez pas la propriété comme une propriété de dépendance, vous pouvez faire en sorte que la propriété utilise un champ de stockage qui appelle le constructeur de type.  Si votre propriété est une propriété de dépendance, vous pouvez devoir initialiser la propriété de collection dans le cadre du constructeur de type par défaut.  En effet, une propriété de dépendance prend sa valeur par défaut des métadonnées, et vous ne voulez généralement pas que la valeur initiale d'une propriété de collection soit une collection statique, partagée.  Une instance de collection doit exister pour chaque instance de type conteneur.  Pour plus d'informations, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Vous pouvez implémenter un type collection personnalisé pour votre propriété de collection.  Du fait du traitement de propriété de collection implicite, le type de collection personnalisé n'a pas besoin de fournir un constructeur par défaut pour qu'il soit utilisé implicitement dans XAML.  Toutefois, vous pouvez fournir éventuellement un constructeur par défaut pour le type collection.  Cette pratique peut s'avérer utile.  À moins que vous ne fournissiez un constructeur par défaut, vous ne pouvez pas déclarer explicitement la collection en tant qu'élément objet.  Certains auteurs de balises considèrent plutôt la collection explicite comme un type de balisage.  En outre, un constructeur par défaut peut simplifier les spécifications d'initialisation lorsque vous créez des objets qui utilisent votre type collection comme une valeur de propriété.  
  
<a name="XAMLCONtent"></a>   
## Déclaration des propriétés de contenu XAML  
 Le langage XAML définit le concept de propriété de contenu de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Chaque classe utilisable dans la syntaxe d'objet peut avoir exactement une propriété de contenu XAML.  Pour déclarer une propriété comme étant la propriété de contenu XAML de votre classe, appliquez <xref:System.Windows.Markup.ContentPropertyAttribute> dans le cadre de la définition de classe.  Spécifiez le nom de la propriété de contenu XAML comme <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> dans l'attribut.  La propriété est spécifiée sous forme de chaîne du nom, pas comme un élément de réflexion tel qu'<xref:System.Reflection.PropertyInfo>.  
  
 Vous pouvez spécifier une propriété de collection comme étant la propriété de contenu XAML.  Cela génère une utilisation de la propriété par laquelle l'élément d'objet peut avoir un ou plusieurs éléments enfants sans éléments d'objet collection intermédiaires ou indicateurs d'éléments de propriété.  Ces éléments sont ensuite traités comme étant la valeur de la propriété de contenu XAML et ils sont ajoutés à l'instance de collection de stockage.  
  
 Certaines propriétés de contenu XAML existantes utilisent le type de propriété de `Object`.  Cela permet d'utiliser une propriété de contenu XAML qui peut prendre des valeurs primitives telles que <xref:System.String> et une valeur d'objet de référence unique.  Si vous suivez ce modèle, votre type se charge de la détermination de type et de la gestion des types possibles.  La justification courante d'un type de contenu <xref:System.Object> consiste à prendre en charge une méthode simple d'ajout de contenu d'objet sous la forme d'une chaîne \(qui reçoit un traitement de présentation par défaut\), ainsi qu'une méthode avancée d'ajout de contenu d'objet qui spécifie une présentation non définie par défaut ou des données supplémentaires.  
  
<a name="Serializing"></a>   
## Sérialisation du XAML  
 Dans certains cas, lorsque vous êtes auteur de contrôle, vous pouvez vous assurer qu'une représentation d'objet pouvant être instanciée en XAML peut également être sérialisée dans le balisage XAML équivalent.  Les spécifications de sérialisation ne sont pas décrites dans cette rubrique.  Consultez [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md) et [Sérialisation et arborescence d'éléments](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md).  
  
## Voir aussi  
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [Vue d'ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [Propriétés de dépendance et chargement XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)