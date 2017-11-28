---
title: "&amp;=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="ae042-102">&amp;=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ae042-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="ae042-103">Opérateur d’assignation AND.</span><span class="sxs-lookup"><span data-stu-id="ae042-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae042-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="ae042-104">Remarks</span></span>  
 <span data-ttu-id="ae042-105">Une expression qui utilise l’opérateur d’assignation `&=`, telle que</span><span class="sxs-lookup"><span data-stu-id="ae042-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```  
x &= y  
```  
  
 <span data-ttu-id="ae042-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="ae042-106">is equivalent to</span></span>  
  
```  
x = x & y  
```  
  
 <span data-ttu-id="ae042-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ae042-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="ae042-108">L’[opérateur &](../../../csharp/language-reference/operators/and-operator.md) effectue une opération AND logique au niveau du bit sur les opérandes de type intégral et une opération AND logique sur les opérandes de type `bool`.</span><span class="sxs-lookup"><span data-stu-id="ae042-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="ae042-109">L’opérateur `&=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur &](../../../csharp/language-reference/operators/and-operator.md) binaire (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="ae042-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae042-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="ae042-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ae042-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae042-111">See Also</span></span>  
 [<span data-ttu-id="ae042-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ae042-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ae042-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ae042-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ae042-114">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="ae042-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
