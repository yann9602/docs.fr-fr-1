---
title: "Gérer des exceptions dans des expressions de requête"
description: "Comment gérer des exceptions dans des expressions de requête."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9ce4a4ca62bb476b2414ec8b93d5633faca53b59
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="87f63-104">Gérer des exceptions dans des expressions de requête</span><span class="sxs-lookup"><span data-stu-id="87f63-104">Handle exceptions in query expressions</span></span>

<span data-ttu-id="87f63-105">Dans le contexte d’une expression de requête, vous pouvez utiliser n’importe quelle méthode.</span><span class="sxs-lookup"><span data-stu-id="87f63-105">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="87f63-106">Toutefois, nous vous recommandons d’éviter d’appeler une méthode dans une expression de requête susceptible de créer un effet secondaire, tel que la modification du contenu de la source de données ou la levée d’une exception.</span><span class="sxs-lookup"><span data-stu-id="87f63-106">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="87f63-107">Cet exemple montre comment éviter la levée d’exceptions lorsque vous appelez des méthodes dans une expression de requête, en respectant les directives générales du .NET Framework relatives à la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="87f63-107">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="87f63-108">Selon ces directives, il est acceptable d’intercepter une exception si vous comprenez pourquoi elle est levée dans un contexte donné.</span><span class="sxs-lookup"><span data-stu-id="87f63-108">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="87f63-109">Pour plus d’informations, consultez les [Bonnes pratiques pour les exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="87f63-109">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="87f63-110">Le dernier exemple montre comment gérer les cas où vous devez lever une exception pendant l’exécution d’une requête.</span><span class="sxs-lookup"><span data-stu-id="87f63-110">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87f63-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="87f63-111">Example</span></span>  

 <span data-ttu-id="87f63-112">L’exemple suivant montre comment déplacer du code de gestion des exceptions en dehors d’une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="87f63-112">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="87f63-113">Ceci est possible uniquement lorsque la méthode ne dépend pas des variables locales de la requête.</span><span class="sxs-lookup"><span data-stu-id="87f63-113">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 <span data-ttu-id="87f63-114">[!code-cs[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="87f63-114">[!code-cs[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="87f63-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="87f63-115">Example</span></span> 

 <span data-ttu-id="87f63-116">Dans certains cas, la meilleure réponse à la levée d’une exception à l’intérieur d’une requête consiste à arrêter immédiatement l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="87f63-116">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="87f63-117">L’exemple suivant montre comment gérer les exceptions pouvant être levées dans le corps d’une requête.</span><span class="sxs-lookup"><span data-stu-id="87f63-117">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="87f63-118">Supposons que `SomeMethodThatMightThrow` puisse provoquer la levée d’une exception qui nécessite l’arrêt de l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="87f63-118">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="87f63-119">Notez que le bloc `try` englobe la boucle `foreach` et non la requête.</span><span class="sxs-lookup"><span data-stu-id="87f63-119">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="87f63-120">Ceci s’explique par le fait que c’est au niveau de la boucle `foreach` que la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="87f63-120">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="87f63-121">Pour plus d’informations, consultez [Introduction aux requêtes LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="87f63-121">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="87f63-122">[!code-cs[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="87f63-122">[!code-cs[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="87f63-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87f63-123">See Also</span></span>  
 [<span data-ttu-id="87f63-124">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="87f63-124">LINQ query expressions</span></span>](index.md)

