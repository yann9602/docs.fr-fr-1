---
title: "%=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a2ac1-102">%=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a2ac1-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="a2ac1-103">Opérateur d’assignation de reste.</span><span class="sxs-lookup"><span data-stu-id="a2ac1-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2ac1-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="a2ac1-104">Remarks</span></span>  
 <span data-ttu-id="a2ac1-105">Une expression qui utilise l’opérateur d’assignation `%=`, telle que</span><span class="sxs-lookup"><span data-stu-id="a2ac1-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="a2ac1-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="a2ac1-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="a2ac1-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="a2ac1-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="a2ac1-108">L’[opérateur %](../../../csharp/language-reference/operators/modulus-operator.md) est prédéfini pour les types numériques de façon à calculer le reste d’une division.</span><span class="sxs-lookup"><span data-stu-id="a2ac1-108">The [% operator](../../../csharp/language-reference/operators/modulus-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="a2ac1-109">L’opérateur `%=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur %](../../../csharp/language-reference/operators/modulus-operator.md) (consultez [operator (informations de référence sur C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a2ac1-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/modulus-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2ac1-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="a2ac1-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a2ac1-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2ac1-111">See Also</span></span>  
 [<span data-ttu-id="a2ac1-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a2ac1-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a2ac1-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a2ac1-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a2ac1-114">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="a2ac1-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
