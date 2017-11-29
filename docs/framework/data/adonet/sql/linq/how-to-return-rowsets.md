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
# <a name="how-to-return-rowsets"></a><span data-ttu-id="82939-102">Comment : retourner des jeux de lignes</span><span class="sxs-lookup"><span data-stu-id="82939-102">How to: Return Rowsets</span></span>
<span data-ttu-id="82939-103">Cet exemple retourne un jeu de lignes de la base de données et inclut un paramètre d'entrée pour filtrer le résultat.</span><span class="sxs-lookup"><span data-stu-id="82939-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="82939-104">Lorsque vous exécutez une procédure stockée qui retourne un ensemble de lignes, vous utilisez un *résultat* classe qui stocke les valeurs retournées par la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="82939-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="82939-105">Pour plus d’informations, consultez [analyse de Code LINQ to SQL Source](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="82939-105">For more information, see [Analyzing LINQ to SQL Source Code](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82939-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="82939-106">Example</span></span>  
 <span data-ttu-id="82939-107">L'exemple suivant représente une procédure stockée qui retourne des lignes de clients et utilise un paramètre d'entrée pour retourner uniquement les lignes dont la ville du client est « London ».</span><span class="sxs-lookup"><span data-stu-id="82939-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="82939-108">L'exemple suppose l'existence d'une classe `CustomersByCityResult` dénombrable.</span><span class="sxs-lookup"><span data-stu-id="82939-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82939-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82939-109">See Also</span></span>  
 [<span data-ttu-id="82939-110">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="82939-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [<span data-ttu-id="82939-111">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="82939-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
