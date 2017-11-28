---
title: "&lt;, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76d53d4c943c886f6b8c8a68e2b8bb12bc9a9d6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="49206-102">&lt;, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="49206-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="49206-103">Tous les types numériques et d’énumération définissent un opérateur relationnel « inférieur à » (`<`) qui retourne `true` si le premier opérande est inférieur au deuxième et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="49206-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49206-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="49206-104">Remarks</span></span>  
 <span data-ttu-id="49206-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `<` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="49206-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="49206-106">Si `<` est surchargé, [>](../../../csharp/language-reference/operators/greater-than-operator.md) doit aussi l’être.</span><span class="sxs-lookup"><span data-stu-id="49206-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="49206-107">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="49206-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49206-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="49206-108">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="49206-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49206-109">See Also</span></span>  
 [<span data-ttu-id="49206-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="49206-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="49206-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="49206-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="49206-112">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="49206-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
