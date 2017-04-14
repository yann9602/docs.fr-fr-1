---
title: "DataAdapters et DataReaders | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataAdapters et DataReaders
Vous pouvez utiliser le **DataReader** ADO.NET pour extraire d'une base de données un flux de données en lecture seule et avant uniquement.  Les résultats sont retournés pendant que la requête s'exécute et stockés dans la mémoire tampon de réseau sur le client jusqu'à ce que vous les demandiez au moyen de la méthode **Read** de **DataReader**.  L'utilisation du **DataReader** peut augmenter les performances de l'application en extrayant les données dès qu'elles sont disponibles, puis en ne stockant \(par défaut\) qu'une seule ligne à la fois dans la mémoire, ce qui réduit la charge du système.  
  
 Un objet <xref:System.Data.Common.DataAdapter> est utilisé pour extraire les données d'une source de données et remplir les tables d'un <xref:System.Data.DataSet>.  Le `DataAdapter` répercute également les modifications apportées au `DataSet` dans la source de données.  `DataAdapter` utilise l'objet `Connection` du fournisseur de données .NET Framework pour se connecter à une source de données et les objets `Command` pour extraire les données de la source et y répercuter les modifications.  
  
 Chaque fournisseur de données .NET Framework inclus dans le .NET Framework comprend un objet <xref:System.Data.Common.DbDataReader> et un objet <xref:System.Data.Common.DbDataAdapter> : le fournisseur de données .NET Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbDataReader> et un objet <xref:System.Data.OleDb.OleDbDataAdapter>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlDataReader> et un objet <xref:System.Data.SqlClient.SqlDataAdapter>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcDataReader> et un objet <xref:System.Data.Odbc.OdbcDataAdapter>, tandis que le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleDataReader> et un objet <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
## Dans cette section  
 [Extraction de données à l'aide d'un DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 Décrit l'objet **DataReader** ADO.NET et son utilisation pour retourner un flux de résultats à partir d'une source de données.  
  
 [Remplissage d'un DataSet à partir d'un DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Explique comment remplir un `DataSet` avec des tables, des colonnes et des lignes au moyen d'un `DataAdapter`.  
  
 [Paramètres de DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Décrit l'utilisation des paramètres avec les propriétés de commande d'un `DataAdapter`, y compris le mappage du contenu d'une colonne d'un `DataSet` à un paramètre de commande.  
  
 [Ajout de contraintes existantes à un DataSet](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Décrit comment ajouter des contraintes existantes à un `DataSet`.  
  
 [Mappages de DataAdapter DataTable et DataColumn](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 Décrit comment configurer des `DataTableMappings` et des `ColumnMappings` pour un `DataAdapter`.  
  
 [Affichage des résultats d'une requête sous forme de pages](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Propose un exemple de visualisation des résultats d'une requête sous forme de pages de données.  
  
 [Mise à jour de sources de données avec des DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Explique comment utiliser un `DataAdapter` pour répercuter les modifications apportées à un objet `DataSet` dans la base de données.  
  
 [Gestion des événements DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 Décrit les événements `DataAdapter` et comment les utiliser.  
  
 [Exécution de traitements par lots à l'aide de DataAdapters](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 Décrit l'amélioration des performances de l'application en réduisant le nombre d'allers\-retours vers SQL Server lors de l'application de mises à jour à partir du `DataSet`.  
  
## Voir aussi  
 [Connexion à une source de données](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)   
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [Transactions et concurrence](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)   
 [Objets DataSet, DataTable et DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)