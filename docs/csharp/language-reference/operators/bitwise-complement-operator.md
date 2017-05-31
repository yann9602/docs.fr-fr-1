---
title: "~, opérateur (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ~_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
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
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: c7245700f78ff52a98c499d895c7eb2f95efe5b6
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="-operator-c-reference"></a>~, opérateur (référence C#)
L’opérateur `~` effectue une opération de complément de bits sur son opérande, qui a pour effet d’inverser chaque bit. Les opérateurs de complément de bits sont prédéfinis pour [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) et [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
> [!NOTE]
>  Le symbole `~` est également utilisé pour déclarer des finaliseurs. Pour plus d’informations, consultez [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="remarks"></a>Remarques  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `~`. Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md). Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)
