---
title: "delegate (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 179e89cea0e683b72e57536d4e4d86b019493aed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-c-reference"></a><span data-ttu-id="92179-102">delegate (référence C#)</span><span class="sxs-lookup"><span data-stu-id="92179-102">delegate (C# Reference)</span></span>
<span data-ttu-id="92179-103">La déclaration d’un type délégué est semblable à une signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="92179-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="92179-104">Elle a une valeur de retour et un nombre quelconque de paramètres de type quelconque :</span><span class="sxs-lookup"><span data-stu-id="92179-104">It has a return value and any number of parameters of any type:</span></span>  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 <span data-ttu-id="92179-105">Un `delegate` est un type référence qui peut être utilisé pour encapsuler une méthode anonyme ou nommée.</span><span class="sxs-lookup"><span data-stu-id="92179-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="92179-106">Les délégués sont comparables aux pointeurs fonction en C++, mais ils offrent l’avantage d’être sûrs et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="92179-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="92179-107">Pour les applications de délégués, consultez [Délégués](../../../csharp/programming-guide/delegates/index.md) et [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="92179-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92179-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="92179-108">Remarks</span></span>  
 <span data-ttu-id="92179-109">Les délégués sont la base des [événements](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="92179-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="92179-110">Un délégué peut être instancié en l’associant à une méthode nommée ou anonyme.</span><span class="sxs-lookup"><span data-stu-id="92179-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="92179-111">Pour plus d’informations, consultez [Méthodes nommées](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) et [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="92179-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
 <span data-ttu-id="92179-112">Le délégué doit être instancié avec une méthode ou une expression lambda qui a un type de retour compatible et des paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="92179-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="92179-113">Pour plus d’informations sur le degré de variance autorisé dans la signature de méthode, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="92179-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="92179-114">Pour une utilisation avec des méthodes anonymes, le délégué et le code à lui associer sont déclarés ensemble.</span><span class="sxs-lookup"><span data-stu-id="92179-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="92179-115">Les deux façons d’instancier un délégué sont décrites dans cette section.</span><span class="sxs-lookup"><span data-stu-id="92179-115">Both ways of instantiating delegates are discussed in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92179-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="92179-116">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="92179-117">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="92179-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92179-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92179-118">See Also</span></span>  
 [<span data-ttu-id="92179-119">Référence C#</span><span class="sxs-lookup"><span data-stu-id="92179-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="92179-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="92179-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="92179-121">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="92179-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="92179-122">Types référence</span><span class="sxs-lookup"><span data-stu-id="92179-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="92179-123">Délégués</span><span class="sxs-lookup"><span data-stu-id="92179-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="92179-124">Événements</span><span class="sxs-lookup"><span data-stu-id="92179-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="92179-125">Délégués avec méthodes nommées et méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="92179-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [<span data-ttu-id="92179-126">Méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="92179-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
