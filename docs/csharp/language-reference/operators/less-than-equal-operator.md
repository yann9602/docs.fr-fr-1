---
title: "&lt;=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
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
ms.openlocfilehash: 931843783888a844d9f90f273b2362d327e8ccbc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="373fe-102">&lt;=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="373fe-102">&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="373fe-103">Tous les types numériques et d’énumération définissent un opérateur relationnel « inférieur ou égal à » (`<=`) qui retourne `true` si le premier opérande est inférieur ou égal au deuxième et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="373fe-103">All numeric and enumeration types define a "less than or equal" relational operator (`<=`) that returns `true` if the first operand is less than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="373fe-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="373fe-104">Remarks</span></span>  
 <span data-ttu-id="373fe-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `<=`.</span><span class="sxs-lookup"><span data-stu-id="373fe-105">User-defined types can overload the `<=` operator.</span></span> <span data-ttu-id="373fe-106">Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="373fe-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="373fe-107">Si `<=` est surchargé, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) doit aussi l’être.</span><span class="sxs-lookup"><span data-stu-id="373fe-107">If `<=` is overloaded, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="373fe-108">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="373fe-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="373fe-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="373fe-109">Example</span></span>  
 <span data-ttu-id="373fe-110">[!code-cs[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="373fe-110">[!code-cs[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="373fe-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="373fe-111">See Also</span></span>  
 <span data-ttu-id="373fe-112">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="373fe-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="373fe-113">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="373fe-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="373fe-114">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="373fe-114">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="373fe-115">explicit</span><span class="sxs-lookup"><span data-stu-id="373fe-115">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)

