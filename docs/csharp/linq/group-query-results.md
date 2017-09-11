---
title: "Regrouper les résultats d’une requête"
description: "Comment regrouper des résultats."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1c1639651699afbe5fb768db26b98a9b2d734315
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="group-query-results"></a><span data-ttu-id="2ea08-104">Regrouper les résultats d’une requête</span><span class="sxs-lookup"><span data-stu-id="2ea08-104">Group query results</span></span>

<span data-ttu-id="2ea08-105">Le regroupement est l’une des fonctionnalités les plus puissantes de LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ea08-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="2ea08-106">Les exemples suivants montrent comment regrouper des données de différentes manières :</span><span class="sxs-lookup"><span data-stu-id="2ea08-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="2ea08-107">Selon une propriété</span><span class="sxs-lookup"><span data-stu-id="2ea08-107">By a single property.</span></span>  
  
-   <span data-ttu-id="2ea08-108">Selon la première lettre d’une propriété de chaîne</span><span class="sxs-lookup"><span data-stu-id="2ea08-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="2ea08-109">Selon une plage numérique calculée</span><span class="sxs-lookup"><span data-stu-id="2ea08-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="2ea08-110">Selon un prédicat booléen ou une autre expression</span><span class="sxs-lookup"><span data-stu-id="2ea08-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="2ea08-111">Selon une clé composée</span><span class="sxs-lookup"><span data-stu-id="2ea08-111">By a compound key.</span></span>  
  
 <span data-ttu-id="2ea08-112">En outre, les deux dernières requêtes projettent leurs résultats dans un nouveau type anonyme qui contient uniquement le prénom et le nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="2ea08-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="2ea08-113">Pour plus d’informations, consultez [group, clause](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2ea08-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea08-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea08-114">Example</span></span>  
 <span data-ttu-id="2ea08-115">Tous les exemples de cette rubrique utilisent les classes d’assistance et les sources de données suivantes.</span><span class="sxs-lookup"><span data-stu-id="2ea08-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 <span data-ttu-id="2ea08-116">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ea08-116">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea08-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea08-117">Example</span></span>  
 <span data-ttu-id="2ea08-118">L’exemple suivant montre comment regrouper des éléments source en utilisant une propriété de l’élément comme clé de groupe.</span><span class="sxs-lookup"><span data-stu-id="2ea08-118">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="2ea08-119">Dans ce cas, la clé est un `string`, qui correspond au nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="2ea08-119">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="2ea08-120">Il est également possible d’utiliser une sous-chaîne comme clé.</span><span class="sxs-lookup"><span data-stu-id="2ea08-120">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="2ea08-121">L’opération de regroupement utilise le comparateur d’égalité par défaut pour le type.</span><span class="sxs-lookup"><span data-stu-id="2ea08-121">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="2ea08-122">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-122">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="2ea08-123">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-123">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 <span data-ttu-id="2ea08-124">[!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ea08-124">[!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea08-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea08-125">Example</span></span>  
 <span data-ttu-id="2ea08-126">L’exemple suivant montre comment regrouper des éléments source en utilisant autre chose qu’une propriété de l’objet comme clé de groupe.</span><span class="sxs-lookup"><span data-stu-id="2ea08-126">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="2ea08-127">Dans cet exemple, la clé est la première lettre du nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="2ea08-127">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="2ea08-128">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-128">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="2ea08-129">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-129">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 <span data-ttu-id="2ea08-130">[!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ea08-130">[!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea08-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea08-131">Example</span></span>  
 <span data-ttu-id="2ea08-132">L’exemple suivant montre comment regrouper des éléments source en utilisant une plage numérique comme clé de groupe.</span><span class="sxs-lookup"><span data-stu-id="2ea08-132">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="2ea08-133">La requête projette ensuite les résultats dans un type anonyme qui contient uniquement le prénom et le nom de l’étudiant, ainsi que la plage de centiles à laquelle appartient l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="2ea08-133">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="2ea08-134">Un type anonyme est utilisé, car il n’est pas nécessaire d’utiliser l’intégralité de l’objet `Student` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="2ea08-134">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="2ea08-135">`GetPercentile` est une fonction d’assistance qui calcule un centile à partir de la note moyenne obtenue par l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="2ea08-135">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="2ea08-136">La méthode retourne un entier compris entre 0 et 10.</span><span class="sxs-lookup"><span data-stu-id="2ea08-136">The method returns an integer between 0 and 10.</span></span>  
  
 <span data-ttu-id="2ea08-137">[!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ea08-137">[!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]</span></span>  
  
 <span data-ttu-id="2ea08-138">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-138">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="2ea08-139">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-139">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 <span data-ttu-id="2ea08-140">[!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ea08-140">[!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea08-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea08-141">Example</span></span>  
 <span data-ttu-id="2ea08-142">L’exemple suivant montre comment regrouper des éléments source en utilisant une expression de comparaison booléenne.</span><span class="sxs-lookup"><span data-stu-id="2ea08-142">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="2ea08-143">Dans cet exemple, l’expression booléenne teste si la note moyenne d’un étudiant est supérieure à 75.</span><span class="sxs-lookup"><span data-stu-id="2ea08-143">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="2ea08-144">Comme dans les exemples précédents, les résultats sont projetés dans un type anonyme, car il n’est pas nécessaire d’avoir l’élément source complet.</span><span class="sxs-lookup"><span data-stu-id="2ea08-144">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="2ea08-145">Notez que les propriétés du type anonyme deviennent des propriétés du membre `Key` et sont accessibles par nom lorsque la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="2ea08-145">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="2ea08-146">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-146">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="2ea08-147">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-147">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 <span data-ttu-id="2ea08-148">[!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ea08-148">[!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea08-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea08-149">Example</span></span>  
 <span data-ttu-id="2ea08-150">L’exemple suivant montre comment utiliser un type anonyme pour encapsuler une clé qui contient plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="2ea08-150">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="2ea08-151">Dans cet exemple, la première valeur de clé est la première lettre du nom de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="2ea08-151">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="2ea08-152">La deuxième valeur de clé est une valeur booléenne qui spécifie si l’étudiant a obtenu une note supérieure à 85 au premier examen.</span><span class="sxs-lookup"><span data-stu-id="2ea08-152">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="2ea08-153">Vous pouvez organiser les groupes selon n’importe quelle propriété de la clé.</span><span class="sxs-lookup"><span data-stu-id="2ea08-153">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="2ea08-154">Copiez-collez la méthode suivante dans la classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-154">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="2ea08-155">Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="2ea08-155">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 <span data-ttu-id="2ea08-156">[!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ea08-156">[!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea08-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ea08-157">See also</span></span>  
 <span data-ttu-id="2ea08-158"><xref:System.Linq.Enumerable.GroupBy%2A></span><span class="sxs-lookup"><span data-stu-id="2ea08-158"><xref:System.Linq.Enumerable.GroupBy%2A></span></span>   
 <span data-ttu-id="2ea08-159"><xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="2ea08-159"><xref:System.Linq.IGrouping%602></span></span>   
 <span data-ttu-id="2ea08-160">[Expressions de requête LINQ](index.md) </span><span class="sxs-lookup"><span data-stu-id="2ea08-160">[LINQ Query Expressions](index.md) </span></span>  
 <span data-ttu-id="2ea08-161">[group, clause](../language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="2ea08-161">[group clause](../language-reference/keywords/group-clause.md) </span></span>  
 <span data-ttu-id="2ea08-162">[Types anonymes](../programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="2ea08-162">[Anonymous Types](../programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="2ea08-163">[Effectuer une sous-requête sur une opération de regroupement](perform-a-subquery-on-a-grouping-operation.md) </span><span class="sxs-lookup"><span data-stu-id="2ea08-163">[Perform a Subquery on a Grouping Operation](perform-a-subquery-on-a-grouping-operation.md) </span></span>  
 <span data-ttu-id="2ea08-164">[Créer un groupe imbriqué](create-a-nested-group.md) </span><span class="sxs-lookup"><span data-stu-id="2ea08-164">[Create a Nested Group](create-a-nested-group.md) </span></span>  
 [<span data-ttu-id="2ea08-165">Regroupement de données</span><span class="sxs-lookup"><span data-stu-id="2ea08-165">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)

