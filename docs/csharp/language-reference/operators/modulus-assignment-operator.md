---
title: "%=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
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
ms.openlocfilehash: 48484a0593102c92304803e5c0697501b0e26e0e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="ea0c1-102">%=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ea0c1-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="ea0c1-103">Opérateur d’assignation de reste.</span><span class="sxs-lookup"><span data-stu-id="ea0c1-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea0c1-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="ea0c1-104">Remarks</span></span>  
 <span data-ttu-id="ea0c1-105">Une expression qui utilise l’opérateur d’assignation `%=`, telle que</span><span class="sxs-lookup"><span data-stu-id="ea0c1-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="ea0c1-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="ea0c1-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="ea0c1-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ea0c1-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="ea0c1-108">L’[opérateur %](../../../csharp/language-reference/operators/modulus-operator.md) est prédéfini pour les types numériques de façon à calculer le reste d’une division.</span><span class="sxs-lookup"><span data-stu-id="ea0c1-108">The [% operator](../../../csharp/language-reference/operators/modulus-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="ea0c1-109">L’opérateur `%=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur %](../../../csharp/language-reference/operators/modulus-operator.md) (consultez [operator (informations de référence sur C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="ea0c1-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/modulus-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea0c1-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea0c1-110">Example</span></span>  
 <span data-ttu-id="ea0c1-111">[!code-cs[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ea0c1-111">[!code-cs[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea0c1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea0c1-112">See Also</span></span>  
 <span data-ttu-id="ea0c1-113">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea0c1-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ea0c1-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea0c1-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="ea0c1-115">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="ea0c1-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

