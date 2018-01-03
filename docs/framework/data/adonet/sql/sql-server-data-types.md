---
title: "Types de données SQL Server et ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fd3982cf8eeeb88a162e77a3ef4b9d6e75e19fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="3b0ba-102">Types de données SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3b0ba-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="3b0ba-103">SQL Server et le .NET Framework sont basés sur des systèmes de types différents, ce qui peut entraîner une perte de données potentielle.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="3b0ba-104">Afin de protéger l'intégrité des données, le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>) fournit des méthodes d'accesseur typé pour utiliser les données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="3b0ba-105">Vous pouvez également utiliser les énumérations des classes <xref:System.Data.SqlDbType> pour spécifier les types de données <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="3b0ba-106">Pour plus d’informations et une table qui décrit les données entre SQL Server et les types de données .NET Framework, les mappages de type, consultez [mappages de Type de données SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="3b0ba-106">For more information and a table that that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="3b0ba-107">SQL Server 2008 introduit de nouveaux types de données conçus pour répondre aux besoins des entreprises en termes d'utilisation des données de date et d'heure, structurées, semi-structurées et non structurées.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="3b0ba-108">Ceux-ci sont décrits dans la documentation en ligne de SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="3b0ba-109">Les types de données SQL Server disponibles pour votre application varient en fonction de la version de SQL Server utilisée.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="3b0ba-110">Pour plus d'informations, consultez la version appropriée de la documentation en ligne de SQL Server dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="3b0ba-111">**Documentation en ligne de SQL Server**</span><span class="sxs-lookup"><span data-stu-id="3b0ba-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="3b0ba-112">Types de données (moteur de base de données)</span><span class="sxs-lookup"><span data-stu-id="3b0ba-112">Data Types (Database Engine)</span></span>](http://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="3b0ba-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3b0ba-113">In This Section</span></span>  
 [<span data-ttu-id="3b0ba-114">SqlTypes et le DataSet</span><span class="sxs-lookup"><span data-stu-id="3b0ba-114">SqlTypes and the DataSet</span></span>](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 <span data-ttu-id="3b0ba-115">Décrit la prise en charge de type pour `SqlTypes` dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="3b0ba-116">Gestion des valeurs null</span><span class="sxs-lookup"><span data-stu-id="3b0ba-116">Handling Null Values</span></span>](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 <span data-ttu-id="3b0ba-117">Montre comment utiliser des valeurs null et la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="3b0ba-118">Comparaison du GUID et des valeurs uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="3b0ba-118">Comparing GUID and uniqueidentifier Values</span></span>](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="3b0ba-119">Montre comment utiliser des valeurs GUID et d'identificateur unique dans SQL Server et le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="3b0ba-120">Données de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="3b0ba-120">Date and Time Data</span></span>](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 <span data-ttu-id="3b0ba-121">Explique comment utiliser les nouveaux types de données de date et d'heure introduits dans SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="3b0ba-122">Grands types définis par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="3b0ba-122">Large UDTs</span></span>](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 <span data-ttu-id="3b0ba-123">Montre comment récupérer des données des UDT volumineux introduits dans SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="3b0ba-124">Données XML dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="3b0ba-124">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 <span data-ttu-id="3b0ba-125">Décrit comment utiliser des données XML récupérées dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3b0ba-126">Référence</span><span class="sxs-lookup"><span data-stu-id="3b0ba-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="3b0ba-127">Décrit la classe `DataSet` et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="3b0ba-128">Décrit l'espace de noms `SqlTypes` et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="3b0ba-129">Décrit l'énumération `SqlDbType` et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="3b0ba-130">Décrit l'énumération `DbType` et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="3b0ba-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0ba-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b0ba-131">See Also</span></span>  
 [<span data-ttu-id="3b0ba-132">Mappages de types de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="3b0ba-132">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="3b0ba-133">Configuration des paramètres et des types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="3b0ba-133">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="3b0ba-134">Paramètres table</span><span class="sxs-lookup"><span data-stu-id="3b0ba-134">Table-Valued Parameters</span></span>](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [<span data-ttu-id="3b0ba-135">Données binaires et de valeur élevée SQL Server</span><span class="sxs-lookup"><span data-stu-id="3b0ba-135">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="3b0ba-136">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="3b0ba-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
