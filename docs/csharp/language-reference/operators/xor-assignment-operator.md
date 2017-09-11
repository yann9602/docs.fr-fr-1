---
title: "^=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
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
ms.openlocfilehash: 33b0dccf5031809bb4fcb73d0f7d6a344accdea3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="48644-102">^=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="48644-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="48644-103">Opérateur d’assignation OR exclusif.</span><span class="sxs-lookup"><span data-stu-id="48644-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48644-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="48644-104">Remarks</span></span>  
 <span data-ttu-id="48644-105">Une expression de la forme</span><span class="sxs-lookup"><span data-stu-id="48644-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="48644-106">est évaluée comme</span><span class="sxs-lookup"><span data-stu-id="48644-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="48644-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="48644-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="48644-108">L’[opérateur ^](../../../csharp/language-reference/operators/xor-operator.md) effectue une opération de bits OR exclusif sur les opérandes de type intégral et une opération OR exclusif logique sur les opérandes de type [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="48644-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="48644-109">L’opérateur ^= ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur ^](../../../csharp/language-reference/operators/xor-operator.md) (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="48644-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48644-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="48644-110">Example</span></span>  
 <span data-ttu-id="48644-111">[!code-cs[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="48644-111">[!code-cs[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48644-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48644-112">See Also</span></span>  
 <span data-ttu-id="48644-113">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="48644-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="48644-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="48644-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="48644-115">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="48644-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

