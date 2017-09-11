---
title: "Opérations de requête de base (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1ced446d6646bd26b9169f5894138e12a38efde7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="d3fb0-102">Opérations de requête de base (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3fb0-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="d3fb0-103">Cette rubrique fournit une brève introduction aux [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions en Visual Basic et certains types d’opérations que vous effectuez dans une requête classiques.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="d3fb0-104">Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3fb0-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="d3fb0-105">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3fb0-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="d3fb0-106">Requêtes</span><span class="sxs-lookup"><span data-stu-id="d3fb0-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [<span data-ttu-id="d3fb0-107">Procédure pas à pas : Écriture de requêtes dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3fb0-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="d3fb0-108">Spécification de la Source de données (début)</span><span class="sxs-lookup"><span data-stu-id="d3fb0-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="d3fb0-109">Dans un [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requête, la première étape consiste à spécifier la source de données que vous souhaitez interroger.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-109">In a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="d3fb0-110">Par conséquent, le `From` clause dans une requête se produit toujours en premier.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="d3fb0-111">Opérateurs de requête sélectionnent et mettre en forme le résultat en fonction du type de la source.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 <span data-ttu-id="d3fb0-112">[!code-vb[VbLINQBasicOps n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-112">[!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-113">Le `From` spécifie la source de données `customers`et un *variable de plage*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-113">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="d3fb0-114">La variable de portée est comme une variable d’itération de boucle, sauf que dans une expression de requête, aucune itération réelle ne se produit.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-114">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="d3fb0-115">Lorsque la requête est exécutée, souvent en utilisant une `For Each` boucle, la variable de portée sert de référence à chaque élément consécutif dans `customers`.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-115">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="d3fb0-116">Étant donné que le compilateur peut déduire le type de `cust`, vous n’êtes pas obligé de spécifier explicitement.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="d3fb0-117">Pour obtenir des exemples de requêtes écrites avec et sans type explicite, consultez [relations des types dans des opérations de requête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-117">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="d3fb0-118">Pour plus d’informations sur l’utilisation de la `From` clause en Visual Basic, consultez [à partir de la Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-118">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="d3fb0-119">Filtrage des données (où)</span><span class="sxs-lookup"><span data-stu-id="d3fb0-119">Filtering Data (Where)</span></span>  
 <span data-ttu-id="d3fb0-120">Probablement l’opération de requête la plus commune consiste à appliquer un filtre sous la forme d’une expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-120">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="d3fb0-121">Ensuite, la requête retourne uniquement les éléments pour lesquels l’expression a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-121">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="d3fb0-122">Un `Where` clause est utilisée pour effectuer le filtrage.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-122">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="d3fb0-123">Le filtre spécifie les éléments de la source de données à inclure dans la séquence résultante.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-123">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="d3fb0-124">Dans l’exemple suivant, que les clients qui ont une adresse à Londres sont inclus.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-124">In the following example, only those customers who have an address in London are included.</span></span>  
  
 <span data-ttu-id="d3fb0-125">[!code-vb[VbLINQBasicOps n °&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-125">[!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-126">Vous pouvez utiliser des opérateurs logiques tels que `And` et `Or` pour associer des expressions de filtre dans un `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-126">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="d3fb0-127">Par exemple, pour retourner uniquement les clients de Londres et dont le nom est Devon, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d3fb0-127">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="d3fb0-128">Pour retourner les clients de Londres ou Paris, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d3fb0-128">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="d3fb0-129">Pour plus d’informations sur l’utilisation de la `Where` clause en Visual Basic, consultez [une Clause Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-129">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="d3fb0-130">Classer des données (Order By)</span><span class="sxs-lookup"><span data-stu-id="d3fb0-130">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="d3fb0-131">Il est souvent pratique de trier les données retournées dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-131">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="d3fb0-132">Le `Order By` clause triera les éléments de la séquence retournée selon un ou plusieurs champs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-132">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="d3fb0-133">Par exemple, la requête suivante trie les résultats selon le `Name` propriété.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-133">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="d3fb0-134">Étant donné que `Name` est une chaîne, les données retournées seront triées par ordre alphabétique, de A à Z.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-134">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 <span data-ttu-id="d3fb0-135">[!code-vb[VbLINQBasicOps n °&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-135">[!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-136">Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la `Order By...Descending` clause.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-136">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="d3fb0-137">La valeur par défaut est `Ascending` lorsque ni `Ascending` ni `Descending` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-137">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="d3fb0-138">Pour plus d’informations sur l’utilisation de la `Order By` clause en Visual Basic, consultez [une Clause Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-138">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="d3fb0-139">Sélection de données (sélection)</span><span class="sxs-lookup"><span data-stu-id="d3fb0-139">Selecting Data (Select)</span></span>  
 <span data-ttu-id="d3fb0-140">Le `Select` spécifie la forme et le contenu d’éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-140">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="d3fb0-141">Par exemple, vous pouvez spécifier si vos résultats seront compose de complet `Customer` des objets, un seul `Customer` propriété, un sous-ensemble de propriétés, une combinaison de propriétés à partir de diverses sources de données, ou un nouveau type de résultat basé sur un calcul.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-141">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="d3fb0-142">Lors de la `Select` clause produit autre chose qu’une copie de l’élément source, l’opération est appelée un *projection*.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-142">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="d3fb0-143">Pour récupérer une collection qui se compose de complet `Customer` objets, sélectionnez la variable de portée elle-même :</span><span class="sxs-lookup"><span data-stu-id="d3fb0-143">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 <span data-ttu-id="d3fb0-144">[!code-vb[VbLINQBasicOps n °&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-144">[!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-145">Si un `Customer` instance est un objet qui compte de nombreux champs, et tout ce que vous souhaitez récupérer est le nom, vous pouvez sélectionner `cust.Name`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-145">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="d3fb0-146">Inférence de type local reconnaît que cela modifie le type de résultat d’une collection de `Customer` objets à une collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-146">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 <span data-ttu-id="d3fb0-147">[!code-vb[VbLINQBasicOps n °&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-147">[!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-148">Pour sélectionner plusieurs champs dans la source de données, vous avez deux possibilités :</span><span class="sxs-lookup"><span data-stu-id="d3fb0-148">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="d3fb0-149">Dans la `Select` clause, spécifiez les champs que vous souhaitez inclure dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-149">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="d3fb0-150">Le compilateur définira un type anonyme dont ces champs en tant que ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-150">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="d3fb0-151">Pour plus d’informations, consultez [les Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-151">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="d3fb0-152">Étant donné que les éléments retournés dans l’exemple suivant sont des instances d’un type anonyme, vous ne peut pas faire référence au type par son nom ailleurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-152">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="d3fb0-153">Le nom du type désigné par le compilateur contient des caractères qui ne sont pas valides dans du code Visual Basic normal.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-153">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="d3fb0-154">Dans l’exemple suivant, les éléments dans la collection retournée par la requête dans `londonCusts4` sont des instances d’un type anonyme</span><span class="sxs-lookup"><span data-stu-id="d3fb0-154">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     <span data-ttu-id="d3fb0-155">[!code-vb[VbLINQBasicOps n °&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-155">[!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]</span></span>  
  
     <span data-ttu-id="d3fb0-156">ou</span><span class="sxs-lookup"><span data-stu-id="d3fb0-156">-or-</span></span>  
  
-   <span data-ttu-id="d3fb0-157">Définissez un type nommé qui contient les champs spécifiques que vous souhaitez inclure dans le résultat, de créer et initialiser des instances du type dans le `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-157">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="d3fb0-158">Utilisez cette option uniquement si vous devez utiliser des résultats individuels en dehors de la collection dans lequel ils sont retournés, ou si vous devez les passer comme paramètres dans les appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-158">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="d3fb0-159">Le type de `londonCusts5` dans l’exemple suivant est IEnumerable (Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-159">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     <span data-ttu-id="d3fb0-160">[!code-vb[VbLINQBasicOps&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-160">[!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]</span></span>  
  
     <span data-ttu-id="d3fb0-161">[!code-vb[VbLINQBasicOps n °&8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-161">[!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-162">Pour plus d’informations sur l’utilisation de la `Select` clause en Visual Basic, consultez [Clause Select](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-162">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="d3fb0-163">Jointure de données (Join et Group Join)</span><span class="sxs-lookup"><span data-stu-id="d3fb0-163">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="d3fb0-164">Vous pouvez combiner plusieurs sources de données dans le `From` clause de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-164">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="d3fb0-165">Par exemple, le code suivant utilise deux sources de données et associe implicitement les propriétés des deux dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-165">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="d3fb0-166">La requête sélectionne les étudiants dont le nom commence par une voyelle.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-166">The query selects students whose last names start with a vowel.</span></span>  
  
 <span data-ttu-id="d3fb0-167">[!code-vb[VbLINQBasicOps&#9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-167">[!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3fb0-168">Vous pouvez exécuter ce code avec la liste d’étudiants créée dans [Comment : créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-168">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="d3fb0-169">Le `Join` mot clé est équivalent à un `INNER JOIN` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-169">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="d3fb0-170">Il associe deux collections basées sur des valeurs de clés correspondantes entre les éléments dans les deux collections.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-170">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="d3fb0-171">La requête retourne tout ou partie des éléments de collection qui ont des valeurs de clés correspondantes.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-171">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="d3fb0-172">Par exemple, le code suivant duplique l’action de la jointure implicite précédente.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-172">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 <span data-ttu-id="d3fb0-173">[!code-vb[VbLINQBasicOps&#10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-173">[!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-174">`Group Join`rassemble des collections dans une collection hiérarchique unique, tout comme un `LEFT JOIN` dans SQL.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-174">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="d3fb0-175">Pour plus d’informations, consultez [Clause Join](../../../../visual-basic/language-reference/queries/join-clause.md) et [Group Join, Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-175">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="d3fb0-176">Regroupement de données (Group By)</span><span class="sxs-lookup"><span data-stu-id="d3fb0-176">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="d3fb0-177">Vous pouvez ajouter un `Group By` clause pour regrouper les éléments d’un résultat de requête en fonction d’un ou plusieurs champs des éléments.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-177">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="d3fb0-178">Par exemple, le code suivant regroupe les étudiants par année de classe.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-178">For example, the following code groups students by class year.</span></span>  
  
 <span data-ttu-id="d3fb0-179">[!code-vb[VbLINQBasicOps&#11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-179">[!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-180">Si vous exécutez ce code à l’aide de la liste d’étudiants créée dans [Comment : créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), la sortie de la `For Each` instruction est :</span><span class="sxs-lookup"><span data-stu-id="d3fb0-180">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="d3fb0-181">Year : Junior</span><span class="sxs-lookup"><span data-stu-id="d3fb0-181">Year: Junior</span></span>  
  
 <span data-ttu-id="d3fb0-182">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="d3fb0-182">Tucker, Michael</span></span>  
  
 <span data-ttu-id="d3fb0-183">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="d3fb0-183">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="d3fb0-184">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="d3fb0-184">Garcia, Debra</span></span>  
  
 <span data-ttu-id="d3fb0-185">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="d3fb0-185">Tucker, Lance</span></span>  
  
 <span data-ttu-id="d3fb0-186">Year : Senior</span><span class="sxs-lookup"><span data-stu-id="d3fb0-186">Year: Senior</span></span>  
  
 <span data-ttu-id="d3fb0-187">Omelchenko, Svetlana remarque</span><span class="sxs-lookup"><span data-stu-id="d3fb0-187">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="d3fb0-188">Ourset a, Michiko</span><span class="sxs-lookup"><span data-stu-id="d3fb0-188">Osada, Michiko</span></span>  
  
 <span data-ttu-id="d3fb0-189">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="d3fb0-189">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="d3fb0-190">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="d3fb0-190">Feng, Hanying</span></span>  
  
 <span data-ttu-id="d3fb0-191">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="d3fb0-191">Adams, Terry</span></span>  
  
 <span data-ttu-id="d3fb0-192">Année : Freshman</span><span class="sxs-lookup"><span data-stu-id="d3fb0-192">Year: Freshman</span></span>  
  
 <span data-ttu-id="d3fb0-193">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="d3fb0-193">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="d3fb0-194">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="d3fb0-194">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="d3fb0-195">La variante indiquée dans le code suivant trie les années de classe, puis trie les étudiants de chaque année par nom de famille.</span><span class="sxs-lookup"><span data-stu-id="d3fb0-195">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 <span data-ttu-id="d3fb0-196">[!code-vb[VbLINQBasicOps&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3fb0-196">[!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]</span></span>  
  
 <span data-ttu-id="d3fb0-197">Pour plus d’informations sur `Group By`, consultez [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3fb0-197">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fb0-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3fb0-198">See Also</span></span>  
 <span data-ttu-id="d3fb0-199"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="d3fb0-199"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="d3fb0-200"> [Mise en route de LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="d3fb0-200"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="d3fb0-201"> [Requêtes](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="d3fb0-201"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="d3fb0-202"> [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d3fb0-202"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="d3fb0-203"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="d3fb0-203"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)</span></span>
