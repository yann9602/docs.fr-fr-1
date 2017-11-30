---
title: From, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ecdc8b70fb1ae164a6c78998ce11db9938fbb56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="f3c05-102">From, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3c05-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="f3c05-103">Spécifie une ou plusieurs variables de plage et une collection à interroger.</span><span class="sxs-lookup"><span data-stu-id="f3c05-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3c05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3c05-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="f3c05-105">Composants</span><span class="sxs-lookup"><span data-stu-id="f3c05-105">Parts</span></span>  
  
|<span data-ttu-id="f3c05-106">Terme</span><span class="sxs-lookup"><span data-stu-id="f3c05-106">Term</span></span>|<span data-ttu-id="f3c05-107">Définition</span><span class="sxs-lookup"><span data-stu-id="f3c05-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="f3c05-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f3c05-108">Required.</span></span> <span data-ttu-id="f3c05-109">A *variable de portée* utilisé pour itérer sur les éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="f3c05-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="f3c05-110">Une variable de portée est utilisée pour faire référence à chaque membre de la `collection` que la requête itère le `collection`.</span><span class="sxs-lookup"><span data-stu-id="f3c05-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="f3c05-111">Doit être un type énumérable.</span><span class="sxs-lookup"><span data-stu-id="f3c05-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="f3c05-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f3c05-112">Optional.</span></span> <span data-ttu-id="f3c05-113">Type d'élément `element`.</span><span class="sxs-lookup"><span data-stu-id="f3c05-113">The type of `element`.</span></span> <span data-ttu-id="f3c05-114">Si aucun `type` est spécifié, le type de `element` est déduit à partir de `collection`.</span><span class="sxs-lookup"><span data-stu-id="f3c05-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="f3c05-115">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f3c05-115">Required.</span></span> <span data-ttu-id="f3c05-116">Fait référence à la collection à interroger.</span><span class="sxs-lookup"><span data-stu-id="f3c05-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="f3c05-117">Doit être un type énumérable.</span><span class="sxs-lookup"><span data-stu-id="f3c05-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3c05-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="f3c05-118">Remarks</span></span>  
 <span data-ttu-id="f3c05-119">Le `From` clause est utilisée pour identifier les données sources pour une requête et les variables qui sont utilisées pour faire référence à un élément dans la collection source.</span><span class="sxs-lookup"><span data-stu-id="f3c05-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="f3c05-120">Ces variables sont appelées *les variables de plage*.</span><span class="sxs-lookup"><span data-stu-id="f3c05-120">These variables are called *range variables*.</span></span> <span data-ttu-id="f3c05-121">Le `From` clause est requise pour une requête, sauf quand le `Aggregate` clause est utilisée pour identifier une requête qui retourne des résultats uniquement regroupés.</span><span class="sxs-lookup"><span data-stu-id="f3c05-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="f3c05-122">Pour plus d’informations, consultez [Aggregate, Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f3c05-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="f3c05-123">Vous pouvez spécifier plusieurs `From` clauses dans une requête pour identifier plusieurs collections à joindre.</span><span class="sxs-lookup"><span data-stu-id="f3c05-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="f3c05-124">Lorsque plusieurs collections sont spécifiées, elles sont itérées indépendamment, ou vous pouvez les joindre si elles sont associées.</span><span class="sxs-lookup"><span data-stu-id="f3c05-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="f3c05-125">Vous pouvez joindre implicitement des collections à l’aide de la `Select` clause, ou explicitement en utilisant la `Join` ou `Group Join` clauses.</span><span class="sxs-lookup"><span data-stu-id="f3c05-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="f3c05-126">En guise d’alternative, vous pouvez spécifier des variables de portée et des collections multiples dans une seule `From` clause, avec chaque variable de portée et les collections séparées des autres par une virgule.</span><span class="sxs-lookup"><span data-stu-id="f3c05-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="f3c05-127">L’exemple de code suivant montre les deux options de syntaxe pour le `From` clause.</span><span class="sxs-lookup"><span data-stu-id="f3c05-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 <span data-ttu-id="f3c05-128">Le `From` clause définit l’étendue d’une requête, qui est semblable à la portée d’un `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="f3c05-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="f3c05-129">Par conséquent, chaque `element` variable de portée dans la portée d’une requête doit avoir un nom unique.</span><span class="sxs-lookup"><span data-stu-id="f3c05-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="f3c05-130">Étant donné que vous pouvez spécifier plusieurs `From` clauses d’une requête, ultérieure `From` clauses peuvent faire référence à des variables de portée dans le `From` clause, ou ils peuvent faire référence à des variables de plage dans une précédente `From` clause.</span><span class="sxs-lookup"><span data-stu-id="f3c05-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="f3c05-131">Par exemple, l’exemple suivant montre une manière imbriquée `From` clause où la collection dans la deuxième clause est basée sur une propriété de la variable de portée dans la première clause.</span><span class="sxs-lookup"><span data-stu-id="f3c05-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 <span data-ttu-id="f3c05-132">Chaque `From` clause peut être suivie de n’importe quelle combinaison de clauses de requête supplémentaires pour affiner la requête.</span><span class="sxs-lookup"><span data-stu-id="f3c05-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="f3c05-133">Vous pouvez affiner la requête comme suit :</span><span class="sxs-lookup"><span data-stu-id="f3c05-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="f3c05-134">Combinez plusieurs collections de manière implicite à l’aide de la `From` et `Select` clauses, ou explicitement en utilisant la `Join` ou `Group Join` clauses.</span><span class="sxs-lookup"><span data-stu-id="f3c05-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="f3c05-135">Utilisez le `Where` clause pour filtrer les résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="f3c05-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="f3c05-136">Trier le résultat à l’aide de la `Order By` clause.</span><span class="sxs-lookup"><span data-stu-id="f3c05-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="f3c05-137">Regrouper des résultats similaires à l’aide du `Group By` clause.</span><span class="sxs-lookup"><span data-stu-id="f3c05-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="f3c05-138">Utilisez le `Aggregate` clause pour identifier les fonctions d’agrégation à évaluer pour le résultat de toute requête.</span><span class="sxs-lookup"><span data-stu-id="f3c05-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="f3c05-139">Utilisez le `Let` clause pour introduire une variable d’itération dont la valeur est déterminée par une expression au lieu d’une collection.</span><span class="sxs-lookup"><span data-stu-id="f3c05-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="f3c05-140">Utilisez le `Distinct` clause pour ignorer les résultats de la requête en double.</span><span class="sxs-lookup"><span data-stu-id="f3c05-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="f3c05-141">Identifier les parties du résultat à retourner à l’aide de la `Skip`, `Take`, `Skip While`, et `Take While` clauses.</span><span class="sxs-lookup"><span data-stu-id="f3c05-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3c05-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3c05-142">Example</span></span>  
 <span data-ttu-id="f3c05-143">La requête suivante expression utilise une `From` clause pour déclarer une variable de portée `cust` pour chaque `Customer` de l’objet dans le `customers` collection.</span><span class="sxs-lookup"><span data-stu-id="f3c05-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="f3c05-144">Le `Where` clause utilise la variable de portée pour restreindre la sortie aux clients à partir de la région spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f3c05-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="f3c05-145">Le `For Each` boucle affiche le nom de société pour chaque client dans le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="f3c05-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f3c05-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3c05-146">See Also</span></span>  
 [<span data-ttu-id="f3c05-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="f3c05-147">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="f3c05-148">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3c05-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="f3c05-149">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="f3c05-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="f3c05-150">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="f3c05-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="f3c05-151">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="f3c05-152">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="f3c05-153">Aggregate (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="f3c05-154">Distinct (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="f3c05-155">Join (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="f3c05-156">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="f3c05-157">Order By (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="f3c05-158">Let (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="f3c05-159">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="f3c05-160">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="f3c05-161">Skip While (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="f3c05-162">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="f3c05-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
