---
title: "Tableau des conversions numériques explicites (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0315810522be319a6bb565c99e1c8f7d1ba4701b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tableau des conversions numériques explicites (référence C#)
Une conversion numérique explicite permet de convertir, à l’aide d’une expression de cast, n’importe quel type numérique en un autre type numérique quand il n’existe pas de conversion implicite. Le tableau suivant liste ces conversions.  
  
 Pour plus d’informations sur les conversions, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|De|À|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong` ou `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` ou `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong` ou `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`, `byte`, `short` ou `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong` ou `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int` ou `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong` ou `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long` ou `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte` ou `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char` ou `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `double`|  
  
## <a name="remarks"></a>Remarques  
  
-   La conversion numérique explicite peut produire un résultat de moindre précision ou entraîner la levée d’exceptions.  
  
-   Quand vous convertissez une valeur de type `decimal` en type intégral, la valeur source est arrondie vers zéro à la valeur intégrale la plus proche. Si la valeur intégrale obtenue se trouve en dehors de la plage du type de destination, une exception <xref:System.OverflowException> est levée.  
  
-   Quand vous convertissez une valeur `double` ou `float` en type intégral, la valeur est tronquée. Si la valeur intégrale obtenue est en dehors de la plage de la valeur de destination, le résultat dépend du contexte de vérification de dépassement de capacité. Dans un contexte vérifié, une exception `OverflowException` est levée, alors que dans un contexte non vérifié, le résultat est une valeur non spécifiée du type de destination.  
  
-   Quand vous convertissez `double` en `float`, la valeur `double` est arrondie à la valeur `float` la plus proche. Si la valeur `double` est inférieure ou supérieure à la plage de valeurs autorisées pour le type de destination, la conversion a pour résultat la valeur zéro ou un nombre infini.  
  
-   Dans le cas d’une conversion de `float` ou `double` en `decimal`, la valeur source est convertie en une représentation `decimal` et arrondie au nombre le plus proche après la 28ème décimale, si nécessaire. Selon la valeur de la valeur source, la conversion peut aboutir à l’un des résultats suivants :  
  
    -   Si la valeur source est trop petite pour être représentée en tant que `decimal`, le résultat est zéro.  
  
    -   Si la valeur source est une valeur non numérique (NaN), un nombre infini ou une valeur trop grande pour être représentée au format `decimal`, une exception `OverflowException` est levée.  
  
-   Quand vous convertissez `decimal` en `float` ou `double`, la valeur `decimal` est arrondie à la valeur `double` ou `float` la plus proche.  
  
 Pour plus d’informations sur la conversion explicite, consultez Conversions explicites dans la spécification du langage C#. Pour plus d’informations sur l’accès à la spécification, consultez [Spécification du langage C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [(), opérateur](../../../csharp/language-reference/operators/invocation-operator.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)

