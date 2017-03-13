---
title: "Conversions de pointeur (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "pointeurs (C#), conversions"
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# Conversions de pointeur (Guide de programmation C#)
Le tableau suivant répertorie les conversions implicites prédéfinies de pointeurs.  Des conversions implicites peuvent avoir lieu dans de nombreuses situations, notamment lors de l'appel de méthodes et de la définition d'instructions d'assignation.  
  
## Conversions de pointeur implicites  
  
|From|Pour|  
|----------|----------|  
|Tout type de pointeur|void\*|  
|null|Tout type de pointeur|  
  
 La conversion de pointeur explicite est utilisée pour effectuer des conversions, pour lesquelles il n'existe aucune conversion implicite, à l'aide d'une expression de cast.  Le tableau suivant répertorie ces conversions explicites.  
  
## Conversions de pointeur explicites  
  
|From|Pour|  
|----------|----------|  
|Tout type de pointeur|Tout autre type de pointeur|  
|sbyte, byte, short, ushort, int, uint, long ou ulong|Tout type de pointeur|  
|Tout type de pointeur|sbyte, byte, short, ushort, int, uint, long ou ulong|  
  
## Exemple  
 Dans l'exemple suivant, un pointeur vers `int` est converti en un pointeur vers `byte`.  Notez que le pointeur pointe vers l'octet adressé le plus bas de la variable.  Lorsque vous incrémentez successivement le résultat, jusqu'à la taille de `int` \(4 octets\), vous pouvez afficher les octets restants de la variable.  
  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)