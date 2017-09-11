---
title: "|, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
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
ms.openlocfilehash: 7524e246df35154ac04e46f2b43edded71be34b1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="d1e04-102">|, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d1e04-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="d1e04-103">Les opérateurs `|` binaires sont prédéfinis pour les types intégraux et `bool`.</span><span class="sxs-lookup"><span data-stu-id="d1e04-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="d1e04-104">Pour les types intégraux, `|` calcule l’opération OR au niveau du bit de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="d1e04-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="d1e04-105">Pour les opérandes `bool`, `|` calcule l’opération OR logique de ses opérandes ; autrement dit, le résultat est `false` si et seulement si ses deux opérandes ont la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="d1e04-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1e04-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="d1e04-106">Remarks</span></span>  
 <span data-ttu-id="d1e04-107">Les types définis par l’utilisateur peuvent surcharger l’opérateur `|` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d1e04-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1e04-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1e04-108">Example</span></span>  
 <span data-ttu-id="d1e04-109">[!code-cs[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d1e04-109">[!code-cs[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e04-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1e04-110">See Also</span></span>  
 <span data-ttu-id="d1e04-111">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d1e04-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d1e04-112">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d1e04-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d1e04-113">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="d1e04-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

