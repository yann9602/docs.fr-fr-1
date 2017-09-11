---
title: "|=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
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
ms.openlocfilehash: f1c0a92414739efc2ab091871e80852737fdf931
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="48dc2-102">|=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="48dc2-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="48dc2-103">Opérateur d’assignation OR.</span><span class="sxs-lookup"><span data-stu-id="48dc2-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48dc2-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="48dc2-104">Remarks</span></span>  
 <span data-ttu-id="48dc2-105">Une expression qui utilise l’opérateur d’assignation `|=`, telle que</span><span class="sxs-lookup"><span data-stu-id="48dc2-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```  
x |= y  
```  
  
 <span data-ttu-id="48dc2-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="48dc2-106">is equivalent to</span></span>  
  
```  
x = x | y  
```  
  
 <span data-ttu-id="48dc2-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="48dc2-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="48dc2-108">L’[opérateur &#124](../../../csharp/language-reference/operators/or-operator.md) effectue une opération OR logique au niveau du bit sur les opérandes intégraux et une opération OR logique sur les opérandes de type bool.</span><span class="sxs-lookup"><span data-stu-id="48dc2-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="48dc2-109">L’opérateur `|=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur &#124;](../../../csharp/language-reference/operators/or-operator.md) (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="48dc2-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48dc2-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="48dc2-110">Example</span></span>  
 <span data-ttu-id="48dc2-111">[!code-cs[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="48dc2-111">[!code-cs[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48dc2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48dc2-112">See Also</span></span>  
 <span data-ttu-id="48dc2-113">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="48dc2-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="48dc2-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="48dc2-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="48dc2-115">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="48dc2-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

