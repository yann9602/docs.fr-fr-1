---
title: "Formuler des projections | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Formuler des projections
Les exemples suivants expliquent comment l'instruction `select` dans C\# et l'instruction `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] peuvent être associées à d'autres fonctionnalités pour former des projections de requête.  
  
## Exemple  
 L'exemple suivant utilise la clause `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] \(clause `select` dans C\#\) pour retourner une séquence de noms de contact pour `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## Exemple  
 L'exemple suivant utilise la clause `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] \(clause `select` dans C\#\) et des *types anonymes* pour retourner une séquence de noms de contact et de numéros de téléphone pour `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## Exemple  
 L'exemple suivant utilise la clause `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] \(clause `select` dans C\#\) et des *types anonymes* pour retourner une séquence de noms de contact et de numéros de téléphone pour les employés.  Les champs `FirstName` et `LastName` sont combinés en un champ unique \(`Name`\) et le champ `HomePhone` est renommé `Phone` dans la séquence obtenue.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## Exemple  
 L'exemple suivant utilise la clause `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] \(clause `select` dans C\#\) et des *types anonymes* pour retourner une séquence de tous les `ProductID` et une valeur calculée nommée `HalfPrice`.  Cette valeur correspond à `UnitPrice` divisé par 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## Exemple  
 L'exemple suivant utilise la clause `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] \(clause `select` dans C\#\) et une *instruction conditionnelle* pour retourner une séquence de noms et de disponibilités de produits.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## Exemple  
 L'exemple suivant utilise une clause `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] \(clause `select` dans C\#\) et un *type connu* \(Name\) pour retourner une séquence des noms d'employés.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## Exemple  
 L'exemple suivant utilise `Select` et `Where` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] \(`select` et `where` dans C\#\) pour retourner une *séquence filtrée* de noms de contact pour les clients de Londres.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## Exemple  
 L'exemple suivant utilise une clause `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] \(clause `select` dans C\#\) et des *types anonymes* pour retourner un *sous\-ensemble spécifique* des données concernant les clients.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## Exemple  
 L'exemple suivant utilise des requêtes imbriquées pour retourner les résultats suivants :  
  
-   Séquence de toutes les commandes et des `OrderID` correspondants.  
  
-   Sous\-séquence des éléments dans la commande pour laquelle il existe une remise.  
  
-   Montant enregistré si le coût d'expédition n'est pas inclus.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)