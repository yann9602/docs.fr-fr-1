---
title: "Op&#233;rations arithm&#233;tiques sur les pointeurs (Guide de programmation C#) | Microsoft Docs"
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
  - "pointeurs (C#), opérations arithmétiques"
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Op&#233;rations arithm&#233;tiques sur les pointeurs (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette rubrique décrit l'utilisation des opérateurs arithmétiques `+` et **\-** pour manipuler les pointeurs.  
  
> [!NOTE]
>  Vous ne pouvez pas exécuter d'opérations arithmétiques sur les pointeurs void.  
  
## Ajout et soustraction de valeurs numériques vers ou à partir de pointeurs  
 Vous pouvez ajouter une valeur `n` de type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), ou [ulong](../../../csharp/language-reference/keywords/ulong.md) à un pointeur, `p`, `` de n'importe quel type à l'exception de `void*`.  Le résultat `p+n` est le pointeur résultant de l'ajout de `n * sizeof(p) to the address of p`.  De même, `p-n` est le pointeur qui résulte de la soustraction de `n * sizeof(p)` de l'adresse de `p`.  
  
## Soustraction des pointeurs  
 Vous pouvez également soustraire des pointeurs du même type.  Le résultat est toujours du type `long`.  Par exemple, si `p1` et `p2` sont des pointeurs du type `pointer-type*`, alors l'expression `p1-p2` produit le résultat :  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Aucune exception n'est générée lorsque l'opération arithmétique produit un dépassement de capacité sur le domaine du pointeur, et le résultat dépend de l'implémentation.  
  
## Exemple  
 [!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)   
 [Manipulation de pointeurs](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)