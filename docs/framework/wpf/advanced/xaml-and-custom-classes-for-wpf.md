---
title: "XAML et classes personnalisées pour WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da599afc94fba617d4df17c57679d8ee4bb05c61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML et classes personnalisées pour WPF
XAML, tel qu’il est implémenté dans les frameworks [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], prend en charge la possibilité de définir une classe ou une structure personnalisée dans n’importe quel langage de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], puis d’accéder à cette classe à l’aide du balisage XAML. Vous pouvez utiliser un mélange de types définis de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et de vos types personnalisés dans le même fichier de balisage, généralement en mappant les types personnalisés à un préfixe d’espace de noms XAML. Cette rubrique décrit les conditions que doit satisfaire une classe personnalisée pour pouvoir être utilisée comme élément XAML.  
  
 
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Classes personnalisées dans les applications ou les assemblys  
 Les classes personnalisées qui sont utilisés dans XAML peuvent être définies de deux façons distinctes : dans le code-behind ou dans un autre code produisant l’application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] principale, ou comme une classe dans un assembly distinct, comme un fichier exécutable ou une DLL utilisée comme bibliothèque de classes. Chacune de ces approches a des avantages et des inconvénients spécifiques.  
  
-   L’avantage de créer une bibliothèque de classes est que ces classes personnalisées peuvent être partagées entre de nombreuses applications différentes. Une bibliothèque distincte facilite également le contrôle des problèmes de gestion des versions des applications et simplifie la création d’une classe là où l’utilisation prévue de la classe est d’être un élément racine dans une page XAML.  
  
-   L’avantage de définir les classes personnalisées dans l’application est que cette technique est relativement légère et réduit les problèmes de déploiement et de test rencontrés quand vous introduisez des assemblys distincts au-delà de l’exécutable principal de l’application.  
  
