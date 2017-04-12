---
title: "Effectuer des jointures à l’aide de clés composites"
description: "Guide pratique pour effectuer des jointures à l’aide de clés composites."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f504c9dabcd7ca2d198d58c6d81e1fde1052e3be
ms.lasthandoff: 03/13/2017

---
# <a name="join-by-using-composite-keys"></a>Effectuer des jointures à l’aide de clés composites

Cet exemple montre comment effectuer des opérations de jointure où vous voulez utiliser plusieurs clés pour définir une correspondance. Ceci s’effectue à l’aide d’une clé composite. Vous créez une clé composite en tant que type anonyme ou typé nommé avec les valeurs que vous voulez comparer. Si la variable de requête doit être passée au-delà des limites de la méthode, utilisez un type nommé qui remplace <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> pour la clé. Les noms des propriétés et l’ordre dans lequel elles se trouvent doivent être identiques dans chaque clé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser une clé composite pour joindre les données de trois tables :  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 L’inférence du type sur les clés composites dépend des noms des propriétés dans les clés et l’ordre dans lequel elles apparaissent. Si les propriétés dans les séquences sources n’ont pas les mêmes noms, vous devez affecter de nouveaux noms dans les clés. Par exemple, si la table `Orders` et la table `OrderDetails` utilisent chacune des noms différents pour leurs colonnes, vous pouvez créer des clés composites en affectant des noms identiques dans les types anonymes :  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 Vous pouvez aussi utiliser des clés composites dans une clause `group`.  

## <a name="see-also"></a>Voir aussi  
 [Expressions de requête LINQ](index.md)   
 [join, clause](../language-reference/keywords/join-clause.md)   
 [group, clause](../language-reference/keywords/group-clause.md)
