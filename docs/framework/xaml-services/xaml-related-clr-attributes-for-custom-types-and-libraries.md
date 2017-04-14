---
title: "XAML-Related CLR Attributes for Custom Types and Libraries | Microsoft Docs"
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
  - "CLR attributes for custom types [XAML Services]"
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# XAML-Related CLR Attributes for Custom Types and Libraries
Cette rubrique décrit les attributs du common language runtime \(CLR\) qui sont définis par les services XAML .NET Framework.  Elle décrit également d'autres attributs CLR définis dans .NET Framework et dotés d'un scénario lié à XAML pour une application aux assemblys ou aux types.  L'association d'attributs CLR aux assemblys, aux types ou aux membres fournit les informations de système de type XAML relatives à vos types.  Ces informations sont fournies à tout consommateur XAML qui utilise les services XAML .NET Framework pour traiter le flux de nœud XAML directement ou via les lecteurs et writers XAML dédiés.  
  
## Attributs CLR XAML pour les types et membres personnalisés  
 L'utilisation d'attributs CLR implique l'emploi du CLR global pour la définition des types ; sinon, ces attributs ne sont pas disponibles.  Si vous utilisez le CLR pour définir le stockage de type, le contexte de schéma XAML par défaut employé par les writers XAML des services XAML .NET Framework peut lire par réflexion les attributs CLR à partir des assemblys de stockage.  
  
 Les sections suivantes décrivent les attributs XAML que vous pouvez appliquer aux types ou membres personnalisés.  Chaque attribut CLR communique des informations qui se rapportent à un système de type XAML.  Dans le chemin de chargement, les informations d'attributs permettent au lecteur XAML de former un flux de nœud XAML valide ou au writer XAML de produire un graphique d'objet approprié.  Dans le chemin d'enregistrement, les informations d'attributs soit permettent au lecteur XAML de former un flux de nœud XAML valide qui reconstitue les informations du système de type XAML, soit déclarent des conseils ou spécifications de sérialisation pour le writer XAML ou d'autres consommateurs XAML.  
  
### AmbientAttribute  
 **Documentation de référence :** <xref:System.Windows.Markup.AmbientAttribute>  
  
 **S'applique aux éléments suivants :** classe, propriété ou membres d'accesseur `get` qui prennent en charge des propriétés pouvant être attachées.  
  
 **Arguments :** aucun  
  
 <xref:System.Windows.Markup.AmbientAttribute> indique que la propriété ou toutes les propriétés qui acceptent ce type doivent être interprétées selon le concept de propriété ambiante en XAML.  Le concept d'« élément ambiant » est lié à la façon dont les processeurs XAML déterminent les propriétaires de types des membres.  Une propriété ambiante est une propriété dont la valeur est censée être disponible dans le contexte de l'analyseur lors de la création d'un graphique d'objet, mais pour laquelle la recherche de membre de type standard est interrompue de façon à permettre la création du jeu de nœuds XAML immédiat.  
  
 Le concept d'« élément ambiant » peut s'appliquer aux membres susceptibles d'être attachés, qui ne sont pas représentés sous forme de propriétés quant à la façon dont les attributs CLR définissent <xref:System.AttributeTargets>.  L'utilisation des attributs de méthode doit s'appliquer uniquement dans le cas d'un accesseur `get` qui prend en charge l'utilisation d'éléments pouvant être attachés pour XAML.  
  
### ConstructorArgumentAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** chaîne qui spécifie le nom de la propriété correspondant à un argument de constructeur unique.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> spécifie qu'un objet peut être initialisé à l'aide d'une syntaxe de constructeur autre que celle par défaut et qu'une propriété portant le nom spécifié fournit les informations de construction.  Ces informations sont destinées principalement à la sérialisation XAML.  Pour plus d'informations, consultez <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### ContentPropertyAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** chaîne qui spécifie le nom d'un membre du type avec attributs.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> indique que la propriété nommée par l'argument doit servir de propriété de contenu XAML pour ce type.  Tous les types dérivés qui peuvent être assignés au type de définition héritent de la définition de la propriété de contenu XAML.  Vous pouvez remplacer la définition d'un type dérivé spécifique en appliquant <xref:System.Windows.Markup.ContentPropertyAttribute> à ce type.  
  
 Pour la propriété qui sert de propriété de contenu XAML, les balises de l'élément de propriété peuvent être omises dans l'utilisation du code XAML.  En général, vous désignez des propriétés de contenu XAML qui favorisent l'utilisation d'un balisage XAML simplifié pour vos modèles de relation contenant\-contenu.  Étant donné qu'un seul membre peut être désigné comme propriété de contenu XAML, vous devez parfois effectuer des choix de conception pour déterminer, parmi plusieurs propriétés de conteneur d'un type, celle qui doit être définie comme propriété de contenu XAML.  Les autres propriétés de conteneur doivent être utilisées avec des éléments de propriété explicites.  
  
 Dans le flux de nœud XAML, les propriétés de contenu XAML produisent encore des nœuds `StartMember` et `EndMember`, à l'aide du nom de la propriété de <xref:System.Xaml.XamlMember>.  Pour déterminer si un membre constitue la propriété de contenu XAML, examinez la valeur <xref:System.Xaml.XamlType> de la position `StartObject` et récupérez la valeur <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### ContentWrapperAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **S'applique à l'élément suivant :** classe \(notamment les types de collections\).  
  
 **Arguments :** <xref:System.Type> qui spécifie le type à utiliser comme type de wrapper de contenu pour le contenu étranger.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> spécifie un ou plusieurs types sur le type de collection associé qui seront utilisés pour inclure du contenu étranger dans un wrapper.  Le contenu étranger fait référence aux cas où les contraintes de système de type sur le type de la propriété de contenu ne capturent pas tous les cas de contenu que l'utilisation du code XAML prend en charge pour le type propriétaire.  Par exemple, la prise en charge XAML disponible pour le contenu d'un type particulier peut accepter les chaînes d'un <xref:System.Collections.ObjectModel.Collection%601> générique fortement typé.  Les wrappers de contenu sont utiles pour migrer les conventions de balisage préexistantes vers la conception XAML des valeurs assignables pour les collections \(par exemple, pour la migration de modèles de contenu lié au texte\).  
  
 Pour spécifier plusieurs types de wrappers de contenu, appliquez l'attribut plusieurs fois.  
  
### DependsOnAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **S'applique à l'élément suivant :** propriété  
  
 **Arguments :** chaîne qui spécifie le nom d'un autre membre du type avec attributs.  
  
 <xref:System.Windows.Markup.DependsOnAttribute> indique que la propriété avec attributs dépend de la valeur d'une autre propriété.  L'application de cet attribut à une définition de propriété permet de s'assurer que les propriétés dépendantes sont traitées en premier lors de l'écriture d'objets XAML.  Les utilisations de <xref:System.Windows.Markup.DependsOnAttribute> spécifient les cas exceptionnels de propriétés appliquées à des types, pour lesquels un ordre d'analyse spécifique doit être suivi de façon à permettre la création d'objets valides.  
  
 Vous pouvez appliquer plusieurs cas de <xref:System.Windows.Markup.DependsOnAttribute> à une définition de propriété.  
  
### MarkupExtensionReturnTypeAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **S'applique à l'élément suivant :** classe, qui est censée être un type dérivé de <xref:System.Windows.Markup.MarkupExtension>.  
  
 **Arguments :** <xref:System.Type> qui spécifie le type le plus précis pouvant être attendu comme résultat `ProvideValue` du <xref:System.Windows.Markup.MarkupExtension> avec attributs.  
  
 Pour plus d'informations, consultez [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### NameScopePropertyAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** prend en charge deux formes d'attributs :  
  
-   Une chaîne qui spécifie le nom d'une propriété du type avec attributs.  
  
-   Une chaîne qui spécifie le nom d'une propriété et un <xref:System.Type> pour le type définissant la propriété nommée.  Cette forme permet de spécifier un membre pouvant être attaché comme propriété de portée de nom XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> spécifie une propriété qui fournit la valeur de portée de nom XAML de la classe avec attributs.  La propriété de portée de nom XAML est censée référencer un objet qui implémente <xref:System.Windows.Markup.INameScope> et contient la portée de nom XAML réelle, son magasin et son comportement.  
  
### RuntimeNamePropertyAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** chaîne qui spécifie le nom de la propriété de nom d'exécution du type avec attributs.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> signale une propriété du type avec attributs qui est mappée à la directive [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md) XAML.  La propriété doit être de type <xref:System.String> et accessible en lecture\/écriture.  
  
 Tous les types dérivés qui peuvent être assignés au type de définition héritent de la définition.  Vous pouvez remplacer la définition d'un type dérivé spécifique en appliquant <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> à ce type.  
  
### TrimSurroundingWhitespaceAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **S'applique aux éléments suivants :** types  
  
 **Arguments :** aucun.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> s'applique aux types spécifiques qui peuvent apparaître en tant qu'éléments enfants dans un contenu significatif d'espaces blancs \(contenu présent dans une collection associée à <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>\).  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> s'applique principalement au chemin d'enregistrement ; il est également disponible au sein du système de type XAML dans le chemin de chargement par le biais de la propriété <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=fullName>.  Pour plus d'informations, consultez [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### TypeConverterAttribute  
 **Documentation de référence** : <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **S'applique aux éléments suivants :** classe, propriété, méthode \(le seul cas de méthode valide pour XAML est un accesseur `get` qui prend en charge un membre pouvant être attaché\).  
  
 **Arguments :** <xref:System.Type> de <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute> dans un contexte XAML référence un <xref:System.ComponentModel.TypeConverter> personnalisé.  Ce <xref:System.ComponentModel.TypeConverter> fournit le comportement de conversion de type pour les types personnalisés ou les membres de ces types.  
  
 Vous appliquez l'attribut <xref:System.ComponentModel.TypeConverterAttribute> à votre type de façon à référencer votre implémentation de convertisseur de type.  Vous pouvez définir des convertisseurs de types pour XAML sur les classes, les structures ou les interfaces.  Vous n'avez pas besoin de fournir la conversion de type pour les énumérations ; cette conversion est prise en charge en mode natif.  
  
 Votre convertisseur de type doit pouvoir convertir une chaîne utilisée pour les attributs ou le texte d'initialisation dans le balisage vers le type de destination souhaité.  Pour plus d'informations, consultez [TypeConverters et XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Au lieu de s'appliquer à toutes les valeurs d'un type, un comportement de convertisseur de type pour XAML peut également être établi sur une propriété spécifique.  Dans ce cas, vous appliquez <xref:System.ComponentModel.TypeConverterAttribute> à la définition de propriété \(c'est\-à\-dire à la définition externe, et non pas aux définitions `get` et `set` spécifiques\).  
  
 Vous pouvez assigner un comportement de convertisseur de type permettant l'utilisation par XAML d'un membre personnalisé susceptible d'être attaché en appliquant <xref:System.ComponentModel.TypeConverterAttribute> à l'accesseur de méthode `get` qui prend en charge l'utilisation de XAML.  
  
 Semblable à <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existait dans le .NET Framework avant l'introduction de XAML ; le modèle de convertisseur de type a été utilisé à d'autres fins.  Pour référencer et utiliser <xref:System.ComponentModel.TypeConverterAttribute>, vous devez le qualifier intégralement ou fournir une instruction `using` pour <xref:System.ComponentModel>.  Vous devez également inclure l'assembly système dans votre projet.  
  
### UidPropertyAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** chaîne qui référence la propriété appropriée par son nom.  
  
 Indique la propriété CLR d'une classe qui associe un alias à la directive x:Uid \([x:Uid Directive](../../../docs/framework/xaml-services/x-uid-directive.md)\).  
  
### UsableDuringInitializationAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** valeur booléenne.  S'il est utilisé dans le cadre du rôle prévu de l'attribut, il doit toujours avoir la valeur `true`.  
  
 Indique si ce type est développé de haut en bas pendant la création de graphiques d'objet XAML.  Il s'agit d'un concept avancé, qui est sans doute étroitement lié à la définition de votre modèle de programmation.  Pour plus d'informations, consultez <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### ValueSerializerAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **S'applique aux éléments suivants :** classe, propriété, méthode \(le seul cas de méthode valide pour XAML est un accesseur `get` qui prend en charge un membre pouvant être attaché\).  
  
 **Arguments :** <xref:System.Type> qui spécifie la classe de prise en charge de sérialiseur de valeur à utiliser lors de la sérialisation de toutes les propriétés du type avec attributs ou de la propriété avec attributs concernée.  
  
 <xref:System.Windows.Markup.ValueSerializer> spécifie une classe de sérialisation de valeur qui nécessite davantage d'informations d'état et de contexte qu'un <xref:System.ComponentModel.TypeConverter>.  Il est possible d'associer un <xref:System.Windows.Markup.ValueSerializer> à un membre pouvant être attaché en appliquant l'attribut <xref:System.Windows.Markup.ValueSerializerAttribute> sur la méthode d'accesseur `get` statique du membre.  La sérialisation de valeur peut également s'appliquer aux énumérations, interfaces et structures, mais pas aux délégués.  
  
### WhitespaceSignificantCollectionAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **S'applique à l'élément suivant :** classe, et notamment les types de collections qui sont censés héberger un contenu mixte, où l'espace blanc placé autour des éléments objets peut être significatif pour la représentation de l'interface utilisateur.  
  
 **Arguments :** aucun.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indique qu'un type de collection doit être traité comme ayant des espaces blancs significatifs par un processeur XAML, ce qui influence la construction des nœuds de valeur du flux de nœud XAML dans la collection.  Pour plus d'informations, consultez [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### XamlDeferLoadAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **S'applique aux éléments suivants :** classe, propriété.  
  
 **Arguments :** prend en charge deux formes d'attributs : les types sous forme de chaînes ou les types en tant que <xref:System.Type>.  Consultez <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Indique qu'une classe ou une propriété utilise le chargement différé pour XAML \(par exemple, dans un comportement de modèle\), et signale la classe qui active le comportement de report et son type de destination\/contenu.  
  
### XamlSetMarkupExtensionAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** nomme le rappel.  
  
 Indique qu'une classe peut utiliser une extension de balisage afin de fournir une valeur pour une ou plusieurs de ses propriétés, et référence un gestionnaire qu'un writer XAML doit appeler avant d'exécuter une opération ensembliste d'extension de balisage sur n'importe quelle propriété de la classe.  
  
### XamlSetTypeConverterAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** nomme le rappel.  
  
 Indique qu'une classe peut utiliser un convertisseur de type afin de fournir une valeur pour une ou plusieurs de ses propriétés, et référence un gestionnaire qu'un writer XAML doit appeler avant d'exécuter une opération ensembliste de convertisseur de type sur n'importe quelle propriété de la classe.  
  
### XmlLangPropertyAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **S'applique à l'élément suivant** : classe  
  
 **Arguments :** chaîne qui spécifie le nom de la propriété à associer en tant qu'alias à `xml:lang` sur le type avec attributs.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> signale une propriété du type avec attributs qui est mappée à la directive `lang` XML.  La propriété n'est pas nécessairement de type <xref:System.String>, mais doit pouvoir être assignée à partir d'une chaîne \(vous pouvez accomplir cette opération en associant un convertisseur de type au type de la propriété ou à la propriété concernée\).  La propriété doit être accessible en lecture\/écriture.  
  
 Le scénario de mappage de `xml:lang` permet à un modèle objet d'exécution d'accéder aux informations de langage spécifiées par XML sans traiter spécifiquement un XMLDOM.  
  
 Tous les types dérivés qui peuvent être assignés au type de définition héritent de la définition.  Vous pouvez remplacer la définition d'un type dérivé spécifique en appliquant <xref:System.Windows.Markup.XmlLangPropertyAttribute> à ce type, bien que ce scénario soit peu courant.  
  
## Attributs CLR XAML au niveau de l'assembly  
 Les sections suivantes décrivent les attributs XAML qui s'appliquent aux assemblys, et non pas aux types ou aux définitions de membre.  Ces attributs sont utiles pour atteindre l'objectif global qui consiste à définir une bibliothèque contenant des types personnalisés à utiliser en XAML.  Certains attributs n'influencent pas nécessairement le flux de nœud XAML directement, mais sont passés dans le flux de nœud afin d'être utilisés par d'autres consommateurs.  Les consommateurs des informations incluent les environnements de conception ou les processus de sérialisation qui ont besoin des informations d'espace de noms XAML et des informations de préfixe associées.  Un contexte de schéma XAML \(y compris celui par défaut des services XAML .NET Framework\) utilise également ces informations.  
  
### XmlnsCompatibleWithAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Arguments :**  
  
-   Chaîne qui spécifie l'identificateur de l'espace de noms XAML à subsumer.  
  
-   Chaîne qui spécifie l'identificateur de l'espace de noms XAML pouvant subsumer l'espace de noms XAML à partir de l'argument précédent.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> spécifie qu'un espace de noms XAML peut être subsumé par un autre espace de noms XAML.  En général, l'espace de noms XAML subsumant est indiqué dans un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> précédemment défini.  Cette technique peut être utilisée pour assurer le contrôle de version d'un vocabulaire XAML dans une bibliothèque et rendre ce dernier compatible avec le balisage précédemment défini pour le vocabulaire associé à la version précédente.  
  
### XmlnsDefinitionAttribute  
 **Documentation de référence** : <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Arguments :**  
  
-   Chaîne qui spécifie l'identificateur de l'espace de noms XAML à définir.  
  
-   Chaîne qui nomme un espace de noms CLR.  L'espace de noms CLR doit définir des types publics dans votre assembly, et un des types d'espace de noms CLR au moins doit être prévu pour l'utilisation de XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> spécifie un mappage sur une base de par\-assembly entre un espace de noms XAML et un espace de noms CLR, qui est ensuite utilisé pour la résolution de type par un writer d'objet XAML ou un contexte de schéma XAML.  
  
 Plusieurs <xref:System.Windows.Markup.XmlnsDefinitionAttribute> peuvent être appliqués à un assembly.  Cette opération peut être effectuée pour toute combinaison des raisons suivantes :  
  
-   La conception de bibliothèque contient plusieurs espaces de noms CLR permettant l'organisation logique de l'accès à l'API d'exécution, mais vous souhaitez que tous les types de ces espaces de noms soient utilisables en XAML par le biais du même espace de noms XAML.  Dans ce cas, vous devez appliquer plusieurs attributs <xref:System.Windows.Markup.XmlnsDefinitionAttribute> avec la même valeur <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>, mais avec des valeurs <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> différentes.  Cette technique s'avère particulièrement utile si vous définissez des mappages pour l'espace de noms XAML que votre infrastructure ou application doit utiliser couramment comme espace de noms XAML par défaut.  
  
-   La conception de bibliothèque contient plusieurs espaces de noms CLR et vous souhaitez délibérément séparer les espaces de noms XAML en fonction des utilisations des types dans ces espaces de noms CLR.  
  
-   Vous définissez un espace de noms CLR dans l'assembly et souhaitez qu'il soit accessible par le biais de plusieurs espaces de noms XAML.  Ce scénario se produit lorsque vous prenez en charge plusieurs vocabulaires avec la même base de code.  
  
-   Vous définissez la prise en charge du langage XAML dans un ou plusieurs espaces de noms CLR.  Pour ces derniers, <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> doit avoir la valeur `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### XmlnsPrefixAttribute  
 **Documentation de référence :** <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Arguments :**  
  
-   Chaîne qui spécifie l'identificateur d'un espace de noms XAML.  
  
-   Chaîne qui spécifie un préfixe recommandé.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> spécifie un préfixe recommandé pour un espace de noms XAML.  Le préfixe est utile lors de l'écriture d'éléments et d'attributs dans un fichier XAML en cas de sérialisation par le <xref:System.Xaml.XamlXmlWriter> des services XAML .NET Framework ou d'interaction avec un environnement de conception faisant appel à des fonctionnalités d'édition XAML.  
  
 Plusieurs <xref:System.Windows.Markup.XmlnsPrefixAttribute> peuvent être appliqués à un assembly.  Cette opération peut être effectuée pour toute combinaison des raisons suivantes :  
  
-   Votre assembly définit des types pour plusieurs espaces de noms XAML.  Dans ce cas, vous devez définir des valeurs de préfixe différentes pour chaque espace de noms XAML.  
  
-   Vous prenez en charge plusieurs vocabulaires et utilisez des préfixes différents pour chaque vocabulaire et chaque espace de noms XAML.  
  
-   Vous définissez la prise en charge du langage XAML dans l'assembly et appliquez un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pour `http://schemas.microsoft.com/winfx/2006/xaml` Dans ce cas, vous devez généralement promouvoir le préfixe `x`.  
  
> [!NOTE]
>  Les services XAML .NET Framework définissent également l'attribut XAML <xref:System.Windows.Markup.RootNamespaceAttribute>.  Il s'agit d'un attribut de niveau assembly qui est conçu pour la prise en charge du système de projet et n'est pas utile pour les types personnalisés XAML.  
  
## Voir aussi  
 <xref:System.Attribute>   
 [Defining Custom Types for Use with .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)