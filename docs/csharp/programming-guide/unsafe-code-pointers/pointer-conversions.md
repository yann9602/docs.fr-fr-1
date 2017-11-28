---
title: Conversions de pointeur (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36589d139c91e04d9e3d8b31281a91c26b85a5d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-conversions-c-programming-guide"></a>Conversions de pointeur (Guide de programmation C#)
Le tableau suivant présente les conversions de pointeur implicites prédéfinies. Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.  
  
## <a name="implicit-pointer-conversions"></a>Conversions de pointeur implicites  
  
|De|Pour|  
|----------|--------|  
|Tout type pointeur|void*|  
|null|Tout type pointeur|  
  
 La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast. Le tableau suivant liste ces conversions.  
  
## <a name="explicit-pointer-conversions"></a>Conversions de pointeur explicites  
  
|De|Pour|  
|----------|--------|  
|Tout type pointeur|Tout autre type pointeur|  
|sbyte, byte, short, ushort, int, uint, long ou ulong|Tout type pointeur|  
|Tout type pointeur|sbyte, byte, short, ushort, int, uint, long ou ulong|  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`. Notez que le pointeur pointe vers l’octet traité le plus faible de la variable. Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Types de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Types](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
