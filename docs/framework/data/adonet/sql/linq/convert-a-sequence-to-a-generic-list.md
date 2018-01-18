---
title: "Comment : convertir une séquence en liste générique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 066ea4d3c4232137fa6dbd758c8a3be1feec9e61
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="convert-a-sequence-to-a-generic-list"></a>Comment : convertir une séquence en liste générique
Utilisez <xref:System.Linq.Enumerable.ToList%2A> pour créer une liste générique à partir d'une séquence.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise <xref:System.Linq.Enumerable.ToList%2A> pour évaluer immédiatement une requête dans un <xref:System.Collections.Generic.List%601>générique.  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
