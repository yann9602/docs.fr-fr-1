---
title: "Comment : retourner la différence définie entre deux séquences"
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
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 120cc6d08d02fd33510903242c44feae3f8ec5c0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="return-the-set-difference-between-two-sequences"></a>Comment : retourner la différence définie entre deux séquences
Utilisez l'opérateur <xref:System.Linq.Queryable.Except%2A> pour retourner la différence définie entre deux séquences.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise <xref:System.Linq.Queryable.Except%2A> pour retourner une séquence de tous les pays dans lesquels résident des `Customers` mais dans lesquels aucun des `Employees` ne réside.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], l'opération <xref:System.Linq.Queryable.Except%2A> est correctement définie sur les jeux uniquement. La sémantique pour les multijeux n'est pas définie.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Traduction des opérateurs de requête standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
