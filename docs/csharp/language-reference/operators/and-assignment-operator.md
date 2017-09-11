---
title: "&amp;=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 15
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
ms.openlocfilehash: 6dec8de5077c07150ea37b88979e7b59b231d610
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="08aa3-102">&amp;=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="08aa3-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="08aa3-103">Opérateur d’assignation AND.</span><span class="sxs-lookup"><span data-stu-id="08aa3-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08aa3-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="08aa3-104">Remarks</span></span>  
 <span data-ttu-id="08aa3-105">Une expression qui utilise l’opérateur d’assignation `&=`, telle que</span><span class="sxs-lookup"><span data-stu-id="08aa3-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```  
x &= y  
```  
  
 <span data-ttu-id="08aa3-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="08aa3-106">is equivalent to</span></span>  
  
```  
x = x & y  
```  
  
 <span data-ttu-id="08aa3-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="08aa3-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="08aa3-108">L’[opérateur &](../../../csharp/language-reference/operators/and-operator.md) effectue une opération AND logique au niveau du bit sur les opérandes de type intégral et une opération AND logique sur les opérandes de type `bool`.</span><span class="sxs-lookup"><span data-stu-id="08aa3-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="08aa3-109">L’opérateur `&=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur &](../../../csharp/language-reference/operators/and-operator.md) binaire (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="08aa3-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08aa3-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="08aa3-110">Example</span></span>  
 <span data-ttu-id="08aa3-111">[!code-cs[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="08aa3-111">[!code-cs[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08aa3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08aa3-112">See Also</span></span>  
 <span data-ttu-id="08aa3-113">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="08aa3-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="08aa3-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="08aa3-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="08aa3-115">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="08aa3-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

