---
title: "Extraction des informations de schéma de base de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09a0ec444801d1fe2caccf9e25a68e3c6ae8f5c2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="8061c-102">Extraction des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="8061c-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="8061c-103">L'obtention des informations de schéma à partir d'une base de données est effectuée avec le processus de découverte de schéma.</span><span class="sxs-lookup"><span data-stu-id="8061c-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="8061c-104">La découverte de schéma permet aux applications de demander que les fournisseurs managés trouvent et retournent des informations sur le schéma de base de données, également appelé *métadonnées*, d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="8061c-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="8061c-105">Différents éléments de schéma de base de données tels que des tables, des colonnes et des procédures stockées, sont exposés à l’aide de collections de schémas.</span><span class="sxs-lookup"><span data-stu-id="8061c-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="8061c-106">Chaque collection de schémas contient une série d’informations de schéma spécifiques au fournisseur utilisé.</span><span class="sxs-lookup"><span data-stu-id="8061c-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="8061c-107">Chacune de l’implémentation de fournisseurs managés .NET Framework le **GetSchema** méthode dans le **connexion** classe et les informations de schéma qui sont retournées à partir de la **GetSchema**méthode se présente sous la forme d’un <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="8061c-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="8061c-108">Le **GetSchema** méthode est une méthode surchargée qui fournit des paramètres facultatifs pour spécifier la collection de schémas à retourner et restreindre la quantité d’informations retournées.</span><span class="sxs-lookup"><span data-stu-id="8061c-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="8061c-109">Les fournisseurs de données .NET Framework pour OLE DB, ODBC, Oracle et SqlClient fournissent un **GetSchemaTable** méthode qui retourne un objet DataTable décrivant les métadonnées de colonne de la **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="8061c-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="8061c-110">Le fournisseur de données .NET Framework pour OLE DB expose également des informations de schéma à l'aide de la méthode <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> de l'objet <xref:System.Data.OleDb.OleDbConnection>.</span><span class="sxs-lookup"><span data-stu-id="8061c-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="8061c-111">En tant qu’arguments, **GetOleDbSchemaTable** prend un <xref:System.Data.OleDb.OleDbSchemaGuid> qui identifie les informations de schéma à retourner et un tableau de restrictions sur ces colonnes retournées.</span><span class="sxs-lookup"><span data-stu-id="8061c-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="8061c-112">**GetOleDbSchemaTable** retourne un <xref:System.Data.DataTable> rempli avec les informations de schéma demandé.</span><span class="sxs-lookup"><span data-stu-id="8061c-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8061c-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8061c-113">In This Section</span></span>  
 [<span data-ttu-id="8061c-114">Collections GetSchema et Schema</span><span class="sxs-lookup"><span data-stu-id="8061c-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="8061c-115">Décrit la **GetSchema** méthode et comment il peut être utilisé pour extraire et restreindre les informations de schéma à partir d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="8061c-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="8061c-116">Restrictions de schéma</span><span class="sxs-lookup"><span data-stu-id="8061c-116">Schema Restrictions</span></span>  
 <span data-ttu-id="8061c-117">Décrit les restrictions de schéma qui peuvent être utilisées avec **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="8061c-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="8061c-118">Collections de schémas courantes</span><span class="sxs-lookup"><span data-stu-id="8061c-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="8061c-119">Décrit toutes les collections de schémas communes prises en charge par tous les fournisseurs .NET Framework managés.</span><span class="sxs-lookup"><span data-stu-id="8061c-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="8061c-120">Collections de schémas SQL Server</span><span class="sxs-lookup"><span data-stu-id="8061c-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="8061c-121">Décrit la collection de schémas prise en charge par le fournisseur .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8061c-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="8061c-122">Collections de schémas Oracle</span><span class="sxs-lookup"><span data-stu-id="8061c-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="8061c-123">Décrit la collection de schémas prise en charge par le fournisseur .NET Framework pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="8061c-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="8061c-124">Collections de schémas ODBC</span><span class="sxs-lookup"><span data-stu-id="8061c-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="8061c-125">Décrit les collections de schémas pour les pilotes ODBC.</span><span class="sxs-lookup"><span data-stu-id="8061c-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="8061c-126">Collections de schémas OLE DB</span><span class="sxs-lookup"><span data-stu-id="8061c-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="8061c-127">Décrit les collections de schémas pour les fournisseurs OLE DB.</span><span class="sxs-lookup"><span data-stu-id="8061c-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8061c-128">Référence</span><span class="sxs-lookup"><span data-stu-id="8061c-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="8061c-129">Décrit la **GetSchema** méthode de la <xref:System.Data.Common.DbConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="8061c-130">Décrit la **GetSchema** méthode de la <xref:System.Data.Odbc.OdbcConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="8061c-131">Décrit la **GetSchema** méthode de la <xref:System.Data.OleDb.OleDbConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="8061c-132">Décrit la **GetSchema** méthode de la <xref:System.Data.OracleClient.OracleConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="8061c-133">Décrit la **GetSchema** méthode de la <xref:System.Data.SqlClient.SqlConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="8061c-134">Décrit la **GetSchemaTable** méthode de la <xref:System.Data.Common.DbDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="8061c-135">Décrit la **GetSchemaTable** méthode de la <xref:System.Data.Odbc.OdbcDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="8061c-136">Décrit la **GetSchemaTable** méthode de la <xref:System.Data.OleDb.OleDbDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="8061c-137">Décrit la **GetSchemaTable** méthode de la <xref:System.Data.OracleClient.OracleDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="8061c-138">Décrit la **GetSchemaTable** méthode de la <xref:System.Data.SqlClient.SqlDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="8061c-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8061c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8061c-139">See Also</span></span>  
 [<span data-ttu-id="8061c-140">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8061c-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="8061c-141">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="8061c-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
