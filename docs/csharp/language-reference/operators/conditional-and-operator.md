---
title: "&amp;&amp;, opérateur (Informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1da61947cbc85e5b3045513e99e013d1e4fae4b3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="7633c-102">&amp;&amp;, opérateur (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="7633c-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="7633c-103">L’opérateur AND conditionnel (`&&`) effectue une opération AND logique sur ses opérandes de type `bool`, mais évalue uniquement le second opérande, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7633c-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7633c-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="7633c-104">Remarks</span></span>  
 <span data-ttu-id="7633c-105">L’opération</span><span class="sxs-lookup"><span data-stu-id="7633c-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="7633c-106">correspond à l’opération</span><span class="sxs-lookup"><span data-stu-id="7633c-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="7633c-107">sauf si `x` a la valeur `false`, auquel cas `y` n’est pas évalué, car le résultat de l’opération AND est `false` quelle que soit la valeur de `y`.</span><span class="sxs-lookup"><span data-stu-id="7633c-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="7633c-108">Ce procédé est connu sous le nom d’évaluation "de court-circuit".</span><span class="sxs-lookup"><span data-stu-id="7633c-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="7633c-109">L’opérateur AND conditionnel ne peut pas être surchargé, mais les surcharges des opérateurs logiques normaux et des opérateurs [true](../../../csharp/language-reference/keywords/true.md) et [false](../../../csharp/language-reference/keywords/false.md) sont, avec certaines restrictions, également considérées comme des surcharges des opérateurs logiques conditionnels.</span><span class="sxs-lookup"><span data-stu-id="7633c-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7633c-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="7633c-110">Example</span></span>  
 <span data-ttu-id="7633c-111">Dans l’exemple suivant, l’expression conditionnelle dans la deuxième instruction `if` évalue seulement le premier opérande, car ce dernier retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="7633c-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 <span data-ttu-id="7633c-112">[!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7633c-112">[!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7633c-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7633c-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7633c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7633c-114">See Also</span></span>  
 <span data-ttu-id="7633c-115">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7633c-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7633c-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7633c-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="7633c-117">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="7633c-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

