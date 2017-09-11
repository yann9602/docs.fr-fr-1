---
title: "&gt;=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
caps.latest.revision: 16
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
ms.openlocfilehash: 59b134ce1e1169b0a5f4583374148d39ceb8326a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="28f11-102">&gt;=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="28f11-102">&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="28f11-103">Tous les types numériques et d’énumération définissent un opérateur relationnel « supérieur ou égal à », `>=`, qui retourne `true` si le premier opérande est supérieur ou égal au second, et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="28f11-103">All numeric and enumeration types define a "greater than or equal" relational operator, `>=` that returns `true` if the first operand is greater than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28f11-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="28f11-104">Remarks</span></span>  
 <span data-ttu-id="28f11-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `>=`.</span><span class="sxs-lookup"><span data-stu-id="28f11-105">User-defined types can overload the `>=` operator.</span></span> <span data-ttu-id="28f11-106">Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="28f11-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="28f11-107">Si `>=` est surchargé, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) doit l’être aussi.</span><span class="sxs-lookup"><span data-stu-id="28f11-107">If `>=` is overloaded, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="28f11-108">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="28f11-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28f11-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="28f11-109">Example</span></span>  
 <span data-ttu-id="28f11-110">[!code-cs[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="28f11-110">[!code-cs[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f11-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28f11-111">See Also</span></span>  
 <span data-ttu-id="28f11-112">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="28f11-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="28f11-113">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="28f11-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="28f11-114">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="28f11-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

