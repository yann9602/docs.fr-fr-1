---
title: "Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 0b35c35be7351fdf45157153ce6ca55fc763c3ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework
Lorsque vous définissez des types personnalisés qui sont des objets métier ou sont des types qui n’ont pas d’une dépendance sur des infrastructures spécifiques, il existe certaines meilleures pratiques pour XAML, vous pouvez suivre. Si vous suivez ces pratiques, les Services XAML .NET Framework et ses lecteurs XAML et les writers XAML peuvent découvrir les caractéristiques XAML de votre type et lui donner une représentation appropriée dans un flux de nœud XAML à l’aide du système de type XAML. Cette rubrique décrit les meilleures pratiques pour les définitions de type, définitions de membre et aux attributs CLR des types ou membres.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Modèles de constructeur et définitions de Type pour XAML  
 Pour être instancié comme un élément objet en XAML, une classe personnalisée doit remplir les conditions suivantes :  
  
-   La classe personnalisée doit être publique et doit exposer un constructeur public de valeur par défaut (sans paramètre). (Consultez la section suivante pour des remarques concernant les structures.)  
  
-   La classe personnalisée ne doit pas être une classe imbriquée. Le « point » dans le chemin d’accès du nom complet extra effectue la division de l’espace de noms classe ambiguë et interfère avec d’autres fonctionnalités XAML telles que les propriétés jointes.  
  
 Si un objet peut être instancié comme un élément objet, l’objet créé peut remplir le formulaire d’élément de propriété de toutes les propriétés qui acceptent l’objet en tant que type sous-jacent.  
  
 Vous pouvez toujours fournir des valeurs d’objet pour les types qui ne répondent pas à ces critères, si vous activez un convertisseur de valeurs. Pour plus d’informations, consultez [convertisseurs de Type et Extensions de balisage pour XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Structures  
 Les structures peuvent toujours être construites en XAML, par définition du CLR. Il s’agit, car un compilateur CLR crée implicitement un constructeur par défaut pour une structure. Ce constructeur initialise toutes les valeurs de propriétés à leurs valeurs par défaut.  
  
 Dans certains cas, le comportement de construction par défaut pour une structure n’est pas souhaitable. Cela peut être, car la structure est destinée à remplir des valeurs et à fonctionner conceptuellement comme une union. En tant qu’union, les valeurs contenues peuvent avoir des interprétations mutuellement exclusives, et par conséquent, aucune de ses propriétés peuvent être définies. Est un exemple d’une telle structure dans le vocabulaire WPF <xref:System.Windows.GridLength>. Ces structures doivent implémenter un convertisseur de type afin que les valeurs peuvent être exprimées sous forme d’attribut, à l’aide des conventions de chaîne qui créent les différents modes ou interprétations des valeurs de la structure. La structure doit également exposer un comportement similaire pour la construction de code via un constructeur non défini par défaut.  
  
### <a name="interfaces"></a>Interfaces  
 Interfaces peuvent être utilisés en tant que types sous-jacents des membres. Le système de type XAML vérifie la liste assignable et attend que l’objet qui est fournie en tant que la valeur peut être assigné à l’interface. Il n’existe aucun concept de la façon dont l’interface doit être présentée en un type XAML tant qu’un type assignable approprié prend en charge les spécifications de construction XAML.  
  
### <a name="factory-methods"></a>Méthodes de fabrique  
 Méthodes de fabrique sont une fonctionnalité de XAML 2009. Ils modifient le principe XAML que les objets doivent avoir des constructeurs par défaut. Méthodes de fabrique ne sont pas documentées dans cette rubrique. Consultez [x : FactoryMethod, Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Énumérations  
 Les énumérations ont un comportement de conversion de type natif XAML. Noms de constantes d’énumération spécifiés en XAML sont résolus par rapport au type énumération sous-jacent et retournent la valeur d’énumération à un writer d’objet XAML.  
  
 XAML prend en charge une utilisation d’indicateurs pour les énumérations avec <xref:System.FlagsAttribute> appliquée. Pour plus d’informations, consultez [XAML Syntax In Detail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md). ([XAML Syntax In Detail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) est rédigée pour les utilisateurs WPF, mais la plupart des informations dans cette rubrique s’applique pour XAML qui n’est pas spécifique à une infrastructure d’implémentation particulière.)  
  
## <a name="member-definitions"></a>Définitions de membre  
 Types peuvent définir des membres pour l’utilisation de XAML. Il est possible de définir des membres utilisables en XAML même si ce type spécifique n’est pas utilisable en XAML. Cela est possible en raison de l’héritage du CLR. Tant que certains type qui hérite du membre prend en charge l’utilisation XAML en tant que type, et le membre prend en charge l’utilisation de XAML pour son type sous-jacent ou a une syntaxe XAML native, ce membre est utilisable en XAML.  
  
### <a name="properties"></a>Propriétés  
 Si vous définissez les propriétés comme propriété CLR publique à l’aide du type CLR `get` et `set` accesseur et méthodes language, le système de type XAML peut signaler la propriété en tant que membre avec les informations appropriées fournies pour <xref:System.Xaml.XamlMember> propriétés, telles que <xref:System.Xaml.XamlMember.IsReadPublic%2A> et <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Propriétés spécifiques peuvent activer une syntaxe de texte en appliquant <xref:System.ComponentModel.TypeConverterAttribute>. Pour plus d’informations, consultez [convertisseurs de Type et Extensions de balisage pour XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 En l’absence d’une syntaxe de texte ou d’une conversion XAML native et en l’absence d’indirection supplémentaire, comme une extension de balisage, le type d’une propriété (<xref:System.Xaml.XamlMember.TargetType%2A> système de type dans le code XAML) doit être en mesure de retourner une instance à un writer d’objet XAML en traitant le t type de cible comme un type CLR.  
  
 L’utilisation de XAML 2009, [x : Reference, Extension de balisage](../../../docs/framework/xaml-services/x-reference-markup-extension.md) peut être utilisé pour fournir des valeurs si les considérations précédentes ne sont pas remplies ; Toutefois, ce n’est plus d’un problème d’utilisation qu’un problème de définition de type.  
  
### <a name="events"></a>Événements  
 Si vous définissez des événements en tant qu’événement CLR public, le système de type XAML peut signaler l’événement en tant que membre avec <xref:System.Xaml.XamlMember.IsEvent%2A> comme `true`. Les gestionnaires d’événements de câblage n’est pas dans l’étendue de capacités de Services XAML .NET Framework ; en revanche, les implémentations et les infrastructures spécifiques.  
  
### <a name="methods"></a>Méthodes  
 Code inline des méthodes n’est pas une fonctionnalité XAML par défaut. Dans la plupart des cas vous ne faites pas directement référence membres de la méthode à partir de XAML, et le rôle des méthodes en XAML est uniquement pour prendre en charge des modèles XAML spécifiques. [Directive x : FactoryMethod](../../../docs/framework/xaml-services/x-factorymethod-directive.md) est une exception.  
  
### <a name="fields"></a>Champs  
 Règles de conception CLR décourager les champs non statiques. Pour les champs statiques, vous pouvez accéder à des valeurs de champ statique uniquement via [x : Static, Extension de balisage](../../../docs/framework/xaml-services/x-static-markup-extension.md); dans ce cas vous ne font rien spéciale dans la définition du CLR pour exposer un champ pour [x : Static](../../../docs/framework/xaml-services/x-static-markup-extension.md) utilisations.  
  
## <a name="attachable-members"></a>Membres pouvant être attachés  
 Membres pouvant être attachés sont exposés à XAML via un modèle de méthode d’accesseur sur un type de définition. Le type de définition n’a pas besoin être utilisable en XAML en tant qu’objet. En fait, il est courant pour déclarer une classe de service dont le rôle est propriétaire du membre et implémenter les comportements connexes, mais autre fonction comme une représentation de l’interface utilisateur. Les sections suivantes, l’espace réservé *PropertyName* représente le nom du membre pouvant être attaché. Ce nom doit être valide dans le [XamlName, grammaire](../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 Soyez prudent de collisions de nom entre ces modèles et d’autres méthodes d’un type. Si un membre existant qui correspond à l’un des modèles, il peut être interprété comme une voie d’accès au membre pouvant être attaché par un processeur XAML même si cela n’était pas votre intention.  
  
#### <a name="the-getpropertyname-accessor"></a>L’accesseur GetPropertyName  
 La signature pour l’accesseur `Get`*NomPropriété* doit être :  
  
 `public static object Get` *NomPropriété* `(object`  `target` `)`  
  
-   L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Vous pouvez l’utiliser pour étendre l’utilisation du membre pouvant être attaché ; utilisations en dehors de la portée prévue lèveront des exceptions de cast non valide puis exposés par une erreur d’analyse XAML. Le nom du paramètre `target` n’est pas obligatoire, mais est nommé `target` par convention, dans la plupart des implémentations.  
  
-   La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation.  
  
 Pour prendre en charge un <xref:System.ComponentModel.TypeConverter> syntaxe de texte activé pour l’utilisation d’attributs du membre pouvant être attaché, appliquez <xref:System.ComponentModel.TypeConverterAttribute> à la `Get` *PropertyName* accesseur. Application à la `get` au lieu du `set` peut sembler non intuitive ; Toutefois, cette convention peut prendre en charge le concept de membres en lecture seule pouvant être attachés qui sont sérialisables, qui est utile dans les scénarios de concepteur.  
  
#### <a name="the-setpropertyname-accessor"></a>L’accesseur SetPropertyName  
 La signature pour le jeu de*PropertyName* accesseur doit être :  
  
 `public static void Set` *NomPropriété* `(object`  `target` `, object`  `value` `)`  
  
-   Le `target` objet peut être spécifié comme un type plus spécifique dans votre implémentation, avec la même logique et les conséquences, comme décrit dans la section précédente.  
  
-   L’objet `value` peut être défini comme un type plus spécifique dans votre implémentation.  
  
 N’oubliez pas que la valeur de cette méthode est l’entrée provenant de l’utilisation de XAML, généralement sous la forme d’attribut. À partir de la forme d’attribut doit être prise en charge de convertisseur de valeur pour une syntaxe de texte, et vous l’attribut le `Get` *PropertyName* accesseur.  
  
### <a name="attachable-member-stores"></a>Magasins de membres pouvant être attachés  
 Les méthodes d’accesseur ne sont généralement pas suffisamment pour fournir un moyen d’y placer les valeurs de membre pouvant être attaché un graphique d’objet, ou pour extraire des valeurs de graphique d’objet et les sérialiser correctement. Pour offrir cette fonctionnalité, le `target` objets dans les signatures d’accesseur précédentes doivent être capables de stocker des valeurs. Le mécanisme de stockage doit être conforme au principe de membre pouvant être attaché le membre est pouvant être attaché aux cibles où le membre pouvant être attaché n’est pas dans la liste des membres. Les Services XAML .NET framework fournit une technique d’implémentation pour le membre pouvant être attaché stocke via les API <xref:System.Xaml.IAttachedPropertyStore> et <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore>est utilisé par les writers XAML pour découvrir l’implémentation du magasin et doit être implémentée sur le type qui est la `target` des accesseurs. La méthode statique <xref:System.Xaml.AttachablePropertyServices> API sont utilisées dans le corps des accesseurs et faire référence au membre pouvant être attaché par son <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Attributs CLR XAML  
 Attribution correctement des types, des membres et des assemblys est importante dans l’ordre au rapport les informations de système de type XAML pour les Services XAML .NET Framework. Cela est utile si vous avez l’intention d’utiliser avec des systèmes XAML basés directement sur les lecteurs XAML des Services XAML .NET Framework et les writers XAML vos types, ou si vous définissez ou utilisez une infrastructure utilisant XAML qui est basée sur les lecteurs XAML et les writers XAML.  
  
 Pour obtenir la liste de chaque attribut XAML qui s’applique à la prise en charge XAML de vos types personnalisés, consultez [Related les attributs CLR pour les bibliothèques et Types personnalisés](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Utilisation  
 L’utilisation de types personnalisés requiert que l’auteur du balisage mappe un préfixe pour l’assembly et l’espace de noms CLR contenant le type personnalisé. Cette procédure n’est pas documentée dans cette rubrique.  
  
## <a name="access-level"></a>Niveau d’accès  
 XAML fournit un moyen pour charger et instancier des types qui ont un `internal` niveau d’accès. Cette fonctionnalité est fournie afin que le code utilisateur peut définir ses propres types, puis instancier les classes à partir du balisage fait également partie de la même portée de code utilisateur.  
  
 Par exemple à partir de WPF, chaque fois que le code utilisateur définit un <xref:System.Windows.Controls.UserControl> qui est conçu comme un moyen de refactoriser un comportement de l’interface utilisateur, mais pas dans le cadre de n’importe quel mécanisme d’extension possibles qui peut être déduite d’une déclaration de la classe de prise en charge avec `public` niveau d’accès. Ces un <xref:System.Windows.Controls.UserControl> peuvent être déclarées avec `internal` accéder si le code de stockage est compilé dans le même assembly à partir duquel il est référencé comme un type XAML.  
  
 Pour une application qui charge le XAML sous confiance totale et utilise <xref:System.Xaml.XamlObjectWriter>, chargement de classes avec `internal` niveau d’accès est toujours activé.  
  
 Pour une application qui charge le XAML en confiance partielle, vous pouvez contrôler les caractéristiques de niveau d’accès à l’aide de la <xref:System.Xaml.Permissions.XamlAccessLevel> API. En outre, les mécanismes de report (par exemple, le système de modèle WPF) doivent pouvoir propager toutes les autorisations de niveau d’accès et de les conserver pour les évaluations de l’exécution éventuelle ; Cela est contrôlé en interne en passant le <xref:System.Xaml.Permissions.XamlAccessLevel> plus d’informations.  
  
### <a name="wpf-implementation"></a>Implémentation de WPF  
 XAML WPF utilise un modèle d’accès de niveau de confiance partiel où Si BAML est chargé avec une confiance partielle, l’accès est limité à <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> pour l’assembly qui est la source BAML. Report, WPF utilise <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> comme un mécanisme pour passer les informations au niveau d’accès.  
  
 Dans la terminologie XAML WPF, un *type interne* est un type qui est défini par le même assembly qui inclut également le XAML de référencement. Un tel type permettre être mappé via un espace de noms XAML qui omet délibérément l’assembly = partie d’un mappage, par exemple, `xmlns:local="clr-namespace:WPFApplication1"`.  Si BAML référence un type interne et que le type a `internal` accéder à niveau, cette opération génère un `GeneratedInternalTypeHelper` classe pour l’assembly. Si vous souhaitez éviter `GeneratedInternalTypeHelper`, vous devez utiliser `public` niveau d’accès ou doit tenir compte de la classe appropriée dans un assembly séparé et rendre celui-ci dépendant.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs CLR XAML pour les bibliothèques et types personnalisés](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)  
 [Services XAML](../../../docs/framework/xaml-services/index.md)
