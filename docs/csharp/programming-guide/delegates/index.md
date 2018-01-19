---
title: "Délégués (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c78b06b23805082251db8bbd7b377ffd36c6ef03
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="fa1dc-102">Délégués (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-102">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="fa1dc-103">Un [délégué](../../../csharp/language-reference/keywords/delegate.md) est un type qui représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="fa1dc-104">Lorsque vous instanciez un délégué, vous pouvez associer son instance à toute méthode ayant une signature et un type de retour compatibles.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-104">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="fa1dc-105">Vous pouvez appeler la méthode par le biais l'instance de délégué.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-105">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="fa1dc-106">Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-106">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="fa1dc-107">Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-107">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="fa1dc-108">Vous créez une méthode personnalisée, et une classe telle qu'un contrôle Windows peut appeler votre méthode lorsqu'un certain événement se produit.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-108">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="fa1dc-109">L'exemple suivant illustre une déclaration de délégué :</span><span class="sxs-lookup"><span data-stu-id="fa1dc-109">The following example shows a delegate declaration:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="fa1dc-110">Toute méthode de n'importe quelle classe ou structure accessible qui correspond au type de délégué, peut être assignée au délégué.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-110">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="fa1dc-111">La méthode peut être une méthode d'instance ou statique.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-111">The method can be either static or an instance method.</span></span> <span data-ttu-id="fa1dc-112">Cela permet de modifier par programme les appels de méthode, mais également d'insérer du nouveau code dans les classes existantes.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-112">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa1dc-113">Dans le contexte de surcharge de méthodes, la signature d'une méthode n'inclut pas la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-113">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="fa1dc-114">Mais dans le contexte des délégués, la signature inclut la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-114">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="fa1dc-115">En d'autres termes, une méthode doit avoir le même type de retour que le délégué.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-115">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="fa1dc-116">Cette capacité à faire référence à une méthode en tant que paramètre fait des délégués les instruments idéaux pour définir des méthodes de rappel.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-116">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="fa1dc-117">Par exemple, une référence à une méthode qui compare deux objets peut être passée comme argument à un algorithme de tri.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-117">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="fa1dc-118">Étant donné que le code de comparaison est dans une procédure distincte, l'algorithme de tri peut être écrit de façon plus générale.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-118">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="fa1dc-119">Vue d'ensemble des délégués</span><span class="sxs-lookup"><span data-stu-id="fa1dc-119">Delegates Overview</span></span>  
 <span data-ttu-id="fa1dc-120">Les délégués ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa1dc-120">Delegates have the following properties:</span></span>  
  
-   <span data-ttu-id="fa1dc-121">Les délégués sont semblables aux pointeurs de fonction C++, mais ils sont de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-121">Delegates are like C++ function pointers but are type safe.</span></span>  
  
-   <span data-ttu-id="fa1dc-122">Les délégués permettent aux méthodes d'être transmises comme des paramètres.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-122">Delegates allow methods to be passed as parameters.</span></span>  
  
-   <span data-ttu-id="fa1dc-123">Les délégués peuvent être utilisés pour définir des méthodes de rappel.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-123">Delegates can be used to define callback methods.</span></span>  
  
-   <span data-ttu-id="fa1dc-124">Les délégués peuvent être chaînés ; par exemple, plusieurs méthodes peuvent être appelées sur un seul événement.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-124">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
-   <span data-ttu-id="fa1dc-125">Les méthodes ne doivent pas correspondre exactement au type du délégué.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-125">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="fa1dc-126">Pour plus d’informations, consultez [Utilisation de la variance dans les délégués](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fa1dc-126">For more information, see [Using Variance in Delegates](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
-   <span data-ttu-id="fa1dc-127">C# version 2.0 a introduit le concept de [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), qui permet de passer des blocs de code en tant que paramètres à la place d'une méthode définie séparément.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-127">C# version 2.0 introduced the concept of [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="fa1dc-128">C# 3.0 a introduit les expressions lambda comme un moyen plus concis d’écrire des blocs de code inline.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-128">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="fa1dc-129">Les méthodes anonymes et les expressions lambda (dans certains contextes) sont toutes deux compilées en types de délégué.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-129">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="fa1dc-130">Ces fonctionnalités sont désormais conjointement désignées par l’expression « fonctions anonymes ».</span><span class="sxs-lookup"><span data-stu-id="fa1dc-130">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="fa1dc-131">Pour plus d’informations sur les expressions lambda, consultez [Fonctions anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="fa1dc-131">For more information about lambda expressions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa1dc-132">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fa1dc-132">In This Section</span></span>  
  
-   [<span data-ttu-id="fa1dc-133">Utilisation de délégués</span><span class="sxs-lookup"><span data-stu-id="fa1dc-133">Using Delegates</span></span>](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [<span data-ttu-id="fa1dc-134">Quand utiliser des délégués à la place d’interfaces (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-134">When to Use Delegates Instead of Interfaces (C# Programming Guide)</span></span>](http://msdn.microsoft.com/library/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [<span data-ttu-id="fa1dc-135">Délégués avec méthodes nommées et méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="fa1dc-135">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [<span data-ttu-id="fa1dc-136">Méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="fa1dc-136">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [<span data-ttu-id="fa1dc-137">Utilisation de la variance dans les délégués</span><span class="sxs-lookup"><span data-stu-id="fa1dc-137">Using Variance in Delegates</span></span>](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [<span data-ttu-id="fa1dc-138">Guide pratique pour combiner des délégués (délégués multicast)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-138">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [<span data-ttu-id="fa1dc-139">Comment : déclarer, instancier et utiliser un délégué</span><span class="sxs-lookup"><span data-stu-id="fa1dc-139">How to: Declare, Instantiate, and Use a Delegate</span></span>](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="fa1dc-140">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="fa1dc-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="fa1dc-141">Chapitres proposés</span><span class="sxs-lookup"><span data-stu-id="fa1dc-141">Featured Book Chapters</span></span>  
 <span data-ttu-id="fa1dc-142">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-142">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
 <span data-ttu-id="fa1dc-143">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) dans [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-143">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) in [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1dc-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa1dc-144">See Also</span></span>  
 <xref:System.Delegate>  
 [<span data-ttu-id="fa1dc-145">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fa1dc-145">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fa1dc-146">Événements</span><span class="sxs-lookup"><span data-stu-id="fa1dc-146">Events</span></span>](../../../csharp/programming-guide/events/index.md)
