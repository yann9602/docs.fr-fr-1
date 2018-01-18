---
title: "Comment : réutiliser une connexion entre une commande ADO.NET et un DataContext"
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
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 196b3c8735168ea935aa1a0d3917dd34b2aa390f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Comment : réutiliser une connexion entre une commande ADO.NET et un DataContext
Étant donné que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fait partie de la [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] famille de technologies et est basée sur les services fournis par [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], vous pouvez réutiliser une connexion entre un [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] commande et un <xref:System.Data.Linq.DataContext>.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant indique comment réutiliser la même connexion entre une commande [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] et le <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [ADO.NET et LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)  
 [Communication avec la base de données](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
