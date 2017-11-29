---
title: "Comment : exécuter directement des commandes SQL"
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
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: feffa98fa890856db579553df6624fef1897b173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-directly-execute-sql-commands"></a>Comment : exécuter directement des commandes SQL
En considérant une connexion <xref:System.Data.Linq.DataContext>, vous pouvez utiliser <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> pour exécuter des commandes SQL qui ne retournent pas d'objets.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple, SQL Server augmente de 1 la valeur de UnitPrice.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : exécuter directement des requêtes SQL](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 [Communication avec la base de données](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
