---
title: "Vue d’ensemble des opérateurs de requête standard (Visual Basic) | Documents Microsoft"
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
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 229b63db761f2a1ed5333fd6f8e4eb9b5c0b75de
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="828c7-102">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="828c7-103">Le *opérateurs de requête standard* sont les méthodes qui forment le modèle LINQ.</span><span class="sxs-lookup"><span data-stu-id="828c7-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="828c7-104">La plupart de ces méthodes fonctionnent sur des séquences, une séquence étant un objet dont le type implémente le <xref:System.Collections.Generic.IEnumerable%601>interface ou <xref:System.Linq.IQueryable%601>interface.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="828c7-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="828c7-105">Les opérateurs de requête standard fournissent des fonctions de requête, notamment le filtrage, la projection, l’agrégation, le tri et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="828c7-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="828c7-106">Il existe deux ensembles d’opérateurs de requête standard LINQ qui opère sur des objets de type <xref:System.Collections.Generic.IEnumerable%601>et l’autre qui opère sur des objets de type <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="828c7-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="828c7-107">Les méthodes qui composent chaque ensemble sont des membres statiques de la <xref:System.Linq.Enumerable>et <xref:System.Linq.Queryable>des classes, respectivement.</xref:System.Linq.Queryable> </xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="828c7-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="828c7-108">Ils sont définis en tant que *les méthodes d’extension* du type lequel elles fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="828c7-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="828c7-109">Cela signifie qu’elles peuvent être appelées à l’aide de la syntaxe de méthode statique ou de syntaxe de méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="828c7-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="828c7-110">En outre, plusieurs méthodes d’opérateur de requête standard opèrent sur des types autres que ceux basés sur <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="828c7-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="828c7-111">Le <xref:System.Linq.Enumerable>type définit deux méthodes telles que les deux fonctionnent sur les objets de type <xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable> </xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="828c7-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="828c7-112">Ces méthodes, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29>et <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, laissez vous activez une collection non paramétrée, ou non générique, à interroger dans le modèle LINQ.</xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> </xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29></span><span class="sxs-lookup"><span data-stu-id="828c7-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="828c7-113">Ils cela en créant une collection fortement typée d’objets.</span><span class="sxs-lookup"><span data-stu-id="828c7-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="828c7-114">La <xref:System.Linq.Queryable>classe définit deux méthodes similaires <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29>et <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, qui opèrent sur des objets de type <xref:System.Linq.Queryable>.</xref:System.Linq.Queryable> </xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="828c7-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="828c7-115">Les opérateurs de requête standard diffèrent dans le déroulement de leur exécution, selon qu’ils retournent une valeur singleton ou une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="828c7-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="828c7-116">Les méthodes qui retournent une valeur singleton (par exemple, <xref:System.Linq.Enumerable.Average%2A>et <xref:System.Linq.Enumerable.Sum%2A>) s’exécutent immédiatement.</xref:System.Linq.Enumerable.Sum%2A> </xref:System.Linq.Enumerable.Average%2A></span><span class="sxs-lookup"><span data-stu-id="828c7-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="828c7-117">Les méthodes qui retournent une séquence de différer l’exécution de la requête et retournent un objet énumérable.</span><span class="sxs-lookup"><span data-stu-id="828c7-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="828c7-118">Dans le cas des méthodes qui fonctionnent sur les collections en mémoire, autrement dit, les méthodes qui étendent <xref:System.Collections.Generic.IEnumerable%601>, l’objet énumérable retourné capture les arguments passés à la méthode.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="828c7-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="828c7-119">Lorsque cet objet est énuméré, la logique de l’opérateur de requête est employée et les résultats de requête sont retournés.</span><span class="sxs-lookup"><span data-stu-id="828c7-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="828c7-120">En revanche, les méthodes qui étendent <xref:System.Linq.IQueryable%601>n’implémentent pas aucun comportement d’interrogation, mais créer une arborescence d’expression qui représente la requête à exécuter.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="828c7-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="828c7-121">Le traitement de requête est contrôlé par la source de <xref:System.Linq.IQueryable%601>objet.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="828c7-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="828c7-122">Les appels aux méthodes de requête peuvent être chaînés ensemble dans une seule requête, ce qui permet aux requêtes de devenir arbitrairement complexes.</span><span class="sxs-lookup"><span data-stu-id="828c7-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="828c7-123">L’exemple de code suivant illustre l’utilisation des opérateurs de requête standard pour obtenir des informations sur une séquence.</span><span class="sxs-lookup"><span data-stu-id="828c7-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="828c7-124">Syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="828c7-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="828c7-125">Certains des opérateurs de requête standard plus fréquemment utilisées sont dédiées à c# et Visual Basic syntaxe de mot clé de langage qui leur permet d’être appelée dans le cadre d’un *requête* *expression*.</span><span class="sxs-lookup"><span data-stu-id="828c7-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="828c7-126">Pour plus d’informations sur les opérateurs de requête standard qui sont dédiées des mots clés et leurs syntaxes correspondantes, consultez [syntaxe d’Expression de requête pour les opérateurs de requête Standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="828c7-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="828c7-127">Extension des opérateurs de requête Standard</span><span class="sxs-lookup"><span data-stu-id="828c7-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="828c7-128">Vous pouvez augmenter l’ensemble des opérateurs de requête standard en création méthodes spécifiques au domaine qui sont appropriés pour votre domaine ou technologie cible.</span><span class="sxs-lookup"><span data-stu-id="828c7-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="828c7-129">Vous pouvez également remplacer les opérateurs de requête standard par vos propres implémentations qui fournissent des services supplémentaires tels que l’évaluation à distance, traduction de requête et l’optimisation.</span><span class="sxs-lookup"><span data-stu-id="828c7-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="828c7-130">Consultez <xref:System.Linq.Enumerable.AsEnumerable%2A>pour obtenir un exemple.</xref:System.Linq.Enumerable.AsEnumerable%2A></span><span class="sxs-lookup"><span data-stu-id="828c7-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="828c7-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="828c7-131">Related Sections</span></span>  
 <span data-ttu-id="828c7-132">Les liens suivants vous renvoient vers des rubriques qui fournissent des informations supplémentaires sur les divers opérateurs de requête standard basée sur la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="828c7-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="828c7-133">Tri des données</span><span class="sxs-lookup"><span data-stu-id="828c7-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="828c7-134">Opérations ensemblistes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="828c7-135">Filtrage des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="828c7-136">Opérations de quantificateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="828c7-137">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="828c7-138">Partitionnement des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="828c7-139">Joindre des opérations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="828c7-140">Regroupement de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="828c7-141">Opérations de génération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="828c7-142">Opérations d’égalité (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="828c7-143">Opérations d’élément (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="828c7-144">Conversion des Types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="828c7-145">Opérations de concaténation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="828c7-146">Opérations d’agrégation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="828c7-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="828c7-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="828c7-147">See Also</span></span>  
 <span data-ttu-id="828c7-148"><xref:System.Linq.Enumerable></xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="828c7-148"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="828c7-149"><xref:System.Linq.Queryable></xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="828c7-149"><xref:System.Linq.Queryable></span></span>   
<span data-ttu-id="828c7-150"> [Introduction à LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="828c7-150"> [Introduction to LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="828c7-151"> [Syntaxe d’Expression de requête pour les opérateurs de requête Standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span><span class="sxs-lookup"><span data-stu-id="828c7-151"> [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span></span>  
<span data-ttu-id="828c7-152"> [Classification des opérateurs de requête Standard en mode d’exécution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md) </span><span class="sxs-lookup"><span data-stu-id="828c7-152"> [Classification of Standard Query Operators by Manner of Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md) </span></span>  
<span data-ttu-id="828c7-153"> [Méthodes d’extension](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="828c7-153"> [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span></span>
