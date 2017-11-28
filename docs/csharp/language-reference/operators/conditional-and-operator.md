---
title: "&amp;&amp;, opérateur (Informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="eba18-102">&amp;&amp;, opérateur (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="eba18-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="eba18-103">L’opérateur AND conditionnel (`&&`) effectue une opération AND logique sur ses opérandes de type `bool`, mais évalue uniquement le second opérande, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="eba18-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eba18-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="eba18-104">Remarks</span></span>  
 <span data-ttu-id="eba18-105">L’opération</span><span class="sxs-lookup"><span data-stu-id="eba18-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="eba18-106">correspond à l’opération</span><span class="sxs-lookup"><span data-stu-id="eba18-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="eba18-107">sauf si `x` a la valeur `false`, auquel cas `y` n’est pas évalué, car le résultat de l’opération AND est `false` quelle que soit la valeur de `y`.</span><span class="sxs-lookup"><span data-stu-id="eba18-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="eba18-108">Ce procédé est connu sous le nom d’évaluation "de court-circuit".</span><span class="sxs-lookup"><span data-stu-id="eba18-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="eba18-109">L’opérateur AND conditionnel ne peut pas être surchargé, mais les surcharges des opérateurs logiques normaux et des opérateurs [true](../../../csharp/language-reference/keywords/true.md) et [false](../../../csharp/language-reference/keywords/false.md) sont, avec certaines restrictions, également considérées comme des surcharges des opérateurs logiques conditionnels.</span><span class="sxs-lookup"><span data-stu-id="eba18-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba18-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="eba18-110">Example</span></span>  
 <span data-ttu-id="eba18-111">Dans l’exemple suivant, l’expression conditionnelle dans la deuxième instruction `if` évalue seulement le premier opérande, car ce dernier retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="eba18-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="eba18-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="eba18-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eba18-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eba18-113">See Also</span></span>  
 [<span data-ttu-id="eba18-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="eba18-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="eba18-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="eba18-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eba18-116">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="eba18-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
