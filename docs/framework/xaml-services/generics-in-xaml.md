---
title: "Generics in XAML | Microsoft Docs"
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
  - "generics [XAML Services]"
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# Generics in XAML
Les services XAML .NET Framework, tels qu'ils sont implémentés dans System.Xaml, prennent en charge l'utilisation des types CLR génériques.  Cette prise en charge inclut la spécification des contraintes de génériques en tant qu'argument de type et l'application de la contrainte par l'appel de la méthode `Add` appropriée pour les cas de collections génériques.  Cette rubrique décrit divers aspects de l'utilisation et du référencement des types génériques en XAML.  
  
## x:TypeArguments  
 `x:TypeArguments` est une directive définie par le langage XAML.  Lorsqu'elle est utilisée en tant que membre d'un type XAML stocké par un type générique, la directive `x:TypeArguments` passe les arguments de types contraints du générique au constructeur de stockage.  Pour obtenir la syntaxe de référence relative à l'utilisation de `x:TypeArguments` par les services XAML .NET Framework, y compris des exemples de syntaxe, consultez [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
 Étant donné que la directive `x:TypeArguments` accepte une chaîne et qu'elle est gérée par le convertisseur de type, elle est généralement déclarée en XAML en tant qu'attribut.  
  
 Dans le flux de nœud XAML, les informations déclarées par `x:TypeArguments` peuvent être obtenues à partir de <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=fullName> au niveau d'une position `StartObject` dans le flux de nœud.  La valeur de retour de <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=fullName> est une liste de valeurs <xref:System.Xaml.XamlType>.  Vous pouvez déterminer si un type XAML représente un type générique en appelant <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=fullName>.  
  
## Règles et conventions syntaxiques relatives aux génériques en XAML  
 En XAML, un type générique doit toujours être représenté comme un générique contraint ; un générique sans contrainte n'est jamais présent dans le système de type XAML ou un flux de nœud XAML, et ne peut pas être représenté dans le balisage XAML.  Un générique peut être référencé dans la syntaxe d'attribut XAML s'il s'agit d'une contrainte de type imbriqué d'un générique référencé par `x:TypeArguments`, ou si `x:Type` fournit une référence de type CLR pour un type générique.  Ce comportement est pris en charge par le biais de la classe <xref:System.Xaml.Schema.XamlTypeTypeConverter> définie par les services XAML .NET Framework.  
  
 Le format de syntaxe d'attribut XAML activé par <xref:System.Xaml.Schema.XamlTypeTypeConverter> modifie la convention syntaxique MSIL\/CLR standard qui utilise les signes « inférieur à » et « supérieur à » pour les types et les contraintes de génériques, et substitue à la place de ces derniers des parenthèses pour le conteneur de contrainte.  Pour obtenir un exemple, consultez [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
## Génériques et fonctionnalités XAML 2009  
 Si vous utilisez le langage XAML 2009, vous pouvez employer des [types intégrés XAML 2009](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) comme éléments d'informations dans `x:TypeArguments` au lieu de mapper les types de base CLR afin d'obtenir des types XAML pour les primitives associées au langage courant.  Par exemple, vous pouvez déclarer les éléments suivants \(les mappages de préfixes ne sont pas indiqués, mais `x` est l'espace de noms XAML du langage XAML 2009\) :  
  
```  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## Prise en charge des génériques dans WPF et d'autres infrastructures v3.5  
 Pour que vous puissiez utiliser XAML 2006 en ciblant spécifiquement WPF, l'attribut [x:Class](../../../docs/framework/xaml-services/x-class-directive.md) doit également être disponible sur le même élément comme  `x:TypeArguments` et cet élément doit être l'élément racine d'un document XAML.  L'élément racine doit être mappé à un type générique avec au moins un argument de type.  C'est le cas notamment de <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Pour prendre en charge des utilisations génériques, les solutions possibles consistent notamment à définir une extension de balisage personnalisée pouvant retourner des types génériques ou à fournir une définition de classe de wrapper qui dérive d'un type générique, mais aplanit la contrainte générique dans sa propre définition de classe.  
  
 Dans WPF, lorsque vous ciblez [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vous pouvez utiliser des fonctionnalités XAML 2009 avec `x:TypeArguments`, mais uniquement pour le langage XAML libre, dont le balisage n'est pas compilé.  Le XAML compilé par balisage pour WPF et la forme de langage BAML de XAML ne prend actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
 Les flux de travail personnalisés de [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] pour [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ne prennent pas en charge l'utilisation du code XAML générique.  
  
## Voir aussi  
 [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)   
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [Built\-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)