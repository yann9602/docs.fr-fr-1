---
title: "Proc&#233;dure&#160;: retourner des jeux de lignes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: retourner des jeux de lignes
Cet exemple retourne un jeu de lignes de la base de données et inclut un paramètre d'entrée pour filtrer le résultat.  
  
 Lorsque vous exécutez une procédure stockée qui retourne un jeu de lignes, vous utilisez une classe de *résultats* qui stocke les valeurs retournées par la procédure stockée.  Pour plus d'informations, consultez [Analyse du code source LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).  
  
## Exemple  
 L'exemple suivant représente une procédure stockée qui retourne des lignes de clients et utilise un paramètre d'entrée pour retourner uniquement les lignes dont la ville du client est « London ».  L'exemple suppose l'existence d'une classe `CustomersByCityResult` dénombrable.  
  
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
  
## Voir aussi  
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)   
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)