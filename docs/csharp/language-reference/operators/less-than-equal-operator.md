---
title: "&lt;=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a74af852451a193aaee70fea2a68ca8ff29cc215
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="eaa76-102">&lt;=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="eaa76-102">&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="eaa76-103">Tous les types numériques et d’énumération définissent un opérateur relationnel « inférieur ou égal à » (`<=`) qui retourne `true` si le premier opérande est inférieur ou égal au deuxième et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="eaa76-103">All numeric and enumeration types define a "less than or equal" relational operator (`<=`) that returns `true` if the first operand is less than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaa76-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="eaa76-104">Remarks</span></span>  
 <span data-ttu-id="eaa76-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `<=`.</span><span class="sxs-lookup"><span data-stu-id="eaa76-105">User-defined types can overload the `<=` operator.</span></span> <span data-ttu-id="eaa76-106">Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="eaa76-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="eaa76-107">Si `<=` est surchargé, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) doit aussi l’être.</span><span class="sxs-lookup"><span data-stu-id="eaa76-107">If `<=` is overloaded, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="eaa76-108">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="eaa76-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaa76-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="eaa76-109">Example</span></span>  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="eaa76-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eaa76-110">See Also</span></span>  
 [<span data-ttu-id="eaa76-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="eaa76-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="eaa76-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="eaa76-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eaa76-113">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="eaa76-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="eaa76-114">explicit</span><span class="sxs-lookup"><span data-stu-id="eaa76-114">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
