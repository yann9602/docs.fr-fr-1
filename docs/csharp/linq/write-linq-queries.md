---
title: "Écrire des requêtes LINQ en C#"
description: "Comment écrire des requêtes."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7051e33a185b0ab898c4b9d7368f8f0e6883c119
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="write-linq-queries-in-c"></a><span data-ttu-id="65fd9-104">Écrire des requêtes LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="65fd9-104">Write LINQ queries in C#</span></span>

<span data-ttu-id="65fd9-105">Cette rubrique présente les trois façons d’écrire une requête LINQ en C# :</span><span class="sxs-lookup"><span data-stu-id="65fd9-105">This topic shows the three ways in which you can write a LINQ query in C#:</span></span>  
  
1.  <span data-ttu-id="65fd9-106">Utilisez la syntaxe de requête.</span><span class="sxs-lookup"><span data-stu-id="65fd9-106">Use query syntax.</span></span>  
  
2.  <span data-ttu-id="65fd9-107">Utilisez la syntaxe de méthode.</span><span class="sxs-lookup"><span data-stu-id="65fd9-107">Use method syntax.</span></span>  
  
3.  <span data-ttu-id="65fd9-108">Utilisez une combinaison de syntaxe de requête et de syntaxe de méthode.</span><span class="sxs-lookup"><span data-stu-id="65fd9-108">Use a combination of query syntax and method syntax.</span></span>  
  
 <span data-ttu-id="65fd9-109">Les exemples suivants montrent des requêtes LINQ simples en utilisant chaque approche répertoriée précédemment.</span><span class="sxs-lookup"><span data-stu-id="65fd9-109">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="65fd9-110">En général, la règle consiste à utiliser (1) dès que possible et à utiliser (2) et (3) dès que cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="65fd9-110">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65fd9-111">Ces requêtes fonctionnent sur les collections simples en mémoire ; toutefois, la syntaxe de base est identique à celle utilisée dans LINQ to Entities et LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="65fd9-111">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65fd9-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="65fd9-112">Example</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="65fd9-113">Syntaxe de requête</span><span class="sxs-lookup"><span data-stu-id="65fd9-113">Query syntax</span></span>  
 <span data-ttu-id="65fd9-114">La méthode recommandée pour écrire la plupart des requêtes consiste à utiliser la *syntaxe de requête* pour créer des *expressions de requête*.</span><span class="sxs-lookup"><span data-stu-id="65fd9-114">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="65fd9-115">L’exemple suivant présente trois expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="65fd9-115">The following example shows three query expressions.</span></span> <span data-ttu-id="65fd9-116">La première expression de requête montre comment filtrer ou restreindre des résultats en appliquant des conditions avec une clause `where`.</span><span class="sxs-lookup"><span data-stu-id="65fd9-116">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="65fd9-117">Tous les éléments de la séquence source dont la valeur est supérieure à 7 ou inférieure à 3 sont retournés.</span><span class="sxs-lookup"><span data-stu-id="65fd9-117">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="65fd9-118">La deuxième expression montre comment classer les résultats retournés.</span><span class="sxs-lookup"><span data-stu-id="65fd9-118">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="65fd9-119">La troisième expression montre comment regrouper des résultats en fonction d’une clé.</span><span class="sxs-lookup"><span data-stu-id="65fd9-119">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="65fd9-120">Cette requête retourne deux groupes en fonction de la première lettre du mot.</span><span class="sxs-lookup"><span data-stu-id="65fd9-120">This query returns two groups based on the first letter of the word.</span></span>  
  
 <span data-ttu-id="65fd9-121">[!code-cs[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="65fd9-121">[!code-cs[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]</span></span>  
  
 <span data-ttu-id="65fd9-122">Notez que le type des requêtes est <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="65fd9-122">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="65fd9-123">Toutes ces requêtes pourraient être écrites à l’aide de `var`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="65fd9-123">All of these queries could be written using `var` as shown in the following example:</span></span>  
  
 `var query = from num in numbers...`  
  
 <span data-ttu-id="65fd9-124">Dans chacun des exemples précédents, les requêtes ne s’exécutent pas réellement tant vous n’avez pas itéré la variable de requête dans une instruction `foreach` ou une autre instruction.</span><span class="sxs-lookup"><span data-stu-id="65fd9-124">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="65fd9-125">Pour plus d’informations, consultez [Introduction aux requêtes LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="65fd9-125">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65fd9-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="65fd9-126">Example</span></span>  
  
## <a name="method-syntax"></a><span data-ttu-id="65fd9-127">Syntaxe de méthode</span><span class="sxs-lookup"><span data-stu-id="65fd9-127">Method syntax</span></span>  
 <span data-ttu-id="65fd9-128">Certaines opérations de requête doivent être exprimées comme un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="65fd9-128">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="65fd9-129">Les plus répandues de ces méthodes retournent des valeurs numériques uniques, telles que <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="65fd9-129">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="65fd9-130">Ces méthodes doivent toujours être appelées en dernier dans toutes les requêtes, car elles ne représentent qu’une valeur unique et ne peuvent pas servir de source pour une opération de requête supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="65fd9-130">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="65fd9-131">L’exemple suivant présente un appel de méthode dans une expression de requête :</span><span class="sxs-lookup"><span data-stu-id="65fd9-131">The following example shows a method call in a query expression:</span></span>  
  
 <span data-ttu-id="65fd9-132">[!code-cs[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="65fd9-132">[!code-cs[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="65fd9-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="65fd9-133">Example</span></span>  
 <span data-ttu-id="65fd9-134">Si la méthode a des paramètres Action ou Func, ceux-ci sont fournis sous la forme d’une expression [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="65fd9-134">If the method has  Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>  
  
 <span data-ttu-id="65fd9-135">[!code-cs[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="65fd9-135">[!code-cs[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]</span></span>  
  
 <span data-ttu-id="65fd9-136">Dans les requêtes précédentes, seule la requête 4 s’exécute immédiatement.</span><span class="sxs-lookup"><span data-stu-id="65fd9-136">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="65fd9-137">Cela s’explique par le fait qu’elle retourne une valeur unique et non une collection <xref:System.Collections.Generic.IEnumerable%601> générique.</span><span class="sxs-lookup"><span data-stu-id="65fd9-137">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="65fd9-138">La méthode elle-même doit utiliser `foreach` pour calculer sa valeur.</span><span class="sxs-lookup"><span data-stu-id="65fd9-138">The method itself has to use `foreach` in order to compute its value.</span></span>  
  
 <span data-ttu-id="65fd9-139">Chacune des requêtes précédentes peut être écrite en utilisant des types implicites avec [var](../language-reference/keywords/var.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="65fd9-139">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>  
  
 <span data-ttu-id="65fd9-140">[!code-cs[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="65fd9-140">[!code-cs[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="65fd9-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="65fd9-141">Example</span></span>  
  
## <a name="mixed-query-and-method-syntax"></a><span data-ttu-id="65fd9-142">Syntaxe de méthode et de requête mixte</span><span class="sxs-lookup"><span data-stu-id="65fd9-142">Mixed query and method syntax</span></span>  
 <span data-ttu-id="65fd9-143">Cet exemple montre comment utiliser la syntaxe de méthode sur les résultats d’une clause de requête.</span><span class="sxs-lookup"><span data-stu-id="65fd9-143">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="65fd9-144">Encadrez simplement l’expression de requête entre parenthèses, puis appliquez l’opérateur point et appelez la méthode.</span><span class="sxs-lookup"><span data-stu-id="65fd9-144">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="65fd9-145">Dans l’exemple suivant, la requête 7 retourne les nombres dont la valeur est comprise entre 3 et 7.</span><span class="sxs-lookup"><span data-stu-id="65fd9-145">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="65fd9-146">Toutefois, il est généralement préférable d’utiliser une deuxième variable pour stocker le résultat de l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="65fd9-146">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="65fd9-147">De cette manière, il est moins probable que la requête ne soit confondue avec les résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="65fd9-147">In this manner, the query is less likely to be confused with the results of the query.</span></span>  
  
 <span data-ttu-id="65fd9-148">[!code-cs[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="65fd9-148">[!code-cs[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]</span></span>  
  
 <span data-ttu-id="65fd9-149">Comme la requête 7 retourne une valeur unique et non une collection, la requête s’exécute immédiatement.</span><span class="sxs-lookup"><span data-stu-id="65fd9-149">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>  
  
 <span data-ttu-id="65fd9-150">La requête précédente peut être écrite en utilisant des types implicites avec `var`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="65fd9-150">The previous query can be written by using implicit typing with `var`, as follows:</span></span>  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 <span data-ttu-id="65fd9-151">Elle peut être écrite dans la syntaxe de méthode comme suit :</span><span class="sxs-lookup"><span data-stu-id="65fd9-151">It can be written in method syntax as follows:</span></span>  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 <span data-ttu-id="65fd9-152">Elle peut être écrite en utilisant des types explicites, comme suit :</span><span class="sxs-lookup"><span data-stu-id="65fd9-152">It can be written by using explicit typing, as follows:</span></span>  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a><span data-ttu-id="65fd9-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65fd9-153">See Also</span></span>  
  <span data-ttu-id="65fd9-154">[Procédure pas à pas : écriture de requêtes en C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="65fd9-154">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 <span data-ttu-id="65fd9-155">[Expressions de requête LINQ](index.md) </span><span class="sxs-lookup"><span data-stu-id="65fd9-155">[LINQ Query Expressions](index.md) </span></span>  
 [<span data-ttu-id="65fd9-156">where, clause</span><span class="sxs-lookup"><span data-stu-id="65fd9-156">where clause</span></span>](../language-reference/keywords/where-clause.md)

