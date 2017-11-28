---
title: "Retourner une requête à partir d’une méthode"
description: "Comment retourner une requête."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="9e8bf-104">Guide pratique pour retourner une requête à partir d'une méthode (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9e8bf-104">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="9e8bf-105">Cet exemple montre comment retourner une requête à partir d’une méthode en tant que valeur de retour et en tant que paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-105">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="9e8bf-106">Les objets de requête sont composables, ce qui signifie que vous pouvez retourner une requête à partir d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-106">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="9e8bf-107">Les objets qui représentent des requêtes ne stockent pas la collection résultante, mais plutôt les étapes pour générer les résultats lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-107">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="9e8bf-108">L’avantage de retourner des objets de requête à partir de méthodes est qu’il est possible de les composer ou modifier encore.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-108">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="9e8bf-109">Par conséquent, toute valeur de retour ou paramètre `out` d’une méthode qui retourne une requête doit également avoir ce type.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-109">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="9e8bf-110">Si une méthode matérialise une requête en un type <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concret, elle est considérée comme retournant les résultats de la requête plutôt que la requête elle-même.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-110">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="9e8bf-111">Une variable de requête retournée à partir d’une méthode peut encore être composée ou modifiée.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-111">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e8bf-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e8bf-112">Example</span></span>  
 <span data-ttu-id="9e8bf-113">Dans l’exemple suivant, la première méthode retourne une requête comme valeur de retour et la seconde méthode retourne une requête comme paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-113">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="9e8bf-114">Notez que, dans les deux cas, une requête est retournée et non pas les résultats d’une requête.</span><span class="sxs-lookup"><span data-stu-id="9e8bf-114">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="9e8bf-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e8bf-115">See Also</span></span>  
 [<span data-ttu-id="9e8bf-116">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="9e8bf-116">LINQ Query Expressions</span></span>](index.md)
