---
title: "(), opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d62e6c93dcc69c892d4ca96ace3806cb1c8d989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="783b9-102">(), opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="783b9-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="783b9-103">En plus d’être utilisées pour spécifier l’ordre des opérations dans une expression, les parenthèses sont utilisées pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="783b9-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="783b9-104">Spécifier des casts ou conversions de type</span><span class="sxs-lookup"><span data-stu-id="783b9-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="783b9-105">Appeler des méthodes ou des délégués</span><span class="sxs-lookup"><span data-stu-id="783b9-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="783b9-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="783b9-106">Remarks</span></span>  
 <span data-ttu-id="783b9-107">Un cast appelle explicitement l’opérateur de conversion d’un type à l’autre. Le cast échoue si aucun opérateur de conversion n’est défini.</span><span class="sxs-lookup"><span data-stu-id="783b9-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="783b9-108">Pour définir un opérateur de conversion, consultez [explicit](../../../csharp/language-reference/keywords/explicit.md) et [implicit](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="783b9-109">L’opérateur `()` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="783b9-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="783b9-110">Pour plus d’informations, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="783b9-111">Une expression de cast peut donner une syntaxe ambiguë.</span><span class="sxs-lookup"><span data-stu-id="783b9-111">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="783b9-112">Par exemple, l’expression `(x)–y` peut être soit interprétée comme une expression de cast (un cast du type -y vers le type x), soit comme une expression additive combinée avec une expression entre parenthèses qui calcule la valeur x-y.</span><span class="sxs-lookup"><span data-stu-id="783b9-112">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="783b9-113">Pour plus d’informations sur l’appel de méthode, consultez [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-113">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="783b9-114">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="783b9-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="783b9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="783b9-115">See Also</span></span>  
 [<span data-ttu-id="783b9-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="783b9-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="783b9-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="783b9-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="783b9-118">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="783b9-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
