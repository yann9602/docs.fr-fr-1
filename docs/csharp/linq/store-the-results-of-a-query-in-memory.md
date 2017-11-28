---
title: "Stocker les résultats d’une requête dans la mémoire"
description: "Comment enregistrer les résultats."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="5ed42-104">Stocker les résultats d’une requête dans la mémoire</span><span class="sxs-lookup"><span data-stu-id="5ed42-104">Store the results of a query in memory</span></span>

<span data-ttu-id="5ed42-105">Une requête est en fait un ensemble d’instructions permettant de récupérer et d’organiser des données.</span><span class="sxs-lookup"><span data-stu-id="5ed42-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="5ed42-106">Les requêtes sont exécutées de manière différée, à mesure que chaque élément dans le résultat est demandé.</span><span class="sxs-lookup"><span data-stu-id="5ed42-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="5ed42-107">Lorsque vous utilisez `foreach` pour effectuer une itération sur les résultats, les éléments sont retournés lorsque vous y accédez.</span><span class="sxs-lookup"><span data-stu-id="5ed42-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="5ed42-108">Pour évaluer une requête et stocker ses résultats sans exécuter une boucle `foreach`, appelez simplement l’une des méthodes suivantes sur la variable de requête :</span><span class="sxs-lookup"><span data-stu-id="5ed42-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="5ed42-109">Lorsque vous stockez les résultats de requête, nous vous recommandons d’assigner l’objet de collection retourné à une nouvelle variable, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5ed42-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ed42-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="5ed42-110">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="5ed42-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ed42-111">See Also</span></span>  
 [<span data-ttu-id="5ed42-112">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="5ed42-112">LINQ Query Expressions</span></span>](index.md)
