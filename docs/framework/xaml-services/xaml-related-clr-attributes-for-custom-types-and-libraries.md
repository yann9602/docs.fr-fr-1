---
title: "Attributs CLR XAML pour les bibliothèques et types personnalisés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 9a445d7e730ecb743d5e4086ec682b12a7bf3ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Attributs CLR XAML pour les bibliothèques et types personnalisés
Cette rubrique décrit les attributs du commun language runtime (CLR) qui sont définis par les Services XAML .NET Framework. Elle décrit également les autres attributs CLR qui sont définis dans le .NET Framework qui ont un scénario XAML pour l’application aux assemblys ou types. Attribution des assemblys, des types ou membres avec ces attributs CLR fournit des informations de système de type XAML relatives à vos types. Vous trouverez des informations à tout consommateur XAML qui utilise les Services XAML .NET Framework pour le traitement de flux de nœud XAML directement ou via les lecteurs XAML dédiés et les writers XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Attributs CLR XAML pour les Types et membres personnalisés  
 À l’aide d’attributs CLR implique que vous définissez vos types à l’aide de CLR global, sinon ces attributs ne sont pas disponibles. Si vous utilisez le CLR pour définir le type de sauvegarde, le contexte de schéma XAML par défaut utilisé par les writers XAML des Services XAML .NET Framework peut lire les attributs CLR par la réflexion sur les assemblys de stockage.  
  
 Les sections suivantes décrivent les attributs XAML que vous pouvez appliquer aux types ou membres personnalisés. Chaque attribut CLR communique des informations qui s’applique à un système de type XAML. Dans le chemin de chargement, les informations d’attributs permettent au lecteur XAML former un flux de nœud XAML valide, ou il permet le writer XAML de produire un graphique d’objet valide. Dans Enregistrer le chemin d’accès, les informations d’attributs soit permettent au lecteur XAML de former un flux de nœud XAML valide qui reconstitue les informations de système de type XAML ; ou bien, il déclare des indicateurs de sérialisation ou de la configuration requise pour le writer XAML ou d’autres consommateurs XAML.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **S’applique à :** classe, propriété, ou `get` membres accesseur qui prennent en charge les propriétés pouvant être attachées.  
  
 **Arguments :** None  
  
 <xref:System.Windows.Markup.AmbientAttribute>Indique que la propriété ou toutes les propriétés qui prennent le type avec attributs, doivent être interprétées selon le concept de propriété ambiante en XAML. Le concept de caractère ambiant renvoie à la façon dont les processeurs XAML déterminent les propriétaires de types des membres. Une propriété ambiante est une propriété où la valeur est censée être disponible dans le contexte de l’analyseur lors de la création d’un graphique d’objet, mais pour laquelle la recherche de membre de type standard est interrompue pour le nœud XAML immédiat création du jeu.  
  
 Le concept d’ambiant peut être appliqué aux membres pouvant être attachés, qui ne sont pas représentés en tant que propriétés en termes de la façon dont les attributs CLR définissent <xref:System.AttributeTargets>. L’utilisation des attributs de méthode doit être appliquée uniquement dans le cas d’un `get` accesseur qui prend en charge l’utilisation pouvant être attachée pour XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** une chaîne qui spécifie le nom de la propriété qui correspond à un argument de constructeur unique.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>Spécifie qu’un objet peut être initialisé à l’aide d’une syntaxe de constructeur par défaut non et qu’une propriété portant le nom spécifié fournit les informations de construction. Ces informations sont principalement destinées à la sérialisation XAML. Pour plus d'informations, consultez <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** une chaîne qui spécifie le nom d’un membre du type avec attributs.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>Indique que la propriété nommée par l’argument doit servir de la propriété de contenu XAML pour ce type. Définition de la propriété de contenu XAML hérite de tous les types dérivés qui peuvent être assignés au type. Vous pouvez remplacer la définition d’un type dérivé spécifique en appliquant <xref:System.Windows.Markup.ContentPropertyAttribute> sur spécifique au type dérivé.  
  
 Pour la propriété qui sert à la propriété de contenu XAML, le balisage pour la propriété property, élément peut être omis dans l’utilisation de XAML. En général, vous désignez des propriétés de contenu XAML qui favorisent un balisage XAML simplifié pour vos modèles de contenu et de la relation contenant-contenu. Étant donné que seul un membre peut être désigné en tant que propriété de contenu XAML, vous devez parfois des choix de conception pour rendre sur lesquels du conteneur de plusieurs propriétés d’un type doivent être désignées comme propriété de contenu XAML. Les autres propriétés de conteneur doivent être utilisées avec les éléments de propriété explicites.  
  
 Dans le flux de nœud XAML, les propriétés de contenu XAML produisent encore `StartMember` et `EndMember` nœuds, en utilisant le nom de la propriété de la <xref:System.Xaml.XamlMember>. Pour déterminer si un membre est la propriété de contenu XAML, examinez le <xref:System.Xaml.XamlType> valeur à partir de la `StartObject` positionner et obtenir la valeur de <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **S’applique à :** (classe), en particulier les types de collection.  
  
 **Arguments :** A <xref:System.Type> qui spécifie le type à utiliser comme type de wrapper de contenu pour le contenu étranger.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>Spécifie un ou plusieurs types sur le type de collection associé qui sera utilisé pour encapsuler le contenu étranger. Le contenu étranger fait référence aux cas où les contraintes de système de type sur le type de la propriété de contenu ne capturent pas tous les cas de contenu possibles qui prend en charge l’utilisation de XAML pour le type propriétaire. Par exemple, prise en charge XAML pour le contenu d’un type particulier peut prendre en charge les chaînes dans un type générique fortement typé <xref:System.Collections.ObjectModel.Collection%601>. Wrappers de contenu sont utiles pour migrer les conventions de balisage préexistantes vers la conception XAML des valeurs assignables pour les collections, telles que les modèles de contenu migration liées au texte.  
  
 Pour spécifier plusieurs types de wrapper de contenu, appliquez l’attribut plusieurs fois.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **S’applique à :** propriété  
  
 **Arguments :** une chaîne qui spécifie le nom d’un autre membre du type avec attributs.  
  
 <xref:System.Windows.Markup.DependsOnAttribute>Indique que la propriété avec attributs dépend de la valeur d’une autre propriété. Appliquer cet attribut à une définition de propriété garantit que les propriétés dépendantes sont traitées en premier dans l’écriture d’objet XAML. Utilisations de <xref:System.Windows.Markup.DependsOnAttribute> spécifier les cas exceptionnels de propriétés sur les types où un ordre spécifique d’analyse doit être suivi de la création d’objet valide.  
  
 Vous pouvez appliquer plusieurs <xref:System.Windows.Markup.DependsOnAttribute> cas à une définition de propriété.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **S’applique à :** (classe), qui est censé être un <xref:System.Windows.Markup.MarkupExtension> type dérivé.  
  
 **Arguments :** A <xref:System.Type> qui spécifie le type le plus précis pouvant être attendu comme le `ProvideValue` résultat d’avec attributs <xref:System.Windows.Markup.MarkupExtension>.  
  
 Pour plus d’informations, consultez [Extensions de balisage pour XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** prend en charge deux formes d’attribution :  
  
-   Chaîne qui spécifie le nom d’une propriété sur le type avec attributs.  
  
-   Une chaîne qui spécifie le nom d’une propriété et un <xref:System.Type> pour le type qui définit la propriété nommée. Ce formulaire est pour la spécification d’un membre pouvant être attaché en tant que la propriété de la portée de nom XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>Spécifie une propriété qui fournit la valeur de la portée de nom XAML pour la classe avec attributs. La propriété de la portée de nom XAML est censée faire référence à un objet qui implémente <xref:System.Windows.Markup.INameScope> et contient la portée de nom XAML réelle, son magasin et son comportement.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** une chaîne qui spécifie le nom de la propriété de nom d’exécution sur le type avec attributs.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>signale une propriété du type avec attributs qui mappe au XAML [Directive x : Name](../../../docs/framework/xaml-services/x-name-directive.md). La propriété doit être de type <xref:System.String> et doit être en lecture/écriture.  
  
 Hérite de la définition de tous les types dérivés qui peuvent être assignés au type. Vous pouvez remplacer la définition d’un type dérivé spécifique en appliquant <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> sur spécifique au type dérivé.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **S’applique à :** Types  
  
 **Arguments :** None.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>est appliqué aux types spécifiques qui peuvent apparaître comme des éléments enfants dans un contenu significatif (contenu présent dans une collection qui a <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>s’applique principalement aux enregistrement chemin d’accès, mais n’est disponible dans le système de type XAML dans le chemin de chargement en examinant <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [traitement des espaces blancs en XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Documentation de référence :**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **S’applique à :** classe, propriété, méthode (le seul cas de méthode XAML valide est un `get` accesseur qui prend en charge d’un membre pouvant être attaché).  
  
 **Arguments :** le <xref:System.Type> de la <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>dans un XAML contexte fait référence à un personnalisé <xref:System.ComponentModel.TypeConverter>. Cela <xref:System.ComponentModel.TypeConverter> fournit le comportement de conversion de type pour les types personnalisés ou les membres de ce type.  
  
 Vous appliquez le <xref:System.ComponentModel.TypeConverterAttribute> à votre type de référence de votre implémentation de convertisseur de type d’attribut. Vous pouvez définir des convertisseurs de type pour XAML sur les classes, structures ou des interfaces. Vous n’avez pas besoin de fournir une conversion de type pour les énumérations, que la conversion est activée en mode natif.  
  
 Le convertisseur de type doit être en mesure de convertir une chaîne qui est utilisée pour les attributs ou le texte d’initialisation dans le balisage, vers le type de destination prévue. Pour plus d’informations, consultez [TypeConverters and XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Au lieu d’appliquer à toutes les valeurs d’un type, un comportement de convertisseur de type pour XAML permettre également être établi sur une propriété spécifique. Dans ce cas, vous appliquez <xref:System.ComponentModel.TypeConverterAttribute> à la définition de propriété (la définition externe, et non pas la spécifique `get` et `set` définitions).  
  
 Un comportement de convertisseur de type pour l’utilisation XAML d’un membre pouvant être attaché personnalisé peut être assigné en appliquant <xref:System.ComponentModel.TypeConverterAttribute> à la `get` accesseur de méthode qui prend en charge l’utilisation de XAML.  
  
 Semblable à <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existait dans le .NET Framework avant l’introduction de XAML, et autres fins pris en charge le modèle de convertisseur de type. Pour référencer et utiliser <xref:System.ComponentModel.TypeConverterAttribute>, vous devez entièrement qualifier ou fournir un `using` instruction pour <xref:System.ComponentModel>. Vous devez également inclure l’assembly système dans votre projet.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** une chaîne qui fait référence à la propriété concernée par nom.  
  
 Indique la propriété CLR d’une classe qui associe un alias le [x : Uid Directive](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** une valeur booléenne. Si utilisé pour l’objectif de l’attribut, cela doit toujours être spécifié en tant que `true`.  
  
 Indique si ce type est généré de haut en bas lors de la création d’un graphique d’objet XAML. Il s’agit d’un concept avancé, qui est sans doute étroitement lié à la définition de votre modèle de programmation. Pour plus d'informations, consultez <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **S’applique à :** classe, propriété, méthode (le seul cas de méthode XAML valide est un `get` accesseur qui prend en charge d’un membre pouvant être attaché).  
  
 **Arguments :** A <xref:System.Type> qui spécifie la classe de prise en charge de sérialiseur de valeur à utiliser lors de la sérialisation de toutes les propriétés du type avec attributs ou spécifique avec attributs de propriété.  
  
 <xref:System.Windows.Markup.ValueSerializer>Spécifie une classe de sérialisation de valeur qui nécessite plus d’état et de contexte qu’un <xref:System.ComponentModel.TypeConverter> est. <xref:System.Windows.Markup.ValueSerializer>peut être associé à un membre pouvant être attaché en appliquant la <xref:System.Windows.Markup.ValueSerializerAttribute> attribut sur la méthode statique `get` méthode d’accesseur pour le membre pouvant être attaché. Sérialisation de la valeur est également applicable pour les énumérations, interfaces et les structures, mais pas pour les délégués.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **S’applique à :** (classe), plus précisément les types de collections sont supposées héberger un contenu mixte, où les espaces blancs autour des éléments de l’objet peut être important pour la représentation sous forme de l’interface utilisateur.  
  
 **Arguments :** None.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>Indique qu’un type de collection doit être traité comme des espaces blancs significatifs par un processeur XAML, ce qui influence la construction des nœuds de valeur du flux de nœud XAML dans la collection. Pour plus d’informations, consultez [traitement des espaces blancs en XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **S’applique à :** propriété, de la classe.  
  
 **Arguments :** attribution de prend en charge deux types sous forme de chaînes de formulaires ou des types en tant que <xref:System.Type>. Consultez <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Indique qu’une classe ou une propriété a chargement différé pour XAML (par exemple, un comportement de modèle) et signale la classe qui active le comportement de report et son type de destination/contenu.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** nomme le rappel.  
  
 Indique qu’une classe peut utiliser une extension de balisage pour fournir une valeur pour un ou plusieurs de ses propriétés et référence un gestionnaire qu’un writer XAML doit appeler avant d’effectuer une opération de jeu d’extension de balisage sur n’importe quelle propriété de la classe.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** nomme le rappel.  
  
 Indique qu’une classe peut utiliser un convertisseur de type pour fournir une valeur pour un ou plusieurs de ses propriétés et référence un gestionnaire qu’un writer XAML doit appeler avant d’effectuer une opération de jeu de convertisseur de type sur n’importe quelle propriété de la classe.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **S’applique à :** classe  
  
 **Arguments :** une chaîne qui spécifie le nom de la propriété alias à `xml:lang` sur le type avec attributs.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>signale une propriété du type avec attributs qui mappe au XML `lang` directive. La propriété n’est pas nécessairement de type <xref:System.String>, mais doit pouvoir être assigné à partir d’une chaîne (Cela peut être accompli en associant un convertisseur de type avec le type de propriété, ou avec la propriété spécifique). La propriété doit être en lecture/écriture.  
  
 Le scénario de mappage `xml:lang` est afin qu’un modèle objet d’exécution puisse accéder aux informations de langage spécifiées par XML sans traiter spécifiquement un XMLDOM.  
  
 Hérite de la définition de tous les types dérivés qui peuvent être assignés au type. Vous pouvez remplacer la définition d’un type dérivé spécifique en appliquant <xref:System.Windows.Markup.XmlLangPropertyAttribute> sur spécifique au type dérivé, même si c’est un scénario rare.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Attributs CLR XAML au niveau de l’Assembly  
 Les sections suivantes décrivent les attributs XAML qui ne sont pas appliquées aux types ou des définitions de membre, mais qui sont appliquées à la place aux assemblys. Ces attributs sont utiles pour l’objectif global de la définition d’une bibliothèque qui contient des types personnalisés à utiliser en XAML. Certains des attributs n’influencent pas nécessairement le flux de nœud XAML directement, mais sont passés dans le flux de nœud pour les autres consommateurs à utiliser. Les consommateurs pour obtenir les informations incluent les environnements de conception ou les processus de sérialisation que vous avez besoin des informations d’espace de noms XAML et des informations de préfixe associées. Un contexte de schéma XAML (y compris la valeur par défaut des Services XAML .NET Framework) également utilise ces informations.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Arguments :**  
  
-   Chaîne qui spécifie l’identificateur de l’espace de noms XAML pour englober.  
  
-   Chaîne qui spécifie l’identificateur de l’espace de noms XAML permettre englober l’espace de noms XAML à partir de l’argument précédent.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>Spécifie qu’un espace de noms XAML peut être utilisé par un autre espace de noms XAML. En règle générale, l’espace de noms XAML inclu est indiqué dans précédemment défini <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Cette technique peut être utilisé pour le contrôle de version d’un vocabulaire XAML dans une bibliothèque et pour le rendre compatible avec le balisage précédemment défini par rapport au plus tôt vocabulaire avec version.  
  
### <a name="xmlnsdefinitionattribute"></a>Dans un XmlnsDefinitionAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Arguments :**  
  
-   Chaîne qui spécifie l’identificateur de l’espace de noms XAML à définir.  
  
-   Chaîne qui désigne un espace de noms CLR. L’espace de noms CLR doit définir des types publics dans votre assembly, et au moins un des types espace de noms CLR doit être destiné pour l’utilisation XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Spécifie un mappage sur une base par assembly entre un espace de noms XAML et un espace de noms CLR, qui est ensuite utilisé pour la résolution de type par un writer d’objet XAML ou un contexte de schéma XAML.  
  
 Plusieurs <xref:System.Windows.Markup.XmlnsDefinitionAttribute> peut être appliqué à un assembly. Cette opération peut être effectuée pour n’importe quelle combinaison des raisons suivantes :  
  
-   La conception de la bibliothèque contient plusieurs espaces de noms CLR pour l’organisation logique de l’accès aux API de runtime ; Toutefois, vous souhaitez que tous les types dans ces espaces de noms pour être utilisable en XAML en référençant le même espace de noms XAML. Dans ce cas, vous devez appliquer plusieurs <xref:System.Windows.Markup.XmlnsDefinitionAttribute> des attributs à l’aide de la même <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> valeur mais différentes <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> valeurs. Cela est particulièrement utile si vous définissez des mappages pour l’espace de noms XAML que votre infrastructure ou application doit utiliser l’espace de noms XAML par défaut dans l’utilisation courante.  
  
-   La conception de la bibliothèque contient plusieurs espaces de noms CLR et que vous souhaitez une séparation d’espace de noms XAML délibérée entre les utilisations des types dans ces espaces de noms CLR.  
  
-   Vous définissez un espace de noms CLR dans l’assembly, et que vous souhaitez qu’il soit accessible via plusieurs espaces de noms XAML. Ce scénario se produit lorsque vous prenez en charge plusieurs vocabulaires avec la même base de code.  
  
-   Vous définissez la prise en charge du langage XAML dans un ou plusieurs espaces de noms CLR. Dans ce cas, le <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> la valeur doit être `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>Dans un XmlnsPrefixAttribute  
 **Documentation de référence :**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Arguments :**  
  
-   Chaîne qui spécifie l’identificateur d’un espace de noms XAML.  
  
-   Chaîne qui spécifie un préfixe recommandé.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Spécifie un préfixe recommandé à utiliser pour un espace de noms XAML. Le préfixe est utile lors de l’écriture d’éléments et attributs dans un fichier XAML qui est sérialisé par les Services XAML .NET Framework <xref:System.Xaml.XamlXmlWriter>, ou quand une bibliothèque d’implémentation en XAML interagit avec un environnement de conception qui a XAML fonctionnalités d’édition.  
  
 Plusieurs <xref:System.Windows.Markup.XmlnsPrefixAttribute> peut être appliqué à un assembly. Cette opération peut être effectuée pour n’importe quelle combinaison des raisons suivantes :  
  
-   Votre assembly définit les types pour plus d’un espace de noms XAML. Dans ce cas, vous devez définir les valeurs de préfixe différent pour chaque espace de noms XAML.  
  
-   Vous prenez en charge plusieurs vocabulaires et que vous utilisez des préfixes différents pour chaque espace de noms XAML et le vocabulaire.  
  
-   Vous définissez la prise en charge du langage XAML dans l’assembly et que vous avez un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pour `http://schemas.microsoft.com/winfx/2006/xaml`. Dans ce cas, vous devez généralement promouvoir le préfixe `x`.  
  
> [!NOTE]
>  Les Services XAML .NET framework définit également l’attribut XAML <xref:System.Windows.Markup.RootNamespaceAttribute>. Cet attribut est un attribut de niveau assembly pour la prise en charge du système de projet, et il ne s’applique pas pour les types personnalisés XAML.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Attribute>  
 [Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
