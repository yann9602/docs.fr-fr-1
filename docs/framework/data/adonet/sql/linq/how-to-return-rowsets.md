---
title: "Comment : retourner des jeux de lignes"
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
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 24211e82633e41256a8c801000c4d3e17d9d8612
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-rowsets"></a>Comment : retourner des jeux de lignes
Cet exemple retourne un jeu de lignes de la base de données et inclut un paramètre d'entrée pour filtrer le résultat.  
  
 Lorsque vous exécutez une procédure stockée qui retourne un ensemble de lignes, vous utilisez un *résultat* classe qui stocke les valeurs retournées par la procédure stockée. Pour plus d’informations, consultez [analyse de Code LINQ to SQL Source](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant représente une procédure stockée qui retourne des lignes de clients et utilise un paramètre d'entrée pour retourner uniquement les lignes dont la ville du client est « London ». L'exemple suppose l'existence d'une classe `CustomersByCityResult` dénombrable.  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
