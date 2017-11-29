---
title: "Comment : combiner des données avec LINQ à l'aide de jointures (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 432be646ce4353fd4627a34f363e7562f6181e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="30234-102">Comment : combiner des données avec LINQ à l'aide de jointures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30234-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="30234-103">Visual Basic fournit le `Join` et `Group Join` pour vous permettre de combiner le contenu de plusieurs collections basées sur des valeurs communes entre les collections de clauses de requête.</span><span class="sxs-lookup"><span data-stu-id="30234-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="30234-104">Ces valeurs sont appelées *clé* valeurs.</span><span class="sxs-lookup"><span data-stu-id="30234-104">These values are known as *key* values.</span></span> <span data-ttu-id="30234-105">Les développeurs familiarisés avec les concepts de base de données relationnelle reconnaîtront la `Join` clause INNER JOIN et `Group Join` clause en tant que, en effet, une jointure externe gauche.</span><span class="sxs-lookup"><span data-stu-id="30234-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="30234-106">Les exemples de cette rubrique montrent quelques façons de combiner des données à l’aide de la `Join` et `Group Join` clauses de requête.</span><span class="sxs-lookup"><span data-stu-id="30234-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="30234-107">Créez un projet et ajouter des exemples de données</span><span class="sxs-lookup"><span data-stu-id="30234-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="30234-108">Pour créer un projet qui contient des types et des exemples de données</span><span class="sxs-lookup"><span data-stu-id="30234-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="30234-109">Pour exécuter les exemples dans cette rubrique, ouvrez Visual Studio et ajoutez un nouveau projet d’Application Console Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="30234-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="30234-110">Double-cliquez sur le fichier Module1.vb créé par Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="30234-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="30234-111">Les exemples de cette rubrique utilisent le `Person` et `Pet` types et les données de l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="30234-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="30234-112">Copiez ce code dans la valeur par défaut `Module1` module créé par Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="30234-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="30234-113">Effectuer une jointure interne à l’aide de la Clause de jointure</span><span class="sxs-lookup"><span data-stu-id="30234-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="30234-114">Une jointure interne combine les données des deux collections.</span><span class="sxs-lookup"><span data-stu-id="30234-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="30234-115">Éléments pour lesquels les valeurs de clé spécifiés correspond à sont inclus.</span><span class="sxs-lookup"><span data-stu-id="30234-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="30234-116">Tous les éléments à partir de des collections qui n’ont pas d’élément correspondant dans l’autre collection sont exclus.</span><span class="sxs-lookup"><span data-stu-id="30234-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="30234-117">En Visual Basic, LINQ fournit deux options pour effectuer une jointure interne : une jointure implicite et une jointure explicite.</span><span class="sxs-lookup"><span data-stu-id="30234-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="30234-118">Une jointure implicite spécifie les collections à joindre dans une `From` clause et identifie les champs clés correspondants dans un `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="30234-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="30234-119">Visual Basic joint implicitement les deux collections basées sur les champs de clé spécifiés.</span><span class="sxs-lookup"><span data-stu-id="30234-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="30234-120">Vous pouvez spécifier une jointure explicite en utilisant la `Join` clause lorsque vous souhaitez être spécifique sur les champs clés dans la jointure.</span><span class="sxs-lookup"><span data-stu-id="30234-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="30234-121">Dans ce cas, un `Where` clause peut toujours être utilisée pour filtrer les résultats de requête.</span><span class="sxs-lookup"><span data-stu-id="30234-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="30234-122">Pour effectuer une jointure interne à l’aide de la clause de jointure</span><span class="sxs-lookup"><span data-stu-id="30234-122">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="30234-123">Ajoutez le code suivant à la `Module1` module dans votre projet pour voir des exemples de jointure interne implicite et explicite.</span><span class="sxs-lookup"><span data-stu-id="30234-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="30234-124">Effectuer une jointure externe gauche à l’aide de la Clause de jointure de groupe</span><span class="sxs-lookup"><span data-stu-id="30234-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="30234-125">Une jointure externe gauche comprend tous les éléments de la collection située du côté gauche de la jointure et uniquement les valeurs de la collection située du côté droit de la jointure correspondantes.</span><span class="sxs-lookup"><span data-stu-id="30234-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="30234-126">Tous les éléments de la collection située du côté droit de la jointure qui n’ont pas d’élément correspondant dans la collection de gauche sont exclus du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="30234-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="30234-127">Le `Group Join` clause effectue, en effet, une jointure externe gauche.</span><span class="sxs-lookup"><span data-stu-id="30234-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="30234-128">La différence entre ce qui est généralement appelé une jointure externe gauche et ce que le `Group Join` clause retourne une valeur qui est la `Group Join` résultats de groupes de clause de la collection située du côté droit de la jointure pour chaque élément dans la collection de gauche.</span><span class="sxs-lookup"><span data-stu-id="30234-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="30234-129">Dans une base de données relationnelle, une jointure externe gauche retourne un résultat non groupé dans laquelle chaque élément dans la requête résultat contient des éléments correspondants des deux collections dans la jointure.</span><span class="sxs-lookup"><span data-stu-id="30234-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="30234-130">Dans ce cas, les éléments de la collection située du côté gauche de la jointure sont répétées pour chaque élément correspondant de la collection de droite.</span><span class="sxs-lookup"><span data-stu-id="30234-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="30234-131">Vous verrez à quoi cela ressemble lorsque vous effectuez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="30234-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="30234-132">Vous pouvez récupérer les résultats d’une `Group Join` requête sous la forme d’un résultat dégroupé en étendant votre requête afin de retourner un élément pour chaque résultat de requête groupé.</span><span class="sxs-lookup"><span data-stu-id="30234-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="30234-133">Pour ce faire, vous devez vous assurer que vous interrogez le `DefaultIfEmpty` méthode de la collection groupée.</span><span class="sxs-lookup"><span data-stu-id="30234-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="30234-134">Cela garantit que les éléments de la collection située du côté gauche de la jointure sont toujours inclus dans le résultat de la requête même s’ils n’ont aucun résultat correspondant à partir de la collection située à droite.</span><span class="sxs-lookup"><span data-stu-id="30234-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="30234-135">Vous pouvez ajouter du code à votre requête pour fournir une valeur de résultat par défaut lorsqu’il n’existe aucune valeur correspondante dans la collection située à droite de la jointure.</span><span class="sxs-lookup"><span data-stu-id="30234-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="30234-136">Pour effectuer une jointure externe gauche à l’aide de la clause Group Join</span><span class="sxs-lookup"><span data-stu-id="30234-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="30234-137">Ajoutez le code suivant à la `Module1` module dans votre projet pour voir des exemples d’une jointure externe gauche groupée et une jointure externe gauche non groupée.</span><span class="sxs-lookup"><span data-stu-id="30234-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="30234-138">Effectuer une jointure à l’aide d’une clé Composite</span><span class="sxs-lookup"><span data-stu-id="30234-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="30234-139">Vous pouvez utiliser la `And` mot clé dans un `Join` ou `Group Join` clause pour identifier les différents champs clés à utiliser lors de la mise en correspondance les valeurs des collections jointes.</span><span class="sxs-lookup"><span data-stu-id="30234-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="30234-140">Le `And` mot clé spécifie que tous les spécifiés les champs clés doivent correspondre pour les éléments à joindre.</span><span class="sxs-lookup"><span data-stu-id="30234-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="30234-141">Pour effectuer une jointure à l’aide d’une clé composite</span><span class="sxs-lookup"><span data-stu-id="30234-141">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="30234-142">Ajoutez le code suivant à la `Module1` module dans votre projet pour voir des exemples d’une jointure qui utilise une clé composite.</span><span class="sxs-lookup"><span data-stu-id="30234-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a><span data-ttu-id="30234-143">Exécutez le Code</span><span class="sxs-lookup"><span data-stu-id="30234-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="30234-144">Pour ajouter du code pour exécuter les exemples</span><span class="sxs-lookup"><span data-stu-id="30234-144">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="30234-145">Remplacez le `Sub Main` dans le `Module1` module dans votre projet avec le code suivant pour exécuter les exemples dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="30234-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  <span data-ttu-id="30234-146">Appuyez sur F5 pour exécuter les exemples.</span><span class="sxs-lookup"><span data-stu-id="30234-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30234-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30234-147">See Also</span></span>  
 [<span data-ttu-id="30234-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="30234-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="30234-149">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30234-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="30234-150">Join (clause)</span><span class="sxs-lookup"><span data-stu-id="30234-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="30234-151">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="30234-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="30234-152">From (clause)</span><span class="sxs-lookup"><span data-stu-id="30234-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="30234-153">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="30234-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="30234-154">Requêtes</span><span class="sxs-lookup"><span data-stu-id="30234-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="30234-155">Transformations de données avec LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="30234-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
