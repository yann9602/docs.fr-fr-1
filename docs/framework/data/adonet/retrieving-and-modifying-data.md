---
title: "Extraction et modification de données dans ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4ea157cd52bf92dace924baaa40f5b1bba6f13a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="768bb-102">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="768bb-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="768bb-103">Une fonction principale de toute application de base de données consiste à se connecter à une source de données et extraire les données qu'elle contient.</span><span class="sxs-lookup"><span data-stu-id="768bb-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="768bb-104">Les fournisseurs de données .NET Framework d’ADO.NET font Office de passerelle entre une application et une source de données, ce qui vous permet d’exécuter des commandes et d’extraire des données à l’aide un **DataReader** ou un **DataAdapter** .</span><span class="sxs-lookup"><span data-stu-id="768bb-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="768bb-105">Une fonction clé de toute application de base de données est la capacité à mettre à jour les données stockées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="768bb-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="768bb-106">Dans ADO.NET, la mise à jour des données implique l’utilisation de la **DataAdapter** et <xref:System.Data.DataSet>, et **commande** objets ; elle peut également impliquer l’utilisation de transactions.</span><span class="sxs-lookup"><span data-stu-id="768bb-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="768bb-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="768bb-107">In This Section</span></span>  
 [<span data-ttu-id="768bb-108">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="768bb-108">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="768bb-109">Décrit comment établir une connexion à une source de données et comment travailler avec des événements de connexion.</span><span class="sxs-lookup"><span data-stu-id="768bb-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="768bb-110">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="768bb-110">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 <span data-ttu-id="768bb-111">Contient des rubriques qui décrivent divers aspects de l'utilisation de chaînes de connexion, y compris des mots clés de chaîne de connexion, des informations de sécurité, ainsi que de leur stockage et leur extraction.</span><span class="sxs-lookup"><span data-stu-id="768bb-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="768bb-112">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="768bb-112">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 <span data-ttu-id="768bb-113">Décrit le regroupement de connexions pour les fournisseurs de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="768bb-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="768bb-114">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="768bb-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="768bb-115">Contient des rubriques qui décrivent comment créer des commandes et des générateurs de commande, configurer des paramètres et exécuter des commandes pour extraire et modifier des données.</span><span class="sxs-lookup"><span data-stu-id="768bb-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="768bb-116">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="768bb-116">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="768bb-117">Contient des rubriques qui décrivent les objets DataReader et DataAdapter, les paramètres, la gestion des événements DataAdapter et l'exécution d'opérations par lots.</span><span class="sxs-lookup"><span data-stu-id="768bb-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="768bb-118">Transactions et accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="768bb-118">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="768bb-119">Contient des rubriques qui décrivent comment effectuer des transactions locales, des transactions distribuées et travailler avec l’accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="768bb-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="768bb-120">Récupération de valeurs d’identité ou de numérotation automatique</span><span class="sxs-lookup"><span data-stu-id="768bb-120">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="768bb-121">Fournit un exemple de mappage des valeurs générées pour un **identité** colonne dans un [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] table ou pour un **NuméroAuto** champ dans une table Microsoft Access, à une colonne d’une ligne insérée dans une table.</span><span class="sxs-lookup"><span data-stu-id="768bb-121">Provides an example of mapping the values generated for an **identity** column in a [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="768bb-122">Traite de la fusion de valeurs d'identité dans un `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="768bb-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="768bb-123">Récupération de données binaires</span><span class="sxs-lookup"><span data-stu-id="768bb-123">Retrieving Binary Data</span></span>](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 <span data-ttu-id="768bb-124">Décrit comment récupérer des données binaires ou grosses structures de données à l’aide de `CommandBehavior`.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="768bb-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="768bb-125">Pour modifier le comportement par défaut d’un `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="768bb-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="768bb-126">Modification des données avec les procédures stockées</span><span class="sxs-lookup"><span data-stu-id="768bb-126">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="768bb-127">Décrit comment utiliser des paramètres d'entrée et sortie de procédure stockée afin d'insérer une ligne dans une base de données et retourner une nouvelle valeur d'identité.</span><span class="sxs-lookup"><span data-stu-id="768bb-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="768bb-128">Récupération des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="768bb-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="768bb-129">Décrit la manière d'obtenir des bases de données ou des catalogues disponibles, des tables et des vues dans une base de données, des contraintes existantes pour des tables et d'autres informations de schéma à partir d'une source de données.</span><span class="sxs-lookup"><span data-stu-id="768bb-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="768bb-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="768bb-130">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="768bb-131">Décrit le modèle fabrique de fournisseurs et illustre l'utilisation des classes de base dans l'espace de noms `System.Data.Common`.</span><span class="sxs-lookup"><span data-stu-id="768bb-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="768bb-132">Suivi des données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="768bb-132">Data Tracing in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-tracing.md)  
 <span data-ttu-id="768bb-133">Décrit la manière dont ADO.NET offre une fonctionnalité intégrée de traçage de données.</span><span class="sxs-lookup"><span data-stu-id="768bb-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="768bb-134">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="768bb-134">Performance Counters</span></span>](../../../../docs/framework/data/adonet/performance-counters.md)  
 <span data-ttu-id="768bb-135">Décrit les compteurs de performance disponibles pour `SqlClient` et `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="768bb-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="768bb-136">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="768bb-136">Asynchronous Programming</span></span>](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 <span data-ttu-id="768bb-137">Décrit la prise en charge [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] de la programmation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="768bb-137">Describes [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="768bb-138">Prise en charge du streaming pour SqlClient</span><span class="sxs-lookup"><span data-stu-id="768bb-138">SqlClient Streaming Support</span></span>](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 <span data-ttu-id="768bb-139">Explique comment écrire des applications qui diffusent en continu les données provenant de [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] sans avoir à les charger complètement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="768bb-139">Discusses how to write applications that stream data from [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768bb-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="768bb-140">See Also</span></span>  
 [<span data-ttu-id="768bb-141">Mappages de types de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="768bb-141">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="768bb-142">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="768bb-142">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="768bb-143">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="768bb-143">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="768bb-144">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="768bb-144">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="768bb-145">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="768bb-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
