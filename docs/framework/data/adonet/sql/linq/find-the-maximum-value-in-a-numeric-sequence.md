---
title: "Rechercher la valeur maximale dans une s&#233;quence num&#233;rique | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Rechercher la valeur maximale dans une s&#233;quence num&#233;rique
Utilisez l'opérateur <xref:System.Linq.Enumerable.Max%2A> pour rechercher la valeur la plus élevée dans une séquence de valeurs numériques.  
  
## Exemple  
 L'exemple suivant recherche la date la plus récente d'embauche parmi tous les employés.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## Exemple  
 L'exemple suivant recherche les unités dont le stock est le plus élevé parmi tous les produits.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `125`.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## Exemple  
 L'exemple suivant utilise Max pour rechercher les `Products` dont le prix unitaire est le plus élevé dans chaque catégorie.  Les résultats sont ensuite répertoriés par catégorie.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## Voir aussi  
 [Requêtes d'agrégation](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)   
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)