---
title: "Guide pratique pour déclarer, instancier et utiliser un délégué (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5a5329b9e99fcd5830a57eb8f97b4edb67ad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="143e3-102">Guide pratique pour déclarer, instancier et utiliser un délégué (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="143e3-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="143e3-103">Dans C# 1.0 et versions ultérieures, vous pouvez déclarer des délégués comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="143e3-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="143e3-104">C# 2.0 offre un moyen plus simple d’écrire la déclaration précédente, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="143e3-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="143e3-105">Dans C# 2.0 et versions ultérieures, vous pouvez aussi utiliser une méthode anonyme pour déclarer et initialiser un [délégué](../../../csharp/language-reference/keywords/delegate.md), comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="143e3-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="143e3-106">Dans C# 3.0 et versions ultérieures, vous pouvez aussi déclarer et instancier des délégués à l’aide d’une expression lambda, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="143e3-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="143e3-107">Pour plus d’informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="143e3-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="143e3-108">L’exemple suivant illustre la déclaration, l’instanciation et l’utilisation d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="143e3-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="143e3-109">La classe `BookDB` encapsule une base de données de librairie qui tient à jour un inventaire des livres.</span><span class="sxs-lookup"><span data-stu-id="143e3-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="143e3-110">Elle expose une méthode, `ProcessPaperbackBooks`, qui recherche tous les livres de poche dans la base de données et appelle un délégué pour chacun d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="143e3-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="143e3-111">Le type `delegate` qui est utilisé se nomme `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="143e3-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="143e3-112">La classe `Test` utilise cette classe pour imprimer les titres et le prix moyen des livres de poche.</span><span class="sxs-lookup"><span data-stu-id="143e3-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="143e3-113">L’utilisation des délégués favorise une bonne séparation des fonctionnalités entre la base de données de librairie et le code client.</span><span class="sxs-lookup"><span data-stu-id="143e3-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="143e3-114">Le code client n’a aucune connaissance de la façon dont les livres sont stockés, ni de la façon dont le code librairie trouve les livres de poche.</span><span class="sxs-lookup"><span data-stu-id="143e3-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="143e3-115">Le code librairie n’a aucune connaissance du traitement effectué sur les livres de poche une fois qu’il les a trouvés.</span><span class="sxs-lookup"><span data-stu-id="143e3-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="143e3-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="143e3-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="143e3-117">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="143e3-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="143e3-118">Déclaration d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="143e3-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="143e3-119">L’instruction suivante déclare un nouveau type délégué.</span><span class="sxs-lookup"><span data-stu-id="143e3-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="143e3-120">Chaque type délégué décrit le nombre et les types des arguments, ainsi que le type de la valeur de retour des méthodes qu’il peut encapsuler.</span><span class="sxs-lookup"><span data-stu-id="143e3-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="143e3-121">Chaque fois qu’un nouvel ensemble de types d’arguments ou de types de valeur de retour est nécessaire, un nouveau type délégué doit être déclaré.</span><span class="sxs-lookup"><span data-stu-id="143e3-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="143e3-122">Instanciation d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="143e3-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="143e3-123">Une fois que vous avez déclaré un type délégué, vous devez créer un objet délégué et l’associer à une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="143e3-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="143e3-124">Pour cela, dans l’exemple précédent vous passez la méthode `PrintTitle` à la méthode `ProcessPaperbackBooks`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="143e3-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="143e3-125">Cela crée un nouvel objet délégué associé à la méthode [statique](../../../csharp/language-reference/keywords/static.md) `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="143e3-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="143e3-126">De même, la méthode non statique `AddBookToTotal` sur l’objet `totaller` est passée comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="143e3-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="143e3-127">Dans les deux cas, un nouvel objet délégué est passé à la méthode `ProcessPaperbackBooks`.</span><span class="sxs-lookup"><span data-stu-id="143e3-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="143e3-128">Une fois un délégué créé, la méthode à laquelle il est associé ne change jamais. Les objets délégué sont immuables.</span><span class="sxs-lookup"><span data-stu-id="143e3-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="143e3-129">Appel d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="143e3-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="143e3-130">Une fois créé, un objet délégué est généralement passé à un autre code qui appellera le délégué.</span><span class="sxs-lookup"><span data-stu-id="143e3-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="143e3-131">Pour appeler un objet délégué, vous devez utiliser le nom de l’objet délégué, suivi des arguments entre parenthèses à passer au délégué.</span><span class="sxs-lookup"><span data-stu-id="143e3-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="143e3-132">Voici un exemple d’appel de délégué :</span><span class="sxs-lookup"><span data-stu-id="143e3-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="143e3-133">Vous pouvez appeler un délégué de manière synchrone, comme dans cet exemple, ou de manière asynchrone à l’aide des méthodes `BeginInvoke` et `EndInvoke`.</span><span class="sxs-lookup"><span data-stu-id="143e3-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="143e3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="143e3-134">See Also</span></span>  
 [<span data-ttu-id="143e3-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="143e3-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="143e3-136">Événements</span><span class="sxs-lookup"><span data-stu-id="143e3-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="143e3-137">Délégués</span><span class="sxs-lookup"><span data-stu-id="143e3-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
