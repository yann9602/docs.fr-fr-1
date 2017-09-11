---
title: "||, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
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
ms.openlocfilehash: 57bcb25b0d453fa59855f40c3189eb4af2bb8b7f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="6e313-102">||, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6e313-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="6e313-103">L’opérateur conditionnel OR (`||`) effectue une opération OR logique de ses opérandes `bool`.</span><span class="sxs-lookup"><span data-stu-id="6e313-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="6e313-104">Si le premier opérande prend la valeur `true`, le deuxième opérande n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="6e313-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="6e313-105">Si le premier opérande prend la valeur `false`, le deuxième opérateur détermine si l’expression OR dans son ensemble prend la valeur `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="6e313-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e313-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="6e313-106">Remarks</span></span>  
 <span data-ttu-id="6e313-107">L’opération</span><span class="sxs-lookup"><span data-stu-id="6e313-107">The operation</span></span>  
  
```  
x || y  
```  
  
 <span data-ttu-id="6e313-108">correspond à l’opération</span><span class="sxs-lookup"><span data-stu-id="6e313-108">corresponds to the operation</span></span>  
  
```  
x | y  
```  
  
 <span data-ttu-id="6e313-109">sauf si `x` a la valeur `true`, auquel cas `y` n’est pas évalué, car l’opération OR a la valeur `true`, indépendamment de la valeur d’`y`.</span><span class="sxs-lookup"><span data-stu-id="6e313-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="6e313-110">Ce concept est connu sous le nom d’évaluation de « court-circuit ».</span><span class="sxs-lookup"><span data-stu-id="6e313-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="6e313-111">L’opérateur OR conditionnel ne peut pas être surchargé, mais les surcharges des opérateurs logiques normaux et des opérateurs [true](../../../csharp/language-reference/keywords/true.md) et [false](../../../csharp/language-reference/keywords/false.md) sont, avec certaines restrictions, également considérées comme des surcharges des opérateurs logiques conditionnels.</span><span class="sxs-lookup"><span data-stu-id="6e313-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e313-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e313-112">Example</span></span>  
 <span data-ttu-id="6e313-113">Dans les exemples suivants, l’expression qui utilise `||` évalue seulement le premier opérande.</span><span class="sxs-lookup"><span data-stu-id="6e313-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="6e313-114">L’expression qui utilise `|` évalue les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="6e313-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="6e313-115">Dans le deuxième exemple, une exception runtime se produit si les deux opérandes sont évalués.</span><span class="sxs-lookup"><span data-stu-id="6e313-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 <span data-ttu-id="6e313-116">[!code-cs[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6e313-116">[!code-cs[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e313-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e313-117">See Also</span></span>  
 <span data-ttu-id="6e313-118">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6e313-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6e313-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6e313-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="6e313-120">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="6e313-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

