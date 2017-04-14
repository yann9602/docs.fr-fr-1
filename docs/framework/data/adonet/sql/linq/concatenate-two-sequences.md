---
title: "Concat&#233;ner deux s&#233;quences | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Concat&#233;ner deux s&#233;quences
Utilisez l'opérateur <xref:System.Linq.Queryable.Concat%2A> pour concaténer deux séquences.  
  
 L'opérateur <xref:System.Linq.Queryable.Concat%2A> est défini pour les multijeux ordonnés pour lesquels l'ordre du destinataire et de l'argument est identique.  
  
 Le classement dans SQL est la dernière étape avant la génération des résultats.  Par conséquent, l'opérateur <xref:System.Linq.Queryable.Concat%2A> est implémenté en utilisant `UNION ALL` et ne conserve pas l'ordre de ses arguments.  Pour vérifier que le classement est correct dans les résultats, assurez\-vous de classer les résultats explicitement.  
  
## Exemple  
 Cet exemple utilise <xref:System.Linq.Queryable.Concat%2A> pour retourner une séquence de tous les numéros de téléphone et de télécopie de `Customer` et `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## Exemple  
 Cet exemple utilise <xref:System.Linq.Queryable.Concat%2A> pour retourner une séquence de tous les mappages de nom et de numéro de téléphone de `Customer` et `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)   
 [Traduction des opérateurs de requête standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)