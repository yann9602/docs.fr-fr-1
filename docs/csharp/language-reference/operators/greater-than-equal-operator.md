---
title: "&gt;=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f020c2bd8756899908681ab72cac7aa2a203c6a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="20e1e-102">&gt;=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="20e1e-102">&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="20e1e-103">Tous les types numériques et d’énumération définissent un opérateur relationnel « supérieur ou égal à », `>=`, qui retourne `true` si le premier opérande est supérieur ou égal au second, et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="20e1e-103">All numeric and enumeration types define a "greater than or equal" relational operator, `>=` that returns `true` if the first operand is greater than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20e1e-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="20e1e-104">Remarks</span></span>  
 <span data-ttu-id="20e1e-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `>=`.</span><span class="sxs-lookup"><span data-stu-id="20e1e-105">User-defined types can overload the `>=` operator.</span></span> <span data-ttu-id="20e1e-106">Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="20e1e-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="20e1e-107">Si `>=` est surchargé, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) doit aussi l’être.</span><span class="sxs-lookup"><span data-stu-id="20e1e-107">If `>=` is overloaded, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="20e1e-108">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="20e1e-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20e1e-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="20e1e-109">Example</span></span>  
 [!code-csharp[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="20e1e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20e1e-110">See Also</span></span>  
 [<span data-ttu-id="20e1e-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="20e1e-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="20e1e-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="20e1e-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="20e1e-113">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="20e1e-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
