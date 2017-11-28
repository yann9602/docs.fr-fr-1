---
title: "Effectuer des jointures à l’aide de clés composites"
description: "Guide pratique pour effectuer des jointures à l’aide de clés composites."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: c285e768d64d1da7e428e29fc67838e87575500c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="7192a-104">Effectuer des jointures à l’aide de clés composites</span><span class="sxs-lookup"><span data-stu-id="7192a-104">Join by using composite keys</span></span>

<span data-ttu-id="7192a-105">Cet exemple montre comment effectuer des opérations de jointure où vous voulez utiliser plusieurs clés pour définir une correspondance.</span><span class="sxs-lookup"><span data-stu-id="7192a-105">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="7192a-106">Ceci s’effectue à l’aide d’une clé composite.</span><span class="sxs-lookup"><span data-stu-id="7192a-106">This is accomplished by using a composite key.</span></span> <span data-ttu-id="7192a-107">Vous créez une clé composite en tant que type anonyme ou typé nommé avec les valeurs que vous voulez comparer.</span><span class="sxs-lookup"><span data-stu-id="7192a-107">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="7192a-108">Si la variable de requête doit être passée au-delà des limites de la méthode, utilisez un type nommé qui substitue <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> pour la clé.</span><span class="sxs-lookup"><span data-stu-id="7192a-108">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="7192a-109">Les noms des propriétés et l’ordre dans lequel elles se trouvent doivent être identiques dans chaque clé.</span><span class="sxs-lookup"><span data-stu-id="7192a-109">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7192a-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="7192a-110">Example</span></span>  
 <span data-ttu-id="7192a-111">L’exemple suivant montre comment utiliser une clé composite pour joindre les données de trois tables :</span><span class="sxs-lookup"><span data-stu-id="7192a-111">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="7192a-112">L’inférence du type sur les clés composites dépend des noms des propriétés dans les clés et l’ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="7192a-112">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="7192a-113">Si les propriétés dans les séquences sources n’ont pas les mêmes noms, vous devez affecter de nouveaux noms dans les clés.</span><span class="sxs-lookup"><span data-stu-id="7192a-113">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="7192a-114">Par exemple, si la table `Orders` et la table `OrderDetails` utilisent chacune des noms différents pour leurs colonnes, vous pouvez créer des clés composites en affectant des noms identiques dans les types anonymes :</span><span class="sxs-lookup"><span data-stu-id="7192a-114">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="7192a-115">Vous pouvez aussi utiliser des clés composites dans une clause `group`.</span><span class="sxs-lookup"><span data-stu-id="7192a-115">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="7192a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7192a-116">See also</span></span>  
 [<span data-ttu-id="7192a-117">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="7192a-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="7192a-118">join, clause</span><span class="sxs-lookup"><span data-stu-id="7192a-118">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="7192a-119">group, clause</span><span class="sxs-lookup"><span data-stu-id="7192a-119">group clause</span></span>](../language-reference/keywords/group-clause.md)
