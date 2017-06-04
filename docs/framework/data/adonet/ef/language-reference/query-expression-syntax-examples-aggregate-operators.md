---
title: "Exemples de syntaxe d&#39;expression de requ&#234;te&#160;: op&#233;rateurs d&#39;agr&#233;gation | Microsoft Docs"
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
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Exemples de syntaxe d&#39;expression de requ&#234;te&#160;: op&#233;rateurs d&#39;agr&#233;gation
Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A> et <xref:System.Linq.Enumerable.Sum%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832) en utilisant la syntaxe d'expression de requête.  Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.  
  
 Les exemples de cette rubrique utilisent les instructions `using`\/`Imports` suivantes :  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## Average  
  
### Exemple  
 L'exemple ci\-dessous utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour trouver le prix moyen courant des produits de chaque style.  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### Exemple  
 L'exemple suivant utilise <xref:System.Linq.Enumerable.Average%2A> pour obtenir le montant total moyen dû de chaque ID de contact.  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### Exemple  
 L'exemple ci\-dessous utilise <xref:System.Linq.Enumerable.Average%2A> pour obtenir les commandes présentant le montant total moyen dû pour chaque ID de contact.  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## Nombre  
  
### Exemple  
 L'exemple suivant utilise <xref:System.Linq.Enumerable.Count%2A> pour retourner la liste des ID de contact et du nombre de commandes de chaque ID de contact.  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### Exemple  
 L'exemple suivant regroupe les produits par couleur et utilise <xref:System.Linq.Enumerable.Count%2A> pour retourner le nombre de produits dans chaque groupe de couleur.  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## Max  
  
### Exemple  
 L'exemple ci\-dessous utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir le montant total dû le plus élevé pour chaque ID de contact.  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### Exemple  
 L'exemple ci\-dessous utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir les commandes présentant le montant total dû le plus élevé pour chaque ID de contact.  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## Min  
  
### Exemple  
 L'exemple ci\-dessous utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir le montant total dû le plus bas pour chaque ID de contact.  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### Exemple  
 L'exemple ci\-dessous utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir les commandes présentant le montant total dû le plus bas pour chaque ID de contact.  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## Sum  
  
### Exemple  
 L'exemple ci\-dessous utilise la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir le montant total dû pour chaque ID de contact.  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## Voir aussi  
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)