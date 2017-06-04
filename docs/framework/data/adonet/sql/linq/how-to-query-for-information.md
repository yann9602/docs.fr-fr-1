---
title: "Proc&#233;dure&#160;: demander des informations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: demander des informations
Les requêtes effectuées dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilisent la même syntaxe que les requêtes effectuées dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  La seule différence est que les objets référencés dans les requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sont mappés aux éléments d'une base de données.  Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement.  
  
 Certaines fonctionnalités de requêtes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] peuvent nécessiter une attention particulière dans les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  Pour plus d'informations, consultez [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).  
  
## Exemple  
 La requête suivante demande une liste de clients de Londres.  Dans cet exemple, `Customers` est une table de l'exemple de base de données Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## Voir aussi  
 [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)   
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [Interrogation de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)