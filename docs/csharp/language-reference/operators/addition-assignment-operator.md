---
title: "+=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: de83f48fc644d8b232d9ef9e1698272f20a27d65
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d9eaa-102">+=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d9eaa-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="d9eaa-103">Opérateur d’assignation d’addition.</span><span class="sxs-lookup"><span data-stu-id="d9eaa-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9eaa-104">Notes</span><span class="sxs-lookup"><span data-stu-id="d9eaa-104">Remarks</span></span>  
 <span data-ttu-id="d9eaa-105">Une expression qui utilise l’opérateur d’assignation `+=`, telle que</span><span class="sxs-lookup"><span data-stu-id="d9eaa-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```  
x += y  
```  
  
 <span data-ttu-id="d9eaa-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="d9eaa-106">is equivalent to</span></span>  
  
```  
x = x + y  
```  
  
 <span data-ttu-id="d9eaa-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="d9eaa-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="d9eaa-108">La signification de l’[opérateur +](../../../csharp/language-reference/operators/addition-operator.md) dépend des types de `x` et `y` (addition pour les opérandes numériques, concaténation pour les opérandes de type chaîne, etc.).</span><span class="sxs-lookup"><span data-stu-id="d9eaa-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="d9eaa-109">L’opérateur `+=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur -](../../../csharp/language-reference/operators/addition-operator.md) (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d9eaa-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="d9eaa-110">L’opérateur `+=` est également utilisé pour spécifier une méthode qui sera appelée en réponse à un événement ; ces méthodes sont appelées « gestionnaires d’événements ».</span><span class="sxs-lookup"><span data-stu-id="d9eaa-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="d9eaa-111">L’utilisation de l’opérateur `+=` dans ce contexte est appelée *abonnement à un événement*.</span><span class="sxs-lookup"><span data-stu-id="d9eaa-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="d9eaa-112">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) et [Délégués](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9eaa-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9eaa-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9eaa-113">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d9eaa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9eaa-114">See Also</span></span>  
 [<span data-ttu-id="d9eaa-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d9eaa-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d9eaa-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d9eaa-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d9eaa-117">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="d9eaa-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
