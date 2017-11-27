---
title: DataAdapters et DataReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e7a0af0b5fabdfacfcc825258242868b0fbb513
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="90ecc-102">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="90ecc-102">DataAdapters and DataReaders</span></span>
<span data-ttu-id="90ecc-103">Vous pouvez utiliser ADO.NET **DataReader** pour récupérer un flux de données en lecture seule et avant uniquement à partir d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="90ecc-103">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="90ecc-104">Les résultats que la requête s’exécute et sont stockés dans la mémoire tampon de réseau sur le client jusqu'à ce que vous les demandez à l’aide de la **en lecture** méthode de la **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="90ecc-104">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="90ecc-105">À l’aide de la **DataReader** peut augmenter les performances de l’application en extrayant les données dès qu’elles sont disponibles et (par défaut) ne stocker qu’une seule ligne à la fois dans la mémoire, ce qui réduit la surcharge du système.</span><span class="sxs-lookup"><span data-stu-id="90ecc-105">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="90ecc-106">Un objet <xref:System.Data.Common.DataAdapter> est utilisé pour extraire les données d'une source de données et remplir les tables d'un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="90ecc-106">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="90ecc-107">Le `DataAdapter` répercute également les modifications apportées au `DataSet` dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="90ecc-107">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="90ecc-108">`DataAdapter` utilise l'objet `Connection` du fournisseur de données .NET Framework pour se connecter à une source de données et les objets `Command` pour extraire les données de la source et y répercuter les modifications.</span><span class="sxs-lookup"><span data-stu-id="90ecc-108">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="90ecc-109">Chaque fournisseur de données .NET Framework inclus dans le .NET Framework comprend un objet <xref:System.Data.Common.DbDataReader> et un objet <xref:System.Data.Common.DbDataAdapter> : le fournisseur de données .NET Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbDataReader> et un objet <xref:System.Data.OleDb.OleDbDataAdapter>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlDataReader> et un objet <xref:System.Data.SqlClient.SqlDataAdapter>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcDataReader> et un objet <xref:System.Data.Odbc.OdbcDataAdapter>, tandis que le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleDataReader> et un objet <xref:System.Data.OracleClient.OracleDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="90ecc-109">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90ecc-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="90ecc-110">In This Section</span></span>  
 [<span data-ttu-id="90ecc-111">La récupération des données à l’aide d’un DataReader</span><span class="sxs-lookup"><span data-stu-id="90ecc-111">Retrieving Data Using a DataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="90ecc-112">Décrit le **DataReader** objet et comment l’utiliser pour retourner un flux de résultats à partir d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="90ecc-112">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="90ecc-113">Remplissage d’un DataSet à partir d’un DataAdapter</span><span class="sxs-lookup"><span data-stu-id="90ecc-113">Populating a DataSet from a DataAdapter</span></span>](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="90ecc-114">Explique comment remplir un `DataSet` avec des tables, des colonnes et des lignes au moyen d'un `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="90ecc-114">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="90ecc-115">Paramètres DataAdapter</span><span class="sxs-lookup"><span data-stu-id="90ecc-115">DataAdapter Parameters</span></span>](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 <span data-ttu-id="90ecc-116">Décrit l'utilisation des paramètres avec les propriétés de commande d'un `DataAdapter`, y compris le mappage du contenu d'une colonne d'un `DataSet` à un paramètre de commande.</span><span class="sxs-lookup"><span data-stu-id="90ecc-116">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="90ecc-117">Ajout de contraintes existantes à un DataSet</span><span class="sxs-lookup"><span data-stu-id="90ecc-117">Adding Existing Constraints to a DataSet</span></span>](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="90ecc-118">Décrit comment ajouter des contraintes existantes à un `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="90ecc-118">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="90ecc-119">Mappages DataAdapter DataTable et DataColumn</span><span class="sxs-lookup"><span data-stu-id="90ecc-119">DataAdapter DataTable and DataColumn Mappings</span></span>](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="90ecc-120">Décrit comment configurer des `DataTableMappings` et des `ColumnMappings` pour un `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="90ecc-120">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="90ecc-121">La pagination des résultats d’une requête</span><span class="sxs-lookup"><span data-stu-id="90ecc-121">Paging Through a Query Result</span></span>](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 <span data-ttu-id="90ecc-122">Propose un exemple de visualisation des résultats d'une requête sous forme de pages de données.</span><span class="sxs-lookup"><span data-stu-id="90ecc-122">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="90ecc-123">Mise à jour de sources de données avec des DataAdapters</span><span class="sxs-lookup"><span data-stu-id="90ecc-123">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="90ecc-124">Explique comment utiliser un `DataAdapter` pour répercuter les modifications apportées à un objet `DataSet` dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="90ecc-124">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="90ecc-125">Gestion des événements DataAdapter</span><span class="sxs-lookup"><span data-stu-id="90ecc-125">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 <span data-ttu-id="90ecc-126">Décrit les événements `DataAdapter` et comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="90ecc-126">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="90ecc-127">Exécution d’opérations de traitement par lots à l’aide de DataAdapters</span><span class="sxs-lookup"><span data-stu-id="90ecc-127">Performing Batch Operations Using DataAdapters</span></span>](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="90ecc-128">Décrit l'amélioration des performances de l'application en réduisant le nombre d'allers-retours vers SQL Server lors de l'application de mises à jour à partir du `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="90ecc-128">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ecc-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90ecc-129">See Also</span></span>  
 [<span data-ttu-id="90ecc-130">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="90ecc-130">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="90ecc-131">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="90ecc-131">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="90ecc-132">Transactions et accès simultané</span><span class="sxs-lookup"><span data-stu-id="90ecc-132">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="90ecc-133">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="90ecc-133">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="90ecc-134">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="90ecc-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
