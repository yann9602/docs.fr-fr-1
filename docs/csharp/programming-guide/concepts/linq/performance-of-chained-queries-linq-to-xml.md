---
title: "Performance des requêtes chaînées (LINQ to XML) (C#)"
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
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7c72c4eebd29152ed4fb95f2ee42075797c60b8a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="bad36-102">Performance des requêtes chaînées (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bad36-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="bad36-103">L'un des principaux avantages de LINQ (et LINQ to XML) est que les requêtes chaînées peuvent offrir la même performance qu'une requête unique plus grande et plus complexe.</span><span class="sxs-lookup"><span data-stu-id="bad36-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="bad36-104">Une requête chaînée est une requête qui utilise une autre requête comme source.</span><span class="sxs-lookup"><span data-stu-id="bad36-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="bad36-105">Par exemple, dans le code simple suivant, `query2` utilise `query1` comme source :</span><span class="sxs-lookup"><span data-stu-id="bad36-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 <span data-ttu-id="bad36-106">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="bad36-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="bad36-107">Cette requête chaînée offre le même profil de performance que l'itération sur une liste liée.</span><span class="sxs-lookup"><span data-stu-id="bad36-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="bad36-108">L'axe <xref:System.Xml.Linq.XContainer.Elements%2A> offre essentiellement la même performance qu'une itération sur une liste liée.</span><span class="sxs-lookup"><span data-stu-id="bad36-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="bad36-109"><xref:System.Xml.Linq.XContainer.Elements%2A> est implémenté en tant qu'itérateur avec exécution différée.</span><span class="sxs-lookup"><span data-stu-id="bad36-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="bad36-110">Cela signifie qu'en plus de l'itération sur la liste liée, il effectue certaines tâches comme l'allocation de l'objet itérateur et le suivi de l'état d'exécution.</span><span class="sxs-lookup"><span data-stu-id="bad36-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="bad36-111">Ces tâches peuvent être divisées en deux catégories : les tâches effectuées lors de la configuration de l'itérateur et les tâches effectuées à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="bad36-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="bad36-112">Les tâches de configuration représentent une part réduite et fixe du travail, tandis que les tâches effectuées à chaque itération sont proportionnelles au nombre d'éléments de la collection source.</span><span class="sxs-lookup"><span data-stu-id="bad36-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="bad36-113">Dans `query1`, la clause `where` indique que la requête doit appeler la méthode <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="bad36-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="bad36-114">Cette méthode est également implémentée en tant qu'itérateur.</span><span class="sxs-lookup"><span data-stu-id="bad36-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="bad36-115">Les tâches de configuration se composent de l'instanciation du délégué qui fera référence à l'expression, en plus de la configuration normale d'un itérateur.</span><span class="sxs-lookup"><span data-stu-id="bad36-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="bad36-116">A chaque itération, le délégué est appelé pour exécuter le prédicat.</span><span class="sxs-lookup"><span data-stu-id="bad36-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="bad36-117">Les tâches de configuration et les tâches effectuées à chaque itération sont similaires aux tâches effectuées lors de l'itération sur l'axe.</span><span class="sxs-lookup"><span data-stu-id="bad36-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="bad36-118">Dans `query1`, la clause select indique que la requête doit appeler la méthode <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="bad36-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="bad36-119">Cette méthode fournit le même profil de performance que la méthode <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="bad36-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="bad36-120">Dans `query2`, la clause `where` et la `select` clause ont toutes deux le même profil de performance que dans `query1`.</span><span class="sxs-lookup"><span data-stu-id="bad36-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="bad36-121">L'itération sur `query2` est donc directement proportionnelle au nombre d'éléments de la source de la première requête, en d'autres termes, elle suit un algorithme linéaire.</span><span class="sxs-lookup"><span data-stu-id="bad36-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="bad36-122">Un exemple Visual Basic correspondant aurait le même profil de performance.</span><span class="sxs-lookup"><span data-stu-id="bad36-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="bad36-123">Pour plus d’informations sur les itérateurs, consultez [yield](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="bad36-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="bad36-124">Pour obtenir un didacticiel plus détaillé sur le chaînage de requêtes, consultez [Didacticiel : Chaînage de requêtes](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span><span class="sxs-lookup"><span data-stu-id="bad36-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad36-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bad36-125">See Also</span></span>  
 [<span data-ttu-id="bad36-126">Performance (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bad36-126">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)

