---
title: "Tableau des conversions num&#233;riques implicites (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversions (C#), numériques implicites"
  - "conversions numériques implicites (C#)"
  - "conversions numériques (C#), implicites"
  - "types (C#), conversions numériques implicites"
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# Tableau des conversions num&#233;riques implicites (r&#233;f&#233;rence C#)
Le tableau suivant répertorie les conversions numériques implicites prédéfinies.  Des conversions implicites peuvent avoir lieu dans de nombreuses situations, notamment lors de l'appel de méthodes et de la définition d'instructions d'assignation.  
  
|From|Pour|  
|----------|----------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`, `long`, `float`, `double` ou `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`, `float`, `double` ou `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`, `ulong`, `float`, `double` ou `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`, `double` ou `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`, `double` ou `decimal`|  
  
## Notes  
  
-   Précision, mais pas d'amplitude peut\-être être perdue dans les conversions à partir de `int`, `uint`, `long`, ou `ulong` à `float` et de `long` ou `ulong` à `double`.  
  
-   Il n'y a pas de conversions implicites vers le type `char`.  
  
-   Il n'y a pas de conversions implicites entre les types virgule flottante et le type `decimal`.  
  
-   Une expression constante de type `int` peut être convertie en `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, à condition que sa valeur se trouve dans la plage de valeurs autorisées pour le type de destination.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)