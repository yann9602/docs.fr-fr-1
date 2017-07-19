---
title: "Opérations arithmétiques sur les pointeurs (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 18
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fc675600526dcaa6afd488fdee57acdc577cf71f
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Opérations arithmétiques sur les pointeurs (Guide de programmation C#)
Cette rubrique décrit l’utilisation des opérateurs arithmétiques `+` et **-** pour manipuler les pointeurs.  
  
> [!NOTE]
>  Vous ne pouvez pas effectuer d’opérations arithmétiques sur les pointeurs void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Ajout et soustraction de valeurs numériques dans les pointeurs  
 Vous pouvez ajouter une valeur `n` de type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) à un pointeur `p` de n’importe quel type à l’exception de `void*`. Le pointeur `p+n` est le résultat de l’ajout de `n * sizeof(p) to the address of p`. De la même façon, `p-n` est le pointeur qui résulte de la soustraction de `n * sizeof(p)` de l’adresse de `p`.  
  
## <a name="subtracting-pointers"></a>Soustraction de pointeurs  
 Vous pouvez également soustraire des pointeurs du même type. Le résultat est toujours du type `long`. Par exemple, si `p1` et `p2` sont des pointeurs du type `pointer-type*`, l’expression `p1-p2` produit le résultat suivant :  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Aucune exception n’est générée si l’opération arithmétique produit un dépassement de capacité sur le domaine du pointeur, et le résultat dépend de l’implémentation.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [Manipulation de pointeurs](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
