---
title: "x:Static Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticExtension"
  - "xStatic"
  - "x:Static"
helpviewer_keywords: 
  - "x:Static markup extension [XAML Services]"
  - "Static markup extension in XAML [XAML Services]"
  - "XAML [XAML Services], x:Static markup extension"
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: 25
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 25
---
# x:Static Markup Extension
Référence à une entité de code statique par valeur définie dans [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] \- moyen conforme.  La propriété statique qui est référencée peut être utilisée pour fournir la valeur d'une propriété en XAML.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`prefix`|Facultatif.  Préfixe qui fait référence à un espace de noms XAML mappé non défini par défaut.  `prefix` est affiché explicitement dans l'utilisation parce que vous référencez rarement des propriétés statiques qui viennent d'un espace de noms XAML par défaut.  Consultez la section Notes.|  
|`typeName`|Obligatoire.  Le nom du type qui définit le membre statique souhaité.|  
|`staticMemberName`|Obligatoire.  Nom du membre de valeur statique souhaité \(constante, propriété statique, champ ou valeur d'énumération\).|  
  
## Notes  
 L'entité de code référencée doit correspondre à l'un des éléments suivants :  
  
-   Constante  
  
-   propriété statique ;  
  
-   Champ  
  
-   Valeur d'énumération.  
  
 La spécification d'une autre entité de code, telle qu'une propriété non statique, génère une erreur au moment de la compilation si le XAML est compilé pour balisage, ou une exception d'analyse de temps de chargement XAML.  
  
 Vous pouvez effectuer des références `x:Static` à des champs ou propriétés statiques situés en dehors de l'espace de noms XAML par défaut pour le document XAML actif. Cela nécessite toutefois un mappage de préfixe.  Les espaces de noms XAML sont presque toujours définis à l'élément racine du document XAML.  
  
 Les opérations de recherche de propriétés statiques peuvent être exécutées par les Services XAML du .NET Framework et leurs lecteurs et writers XAML, lors de l'exécution avec le contexte de schéma XAML par défaut.  Ce contexte de schéma XAML peut utiliser la réflexion CLR pour fournir les valeurs statiques nécessaires à la construction de graphiques d'objets.  Le `typeName` que vous spécifiez est en fait un nom de type XAML, et non pas un nom de type CLR, bien qu'il s'agisse essentiellement du même nom lors de l'utilisation du contexte de schéma XAML par défaut ou de  toutes les infrastructures d'implémentation XAML existantes basées sur CLR.  
  
 Utilisez l'avertissement lorsque vous faites des références `x:Static` qui ne sont pas directement le type de la valeur d'une propriété.  Dans la séquence de traitement XAML, les valeurs fournies d'une extension de balisage n'appellent pas une conversion de valeurs supplémentaire.  Ceci est vrai, même si les résultats de votre référence `x:Static` créent une chaîne de texte et une conversion de valeur pour les valeurs d'attribut basées sur une chaîne de texte ont lieu typiquement pour ce membre spécifique ou pour toutes les valeurs membres du type de retour.  
  
 La syntaxe d'attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.  Le jeton de chaîne fourni après la chaîne d'identificateur `x:Static` est assigné en tant que valeur <xref:System.Windows.Markup.StaticExtension.Member%2A> de la classe d'extension <xref:System.Windows.Markup.StaticExtension> sous\-jacente.  
  
 Il existe deux autres utilisations de XAML qui sont techniquement possibles.  Toutefois, ces utilisations sont moins courantes parce qu'elles sont inutilement détaillées :  
  
 **Syntaxe des éléments objet :** `<x:Static Member="``prefix``:``typeName``.``staticMemberName``" .../>`  
  
 **Syntaxe d'attribut avec propriété Member explicite pour la chaîne d'initialisation :** `<``object````property``="{x:Static Member=``prefix``:``typeName``.``staticMemberName``}" .../>`  
  
 Dans l'implémentation des services XAML .NET Framework, la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.Markup.StaticExtension>.  
  
 `x:Static` est une extension de balisage.  En XAML, toutes les extensions de balisage utilisent les caractères `{` et `}` dans leur syntaxe d'attributs, convention selon laquelle un processeur XAML reconnaît qu'une extension de balisage doit fournir une valeur.  Pour plus d'informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## Remarques sur l'utilisation de WPF  
 L'espace de noms XAML par défaut que vous utilisez pour la programmation WPF ne contient pas beaucoup de propriétés statiques utiles. La plupart des propriétés statiques utiles sont prises en charge, tel qu'avec les convertisseurs de type qui en facilitent l'utilisation sans nécessiter `{x:Static}`.  Pour les propriétés statiques, vous devez mapper un préfixe pour un espace de noms XAML si l'un des éléments suivants est vrai :  
  
-   Vous référencez un type qui existe dans WPF, mais qui ne fait pas partie de l'espace de noms XAML par défaut \([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]\).  Cette situation est courante lors de l'utilisation de `x:Static`.  Par exemple, vous pouvez utiliser une référence `x:Static` avec un mappage d'espace de noms XAML à l'espace de noms CLR <xref:System> et à l'assembly mscorlib de manière à référencer les propriétés statiques de la classe <xref:System.Environment>.  
  
-   Vous référencez un type d'un assembly personnalisé.  
  
-   Vous référencez un type qui existe dans un assembly WMPF, mais qui se trouve dans un espace de noms CLR qui n'a pas été mappé pour faire partie de l'espace de noms XAML par défaut WPF.  Le mappage d'espaces de noms CLR dans l'espace de noms XAML par défaut pour WPF est exécuté par les définitions dans les différents assemblys WPF \(pour plus d'informations sur ce concept, consultez [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](../../../ocs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)\).  Les espaces de noms CLR non mappés peuvent exister si cet espace de noms CLR est composé principalement de définitions de classe qui ne sont généralement pas prévues pour XAML, telles que <xref:System.Windows.Threading>.  
  
 Pour plus d'informations sur l'utilisation des préfixes et des espaces de noms XAML pour WPF, consultez [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](../../../ocs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## Voir aussi  
 [x:Type Markup Extension](../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)