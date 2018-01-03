---
title: "Requêtes d'analyse croisée (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 059dd39f3583c3b8fcf6736e514b9cc4870d3ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cross-table-queries-linq-to-dataset"></a>Requêtes d'analyse croisée (LINQ to DataSet)
Outre l'interrogation d'une table unique, vous pouvez également exécuter des requêtes à tables croisées dans [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Cela en utilisant un *jointure*. Une jointure est l'association d'objets d'une source de données avec des objets qui partagent un attribut commun dans une autre source de données, comme un produit ou un ID de contact. Dans la programmation orientée objets, les relations entre les objets sont relativement faciles à explorer car chaque objet possède un membre faisant référence à un autre objet. Dans les tables de base de données externe, toutefois, l'exploration des relations n'est pas aussi simple. Les tables de base de données ne contiennent pas de relations intégrées. Dans ces cas particuliers, l'opération de jointure peut servir à faire correspondre des éléments de chaque source. Par exemple, avec deux tables qui contiennent des informations sur les produits et des informations sur les ventes, vous pourriez utiliser une opération de jointure pour faire correspondre les informations sur les ventes et les produits pour la même commande.  
  
 L'infrastructure [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] fournit deux opérateurs de jointure, <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>. Ces opérateurs effectuent *équijointures*: autrement dit, les jointures qui correspondent aux données de deux sources uniquement lorsque leurs clés sont égales. (Par contraste, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] prend en charge des opérateurs de jointure autres que `equals`, comme l'opérateur `less than`.)  
  
 En termes de base de données relationnelle, <xref:System.Linq.Enumerable.Join%2A> implémente une jointure interne. Une jointure interne est un type de jointure dans lequel seuls les objets qui ont une correspondance dans le data set opposé sont retournés.  
  
 Le <xref:System.Linq.Enumerable.GroupJoin%2A> opérateurs n’ont aucun équivalent direct en termes de base de données relationnelle ; elles implémentent un sur-ensemble de jointures internes et de jointures externes gauches. Une jointure externe gauche est une jointure qui retourne chaque élément de la première collection (gauche), même si elle n’a pas d’éléments corrélés dans la seconde collection.  
  
 Pour plus d’informations sur les jointures, consultez [les opérations de jointures](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant effectue une jointure traditionnelle des tables `SalesOrderHeader` et `SalesOrderDetail` de l'exemple de base de données AdventureWorks pour obtenir les commandes en ligne du mois d'août.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Requêtes de table unique](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [Interrogation de DataSets typés](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [Opérations de jointure](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [Exemples LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
