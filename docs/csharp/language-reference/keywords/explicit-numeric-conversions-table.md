---
title: "Tableau des conversions num&#233;riques explicites (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversions (C#), numériques explicites"
  - "conversions numériques explicites (C#)"
  - "conversions numériques (C#), explicites"
  - "types de données numériques (C#)"
  - "conversion de type (C#), numériques explicites"
  - "types (C#), conversions numériques explicites"
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# Tableau des conversions num&#233;riques explicites (r&#233;f&#233;rence C#)
Une conversion numérique explicite permet de convertir, à l'aide d'une expression de cast, n'importe quel type numérique en un autre type numérique lorsqu'il n'existe pas de conversion implicite.  Le tableau suivant répertorie ces conversions explicites.  
  
 Pour plus d'informations sur les conversions, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|From|Pour|  
|----------|----------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong` ou `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` ou `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong` ou `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`,  `byte`, `short` ou `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, `` ou `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int` ou `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`,  `int`, `uint`, `ulong` ou `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`,  `int`, `uint`, `long` ou `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte` ou `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `` ou `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `` ou `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `double`|  
  
## Notes  
  
-   Une conversion numérique explicite peut produire un résultat de moindre précision ou entraîner la levée d'exceptions.  
  
-   Lorsque vous convertissez une valeur de type `decimal` en type intégral, la valeur source est arrondie vers zéro à la valeur intégrale la plus proche.  Si la valeur intégrale obtenue se trouve en dehors de la plage du type de destination, une exception <xref:System.OverflowException> est levée.  
  
-   Lorsque vous convertissez une valeur `double` ou `float` en un type intégral, la valeur est tronquée.  Si la valeur intégrale obtenue est en dehors de la plage de la valeur de destination, le résultat dépend du contexte de vérification de dépassement de capacité.  Dans un contexte vérifié \(checked\), une exception `OverflowException` est levée, alors que dans un contexte non vérifié \(unchecked\), le résultat est une valeur non spécifiée du type de destination.  
  
-   Lorsque vous convertissez `double` en `float`, la valeur `double` est arrondie à la valeur `float` la plus proche.  Si la valeur `double` est inférieure ou supérieure à la plage de valeurs autorisées pour le type de destination, la conversion a pour résultat la valeur zéro ou un nombre infini.  
  
-   Dans le cas d'une conversion de `float` ou `double` en `decimal`, la valeur source est convertie en une représentation `decimal` et arrondie, si nécessaire, au nombre le plus proche après la 28ème décimale.  Selon la valeur de la valeur source, la conversion peut avoir l'un des résultats suivants :  
  
    -   Si la valeur source est trop petite pour être représentée en tant que `decimal`, le résultat est zéro.  
  
    -   Si la valeur source est une valeur non numérique \(NaN\), un nombre infini ou une valeur trop grande pour être représentée au format `decimal`, une exception `OverflowException` est levée.  
  
-   Lorsque vous convertissez `decimal` en `float` ou `double`, la valeur `decimal` est arrondie au `double` le plus proche ou à la valeur `float`.  
  
 Pour plus d'informations sur la conversion explicite, consultez Conversions explicites, dans la spécification du langage C\#.  Pour plus d'informations sur l'accès à la spécification, consultez [Spécification du langage C\#](../../../csharp/language-reference/language-specification.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [\(\), opérateur](../../../csharp/language-reference/operators/invocation-operator.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)