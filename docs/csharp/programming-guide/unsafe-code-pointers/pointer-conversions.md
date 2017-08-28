---
title: Conversions de pointeur (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
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
ms.openlocfilehash: e415d892d979e2bdcd648256150e2a96b1772ce4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-conversions-c-programming-guide"></a>Conversions de pointeur (Guide de programmation C#)
Le tableau suivant présente les conversions de pointeur implicites prédéfinies. Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.  
  
## <a name="implicit-pointer-conversions"></a>Conversions de pointeur implicites  
  
|De|Vers|  
|----------|--------|  
|Tout type pointeur|void*|  
|null|Tout type pointeur|  
  
 La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast. Le tableau suivant liste ces conversions.  
  
## <a name="explicit-pointer-conversions"></a>Conversions de pointeur explicites  
  
|De|Vers|  
|----------|--------|  
|Tout type pointeur|Tout autre type pointeur|  
|sbyte, byte, short, ushort, int, uint, long ou ulong|Tout type pointeur|  
|Tout type pointeur|sbyte, byte, short, ushort, int, uint, long ou ulong|  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`. Notez que le pointeur pointe vers l’octet traité le plus faible de la variable. Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.  
  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)

