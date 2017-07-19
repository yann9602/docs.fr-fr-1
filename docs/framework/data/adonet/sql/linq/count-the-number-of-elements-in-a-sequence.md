---
title: "D&#233;nombrer les &#233;l&#233;ments d&#39;une s&#233;quence | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# D&#233;nombrer les &#233;l&#233;ments d&#39;une s&#233;quence
Utilisez l'opérateur <xref:System.Linq.Enumerable.Count%2A> pour compter le nombre d'éléments dans une séquence.  
  
 L'exécution de cette requête sur la base de données Northwind génère le résultat suivant : `91`.  
  
## Exemple  
 L'exemple suivant compte le nombre de `Customers` dans la base de données.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## Exemple  
 L'exemple suivant compte le nombre de produits dans la base de données qui n'ont pas été arrêtés.  
  
 L'exécution de cet exemple sur la base de données Northwind génère le résultat suivant : `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## Voir aussi  
 [Requêtes d'agrégation](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)   
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)