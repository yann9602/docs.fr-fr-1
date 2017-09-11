---
title: "orderby, clause (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- orderby
- orderby_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: 17
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
ms.openlocfilehash: ec9507e4c1d9691d90d47cdbb20fdb22fc281d24
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="6a91b-102">orderby, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="6a91b-102">orderby clause (C# Reference)</span></span>
<span data-ttu-id="6a91b-103">Dans une expression de requête, la clause `orderby` a pour effet de trier la séquence ou la sous-séquence (groupe) retournée par ordre croissant ou décroissant.</span><span class="sxs-lookup"><span data-stu-id="6a91b-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="6a91b-104">Il est possible de spécifier plusieurs clés de façon à effectuer une ou plusieurs opérations de tri secondaire.</span><span class="sxs-lookup"><span data-stu-id="6a91b-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="6a91b-105">Le tri est effectué par le comparateur par défaut du type de l’élément.</span><span class="sxs-lookup"><span data-stu-id="6a91b-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="6a91b-106">L'ordre de tri par défaut est le tri croissant.</span><span class="sxs-lookup"><span data-stu-id="6a91b-106">The default sort order is ascending.</span></span> <span data-ttu-id="6a91b-107">Vous pouvez aussi spécifier un comparateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6a91b-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="6a91b-108">Cependant, sa disponibilité est soumise à l’utilisation d’une syntaxe fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="6a91b-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="6a91b-109">Pour plus d’informations, consultez [Tri des données](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48).</span><span class="sxs-lookup"><span data-stu-id="6a91b-109">For more information, see [Sorting Data](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a91b-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a91b-110">Example</span></span>  
 <span data-ttu-id="6a91b-111">Dans l’exemple suivant, la première requête trie les mots par ordre alphabétique à partir de A, tandis que la deuxième requête trie les mêmes mots par ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="6a91b-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="6a91b-112">(Le mot clé `ascending` est la valeur de tri par défaut et peut être omis.)</span><span class="sxs-lookup"><span data-stu-id="6a91b-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>  
  
 <span data-ttu-id="6a91b-113">[!code-cs[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6a91b-113">[!code-cs[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a91b-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a91b-114">Example</span></span>  
 <span data-ttu-id="6a91b-115">L’exemple suivant effectue un tri principal sur les noms des étudiants, puis un tri secondaire sur leurs prénoms.</span><span class="sxs-lookup"><span data-stu-id="6a91b-115">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>  
  
 <span data-ttu-id="6a91b-116">[!code-cs[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6a91b-116">[!code-cs[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a91b-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="6a91b-117">Remarks</span></span>  
 <span data-ttu-id="6a91b-118">Au moment de la compilation, la clause `orderby` est traduite en appel à la méthode <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="6a91b-118">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="6a91b-119">Les différentes clés présentes dans la clause `orderby` sont traduites en appels à la méthode <xref:System.Linq.Enumerable.ThenBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="6a91b-119">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a91b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a91b-120">See Also</span></span>  
 <span data-ttu-id="6a91b-121">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6a91b-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6a91b-122">[Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="6a91b-122">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="6a91b-123">[Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="6a91b-123">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="6a91b-124">[group, clause](../../../csharp/language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="6a91b-124">[group clause](../../../csharp/language-reference/keywords/group-clause.md) </span></span>  
 [<span data-ttu-id="6a91b-125">Bien démarrer avec LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="6a91b-125">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

