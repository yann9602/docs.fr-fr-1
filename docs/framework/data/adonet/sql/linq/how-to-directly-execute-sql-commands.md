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
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="1b680-102">Comment : exécuter directement des commandes SQL</span><span class="sxs-lookup"><span data-stu-id="1b680-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="1b680-103">En considérant une connexion <xref:System.Data.Linq.DataContext>, vous pouvez utiliser <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> pour exécuter des commandes SQL qui ne retournent pas d'objets.</span><span class="sxs-lookup"><span data-stu-id="1b680-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b680-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b680-104">Example</span></span>  
 <span data-ttu-id="1b680-105">Dans l'exemple, SQL Server augmente de 1 la valeur de UnitPrice.</span><span class="sxs-lookup"><span data-stu-id="1b680-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1b680-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b680-106">See Also</span></span>  
 [<span data-ttu-id="1b680-107">Comment : exécuter directement des requêtes SQL</span><span class="sxs-lookup"><span data-stu-id="1b680-107">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 [<span data-ttu-id="1b680-108">Communication avec la base de données</span><span class="sxs-lookup"><span data-stu-id="1b680-108">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
