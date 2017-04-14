---
title: "Defining Custom Types for Use with .NET Framework XAML Services | Microsoft Docs"
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
  - "defining custom types [XAML Services]"
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
caps.latest.revision: 11
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 11
---
# Defining Custom Types for Use with .NET Framework XAML Services
Lorsque vous définissez des types personnalisés correspondant à des objets métier ou des types n'ayant pas de dépendance sur des infrastructures spécifiques, vous pouvez suivre certains meilleures pratiques pour XAML.  Si vous respectez ces pratiques, les services XAML .NET Framework et leurs lecteurs et writers XAML pourront découvrir les caractéristiques XAML de votre type et le représenter de façon appropriée dans un flux de nœud XAML à l'aide du système de type XAML.  Cette rubrique décrit des meilleures pratiques applicables aux définitions de type, aux définitions de membre et aux attributs CLR des types ou des membres.  
  
## Modèles de constructeur et définitions de type pour XAML  
 Pour pouvoir être instanciée comme un élément objet en XAML, une classe personnalisée doit remplir les conditions suivantes :  
  
-   La classe personnalisée doit être publique et exposer un constructeur public par défaut \(sans paramètre\).  \(Consultez la section suivante pour prendre connaissance des remarques sur les structures.\)  
  
-   La classe personnalisée ne doit pas être une classe imbriquée.  Le « point » supplémentaire présent dans le chemin de nom complet rend la division d'espace de noms de classe ambiguë et interfère avec d'autres fonctionnalités XAML telles que les propriétés jointes.  
  
 Si un objet peut être instancié en tant qu'élément objet, l'objet créé peut remplir la forme d'élément de propriété de toute propriété acceptant l'objet comme type sous\-jacent.  
  
 Vous pouvez encore fournir des valeurs d'objet pour les types qui ne sont pas conformes à ces critères si vous activez un convertisseur de valeurs.  Pour plus d'informations, consultez [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
### Structures  
 Les structures peuvent toujours être construites en XAML, par le biais de la définition du CLR.  En effet, un compilateur CLR crée implicitement un constructeur par défaut pour une structure.  Ce constructeur initialise toutes les valeurs par défaut de toutes les propriétés.  
  
 Dans certains cas, le comportement de construction par défaut d'une structure n'est pas souhaitable.  Cela peut être dû au fait que la structure est destinée à remplir des valeurs et à fonctionner conceptuellement comme une union.  En tant qu'union, les valeurs qu'elle contient peuvent avoir des interprétations mutuellement exclusives et, par conséquent, aucune de ses propriétés ne peut être définie.  <xref:System.Windows.GridLength> est un exemple de ce type de structure existant dans le vocabulaire WPF.  Ces structures doivent implémenter un convertisseur de type de telle sorte que les valeurs puissent être exprimées sous forme d'attribut, à l'aide de conventions de chaîne qui créent les différents modes ou interprétations des valeurs de structure.  La structure doit également exposer un comportement semblable pour la construction de code via un constructeur non défini par défaut.  
  
### Interfaces  
 Les interfaces peuvent être utilisées comme types sous\-jacents des membres.  Le système de type XAML vérifie la liste assignable et attend que l'objet fourni comme valeur puisse être assigné à l'interface.  Aucun concept ne définit la façon dont l'interface doit être présentée en tant que type XAML, dans la mesure où un type assignable approprié prend en charge les spécifications de construction XAML.  
  
### Méthodes de fabrique  
 Les méthodes de fabrique constituent une fonctionnalité XAML 2009.  Elles modifient le principe XAML selon lequel les objets doivent avoir des constructeurs par défaut.  Elles ne sont pas documentées dans cette rubrique.  Consultez [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md).  
  
## Énumérations  
 Les énumérations suivent le comportement de conversion de type natif XAML.  Les noms de constantes d'énumération spécifiés en XAML sont résolus par rapport au type énumération sous\-jacent et retournent la valeur d'énumération à un writer d'objet XAML.  
  
 XAML prend en charge une utilisation des énumérations avec indicateurs par le biais de <xref:System.FlagsAttribute>.  Pour plus d'informations, consultez [Syntaxe XAML en détail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  \(La rubrique [Syntaxe XAML en détail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) est rédigée pour les utilisateurs de WPF, mais la plupart des informations qu'elle contient s'appliquent au code XAML qui n'est pas spécifique à une infrastructure d'implémentation particulière.\)  
  
## Définitions de membre  
 Les types peuvent définir des membres pour l'utilisation de XAML.  Ils ont la possibilité de définir des membres utilisables en XAML même s'ils ne peuvent pas eux\-mêmes être employés dans ce langage.  Cette possibilité est due à l'héritage du CLR.  Dans la mesure où un type qui hérite du membre prend en charge l'utilisation de XAML en tant que type, et que le membre prend en charge l'utilisation de XAML pour son type sous\-jacent ou dispose d'une syntaxe XAML native, ce membre peut être utilisé en XAML.  
  
### Propriétés  
 Si vous définissez les propriétés comme propriété CLR publiques à l'aide des méthodes d'accesseur `get` et `set` classiques et de mots\-clés du langage, le système de type XAML peut signaler la propriété comme membre disposant des informations appropriées pour les propriétés <xref:System.Xaml.XamlMember>, comme par exemple <xref:System.Xaml.XamlMember.IsReadPublic%2A> et <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Les propriétés spécifiques peuvent activer une syntaxe de texte en appliquant <xref:System.ComponentModel.TypeConverterAttribute>.  Pour plus d'informations, consultez [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 En l'absence d'une syntaxe de texte ou d'une conversion XAML native, et en l'absence d'indirection supplémentaire telle que l'utilisation d'une extension de balisage, le type d'une propriété \(<xref:System.Xaml.XamlMember.TargetType%2A> dans le système de type XAML\) doit pouvoir retourner une instance à un writer d'objet XAML en traitant le type cible comme un type CLR.  
  
 Lors de l'utilisation de XAML 2009, [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md) peut être employé pour fournir des valeurs si les considérations ci\-dessus ne sont pas réunies, mais il s'agit plutôt d'un problème d'utilisation que d'un problème de définition de type.  
  
### Événements  
 Si vous définissez des événements en tant qu'événement CLR public, le système de type XAML peut les signaler en tant que membre, avec <xref:System.Xaml.XamlMember.IsEvent%2A> ayant la valeur `true`.  Le câblage des gestionnaires d'événements n'est pas dans la portée des fonctions des services XAML .NET Framework et relève d'infrastructures et implémentations spécifiques.  
  
### Méthodes  
 Le code inline des méthodes n'est pas une fonction XAML par défaut.  Dans la plupart des cas, vous ne référencez pas directement les membres de méthode à partir de XAML et le rôle des méthodes en XAML consiste uniquement à prendre en charge des modèles XAML spécifiques.  La directive x:FactoryMethod \([x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md)\) est une exception.  
  
### Champs  
 Les règles de conception du CLR déconseillent l'utilisation des champs non statiques.  Vous pouvez accéder aux valeurs des champ statiques uniquement via l'extension de balisage x:Static \([x:Static Markup Extension](../../../docs/framework/xaml-services/x-static-markup-extension.md)\) ; dans ce cas, aucune disposition particulière n'est nécessaire dans la définition du CLR afin d'exposer un champ pour les utilisations de [x:Static](../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
## Membres pouvant être attachés  
 Les membres pouvant être attachés sont exposés à XAML via un modèle de méthode d'accesseur sur un type de définition.  Le type de définition lui\-même ne doit pas nécessairement être utilisable en XAML en tant qu'objet.  Vous pouvez déclarer une classe de service dont le rôle est d'être propriétaire du membre pouvant être attaché et d'implémenter les comportements connexes, sans autre fonction \(représentation de l'interface utilisateur, par exemple\).  Pour les sections suivantes, l'espace réservé *PropertyName* représente le nom du membre pouvant être attaché.  Ce nom doit être valide dans la grammaire XamlName \([XamlName, grammaire](../../../docs/framework/xaml-services/xamlname-grammar.md)\).  
  
 Veillez à éviter les collisions de nom entre ces modèles et d'autres méthodes d'un type.  Si un membre existant correspond à un des modèles, il peut être interprété comme une voie d'accès au membre pouvant être attaché par un processeur XAML même si vous ne le souhaitez pas.  
  
#### Accesseur GetPropertyName  
 La signature de l'accesseur `Get`*NomPropriété* doit être la suivante :  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   L'objet `target` peut être défini comme un type plus spécifique dans votre implémentation.  Vous pouvez utiliser cette méthode pour définir la portée d'utilisation du membre pouvant être attaché ; les utilisations hors de la portée prévue lèveront des exceptions de casts non valides qui sont ensuite signalées par une erreur d'analyse XAML.  Le nom de paramètre `target` n'est pas obligatoire ; ce paramètre est nommé `target` par convention dans la plupart des implémentations.  
  
-   La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation.  
  
 Pour prendre en charge une syntaxe de texte compatible avec <xref:System.ComponentModel.TypeConverter> pour l'utilisation des attributs du membre pouvant être attaché, appliquez <xref:System.ComponentModel.TypeConverterAttribute> à l'accesseur `Get` *PropertyName*.  L'approche qui consiste à appliquer l'attribut à `get` plutôt qu'à `set` peut sembler non intuitive ; toutefois, cette convention permet de prendre en charge le concept de membres pouvant être attachés, accessibles en lecture seule et sérialisables, ce qui s'avère utile dans les scénarios de concepteur.  
  
#### Accesseur SetPropertyName  
 La signature de l'accesseur Set*PropertyName* doit être la suivante :  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   L'objet `target` peut être défini comme un type plus spécifique dans votre implémentation, avec la même logique et les mêmes conséquences que celles décrites dans la section précédente.  
  
-   L'objet `value` peut être défini comme un type plus spécifique dans votre implémentation.  
  
 Rappelez\-vous que la valeur de cette méthode est l'entrée provenant de l'utilisation de XAML, en général sous forme d'attribut.  À partir d'une forme d'attribut, un convertisseur de valeurs doit prendre en charge une syntaxe de texte et l'attribut doit être appliqué à l'accesseur `Get`*PropertyName*.  
  
### Magasins de membres pouvant être attachés  
 Les méthodes d'accesseur ne sont généralement pas suffisantes pour permettre de placer des valeurs de membres pouvant être attachés dans un graphique d'objet ou récupérer des valeurs dans le graphique d'objet et les sérialiser correctement.  Pour fournir cette fonctionnalité, les objets `target` des signatures d'accesseur précédentes doivent être capables d'enregistrer des valeurs.  Le mécanisme de stockage doit être compatible avec le principe de membre pouvant être attaché suivant : le membre est susceptible d'être lié aux cibles pour lesquelles le membre pouvant être attaché ne figure pas dans la liste des membres.  Les services XAML .NET Framework fournissent une technique d'implémentation pour des magasins de membres pouvant être attachés via les API <xref:System.Xaml.IAttachedPropertyStore> et <xref:System.Xaml.AttachablePropertyServices>.  L'élément <xref:System.Xaml.IAttachedPropertyStore> est utilisé par les writers XAML pour découvrir l'implémentation des magasins et doit être implémenté sur le type `target` des accesseurs.  Les API statiques <xref:System.Xaml.AttachablePropertyServices> sont utilisées dans le corps des accesseurs et font référence au membre pouvant être attaché par son <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## Attributs CLR XAML  
 Il est important d'associer vos types, membres et assemblys à des attributs appropriés pour signaler les informations de système de type XAML aux services XAML .NET Framework.  Cette opération est utile si vous prévoyez d'utiliser vos types avec des systèmes XAML basés directement sur les lecteurs et writers XAML des services XAML .NET Framework, ou si vous définissez ou utilisez une infrastructure faisant appel à XAML et basée sur ces lecteurs et writers XAML.  
  
 Pour obtenir une liste de tous les attributs XAML qui sont utiles pour la prise en charge XAML de vos types personnalisés, consultez [XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## Utilisation  
 L'utilisation de types personnalisés requiert que l'auteur du balisage mappe un préfixe pour l'assembly et l'espace de noms CLR qui contiennent ces types.  Cette procédure n'est pas documentée dans cette rubrique.  
  
## Niveau d'accès  
 XAML permet de charger et d'instancier les types qui disposent d'un niveau d'accès `internal`.  Cette fonction est fournie afin que le code utilisateur puisse définir ses propres types, puis instancier les classes de marques faisant également partie de la même portée de code utilisateur.  
  
 Exemple de WPF : chaque fois que le code utilisateur définit un élément <xref:System.Windows.Controls.UserControl> conçu comme une méthode de refactorisation d'un comportement d'interface utilisateur mais ne faisant pas partie d'un mécanisme d'extension qui pourrait être implicite via la déclaration de la classe de prise en charge avec un niveau d'accès `public`.  Un tel élément <xref:System.Windows.Controls.UserControl> peut être déclaré avec un accès `internal` si le code de prise en charge est compilé dans le même assembly à partir duquel il est référencé comme type XAML.  
  
 Pour une application chargeant du langage XAML sous confiance totale et utilisant un élément <xref:System.Xaml.XamlObjectWriter>, le chargement de classes avec niveau d'accès `internal` est toujours activé.  
  
 Dans le cas d'une application chargeant du langage XAML avec un niveau de confiance partielle, vous pouvez contrôler les caractéristiques de niveau d'accès en utilisant l'élément <xref:System.Xaml.Permissions.XamlAccessLevel> à l'aide de l'API.  En outre, les mécanismes de différé \(système de modèles WPF, par exemple\) doivent être en mesure de propager les autorisations de niveau d'accès et de les conserver pour les évaluations finales au moment de l'exécution ; cela est géré en interne via la transmission des informations <xref:System.Xaml.Permissions.XamlAccessLevel>.  
  
### Implémentation WPF  
 Le langage XAML WPF utilise un modèle d'accès à niveau de confiance partielle présentant la caractéristique suivante : si BAML est chargé avec un niveau de confiance partielle, l'accès est limité à l'élément <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> pour l'assembly qui est la source BAML.  Pour le différé, WPF utilise l'élément <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=fullName> comme mécanisme de transmission des informations du niveau d'accès.  
  
 Dans la terminologie XAML WPF, un *type interne* est un type défini par le même same assembly que celui qui inclut le XAML de référencement.  Ce type peut être mappé par un espace de noms XAML qui omet délibérément la partie assembly\= d'un mappage ; exemple : `xmlns:local="clr-namespace:WPFApplication1"`.  Si BAML référence un type interne et que ce type dispose d'un niveau d'accès `internal`, cela génère une classe `GeneratedInternalTypeHelper` pour l'assembly.  Si vous souhaitez éviter `GeneratedInternalTypeHelper`, vous devez utiliser un niveau d'accès `public` ou placer la classe appropriée dans un assembly séparé et rendre celui\-ci dépendant.  
  
## Voir aussi  
 [XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)   
 [XAML Services](../../../docs/framework/xaml-services/index.md)