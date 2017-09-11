---
title: "select, clause (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
dev_langs:
- CSharp
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a505399eb79cbecbefcc53953329279a4abd92f6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="select-clause-c-reference"></a><span data-ttu-id="61d72-102">select, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="61d72-102">select clause (C# Reference)</span></span>
<span data-ttu-id="61d72-103">Dans une expression de requête, la clause `select` spécifie le type de valeurs qui sont générées quand la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="61d72-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="61d72-104">Le résultat est basé sur l’évaluation de toutes les clauses précédentes et sur toutes les expressions de la clause `select` elle-même.</span><span class="sxs-lookup"><span data-stu-id="61d72-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="61d72-105">Une expression de requête doit se terminer par une clause `select` ou par une clause [group](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="61d72-105">A query expression must terminate with either a `select` clause or a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>  
  
 <span data-ttu-id="61d72-106">L’exemple suivant présente une clause `select` simple dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="61d72-106">The following example shows a simple `select` clause in a query expression.</span></span>  
  
 <span data-ttu-id="61d72-107">[!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="61d72-107">[!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]</span></span>  
  
 <span data-ttu-id="61d72-108">Le type de la séquence générée par la clause `select` détermine le type de la variable de requête `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="61d72-108">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="61d72-109">Dans le cas le plus simple, la clause `select` spécifie uniquement la variable de portée.</span><span class="sxs-lookup"><span data-stu-id="61d72-109">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="61d72-110">La séquence retournée contient alors des éléments du même type que la source de données.</span><span class="sxs-lookup"><span data-stu-id="61d72-110">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="61d72-111">Pour plus d’informations, consultez [Relations des types dans des opérations de requête LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="61d72-111">For more information, see [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="61d72-112">Toutefois, la clause `select` fournit également un mécanisme puissant pour transformer (ou *projeter*) les données sources en nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="61d72-112">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="61d72-113">Pour plus d’informations, consultez [Transformations de données avec LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="61d72-113">For more information, see [Data Transformations with LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61d72-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="61d72-114">Example</span></span>  
 <span data-ttu-id="61d72-115">L’exemple suivant affiche l’ensemble des différentes formes que peut prendre une clause `select`.</span><span class="sxs-lookup"><span data-stu-id="61d72-115">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="61d72-116">Dans chaque requête, notez la relation entre la clause `select` et le type de la *variable de requête* (`studentQuery1`, `studentQuery2`, etc.).</span><span class="sxs-lookup"><span data-stu-id="61d72-116">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>  
  
 <span data-ttu-id="61d72-117">[!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="61d72-117">[!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]</span></span>  
  
 <span data-ttu-id="61d72-118">Comme indiqué dans `studentQuery8` dans l’exemple précédent, vous pouvez parfois souhaiter que les éléments de la séquence retournée contiennent uniquement un sous-ensemble des propriétés des éléments sources.</span><span class="sxs-lookup"><span data-stu-id="61d72-118">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="61d72-119">En limitant au maximum la séquence retournée, vous pouvez réduire les besoins en ressources mémoire et augmenter la vitesse d’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="61d72-119">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="61d72-120">Pour ce faire, créez un type anonyme dans la clause `select` et utilisez un initialiseur d’objet pour l’initialiser avec les propriétés appropriées de l’élément source.</span><span class="sxs-lookup"><span data-stu-id="61d72-120">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="61d72-121">Pour obtenir un exemple de la procédure à suivre, consultez [Initialiseurs d’objet et de collection](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="61d72-121">For an example of how to do this, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61d72-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="61d72-122">Remarks</span></span>  
 <span data-ttu-id="61d72-123">Au moment de la compilation, la clause `select` traduite en un appel de méthode à l’opérateur de requête standard <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="61d72-123">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d72-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61d72-124">See Also</span></span>  
 <span data-ttu-id="61d72-125">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="61d72-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="61d72-126">[Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="61d72-126">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="61d72-127">[from, clause](../../../csharp/language-reference/keywords/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="61d72-127">[from clause](../../../csharp/language-reference/keywords/from-clause.md) </span></span>  
 <span data-ttu-id="61d72-128">[partielle, méthode (Référence C#)](../../../csharp/language-reference/keywords/partial-method.md) </span><span class="sxs-lookup"><span data-stu-id="61d72-128">[partial (Method) (C# Reference)](../../../csharp/language-reference/keywords/partial-method.md) </span></span>  
 <span data-ttu-id="61d72-129">[Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="61d72-129">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="61d72-130">[Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="61d72-130">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="61d72-131">Bien démarrer avec LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="61d72-131">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

