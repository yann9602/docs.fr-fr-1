---
title: "Exemples de syntaxe d&#39;expression de requ&#234;te&#160;: regroupement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Exemples de syntaxe d&#39;expression de requ&#234;te&#160;: regroupement
Les exemples de cette rubrique montrent comment utiliser la méthode `GroupBy` pour interroger le [modèle de vente AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832) à l'aide de la syntaxe d'expression de requête.  Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.  
  
 Les exemples de cette rubrique utilisent les instructions `using`\/`Imports` suivantes :  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## Exemple  
 L'exemple ci\-dessous retourne des objets `Address` regroupés selon le code postal.  Les résultats sont projetés dans un type anonyme.  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## Exemple  
 L'exemple ci\-dessous retourne des objets `Contact` regroupés selon la première lettre du nom de famille des contacts.  Les résultats sont également triés selon la première lettre du nom de famille et projetés dans un type anonyme.  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## Exemple  
 L'exemple ci\-dessous retourne des objets `SalesOrderHeader` regroupés par code client \(Customer ID\).  Le nombre de ventes réalisées pour chaque client est également retourné.  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## Voir aussi  
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)