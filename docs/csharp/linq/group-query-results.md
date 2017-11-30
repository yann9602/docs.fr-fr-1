---
title: "Regrouper les résultats d’une requête"
description: "Comment regrouper des résultats."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: ca68cf96a2c27bbd1999d5445c14fc93e8e2566c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="group-query-results"></a><span data-ttu-id="d64f9-104">Regrouper les résultats d’une requête</span><span class="sxs-lookup"><span data-stu-id="d64f9-104">Group query results</span></span>

<span data-ttu-id="d64f9-105">Le regroupement est l’une des fonctionnalités les plus puissantes de LINQ.</span><span class="sxs-lookup"><span data-stu-id="d64f9-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="d64f9-106">Les exemples suivants montrent comment regrouper des données de différentes manières :</span><span class="sxs-lookup"><span data-stu-id="d64f9-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="d64f9-107">Selon une propriété</span><span class="sxs-lookup"><span data-stu-id="d64f9-107">By a single property.</span></span>  
  
-   <span data-ttu-id="d64f9-108">Selon la première lettre d’une propriété de chaîne</span><span class="sxs-lookup"><span data-stu-id="d64f9-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="d64f9-109">Selon une plage numérique calculée</span><span class="sxs-lookup"><span data-stu-id="d64f9-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="d64f9-110">Selon un prédicat booléen ou une autre expression</span><span class="sxs-lookup"><span data-stu-id="d64f9-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="d64f9-111">Selon une clé composée</span><span class="sxs-lookup"><span data-stu-id="d64f9-111">By a compound key.</span></span>  
  
 <span data-ttu-id="d64f9-112">En outre, les deux dernières requêtes projettent leurs résultats dans un nouveau type anonyme qui contient uniquement le prénom et le nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="d64f9-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="d64f9-113">Pour plus d’informations, consultez [group, clause](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d64f9-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d64f9-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="d64f9-114">Example</span></span>  
 <span data-ttu-id="d64f9-115">Tous les exemples de cette rubrique utilisent les classes d’assistance et les sources de données suivantes.</span><span class="sxs-lookup"><span data-stu-id="d64f9-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d64f9-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d64f9-116">Example</span></span>  
 <span data-ttu-id="d64f9-117">L’exemple suivant montre comment regrouper des éléments source en utilisant une propriété de l’élément comme clé de groupe.</span><span class="sxs-lookup"><span data-stu-id="d64f9-117">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="d64f9-118">Dans ce cas, la clé est un `string`, qui correspond au nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="d64f9-118">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="d64f9-119">Il est également possible d’utiliser une sous-chaîne comme clé.</span><span class="sxs-lookup"><span data-stu-id="d64f9-119">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="d64f9-120">L’opération de regroupement utilise le comparateur d’égalité par défaut pour le type.</span><span class="sxs-lookup"><span data-stu-id="d64f9-120">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="d64f9-121">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-121">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d64f9-122">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-122">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="d64f9-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="d64f9-123">Example</span></span>  
 <span data-ttu-id="d64f9-124">L’exemple suivant montre comment regrouper des éléments source en utilisant autre chose qu’une propriété de l’objet comme clé de groupe.</span><span class="sxs-lookup"><span data-stu-id="d64f9-124">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="d64f9-125">Dans cet exemple, la clé est la première lettre du nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="d64f9-125">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="d64f9-126">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-126">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d64f9-127">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-127">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="d64f9-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="d64f9-128">Example</span></span>  
 <span data-ttu-id="d64f9-129">L’exemple suivant montre comment regrouper des éléments source en utilisant une plage numérique comme clé de groupe.</span><span class="sxs-lookup"><span data-stu-id="d64f9-129">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="d64f9-130">La requête projette ensuite les résultats dans un type anonyme qui contient uniquement le prénom et le nom de l’étudiant, ainsi que la plage de centiles à laquelle appartient l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="d64f9-130">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="d64f9-131">Un type anonyme est utilisé, car il n’est pas nécessaire d’utiliser l’intégralité de l’objet `Student` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="d64f9-131">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="d64f9-132">`GetPercentile` est une fonction d’assistance qui calcule un centile à partir de la note moyenne obtenue par l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="d64f9-132">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="d64f9-133">La méthode retourne un entier compris entre 0 et 10.</span><span class="sxs-lookup"><span data-stu-id="d64f9-133">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="d64f9-134">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-134">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d64f9-135">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-135">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="d64f9-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="d64f9-136">Example</span></span>  
 <span data-ttu-id="d64f9-137">L’exemple suivant montre comment regrouper des éléments source en utilisant une expression de comparaison booléenne.</span><span class="sxs-lookup"><span data-stu-id="d64f9-137">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="d64f9-138">Dans cet exemple, l’expression booléenne teste si la note moyenne d’un étudiant est supérieure à 75.</span><span class="sxs-lookup"><span data-stu-id="d64f9-138">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="d64f9-139">Comme dans les exemples précédents, les résultats sont projetés dans un type anonyme, car il n’est pas nécessaire d’avoir l’élément source complet.</span><span class="sxs-lookup"><span data-stu-id="d64f9-139">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="d64f9-140">Notez que les propriétés du type anonyme deviennent des propriétés du membre `Key` et sont accessibles par nom lorsque la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d64f9-140">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="d64f9-141">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-141">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d64f9-142">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-142">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="d64f9-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="d64f9-143">Example</span></span>  
 <span data-ttu-id="d64f9-144">L’exemple suivant montre comment utiliser un type anonyme pour encapsuler une clé qui contient plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="d64f9-144">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="d64f9-145">Dans cet exemple, la première valeur de clé est la première lettre du nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="d64f9-145">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="d64f9-146">La deuxième valeur de clé est une valeur booléenne qui spécifie si l’étudiant a obtenu une note supérieure à 85 au premier examen.</span><span class="sxs-lookup"><span data-stu-id="d64f9-146">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="d64f9-147">Vous pouvez organiser les groupes selon n’importe quelle propriété de la clé.</span><span class="sxs-lookup"><span data-stu-id="d64f9-147">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="d64f9-148">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-148">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d64f9-149">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-149">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d64f9-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d64f9-150">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="d64f9-151">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="d64f9-151">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="d64f9-152">group, clause</span><span class="sxs-lookup"><span data-stu-id="d64f9-152">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="d64f9-153">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="d64f9-153">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="d64f9-154">Effectuer une sous-requête sur une opération de regroupement</span><span class="sxs-lookup"><span data-stu-id="d64f9-154">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="d64f9-155">Créer un groupe imbriqué</span><span class="sxs-lookup"><span data-stu-id="d64f9-155">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="d64f9-156">Regroupement de données</span><span class="sxs-lookup"><span data-stu-id="d64f9-156">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
