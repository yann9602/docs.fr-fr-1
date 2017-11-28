---
title: "^=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ^=_CSharpKeyword
helpviewer_keywords: ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f6b06-102">^=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f6b06-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="f6b06-103">Opérateur d’assignation OR exclusif.</span><span class="sxs-lookup"><span data-stu-id="f6b06-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6b06-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6b06-104">Remarks</span></span>  
 <span data-ttu-id="f6b06-105">Une expression sous la forme</span><span class="sxs-lookup"><span data-stu-id="f6b06-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="f6b06-106">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="f6b06-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="f6b06-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="f6b06-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f6b06-108">L’[opérateur ^](../../../csharp/language-reference/operators/xor-operator.md) effectue une opération de bits OR exclusif sur les opérandes de type intégral et une opération OR exclusif logique sur les opérandes de type [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="f6b06-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="f6b06-109">L’opérateur ^= ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur ^](../../../csharp/language-reference/operators/xor-operator.md) (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f6b06-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6b06-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6b06-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f6b06-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6b06-111">See Also</span></span>  
 [<span data-ttu-id="f6b06-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f6b06-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f6b06-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f6b06-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f6b06-114">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="f6b06-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
