---
title: "(), opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
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
ms.openlocfilehash: 1b0a683880f0791ee69ea5971756d104323b4303
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="dd3e9-102">(), opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dd3e9-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="dd3e9-103">En plus d’être utilisées pour spécifier l’ordre des opérations dans une expression, les parenthèses sont utilisées pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="dd3e9-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="dd3e9-104">Spécifier des casts ou conversions de type</span><span class="sxs-lookup"><span data-stu-id="dd3e9-104">Specify casts, or type conversions.</span></span>  
  
     <span data-ttu-id="dd3e9-105">[!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dd3e9-105">[!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]</span></span>  
  
2.  <span data-ttu-id="dd3e9-106">Appeler des méthodes ou des délégués</span><span class="sxs-lookup"><span data-stu-id="dd3e9-106">Invoke methods or delegates.</span></span>  
  
     <span data-ttu-id="dd3e9-107">[!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="dd3e9-107">[!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd3e9-108">Notes</span><span class="sxs-lookup"><span data-stu-id="dd3e9-108">Remarks</span></span>  
 <span data-ttu-id="dd3e9-109">Un cast appelle explicitement l’opérateur de conversion d’un type à l’autre. Le cast échoue si aucun opérateur de conversion n’est défini.</span><span class="sxs-lookup"><span data-stu-id="dd3e9-109">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="dd3e9-110">Pour définir un opérateur de conversion, consultez [explicit](../../../csharp/language-reference/keywords/explicit.md) et [implicit](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="dd3e9-110">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="dd3e9-111">L’opérateur `()` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="dd3e9-111">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="dd3e9-112">Pour plus d’informations, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="dd3e9-112">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="dd3e9-113">Une expression de cast peut donner une syntaxe ambiguë.</span><span class="sxs-lookup"><span data-stu-id="dd3e9-113">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="dd3e9-114">Par exemple, l’expression `(x)–y` peut être soit interprétée comme une expression de cast (un cast du type -y vers le type x), soit comme une expression additive combinée avec une expression entre parenthèses qui calcule la valeur x-y.</span><span class="sxs-lookup"><span data-stu-id="dd3e9-114">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="dd3e9-115">Pour plus d’informations sur l’appel de méthode, consultez [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="dd3e9-115">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dd3e9-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="dd3e9-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd3e9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd3e9-117">See Also</span></span>  
 <span data-ttu-id="dd3e9-118">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd3e9-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="dd3e9-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd3e9-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="dd3e9-120">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="dd3e9-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

