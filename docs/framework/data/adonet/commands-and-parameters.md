---
title: "Commandes et paramètres"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1086a8775c2bc478c91d74656cfbebc5408727ce
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="commands-and-parameters"></a><span data-ttu-id="a00a0-102">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="a00a0-102">Commands and Parameters</span></span>
<span data-ttu-id="a00a0-103">Après avoir établi une connexion à une source de données, vous pouvez exécuter des commandes et retourner les résultats de la source de données à l'aide d'un objet <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="a00a0-103">After establishing a connection to a data source, you can execute commands and return results from the data source using a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="a00a0-104">Vous pouvez créer une commande en utilisant l'un des constructeurs de commande du fournisseur de données .NET Framework avec lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="a00a0-104">You can create a command using one of the command constructors for the .NET Framework data provider you are working with.</span></span> <span data-ttu-id="a00a0-105">Les constructeurs acceptent des arguments optionnels, comme une instruction SQL à exécuter au niveau de la source de données, un objet <xref:System.Data.Common.DbConnection> ou un objet <xref:System.Data.Common.DbTransaction>.</span><span class="sxs-lookup"><span data-stu-id="a00a0-105">Constructors can take optional arguments, such as an SQL statement to execute at the data source, a <xref:System.Data.Common.DbConnection> object, or a <xref:System.Data.Common.DbTransaction> object.</span></span> <span data-ttu-id="a00a0-106">Vous pouvez également configurer ces objets en tant que propriétés de la commande.</span><span class="sxs-lookup"><span data-stu-id="a00a0-106">You can also configure those objects as properties of the command.</span></span> <span data-ttu-id="a00a0-107">Vous pouvez aussi créer une commande pour une connexion particulière à l'aide de la méthode <xref:System.Data.Common.DbConnection.CreateCommand%2A> d'un objet `DbConnection`.</span><span class="sxs-lookup"><span data-stu-id="a00a0-107">You can also create a command for a particular connection using the <xref:System.Data.Common.DbConnection.CreateCommand%2A> method of a `DbConnection` object.</span></span> <span data-ttu-id="a00a0-108">L'instruction SQL en cours d'exécution par la commande peut être configurée à l'aide de la propriété <xref:System.Data.Common.DbCommand.CommandText%2A>.</span><span class="sxs-lookup"><span data-stu-id="a00a0-108">The SQL statement being executed by the command can be configured using the <xref:System.Data.Common.DbCommand.CommandText%2A> property.</span></span>  
  
 <span data-ttu-id="a00a0-109">Chaque fournisseur de données .NET Framework inclus dans le .NET Framework possède un objet `Command`.</span><span class="sxs-lookup"><span data-stu-id="a00a0-109">Each .NET Framework data provider included with the .NET Framework has a `Command` object.</span></span> <span data-ttu-id="a00a0-110">Le fournisseur de données .NET Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbCommand>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlCommand>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcCommand> et le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="a00a0-110">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a00a0-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a00a0-111">In This Section</span></span>  
 [<span data-ttu-id="a00a0-112">Exécution d’une commande</span><span class="sxs-lookup"><span data-stu-id="a00a0-112">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 <span data-ttu-id="a00a0-113">Décrit l'objet `Command` et son utilisation pour exécuter des requêtes et des commandes sur une source de données.</span><span class="sxs-lookup"><span data-stu-id="a00a0-113">Describes the ADO.NET `Command` object and how to use it to execute queries and commands against a data source.</span></span>  
  
 [<span data-ttu-id="a00a0-114">Configuration des paramètres et des types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="a00a0-114">Configuring Parameters and Parameter Data Types</span></span>](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="a00a0-115">Décrit l'utilisation des paramètres `Command`, y compris la direction, les types de données et la syntaxe des paramètres.</span><span class="sxs-lookup"><span data-stu-id="a00a0-115">Describes working with `Command` parameters, including direction, data types, and parameter syntax.</span></span>  
  
 [<span data-ttu-id="a00a0-116">Génération de commandes avec CommandBuilders</span><span class="sxs-lookup"><span data-stu-id="a00a0-116">Generating Commands with CommandBuilders</span></span>](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 <span data-ttu-id="a00a0-117">Décrit l'utilisation de générateurs de commande pour générer automatiquement les commandes INSERT, UPDATE et DELETE pour un `DataAdapter` ayant une commande SELECT d'analyse unique.</span><span class="sxs-lookup"><span data-stu-id="a00a0-117">Describes how to use command builders to automatically generate INSERT, UPDATE, and DELETE commands for a `DataAdapter` that has a single-table SELECT command.</span></span>  
  
 [<span data-ttu-id="a00a0-118">Obtention d’une valeur unique à partir d’une base de données</span><span class="sxs-lookup"><span data-stu-id="a00a0-118">Obtaining a Single Value from a Database</span></span>](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 <span data-ttu-id="a00a0-119">Décrit comment utiliser la méthode `ExecuteScalar` d'un objet `Command` pour retourner une valeur unique à partir d'une requête de base de données.</span><span class="sxs-lookup"><span data-stu-id="a00a0-119">Describes how to use the `ExecuteScalar` method of a `Command` object to return a single value from a database query.</span></span>  
  
 [<span data-ttu-id="a00a0-120">Utilisation des commandes pour modifier les données</span><span class="sxs-lookup"><span data-stu-id="a00a0-120">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 <span data-ttu-id="a00a0-121">Explique comment utiliser un fournisseur de données pour exécuter des procédures stockées ou des instructions DDL (Data Definition Language).</span><span class="sxs-lookup"><span data-stu-id="a00a0-121">Describes how to use a data provider to execute stored procedures or data definition language (DDL) statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00a0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a00a0-122">See Also</span></span>  
 [<span data-ttu-id="a00a0-123">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="a00a0-123">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="a00a0-124">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="a00a0-124">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="a00a0-125">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="a00a0-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="a00a0-126">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="a00a0-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
