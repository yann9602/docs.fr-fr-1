---
title: "Effectuer des opérations de jointure personnalisées"
description: "Guide pratique pour effectuer des opérations de jointure personnalisées."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: fef146c92a5cbbf21f8f1688f221c2bd45c99de7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="3cc47-104">Effectuer des opérations de jointure personnalisées</span><span class="sxs-lookup"><span data-stu-id="3cc47-104">Perform custom join operations</span></span>

<span data-ttu-id="3cc47-105">Cet exemple montre comment effectuer des opérations de jointure qui ne sont pas possibles avec la clause `join`.</span><span class="sxs-lookup"><span data-stu-id="3cc47-105">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="3cc47-106">Dans une expression de requête, la clause `join` est limitée à et optimisée pour les équijointures, qui sont de loin le type le plus courant d’opération de jointure.</span><span class="sxs-lookup"><span data-stu-id="3cc47-106">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="3cc47-107">Quand vous effectuez une équijointure, l’utilisation de la clause `join` offre généralement les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="3cc47-107">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="3cc47-108">Toutefois, la clause `join` ne peut pas être utilisée dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="3cc47-108">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="3cc47-109">Quand la jointure est basée sur une expression de prédicat d’inégalité (une non-équijointure).</span><span class="sxs-lookup"><span data-stu-id="3cc47-109">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="3cc47-110">Quand la jointure est basée sur plusieurs expressions de prédicat d’égalité ou d’inégalité.</span><span class="sxs-lookup"><span data-stu-id="3cc47-110">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="3cc47-111">Quand vous devez introduire une variable de portée temporaire pour la séquence de droite (interne) avant l’opération de jointure.</span><span class="sxs-lookup"><span data-stu-id="3cc47-111">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="3cc47-112">Pour effectuer des jointures qui ne sont pas des équijointures, vous pouvez utiliser plusieurs clauses `from` pour introduire chaque source de données indépendamment.</span><span class="sxs-lookup"><span data-stu-id="3cc47-112">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="3cc47-113">Vous appliquez ensuite une expression de prédicat dans une clause `where` à la variable de portée pour chaque source.</span><span class="sxs-lookup"><span data-stu-id="3cc47-113">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="3cc47-114">L’expression peut également prendre la forme d’un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="3cc47-114">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cc47-115">Ne confondez pas ce type d’opération de jointure personnalisée avec l’utilisation de plusieurs clauses `from` permettant d’accéder aux collections internes.</span><span class="sxs-lookup"><span data-stu-id="3cc47-115">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="3cc47-116">Pour plus d’informations, consultez [join, clause](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3cc47-116">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cc47-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="3cc47-117">Example</span></span>  
 <span data-ttu-id="3cc47-118">Dans l’exemple suivant, la première méthode présente une jointure croisée simple.</span><span class="sxs-lookup"><span data-stu-id="3cc47-118">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="3cc47-119">Les jointures croisées doivent être utilisées avec précaution, car elles peuvent produire des jeux de résultats très volumineux.</span><span class="sxs-lookup"><span data-stu-id="3cc47-119">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="3cc47-120">Toutefois, elles peuvent être utiles dans certains scénarios pour créer des séquences sources sur lesquelles exécuter des requêtes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3cc47-120">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="3cc47-121">La deuxième méthode produit une séquence de tous les produits dont l’ID de catégorie est répertorié dans la liste des catégories à gauche.</span><span class="sxs-lookup"><span data-stu-id="3cc47-121">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="3cc47-122">Notez l’utilisation de la clause `let` et de la méthode `Contains` pour créer un tableau temporaire.</span><span class="sxs-lookup"><span data-stu-id="3cc47-122">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="3cc47-123">Il est également possible de créer le tableau avant la requête et de supprimer la première clause `from`.</span><span class="sxs-lookup"><span data-stu-id="3cc47-123">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="3cc47-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="3cc47-124">Example</span></span>  
 <span data-ttu-id="3cc47-125">Dans l’exemple suivant, la requête doit joindre deux séquences sur la base des clés correspondantes qui, pour la séquence interne (à droite), ne peuvent pas être obtenues avant la clause de jointure elle-même.</span><span class="sxs-lookup"><span data-stu-id="3cc47-125">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="3cc47-126">Si cette jointure a été effectuée avec une clause `join`, la méthode `Split` doit être appelée pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="3cc47-126">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="3cc47-127">L’utilisation de plusieurs clauses `from` permet d’éviter à la requête la surcharge inhérente à la répétition de l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="3cc47-127">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="3cc47-128">Toutefois, comme la clause `join` est optimisée, dans ce cas particulier, son utilisation peut s’avérer plus rapide que d’utiliser plusieurs clauses `from`.</span><span class="sxs-lookup"><span data-stu-id="3cc47-128">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="3cc47-129">Les résultats dépendront principalement de la surcharge liée à l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3cc47-129">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3cc47-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cc47-130">See also</span></span>  
 [<span data-ttu-id="3cc47-131">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="3cc47-131">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="3cc47-132">join, clause</span><span class="sxs-lookup"><span data-stu-id="3cc47-132">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="3cc47-133">Classer les résultats d’une clause Join</span><span class="sxs-lookup"><span data-stu-id="3cc47-133">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
