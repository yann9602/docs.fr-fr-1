---
title: "where, clause (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
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
ms.openlocfilehash: 97d7c16d6bf8048e621141fff52a47907881fd2f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="where-clause-c-reference"></a><span data-ttu-id="93e75-102">where, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="93e75-102">where clause (C# Reference)</span></span>
<span data-ttu-id="93e75-103">La clause `where` est utilisée dans une expression de requête pour spécifier les éléments de la source de données qui seront retournés dans l’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="93e75-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="93e75-104">Elle applique une condition booléenne (un *prédicat*) à chaque élément source (référencé par la variable de portée) et retourne ceux pour lesquels la condition spécifiée est remplie.</span><span class="sxs-lookup"><span data-stu-id="93e75-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="93e75-105">Une expression de requête unique peut contenir plusieurs clauses `where` et une clause unique peut contenir plusieurs sous-expressions de prédicat.</span><span class="sxs-lookup"><span data-stu-id="93e75-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93e75-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="93e75-106">Example</span></span>  
 <span data-ttu-id="93e75-107">Dans l’exemple suivant, la clause `where` élimine par filtrage tous les nombres excepté ceux inférieurs à cinq.</span><span class="sxs-lookup"><span data-stu-id="93e75-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="93e75-108">Si vous supprimez la clause `where`, tous les nombres de la source de données seront retournés.</span><span class="sxs-lookup"><span data-stu-id="93e75-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="93e75-109">L’expression `num < 5` est le prédicat qui est appliqué à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="93e75-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 <span data-ttu-id="93e75-110">[!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="93e75-110">[!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="93e75-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="93e75-111">Example</span></span>  
 <span data-ttu-id="93e75-112">Dans une clause `where` unique, vous pouvez spécifier autant de prédicats que nécessaire à l’aide des opérateurs [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md).</span><span class="sxs-lookup"><span data-stu-id="93e75-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="93e75-113">Dans l’exemple suivant, la requête spécifie deux prédicats pour sélectionner uniquement les nombres pairs inférieurs à cinq.</span><span class="sxs-lookup"><span data-stu-id="93e75-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 <span data-ttu-id="93e75-114">[!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="93e75-114">[!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="93e75-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="93e75-115">Example</span></span>  
 <span data-ttu-id="93e75-116">Une clause `where` peut contenir une ou plusieurs méthodes qui retournent des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="93e75-116">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="93e75-117">Dans l’exemple suivant, la clause `where` utilise une méthode pour déterminer si la valeur actuelle de la variable de portée est paire ou impaire.</span><span class="sxs-lookup"><span data-stu-id="93e75-117">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 <span data-ttu-id="93e75-118">[!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="93e75-118">[!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93e75-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="93e75-119">Remarks</span></span>  
 <span data-ttu-id="93e75-120">La clause `where` est un mécanisme de filtrage.</span><span class="sxs-lookup"><span data-stu-id="93e75-120">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="93e75-121">Elle peut être placée à presque n’importe quel endroit d’une expression de requête, sauf qu’elle ne peut pas être la première ni la dernière clause.</span><span class="sxs-lookup"><span data-stu-id="93e75-121">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="93e75-122">Une clause `where` peut apparaître avant ou après une clause [group](../../../csharp/language-reference/keywords/group-clause.md) selon que vous devez filtrer les éléments sources avant ou après leur regroupement.</span><span class="sxs-lookup"><span data-stu-id="93e75-122">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="93e75-123">Si un prédicat spécifié n’est pas valide pour les éléments de la source de données, une erreur de compilation est générée.</span><span class="sxs-lookup"><span data-stu-id="93e75-123">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="93e75-124">C’est l’un des avantages de la vérification de type fort fourni par [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93e75-124">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="93e75-125">Au moment de la compilation, le mot clé `where` est converti en appel à la méthode d’opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="93e75-125">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e75-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93e75-126">See Also</span></span>  
 <span data-ttu-id="93e75-127">[Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="93e75-127">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="93e75-128">[from, clause](../../../csharp/language-reference/keywords/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="93e75-128">[from clause](../../../csharp/language-reference/keywords/from-clause.md) </span></span>  
 <span data-ttu-id="93e75-129">[select, clause](../../../csharp/language-reference/keywords/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="93e75-129">[select clause](../../../csharp/language-reference/keywords/select-clause.md) </span></span>  
 <span data-ttu-id="93e75-130">[Filtrage des données](http://msdn.microsoft.com/library/cee88d0f-31aa-4c60-9452-cc122ed0057d) </span><span class="sxs-lookup"><span data-stu-id="93e75-130">[Filtering Data](http://msdn.microsoft.com/library/cee88d0f-31aa-4c60-9452-cc122ed0057d) </span></span>  
 <span data-ttu-id="93e75-131">[Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="93e75-131">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="93e75-132">Bien démarrer avec LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="93e75-132">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

