---
title: "L’exécution différée et évaluation différées dans LINQ to XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a465c4448157505a42db57202298cb18e44a562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a><span data-ttu-id="279cb-102">L’exécution différée et évaluation différées dans LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="279cb-102">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="279cb-103">Les opérations de requête et d'axe sont souvent implémentées pour utiliser l'exécution différée.</span><span class="sxs-lookup"><span data-stu-id="279cb-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="279cb-104">Cette rubrique explique les conditions requises et les avantages de l'exécution différée et certaines considérations relatives à l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="279cb-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="279cb-105">Exécution différée</span><span class="sxs-lookup"><span data-stu-id="279cb-105">Deferred Execution</span></span>  
 <span data-ttu-id="279cb-106">Le terme "exécution différée" signifie que l’évaluation d’une expression est retardée jusqu’à ce que sa valeur *réalisée* soit réellement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="279cb-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="279cb-107">L'exécution différée peut améliorer sensiblement les performances lorsque vous devez manipuler de grandes collectes de données, en particulier dans les programmes qui contiennent une série de manipulations ou de requêtes chaînées.</span><span class="sxs-lookup"><span data-stu-id="279cb-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="279cb-108">Dans le meilleur cas, l'exécution différée autorise une seule itération dans la collection source.</span><span class="sxs-lookup"><span data-stu-id="279cb-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="279cb-109">Les technologies LINQ utilisent beaucoup l'exécution différée dans les membres des classes <xref:System.Linq?displayProperty=nameWithType> principales et dans les méthodes d'extension dans les différents espaces de noms LINQ, tels que <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="279cb-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="279cb-110">Évaluation stricte et évaluation différée</span><span class="sxs-lookup"><span data-stu-id="279cb-110">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="279cb-111">Lorsque vous écrivez une méthode qui implémente l'exécution différée, vous devez également décider s'il faut implémenter la méthode à l'aide de l'évaluation différée ou de l'évaluation stricte.</span><span class="sxs-lookup"><span data-stu-id="279cb-111">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="279cb-112">Avec l’*évaluation différée*, un seul élément de la collection source est traité pendant chaque appel à l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="279cb-112">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="279cb-113">Il s'agit du mode d'implémentation par défaut des itérateurs.</span><span class="sxs-lookup"><span data-stu-id="279cb-113">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="279cb-114">Avec l’*évaluation stricte*, le premier appel à l’itérateur entraîne le traitement de l’ensemble de la collection.</span><span class="sxs-lookup"><span data-stu-id="279cb-114">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="279cb-115">Une copie temporaire de la collection source peut également être nécessaire.</span><span class="sxs-lookup"><span data-stu-id="279cb-115">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="279cb-116">Par exemple, la méthode <xref:System.Linq.Enumerable.OrderBy%2A> doit trier l'ensemble de la collection avant de renvoyer le premier élément.</span><span class="sxs-lookup"><span data-stu-id="279cb-116">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="279cb-117">L'évaluation différée procure en général de meilleures performances car elle répartit le traitement de surcharge de manière égale durant l'évaluation de la collection et limite l'utilisation des données temporaires.</span><span class="sxs-lookup"><span data-stu-id="279cb-117">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="279cb-118">Bien entendu, pour certaines opérations il est impossible d'éviter la matérialisation de résultats intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="279cb-118">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="279cb-119">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="279cb-119">Next Steps</span></span>  
 <span data-ttu-id="279cb-120">La rubrique suivante de ce didacticiel illustre l'exécution différée :</span><span class="sxs-lookup"><span data-stu-id="279cb-120">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="279cb-121">Exemple d’exécution différée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="279cb-121">Deferred Execution Example (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="279cb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="279cb-122">See Also</span></span>  
 [<span data-ttu-id="279cb-123">Didacticiel : Différée d’exécution (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="279cb-123">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)  
 [<span data-ttu-id="279cb-124">Concepts et terminologie (Transformation fonctionnelle) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="279cb-124">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [<span data-ttu-id="279cb-125">Opérations d’agrégation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="279cb-125">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
