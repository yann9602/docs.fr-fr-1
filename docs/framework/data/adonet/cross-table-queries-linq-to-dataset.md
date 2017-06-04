---
title: "Requ&#234;tes d&#39;analyse crois&#233;e (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Requ&#234;tes d&#39;analyse crois&#233;e (LINQ to DataSet)
Outre l'interrogation d'une table unique, vous pouvez également exécuter des requêtes à tables croisées dans [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Pour cela, vous utilisez une *jointure*.  Une jointure est l'association d'objets d'une source de données avec des objets qui partagent un attribut commun dans une autre source de données, comme un produit ou un ID de contact.  Dans la programmation orientée objets, les relations entre les objets sont relativement faciles à explorer, car chaque objet possède un membre faisant référence à un autre objet. Dans les tables de base de données externe, toutefois, l'exploration des relations n'est pas aussi simple.  Les tables de base de données ne contiennent pas de relations intégrées. Dans ces cas particuliers, l'opération de jointure peut servir à faire correspondre des éléments de chaque source.  Par exemple, avec deux tables qui contiennent des informations sur les produits et des informations sur les ventes, vous pourriez utiliser une opération de jointure pour faire correspondre les informations sur les ventes et les produits pour la même commande.  
  
 L'infrastructure [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] fournit deux opérateurs de jointure, <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>. Ces opérateurs effectuent des *équijointures*, c'est\-à\-dire des jointures qui associent deux sources de données uniquement lorsque leurs clés sont identiques.  \(Par contraste, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] prend en charge des opérateurs de jointure autres que `equals`, comme l'opérateur `less than`.\)  
  
 En termes de base de données relationnelle, <xref:System.Linq.Enumerable.Join%2A> implémente une jointure interne.  Une jointure interne est un type de jointure dans lequel seuls les objets qui ont une correspondance dans le data set opposé sont retournés.  
  
 L'opérateur <xref:System.Linq.Enumerable.GroupJoin%2A> n'a aucun équivalent direct dans la terminologie de base de données relationnelle, mais il implémente un sur\-ensemble de jointures internes et de jointures externes gauches. Une jointure externe gauche est une jointure qui retourne chaque élément de la première collection \(gauche\), même si elle n'a pas d'éléments corrélés dans la deuxième collection.  
  
 Pour plus d'informations sur les jointures, voir [Join Operations](../../../../ocs/visual-basic/programming-guide/concepts/linq/join-operations.md).  
  
## Exemple  
 L'exemple suivant effectue une jointure traditionnelle des tables `SalesOrderHeader` et `SalesOrderDetail` de l'exemple de base de données AdventureWorks pour obtenir les commandes en ligne du mois d'août.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## Voir aussi  
 [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [Requêtes d'analyse unique](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)   
 [Interrogation de DataSets typés](../../../../docs/framework/data/adonet/querying-typed-datasets.md)   
 [Join Operations](../../../../ocs/visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Exemples de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)