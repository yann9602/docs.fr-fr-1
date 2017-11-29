---
title: "&gt;&gt;=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6bd0a61860c35a485d61585a90ba297f75d8cf1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="5b1ad-102">&gt;&gt;=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="5b1ad-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="5b1ad-103">Opérateur d’assignation de décalage vers la droite.</span><span class="sxs-lookup"><span data-stu-id="5b1ad-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b1ad-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="5b1ad-104">Remarks</span></span>  
 <span data-ttu-id="5b1ad-105">Une expression sous la forme</span><span class="sxs-lookup"><span data-stu-id="5b1ad-105">An expression of the form</span></span>  
  
```  
x >>= y  
```  
  
 <span data-ttu-id="5b1ad-106">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="5b1ad-106">is evaluated as</span></span>  
  
```  
x = x >> y  
```  
  
 <span data-ttu-id="5b1ad-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="5b1ad-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="5b1ad-108">L’[opérateur >>](../../../csharp/language-reference/operators/right-shift-operator.md) décale `x` vers la droite de la valeur spécifiée par `y`.</span><span class="sxs-lookup"><span data-stu-id="5b1ad-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="5b1ad-109">L’opérateur >>= ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur >>](../../../csharp/language-reference/operators/right-shift-operator.md) (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="5b1ad-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b1ad-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b1ad-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5b1ad-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b1ad-111">See Also</span></span>  
 [<span data-ttu-id="5b1ad-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="5b1ad-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5b1ad-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5b1ad-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5b1ad-114">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="5b1ad-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
