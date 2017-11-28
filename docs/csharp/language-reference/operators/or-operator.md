---
title: "|, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 374adc30e6937a68d67bfae152f2546c854b829b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="859f0-102">|, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="859f0-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="859f0-103">Les opérateurs `|` binaires sont prédéfinis pour les types intégraux et `bool`.</span><span class="sxs-lookup"><span data-stu-id="859f0-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="859f0-104">Pour les types intégraux, `|` calcule l’opération OR au niveau du bit de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="859f0-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="859f0-105">Pour les opérandes `bool`, `|` calcule l’opération OR logique de ses opérandes ; autrement dit, le résultat est `false` si et seulement si ses deux opérandes ont la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="859f0-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="859f0-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="859f0-106">Remarks</span></span>  
 <span data-ttu-id="859f0-107">Les types définis par l’utilisateur peuvent surcharger l’opérateur `|` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="859f0-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="859f0-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="859f0-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="859f0-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="859f0-109">See Also</span></span>  
 [<span data-ttu-id="859f0-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="859f0-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="859f0-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="859f0-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="859f0-112">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="859f0-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
