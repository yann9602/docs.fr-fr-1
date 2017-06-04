---
title: "Retourner l&#39;union d&#233;finie de deux s&#233;quences | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Retourner l&#39;union d&#233;finie de deux s&#233;quences
Utilisez l'opérateur <xref:System.Linq.Queryable.Union%2A> pour retourner l'union définie de deux séquences.  
  
## Exemple  
 Cet exemple utilise <xref:System.Linq.Queryable.Union%2A> pour retourner une séquence de tous les pays comportant des `Customers` ou des `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], l'opérateur <xref:System.Linq.Queryable.Union%2A> est défini pour des multijeux comme la concaténation non ordonnée des multijeux \(le résultat de la clause `UNION ALL` dans SQL\).  
  
## Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)   
 [Traduction des opérateurs de requête standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)