-   Qu’elles soient définies dans le même assembly ou dans un autre, les classes personnalisées doivent être mappées entre l’espace de noms CLR et l’espace de noms XML pour pouvoir être utilisées dans XAML en tant qu’éléments. Consultez [Espaces de noms XAML et mappage d’espace de noms pour XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Spécifications pour une classe personnalisée comme élément XAML  
 Pour pouvoir être instanciée comme élément objet, votre classe doit répondre aux spécifications suivantes :  
  
-   Votre classe personnalisée doit être publique et prendre en charge un constructeur public (sans paramètre). (Consultez la section suivante pour des remarques concernant les structures.)  
  
-   Votre classe personnalisée ne doit pas être une classe imbriquée. Les classes imbriquées et le « point » dans leur syntaxe générale d’utilisation du CLR interfèrent avec d’autres fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et/ou XAML, comme les propriétés attachées.  
  
 En plus de permettre une syntaxe d’élément objet, votre définition d’objet permet également la syntaxe des éléments de propriété pour les autres propriétés publiques qui prennent cet objet comme type de valeur. La raison en est que l’objet peut maintenant être instancié comme un élément objet et qu’il peut remplir la valeur de l’élément propriété d’une telle propriété.  
  
### <a name="structures"></a>Structures  
 Les structures que vous définissez comme types personnalisés peuvent toujours être construites en XAML dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. La raison en est que les compilateurs [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] créent implicitement un constructeur par défaut pour une structure qui initialise toutes les propriétés à leurs valeurs par défaut. Dans certains cas, le comportement de construction et/ou l’utilisation de l’élément objet par défaut pour une structure ne sont pas souhaitables. La raison peut en être que la structure est destinée à remplir des valeurs et à fonctionner conceptuellement comme une union, où les valeurs contenues peuvent avoir des interprétations mutuellement exclusives, aucune de ses propriétés ne pouvant donc être définie. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exemple d’une telle structure est <xref:System.Windows.GridLength>. En règle générale, ces structures doivent implémenter un convertisseur de type, de sorte que les valeurs peuvent être exprimées sous forme d’attribut, en utilisant des conventions de chaîne qui créent les différents modes ou interprétations des valeurs de la structure. La structure doit également exposer un comportement similaire pour la construction de code via un constructeur non défini par défaut.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Spécifications pour les propriétés d’une classe personnalisée en tant qu’attributs XAML  
 Les propriétés doivent référencer un type par valeur (comme une primitive) ou utiliser une classe pour un type qui a un constructeur par défaut ou un convertisseur de type dédié auquel un processeur XAML peut accéder. Dans l’implémentation XAML CLR, les processeurs XAML recherchent de tels convertisseurs via la prise en charge native pour les primitives de langage, ou via l’application de <xref:System.ComponentModel.TypeConverterAttribute> à un type ou membre dans les définitions de type de stockage  
  
 La propriété peut aussi référencer un type d’une classe abstraite ou une interface. Pour les classes abstraites ou les interfaces, l’analyse XAML nécessite que la valeur de propriété soit remplie avec des instances de classe pratiques qui implémentent l’interface, ou avec des instances des types qui dérivent de la classe abstraite.  
  
 Les propriétés peuvent être déclarées sur une classe abstraite, mais ne peuvent être définies sur des classes pratiques qui dérivent de la classe abstraite. La raison en est que la création de l’élément objet pour la classe nécessite un constructeur public par défaut sur la classe.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Syntaxe d’attribut activée par TypeConverter  
 Si vous fournissez un convertisseur de type attribué dédié au niveau de la classe, la conversion de type appliquée permet la syntaxe d’attribut pour les propriétés qui doivent instancier ce type. Un convertisseur de type n’active pas l’utilisation d’élément objet du type ; seule la présence d’un constructeur par défaut pour ce type permet l’utilisation d’éléments objet. Par conséquent, les propriétés qui sont activées par un convertisseur de type ne sont généralement pas utilisables dans la syntaxe de propriété, sauf si le type lui-même prend également en charge la syntaxe d’élément objet. L’exception à cela est que vous pouvez spécifier une syntaxe des éléments de propriété, mais que l’élément de propriété doit alors contenir une chaîne. Cette utilisation est essentiellement équivalente à une utilisation de syntaxe d’attribut ; une telle utilisation n’est pas courante, sauf s’il existe un besoin pour la gestion des espaces plus robuste de la valeur d’attribut. Par exemple, voici une utilisation d’élément de propriété qui prend une chaîne et l’utilisation d’attribut équivalente :  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Exemples de propriétés où la syntaxe d’attribut est autorisée mais syntaxe d’élément de propriété qui contient un élément d’objet n’est pas autorisé via XAML sont les propriétés qui prennent le <xref:System.Windows.Input.Cursor> type. Le <xref:System.Windows.Input.Cursor> classe a un convertisseur de type dédié <xref:System.Windows.Input.CursorConverter>, mais n’expose ne pas un constructeur par défaut, donc la <xref:System.Windows.FrameworkElement.Cursor%2A> propriété peut uniquement être définie via la syntaxe d’attribut bien réel <xref:System.Windows.Input.Cursor> type est un type référence.  
  
### <a name="per-property-type-converters"></a>Convertisseurs de type par propriété  
 Une autre possibilité est que la propriété proprement dite puisse déclarer un convertisseur de type au niveau de la propriété. Cela permet un « mini langage » qui instancie des objets du type de la propriété inline en traitant les valeurs de chaîne entrantes de l’attribut comme entrée pour une <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> opération basée sur le type approprié. En général, ceci vise à fournir un accesseur pratique, et non pas à être le seul moyen de permettre la définition d’une propriété dans XAML. Cependant, il est également possible d’utiliser des convertisseurs de type pour les attributs où vous voulez utiliser des types [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] existants qui ne fournissent pas de constructeur par défaut ni de convertisseur de type attribué. Les exemples à partir de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API sont certaines propriétés qui prennent le <xref:System.Globalization.CultureInfo> type. Dans ce cas, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisé existants [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] <xref:System.Globalization.CultureInfo> type pour mieux résoudre les scénarios de compatibilité et de migration qui ont été utilisés dans les versions antérieures du .NET Framework, mais la <xref:System.Globalization.CultureInfo> type ne prenait pas en charge les constructeurs nécessaires ou au niveau du type de conversion de type pour être utilisable comme une valeur de propriété XAML directement.  
  
 Quand vous exposez une propriété qui a une utilisation XAML, en particulier si vous êtes un créateur de contrôles, vous devez absolument envisager de stocker cette propriété avec une propriété de dépendance. Cela est particulièrement vrai si vous utilisez existants [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implémentation du processeur XAML, car vous pouvez améliorer les performances à l’aide de <xref:System.Windows.DependencyProperty> sauvegarde. Une propriété de dépendance exposera des fonctionnalités du système de propriétés pour votre propriété, que les utilisateurs viendront à attendre pour une propriété accessible de XAML. Ceci inclut des fonctionnalités comme l’animation, la liaison de données et la prise en charge des styles. Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) et [Propriétés de dépendance et chargement XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Écriture et attribution d’un convertisseur de type  
 Vous devrez parfois écrire une personnalisée <xref:System.ComponentModel.TypeConverter> dérivée de la classe pour fournir une conversion de type pour votre type de propriété. Pour savoir comment dériver et créer un convertisseur de type qui peut prendre en charge les utilisations de code XAML et comment appliquer le <xref:System.ComponentModel.TypeConverterAttribute>, consultez [TypeConverters and XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Spécifications pour la syntaxe d’attribut de gestionnaire d’événements XAML sur les événements d’une classe personnalisée  
 Pour être utilisable comme événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], l’événement doit être exposé comme un événement public sur une classe qui prend en charge un constructeur par défaut, ou dans une classe abstraite où l’événement est accessible sur des classes dérivées. Pour pouvoir être utilisé pour des raisons pratiques comme un événement routé, votre [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] événement doit implémenter explicite `add` et `remove` , ces méthodes ajouter et suppriment des gestionnaires pour les [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] signature d’événement et envoient ces gestionnaires pour le <xref:System.Windows.UIElement.AddHandler%2A>et <xref:System.Windows.UIElement.RemoveHandler%2A> méthodes. Ces méthodes ajoutent ou suppriment les gestionnaires dans le magasin de gestionnaires d’événements routés sur l’instance à laquelle l’événement est attaché.  
  
> [!NOTE]
>  Il est possible d’inscrire directement des événements routés à l’aide de gestionnaires de <xref:System.Windows.UIElement.AddHandler%2A>et à ne pas définir délibérément un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] événement qui expose l’événement routé. Ceci est généralement non recommandé, car l’événement n’activera pas la syntaxe d’attribut XAML pour attacher des gestionnaires, et votre classe résultante offrira une vue XAML moins transparente des fonctionnalités de ce type.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Écriture de propriétés de collection  
 Les propriétés qui prennent un type collection ont une syntaxe XAML qui vous permet de spécifier les objets qui sont ajoutés à la collection. Cette syntaxe a deux fonctions importantes.  
  
-   L’objet qui est l’objet collection n’a pas besoin d’être spécifié dans la syntaxe d’élément objet. La présence de ce type de collection est implicite quand vous spécifiez une propriété dans XAML qui prend un type collection.  
  
-   Les éléments enfants de la propriété de collection dans le balisage sont traités pour devenir membres de la collection. Normalement, l’accès du code aux membres d’une collection est effectué via des méthodes de liste/dictionnaire,comme `Add`, ou via un indexeur. La syntaxe XAML ne prend cependant pas en charge les méthodes ou les indexeurs (exception : XAML 2009 peut prendre en charge des méthodes, mais l’utilisation de XAML 2009 restreint les utilisations possibles de WPF ; consultez [Fonctionnalités du langage XAML 2009](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)). Les collections sont à l’évidence une spécification très courante pour générer une arborescence d’éléments, et vous devez disposer d’un moyen de remplir ces collections dans du XAML déclaratif. Par conséquent, les éléments enfants d’une propriété de collection sont traités en les ajoutant à la collection qui est la valeur du type de propriété de collection.  
  
 L’implémentation des services XAML .NET Framework, et donc le processeur XAML WPF, utilisent la définition suivante pour ce qui constitue une propriété de collection. Le type de propriété de la propriété doit répondre à une des conditions suivantes :  
  
-   Implémente <xref:System.Collections.IList>.  
  
-   Implémente <xref:System.Collections.IDictionary> ou l’équivalent générique (<xref:System.Collections.Generic.IDictionary%602>).  
  
-   Dérive de <xref:System.Array> (pour plus d’informations sur les tableaux en XAML, consultez [x : Array, Extension de balisage](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
-   Implémente <xref:System.Windows.Markup.IAddChild> (une interface définie par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Chacun de ces types dans CLR a une méthode `Add`, qui est utilisée par le processeur XAML pour ajouter des éléments à la collection sous-jacente lors de la création du graphe d’objets.  
  
> [!NOTE]
>  Le type générique `List` et `Dictionary` interfaces (<xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IDictionary%602>) ne sont pas pris en charge pour la détection de collection par le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processeur XAML. Toutefois, vous pouvez utiliser la <xref:System.Collections.Generic.List%601> classe comme classe de base, car elle implémente <xref:System.Collections.IList> directement, ou <xref:System.Collections.Generic.Dictionary%602> comme classe de base, car elle implémente <xref:System.Collections.IDictionary> directement.  
  
 Quand vous déclarez une propriété qui prend une collection, soyez attentif à la façon dont cette valeur de propriété est initialisée dans les nouvelles instances du type. Si vous n’implémentez pas la propriété en tant que propriété de dépendance, il convient que la propriété utilise un champ de stockage qui appelle le constructeur du type collection. Si votre propriété est une propriété de dépendance, vous devez initialiser la propriété de collection dans le cadre du constructeur de type par défaut. La raison en est qu’une propriété de dépendance prend sa valeur par défaut à partir des métadonnées, et vous ne voulez généralement pas que la valeur initiale d’une propriété de collection soit une collection statique et partagée. Il doit exister une instance de la collection pour chaque instance de type conteneur. Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Vous pouvez implémenter un type de collection personnalisé pour votre propriété de collection. En raison du traitement de propriété de collection implicite, le type de collection personnalisé n’a pas besoin de fournir un constructeur par défaut pour pouvoir être utilisé implicitement dans XAML. Cependant, vous pouvez éventuellement fournir un constructeur par défaut pour le type de collection. Cette pratique peut être utile. Sauf si vous fournissez un constructeur par défaut, vous ne pouvez pas déclarer explicitement la collection comme un élément objet. Certains créateurs de balisage peuvent préférer voir la collection explicite comme une question de style de balisage. En outre, un constructeur par défaut peut simplifier les spécifications d’initialisation lorsque vous créez des objets qui utilisent votre type de collection comme une valeur de propriété.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Déclaration de propriétés de contenu XAML  
 Le langage XAML définit le concept de propriété de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Chaque classe utilisable dans la syntaxe d’objet peut avoir une et une seule propriété de contenu XAML. Pour déclarer une propriété à la propriété de contenu XAML pour votre classe, appliquez le <xref:System.Windows.Markup.ContentPropertyAttribute> dans le cadre de la définition de classe. Spécifiez le nom de la propriété de contenu XAML en tant que le <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> dans l’attribut. La propriété est spécifiée sous forme de chaîne par nom, pas comme une construction de réflexion comme <xref:System.Reflection.PropertyInfo>.  
  
 Vous pouvez spécifier qu’une propriété de collection doit être la propriété de contenu XAML. Ceci aboutit à une utilisation de cette propriété où l’élément objet peut avoir un ou plusieurs éléments enfants, sans éléments objet de collection intermédiaires ou de balises d’élément de propriété. Ces éléments sont ensuite traités comme étant la valeur pour la propriété de contenu XAML et ajoutés à l’instance de collection de stockage.  
  
 Certaines propriétés de contenu XAML existantes utilisent le type de propriété `Object`. Cela permet un contenu de valeurs de propriété qui peut prendre primitive telles que de XAML un <xref:System.String> , ainsi que d’une valeur d’objet de référence unique. Si vous suivez ce modèle, votre type est responsable de la détermination du type, ainsi que de la gestion des types possibles. La raison par défaut pour un <xref:System.Object> contenu est de type pour prendre en charge les deux un moyen simple d’ajout de contenu de l’objet sous forme de chaîne (qui reçoit un traitement de présentation par défaut), ou une méthode avancée d’ajout de contenu d’objet qui spécifie une présentation par défaut ou données supplémentaires.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Sérialisation du XAML  
 Dans certains cas, par exemple si vous êtes créateur de contrôles, vous voulez aussi garantir qu’une représentation d’objet qui peut être instanciée en XAML peut également être sérialisée dans un balisage XAML équivalent. Les spécifications de la sérialisation ne sont pas décrites dans cette rubrique. Consultez [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md) et [Sérialisation et arborescence d’éléments](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Vue d’ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Propriétés de dépendance et chargement XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
