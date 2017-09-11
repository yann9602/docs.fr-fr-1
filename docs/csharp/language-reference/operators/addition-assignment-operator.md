---
title: "+=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
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
ms.openlocfilehash: 42567b2d8e7d9b694ce64ccb88e0fd4bfe05b020
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="fe591-102">+=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="fe591-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="fe591-103">Opérateur d’assignation d’addition.</span><span class="sxs-lookup"><span data-stu-id="fe591-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe591-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="fe591-104">Remarks</span></span>  
 <span data-ttu-id="fe591-105">Une expression qui utilise l’opérateur d’assignation `+=`, telle que</span><span class="sxs-lookup"><span data-stu-id="fe591-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```  
x += y  
```  
  
 <span data-ttu-id="fe591-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="fe591-106">is equivalent to</span></span>  
  
```  
x = x + y  
```  
  
 <span data-ttu-id="fe591-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="fe591-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="fe591-108">La signification de l’[opérateur +](../../../csharp/language-reference/operators/addition-operator.md) dépend des types de `x` et `y` (addition pour les opérandes numériques, concaténation pour les opérandes de type chaîne, etc.).</span><span class="sxs-lookup"><span data-stu-id="fe591-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="fe591-109">L’opérateur `+=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur -](../../../csharp/language-reference/operators/addition-operator.md) (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="fe591-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="fe591-110">L’opérateur `+=` est également utilisé pour spécifier une méthode qui sera appelée en réponse à un événement ; ces méthodes sont appelées « gestionnaires d’événements ».</span><span class="sxs-lookup"><span data-stu-id="fe591-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="fe591-111">L’utilisation de l’opérateur `+=` dans ce contexte est appelée *abonnement à un événement*.</span><span class="sxs-lookup"><span data-stu-id="fe591-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="fe591-112">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="fe591-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span> <span data-ttu-id="fe591-113">et [Délégués](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="fe591-113">and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe591-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="fe591-114">Example</span></span>  
 <span data-ttu-id="fe591-115">[!code-cs[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="fe591-115">[!code-cs[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe591-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe591-116">See Also</span></span>  
 <span data-ttu-id="fe591-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="fe591-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="fe591-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fe591-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="fe591-119">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="fe591-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

