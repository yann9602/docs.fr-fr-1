---
title: "Exécution et évaluation différées dans LINQ to XML (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 10ecebc2563df5a12b71a743727b1be21b19b671
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a><span data-ttu-id="a140e-102">Exécution et évaluation différées dans LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a140e-102">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>
<span data-ttu-id="a140e-103">Les opérations de requête et d'axe sont souvent implémentées pour utiliser l'exécution différée.</span><span class="sxs-lookup"><span data-stu-id="a140e-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="a140e-104">Cette rubrique explique les conditions requises et les avantages de l'exécution différée et certaines considérations relatives à l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="a140e-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="a140e-105">Exécution différée</span><span class="sxs-lookup"><span data-stu-id="a140e-105">Deferred Execution</span></span>  
 <span data-ttu-id="a140e-106">Le terme "exécution différée" signifie que l’évaluation d’une expression est retardée jusqu’à ce que sa valeur *réalisée* soit réellement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a140e-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="a140e-107">L'exécution différée peut améliorer sensiblement les performances lorsque vous devez manipuler de grandes collectes de données, en particulier dans les programmes qui contiennent une série de manipulations ou de requêtes chaînées.</span><span class="sxs-lookup"><span data-stu-id="a140e-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="a140e-108">Dans le meilleur cas, l'exécution différée autorise une seule itération dans la collection source.</span><span class="sxs-lookup"><span data-stu-id="a140e-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="a140e-109">Les technologies LINQ utilisent beaucoup l'exécution différée dans les membres des classes <xref:System.Linq?displayProperty=fullName> principales et dans les méthodes d'extension dans les différents espaces de noms LINQ, tels que <xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="a140e-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=fullName> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="a140e-110">L’exécution différée est prise en charge directement dans le langage C# par le mot clé [yield](../../../../csharp/language-reference/keywords/yield.md) (sous la forme de l’instruction `yield-return`) quand elle est utilisée dans un bloc itérateur.</span><span class="sxs-lookup"><span data-stu-id="a140e-110">Deferred execution is supported directly in the C# language by the [yield](../../../../csharp/language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="a140e-111">Un tel itérateur doit renvoyer une collection de type <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> (ou un type dérivé).</span><span class="sxs-lookup"><span data-stu-id="a140e-111">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="a140e-112">Évaluation stricte et évaluation différée</span><span class="sxs-lookup"><span data-stu-id="a140e-112">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="a140e-113">Lorsque vous écrivez une méthode qui implémente l'exécution différée, vous devez également décider s'il faut implémenter la méthode à l'aide de l'évaluation différée ou de l'évaluation stricte.</span><span class="sxs-lookup"><span data-stu-id="a140e-113">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="a140e-114">Avec l’*évaluation différée*, un seul élément de la collection source est traité pendant chaque appel à l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="a140e-114">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="a140e-115">Il s'agit du mode d'implémentation par défaut des itérateurs.</span><span class="sxs-lookup"><span data-stu-id="a140e-115">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="a140e-116">Avec l’*évaluation stricte*, le premier appel à l’itérateur entraîne le traitement de l’ensemble de la collection.</span><span class="sxs-lookup"><span data-stu-id="a140e-116">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="a140e-117">Une copie temporaire de la collection source peut également être nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a140e-117">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="a140e-118">Par exemple, la méthode <xref:System.Linq.Enumerable.OrderBy%2A> doit trier l'ensemble de la collection avant de renvoyer le premier élément.</span><span class="sxs-lookup"><span data-stu-id="a140e-118">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="a140e-119">L'évaluation différée procure en général de meilleures performances car elle répartit le traitement de surcharge de manière égale durant l'évaluation de la collection et limite l'utilisation des données temporaires.</span><span class="sxs-lookup"><span data-stu-id="a140e-119">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="a140e-120">Bien entendu, pour certaines opérations il est impossible d'éviter la matérialisation de résultats intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="a140e-120">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a140e-121">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a140e-121">Next Steps</span></span>  
 <span data-ttu-id="a140e-122">La rubrique suivante de ce didacticiel illustre l'exécution différée :</span><span class="sxs-lookup"><span data-stu-id="a140e-122">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="a140e-123">Exemple d’exécution différée (C#)</span><span class="sxs-lookup"><span data-stu-id="a140e-123">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="a140e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a140e-124">See Also</span></span>  
 <span data-ttu-id="a140e-125">[Didacticiel : chaînage de requêtes (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) </span><span class="sxs-lookup"><span data-stu-id="a140e-125">[Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) </span></span>  
 <span data-ttu-id="a140e-126">[Concepts et terminologie (transformation fonctionnelle) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a140e-126">[Concepts and Terminology (Functional Transformation) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md) </span></span>  
 <span data-ttu-id="a140e-127">[Opérations d’agrégation (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md) </span><span class="sxs-lookup"><span data-stu-id="a140e-127">[Aggregation Operations (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md) </span></span>  
 [<span data-ttu-id="a140e-128">yield</span><span class="sxs-lookup"><span data-stu-id="a140e-128">yield</span></span>](../../../../csharp/language-reference/keywords/yield.md)

