---
title: "Opérations de requête LINQ de base (C#)"
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
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: 39
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e5dbebb7950678a0f40ec774d23b42dfe89cff49
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="5c55d-102">Opérations de requête LINQ de base (C#)</span><span class="sxs-lookup"><span data-stu-id="5c55d-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="5c55d-103">Cette rubrique présente brièvement les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] et quelques-uns des types d’opérations classiques que vous effectuez dans une requête.</span><span class="sxs-lookup"><span data-stu-id="5c55d-103">This topic gives a brief introduction to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="5c55d-104">Vous trouverez des informations plus détaillées dans les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c55d-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="5c55d-105">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="5c55d-105">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [<span data-ttu-id="5c55d-106">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="5c55d-106">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [<span data-ttu-id="5c55d-107">Procédure pas à pas : écriture de requêtes en C#</span><span class="sxs-lookup"><span data-stu-id="5c55d-107">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  <span data-ttu-id="5c55d-108">Si vous êtes déjà familiarisé avec un langage de requête tel que SQL ou XQuery, vous pouvez ignorer la plupart des informations de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="5c55d-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="5c55d-109">Consultez le paragraphe « Clause `from` » de la section suivante pour en savoir plus sur l’ordre des clauses dans les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c55d-109">Read about the "`from` clause" in the next section to learn about the order of clauses in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="5c55d-110">Obtention d’une source de données</span><span class="sxs-lookup"><span data-stu-id="5c55d-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="5c55d-111">Dans une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], la première étape consiste à spécifier la source de données.</span><span class="sxs-lookup"><span data-stu-id="5c55d-111">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source.</span></span> <span data-ttu-id="5c55d-112">Dans C#, comme dans la plupart des langages de programmation, une variable doit être déclarée avant de pouvoir être utilisée.</span><span class="sxs-lookup"><span data-stu-id="5c55d-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="5c55d-113">Dans une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], la clause `from` apparaît en premier pour introduire la source de données (`customers`) et la *variable de portée* (`cust`).</span><span class="sxs-lookup"><span data-stu-id="5c55d-113">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 <span data-ttu-id="5c55d-114">[!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c55d-114">[!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]</span></span>  
  
 <span data-ttu-id="5c55d-115">La variable de portée est similaire à la variable d’itération dans une boucle `foreach`, à la différence qu’aucune itération réelle ne se produit dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="5c55d-115">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="5c55d-116">Quand la requête est exécutée, la variable de portée sert de référence à chaque élément consécutif dans `customers`.</span><span class="sxs-lookup"><span data-stu-id="5c55d-116">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="5c55d-117">Comme le compilateur déduit le type de `cust`, vous n’avez pas à le spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="5c55d-117">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="5c55d-118">Des variables de portée supplémentaires peuvent être introduites par une clause `let`.</span><span class="sxs-lookup"><span data-stu-id="5c55d-118">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="5c55d-119">Pour plus d’informations, consultez [let, clause](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c55d-119">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c55d-120">Pour les sources de données non génériques telles que <xref:System.Collections.ArrayList>, la variable de portée doit être explicitement typée.</span><span class="sxs-lookup"><span data-stu-id="5c55d-120">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="5c55d-121">Pour plus d’informations, consultez [Guide pratique pour interroger un ArrayList avec LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) et [from, clause](../../../../csharp/language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c55d-121">For more information, see [How to: Query an ArrayList with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) and [from clause](../../../../csharp/language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="5c55d-122">Filtrage</span><span class="sxs-lookup"><span data-stu-id="5c55d-122">Filtering</span></span>  
 <span data-ttu-id="5c55d-123">L'opération de requête la plus courante est probablement l'application d'un filtre sous forme d'expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="5c55d-123">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="5c55d-124">Du fait du filtre, la requête retourne uniquement les éléments pour lesquels l’expression a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="5c55d-124">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="5c55d-125">Le résultat est produit à l'aide de la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="5c55d-125">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="5c55d-126">En effet, le filtre spécifie les éléments à exclure de la séquence source.</span><span class="sxs-lookup"><span data-stu-id="5c55d-126">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="5c55d-127">Dans l’exemple suivant, seuls les clients (`customers`) qui ont une adresse à Londres sont retournés.</span><span class="sxs-lookup"><span data-stu-id="5c55d-127">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 <span data-ttu-id="5c55d-128">[!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c55d-128">[!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]</span></span>  
  
 <span data-ttu-id="5c55d-129">Vous pouvez utiliser les opérateurs logiques C# `AND` et `OR` habituels pour appliquer le nombre d’expressions de filtre nécessaire dans la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="5c55d-129">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="5c55d-130">Par exemple, pour retourner uniquement les clients situés à « Londres » ET (`AND`) dont le nom est « Devon », vous devez écrire le code suivant :</span><span class="sxs-lookup"><span data-stu-id="5c55d-130">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 <span data-ttu-id="5c55d-131">[!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c55d-131">[!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]</span></span>  
  
 <span data-ttu-id="5c55d-132">Pour retourner les clients situés à Londres ou à Paris, vous devez écrire le code suivant :</span><span class="sxs-lookup"><span data-stu-id="5c55d-132">To return customers from London or Paris, you would write the following code:</span></span>  
  
 <span data-ttu-id="5c55d-133">[!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c55d-133">[!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]</span></span>  
  
 <span data-ttu-id="5c55d-134">Pour plus d’informations, consultez [where, clause](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c55d-134">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="5c55d-135">Classement</span><span class="sxs-lookup"><span data-stu-id="5c55d-135">Ordering</span></span>  
 <span data-ttu-id="5c55d-136">Il est souvent utile de trier les données retournées.</span><span class="sxs-lookup"><span data-stu-id="5c55d-136">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="5c55d-137">La clause `orderby` permet de trier les éléments de la séquence retournée en fonction du comparateur par défaut pour le type qui est trié.</span><span class="sxs-lookup"><span data-stu-id="5c55d-137">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="5c55d-138">Par exemple, la requête suivante peut être étendue pour trier les résultats selon la propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="5c55d-138">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="5c55d-139">Comme `Name` est une chaîne, le comparateur par défaut effectue un tri alphabétique de A à Z.</span><span class="sxs-lookup"><span data-stu-id="5c55d-139">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 <span data-ttu-id="5c55d-140">[!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c55d-140">[!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]</span></span>  
  
 <span data-ttu-id="5c55d-141">Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la clause `orderby…descending`.</span><span class="sxs-lookup"><span data-stu-id="5c55d-141">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="5c55d-142">Pour plus d’informations, consultez [orderby, clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c55d-142">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="5c55d-143">Regroupement</span><span class="sxs-lookup"><span data-stu-id="5c55d-143">Grouping</span></span>  
 <span data-ttu-id="5c55d-144">La clause `group` vous permet de grouper vos résultats selon une clé que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="5c55d-144">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="5c55d-145">Par exemple, vous pouvez spécifier un regroupement des résultats par ville (`City`) pour que tous les clients de Londres ou Paris soient dans des groupes individuels.</span><span class="sxs-lookup"><span data-stu-id="5c55d-145">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="5c55d-146">Dans ce cas, utilisez la clé `cust.City`.</span><span class="sxs-lookup"><span data-stu-id="5c55d-146">In this case, `cust.City` is the key.</span></span>  
  
 <span data-ttu-id="5c55d-147">[!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c55d-147">[!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]</span></span>  
  
 <span data-ttu-id="5c55d-148">Quand vous terminez une requête avec une clause `group`, les résultats sont présentés sous la forme d’une liste de listes.</span><span class="sxs-lookup"><span data-stu-id="5c55d-148">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="5c55d-149">Chaque élément de la liste est un objet qui a un membre `Key` et une liste d’éléments qui sont regroupés sous cette clé.</span><span class="sxs-lookup"><span data-stu-id="5c55d-149">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="5c55d-150">Quand vous itérez une requête qui produit une séquence de groupes, vous devez utiliser une boucle `foreach` imbriquée.</span><span class="sxs-lookup"><span data-stu-id="5c55d-150">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="5c55d-151">La boucle externe itère chaque groupe et la boucle interne itère les membres de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="5c55d-151">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="5c55d-152">Si vous devez faire référence aux résultats d’une opération de regroupement, utilisez le mot clé `into` pour créer un identificateur susceptible d’être interrogé ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="5c55d-152">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="5c55d-153">La requête suivante retourne uniquement les groupes qui contiennent plus de deux clients :</span><span class="sxs-lookup"><span data-stu-id="5c55d-153">The following query returns only those groups that contain more than two customers:</span></span>  
  
 <span data-ttu-id="5c55d-154">[!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c55d-154">[!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]</span></span>  
  
 <span data-ttu-id="5c55d-155">Pour plus d’informations, consultez [group, clause](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c55d-155">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="5c55d-156">Jointure</span><span class="sxs-lookup"><span data-stu-id="5c55d-156">Joining</span></span>  
 <span data-ttu-id="5c55d-157">Les opérations de jointure créent des associations entre les séquences qui ne sont pas explicitement modélisées dans les sources de données.</span><span class="sxs-lookup"><span data-stu-id="5c55d-157">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="5c55d-158">Par exemple, effectuez une jointure pour rechercher tous les clients et distributeurs qui se trouvent au même endroit.</span><span class="sxs-lookup"><span data-stu-id="5c55d-158">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="5c55d-159">Dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], la clause `join` fonctionne toujours par rapport à des collections d’objets plutôt que directement par rapport à des tables de base de données.</span><span class="sxs-lookup"><span data-stu-id="5c55d-159">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 <span data-ttu-id="5c55d-160">[!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c55d-160">[!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]</span></span>  
  
 <span data-ttu-id="5c55d-161">Dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], vous n’avez pas à utiliser `join` aussi souvent que vous le faites dans SQL, car les clés étrangères dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sont représentées dans le modèle objet comme des propriétés qui contiennent une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="5c55d-161">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] you do not have to use `join` as often as you do in SQL because foreign keys in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="5c55d-162">Par exemple, un objet `Customer` contient une collection d’objets `Order`.</span><span class="sxs-lookup"><span data-stu-id="5c55d-162">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="5c55d-163">Au lieu d’effectuer une jointure, accédez aux commandes en utilisant la notation par points :</span><span class="sxs-lookup"><span data-stu-id="5c55d-163">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```  
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="5c55d-164">Pour plus d’informations, consultez [join, clause](../../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c55d-164">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="5c55d-165">Sélection (projections)</span><span class="sxs-lookup"><span data-stu-id="5c55d-165">Selecting (Projections)</span></span>  
 <span data-ttu-id="5c55d-166">La clause `select` produit les résultats de la requête et spécifie la « forme » ou le type de chaque élément retourné.</span><span class="sxs-lookup"><span data-stu-id="5c55d-166">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="5c55d-167">Par exemple, spécifiez si les résultats doivent contenir des objets `Customer` complets, un seul membre, un sous-ensemble de membres ou un type de résultat complètement différent basé sur un calcul ou une création d’objet.</span><span class="sxs-lookup"><span data-stu-id="5c55d-167">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="5c55d-168">Quand la clause `select` produit autre chose qu’une copie de l’élément source, l’opération est appelée *projection*.</span><span class="sxs-lookup"><span data-stu-id="5c55d-168">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="5c55d-169">L’utilisation de projections pour transformer des données est une fonctionnalité puissante des expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c55d-169">The use of projections to transform data is a powerful capability of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="5c55d-170">Pour plus d’informations, consultez [Transformations de données avec LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) et [select, clause](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c55d-170">For more information, see [Data Transformations with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c55d-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c55d-171">See Also</span></span>  
 <span data-ttu-id="5c55d-172">[Bien démarrer avec LINQ en C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="5c55d-172">[Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
 <span data-ttu-id="5c55d-173">[Expressions de requête LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="5c55d-173">[LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="5c55d-174">[Procédure pas à pas : écriture de requêtes en C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="5c55d-174">[Walkthrough: Writing Queries in C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 <span data-ttu-id="5c55d-175">[Mots clés de requête (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="5c55d-175">[Query Keywords (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 [<span data-ttu-id="5c55d-176">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="5c55d-176">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

