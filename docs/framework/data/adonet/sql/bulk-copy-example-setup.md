---
title: "Configuration de l&#39;exemple de copie en bloc | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Configuration de l&#39;exemple de copie en bloc
La classe <xref:System.Data.SqlClient.SqlBulkCopy> permet d'écrire des données uniquement dans des tables SQL Server.  Les exemples de code de cette rubrique utilisent l'exemple de base de données SQL Server, **AdventureWorks** .  Pour éviter de modifier les exemples de code des tables existantes, créez des tables et écrivez des données dans celles\-ci.  
  
 Les tables **BulkCopyDemoMatchingColumns** et **BulkCopyDemoDifferentColumns** reposent toutes deux sur la table **Production.Products** de la base de données **AdventureWorks**.  Dans les exemples de code qui utilisent ces tables, les données sont ajoutées à partir de la table **Production.Products** à l'un de ces exemples de table.  La table **BulkCopyDemoDifferentColumns** est utilisée lorsque l'exemple illustre la façon de mapper des colonnes à partir des données sources vers la table de destination ; **BulkCopyDemoMatchingColumns** est utilisé pour la plupart des autres exemples.  
  
 Quelques exemples de code montrent comment utiliser une classe <xref:System.Data.SqlClient.SqlBulkCopy> pour écrire plusieurs tables.  Pour ces exemples, les tables **BulkCopyDemoOrderHeader** et **BulkCopyDemoOrderDetail** sont utilisées comme tables de destination.  Ces tables reposent sur les tables **Sales.SalesOrderHeader** et **Sales.SalesOrderDetail** de la base de données **AdventureWorks**.  
  
> [!NOTE]
>  Les exemples de code **SqlBulkCopy** sont fournis uniquement pour illustrer la syntaxe de l'utilisation de **SqlBulkCopy**.   Si les tables sources et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact\-SQL `INSERT … SELECT` pour copier les données.  
  
## Configuration de table  
 Pour créer les tables nécessaires pour que les exemples de code s'exécutent correctement, vous devez exécuter les instructions Transact\-SQL suivantes dans une base de données SQL Server.  
  
```  
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED   
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED   
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED   
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED   
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## Voir aussi  
 [Opérations de copie en bloc dans SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)