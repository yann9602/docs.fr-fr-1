---
title: "Retourner une requête à partir d’une méthode"
description: "Comment retourner une requête."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 747345f0a765bc6cbe947a2b0c7bc025eb599550
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="a1743-104">Guide pratique pour retourner une requête à partir d'une méthode (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a1743-104">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="a1743-105">Cet exemple montre comment retourner une requête à partir d’une méthode en tant que valeur de retour et en tant que paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="a1743-105">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="a1743-106">Les objets de requête sont composables, ce qui signifie que vous pouvez retourner une requête à partir d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="a1743-106">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="a1743-107">Les objets qui représentent des requêtes ne stockent pas la collection résultante, mais plutôt les étapes pour générer les résultats lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a1743-107">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="a1743-108">L’avantage de retourner des objets de requête à partir de méthodes est qu’il est possible de les composer ou modifier encore.</span><span class="sxs-lookup"><span data-stu-id="a1743-108">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="a1743-109">Par conséquent, toute valeur de retour ou paramètre `out` d’une méthode qui retourne une requête doit également avoir ce type.</span><span class="sxs-lookup"><span data-stu-id="a1743-109">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="a1743-110">Si une méthode matérialise une requête en un type <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concret, elle est considérée comme retournant les résultats de la requête plutôt que la requête elle-même.</span><span class="sxs-lookup"><span data-stu-id="a1743-110">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="a1743-111">Une variable de requête retournée à partir d’une méthode peut encore être composée ou modifiée.</span><span class="sxs-lookup"><span data-stu-id="a1743-111">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1743-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1743-112">Example</span></span>  
 <span data-ttu-id="a1743-113">Dans l’exemple suivant, la première méthode retourne une requête comme valeur de retour et la seconde méthode retourne une requête comme paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="a1743-113">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="a1743-114">Notez que, dans les deux cas, une requête est retournée et non pas les résultats d’une requête.</span><span class="sxs-lookup"><span data-stu-id="a1743-114">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 <span data-ttu-id="a1743-115">[!code-cs[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a1743-115">[!code-cs[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a1743-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1743-116">See Also</span></span>  
 [<span data-ttu-id="a1743-117">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="a1743-117">LINQ Query Expressions</span></span>](index.md)

