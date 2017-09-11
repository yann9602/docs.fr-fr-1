---
title: "-=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
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
ms.openlocfilehash: d7f26ae1fce54eb0d03a314a83ce523baeb3f348
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="--operator-c-reference"></a><span data-ttu-id="3be9e-102">-=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3be9e-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="3be9e-103">Opérateur d’assignation de soustraction.</span><span class="sxs-lookup"><span data-stu-id="3be9e-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3be9e-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="3be9e-104">Remarks</span></span>  
 <span data-ttu-id="3be9e-105">Une expression qui utilise l’opérateur d’assignation `-=`, telle que</span><span class="sxs-lookup"><span data-stu-id="3be9e-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```  
x -= y  
```  
  
 <span data-ttu-id="3be9e-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="3be9e-106">is equivalent to</span></span>  
  
```  
x = x - y  
```  
  
 <span data-ttu-id="3be9e-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3be9e-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="3be9e-108">La signification de l’[opérateur -](../../../csharp/language-reference/operators/subtraction-operator.md) dépend des types de `x` et `y` (soustraction pour les opérandes numériques, suppression de délégués pour les opérandes délégués, etc.).</span><span class="sxs-lookup"><span data-stu-id="3be9e-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="3be9e-109">L’opérateur `-=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur -](../../../csharp/language-reference/operators/subtraction-operator.md) (voir [opérateur](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3be9e-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="3be9e-110">L’opérateur -= est également utilisé en C# pour annuler l’abonnement à un événement.</span><span class="sxs-lookup"><span data-stu-id="3be9e-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="3be9e-111">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="3be9e-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3be9e-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3be9e-112">Example</span></span>  
 <span data-ttu-id="3be9e-113">[!code-cs[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3be9e-113">[!code-cs[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be9e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3be9e-114">See Also</span></span>  
 <span data-ttu-id="3be9e-115">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3be9e-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="3be9e-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3be9e-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="3be9e-117">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="3be9e-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

