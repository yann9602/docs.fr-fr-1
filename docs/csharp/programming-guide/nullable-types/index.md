---
title: "Types Nullable (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, types Nullable"
  - "types Nullable (C#)"
  - "types (C#), Nullable"
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
caps.handback.revision: 44
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Types Nullable (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les types Nullable sont des instances du struct <xref:System.Nullable%601?displayProperty=fullName>.  Un type Nullable peut représenter la plage correcte de valeurs pour son type valeur sous\-jacent, plus une valeur `null` supplémentaire.  Par exemple, un `Nullable<Int32>`, prononcé « Nullable d'Int32 », peut avoir une valeur comprise entre \-2147483648 et 2147483647, ou la valeur `null`.  Les valeurs [true](../../../csharp/language-reference/keywords/true.md) [false](../../../csharp/language-reference/keywords/false.md) ou [Null](../../../csharp/language-reference/keywords/null.md) peuvent être assignées à un type `Nullable<bool>`.  La possibilité d'assigner `null` à des types numériques et booléens est particulièrement utile lorsque vous utilisez des bases de données et d'autres types de données contenant des éléments auxquels vous ne pouvez pas assigner de valeur.  Par exemple, un champ booléen dans une base de données peut stocker les valeurs `true` ou `false`, ou peut être indéfini.  
  
 [!code-cs[csProgGuideTypes#3](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
 La sortie suivante sera affichée :  
  
 `num = Null`  
  
 `Nullable object must have a value.`  
  
 Pour plus d'exemples, consultez [Utilisation de types Nullable](../../../csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## Vue d'ensemble des types Nullable  
 Les types Nullable ont les caractéristiques suivantes :  
  
-   Les types Nullable représentent des variables de type valeur auxquelles vous pouvez assigner la valeur `null`.  Vous ne pouvez pas créer de type Nullable sur la base d'un type référence.  \(Les types référence prennent déjà en charge la valeur `null`.\)  
  
-   La syntaxe `T?` est le format abrégé de <xref:System.Nullable%601>, où `T` est un type valeur.  Les deux formats sont interchangeables.  
  
-   Assignez une valeur à un type Nullable comme pour un type valeur ordinaire, par exemple `int? x = 10;` ou `double? d = 4.108`.  Un type Nullable peut également être se voir assigner a valeur `null` :  `int? x = null.`  
  
-   Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> pour retourner la valeur assignée ou la valeur par défaut pour le type sous\-jacent si la valeur est `null`, par exemple  `int j = x.GetValueOrDefault();`  
  
-   Utilisez les propriétés en lecture seule <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A> pour rechercher une valeur Null et la récupérer, comme indiqué dans l'exemple suivant : `if(x.HasValue) j = x.Value;`  
  
    -   La propriété `HasValue` retourne `true` si la variable contient une valeur ou `false` si c'est `null`.  
  
    -   La propriété `Value` retourne une valeur si une valeur est assignée.  Sinon, <xref:System.InvalidOperationException?displayProperty=fullName> est levé.  
  
    -   La valeur par défaut de `HasValue` est `false`.  La propriété `Value` n'a pas de valeur par défaut.  
  
    -   Vous pouvez également utiliser les opérateurs `==` et `!=` avec un type Nullable, comme indiqué dans l'exemple suivant : `if (x != null) y = x;`  
  
-   Utilisez l'opérateur `??` pour assigner une valeur par défaut qui sera appliquée lorsqu'un type Nullable dont la valeur actuelle est `null` est assigné à un type non Nullable, par exemple `int? x = null; int y = x ?? -1;`  
  
-   Les types Nullable imbriqués ne sont pas autorisés.  La ligne suivante ne sera pas compilée : `Nullable<Nullable<int>> n;`  
  
## Rubriques connexes  
 Pour plus d'informations :  
  
-   [Utilisation de types Nullable](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Boxing des types Nullable](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [?? Opérateur](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 <xref:System.Nullable>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [C\#](../../../csharp/csharp.md)   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Que est exactement moyen « soulevé » ?](http://go.microsoft.com/fwlink/?LinkId=112382)