---
title: "&gt;, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc7c173ecc97bd3ca3b76a92ccbabc0f40062ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="6b04e-102">&gt;, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6b04e-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="6b04e-103">Tous les types numériques et d’énumération définissent un opérateur relationnel « supérieur à » (`>`) qui retourne `true` si le premier opérande est supérieur au second, et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="6b04e-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b04e-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="6b04e-104">Remarks</span></span>  
 <span data-ttu-id="6b04e-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `>` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6b04e-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="6b04e-106">Si `>` est surchargé, [<](../../../csharp/language-reference/operators/less-than-operator.md) doit aussi l’être.</span><span class="sxs-lookup"><span data-stu-id="6b04e-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="6b04e-107">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="6b04e-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b04e-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b04e-108">Example</span></span>  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6b04e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b04e-109">See Also</span></span>  
 [<span data-ttu-id="6b04e-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="6b04e-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6b04e-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6b04e-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6b04e-112">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="6b04e-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="6b04e-113">explicit</span><span class="sxs-lookup"><span data-stu-id="6b04e-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
