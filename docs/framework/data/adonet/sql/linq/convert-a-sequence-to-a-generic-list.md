---
title: "Convertir une s&#233;quence en liste g&#233;n&#233;rique | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Convertir une s&#233;quence en liste g&#233;n&#233;rique
Utilisez <xref:System.Linq.Enumerable.ToList%2A> pour créer une liste générique à partir d'une séquence.  
  
## Exemple  
 L'exemple suivant utilise <xref:System.Linq.Enumerable.ToList%2A> pour évaluer immédiatement une requête dans un <xref:System.Collections.Generic.List%601>générique.  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)