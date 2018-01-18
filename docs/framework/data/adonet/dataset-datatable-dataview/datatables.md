---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 439b951779393d6ac232e6a1a622515905e837ad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="datatables"></a><span data-ttu-id="a3c36-102">DataTables</span><span class="sxs-lookup"><span data-stu-id="a3c36-102">DataTables</span></span>
<span data-ttu-id="a3c36-103">Un objet <xref:System.Data.DataSet> est constitué d'une collection de tables, de relations et de contraintes.</span><span class="sxs-lookup"><span data-stu-id="a3c36-103">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="a3c36-104">Dans ADO.NET, <xref:System.Data.DataTable> objets sont utilisés pour représenter les tables dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a3c36-104">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="a3c36-105">A **DataTable** représente une table de données relationnelles de la mémoire ; les données seront locales pour le. Application basée sur le réseau dans lequel il réside, mais peut être rempli à partir d’une source de données telles que Microsoft SQL Server à l’aide un **DataAdapter** pour plus d’informations, consultez [remplissage d’un DataSet à partir d’un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .</span><span class="sxs-lookup"><span data-stu-id="a3c36-105">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="a3c36-106">Le **DataTable** classe est un membre de la **System.Data** espace de noms dans la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3c36-106">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="a3c36-107">Vous pouvez créer et utiliser un **DataTable** indépendamment ou en tant que membre d’un **DataSet**, et **DataTable** objets peuvent également être utilisés conjointement avec d’autres objets .NET Framework, y compris le <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="a3c36-107">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="a3c36-108">Accéder à la collection de tables dans un **DataSet** via la **Tables** propriété de la **DataSet** objet.</span><span class="sxs-lookup"><span data-stu-id="a3c36-108">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="a3c36-109">Le schéma, ou structure, d'une table est représenté par des colonnes et des contraintes.</span><span class="sxs-lookup"><span data-stu-id="a3c36-109">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="a3c36-110">Vous définissez le schéma d’un **DataTable** à l’aide de <xref:System.Data.DataColumn> objets ainsi que <xref:System.Data.ForeignKeyConstraint> et <xref:System.Data.UniqueConstraint> objets.</span><span class="sxs-lookup"><span data-stu-id="a3c36-110">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="a3c36-111">Les colonnes d'une table peuvent mapper aux colonnes d'une source de données. Elles contiennent des valeurs calculées à partir d'expressions, incrémentent automatiquement leurs valeurs ou contiennent des valeurs de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="a3c36-111">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="a3c36-112">Outre un schéma, un **DataTable** doit également avoir des lignes pour contenir et trier les données.</span><span class="sxs-lookup"><span data-stu-id="a3c36-112">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="a3c36-113">La classe <xref:System.Data.DataRow> représente les données en cours contenues dans une table.</span><span class="sxs-lookup"><span data-stu-id="a3c36-113">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="a3c36-114">Vous utilisez la **DataRow** et ses propriétés et méthodes pour extraire, évaluer et manipuler les données dans une table.</span><span class="sxs-lookup"><span data-stu-id="a3c36-114">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="a3c36-115">Comme vous accéder et modifier les données dans une ligne, la **DataRow** objet conserve son état d’origine et actuelle.</span><span class="sxs-lookup"><span data-stu-id="a3c36-115">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="a3c36-116">Vous pouvez créer des relations parent-enfant entre des tables à l'aide d'une ou plusieurs colonnes connexes de ces tables.</span><span class="sxs-lookup"><span data-stu-id="a3c36-116">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="a3c36-117">Vous créez une relation entre **DataTable** à l’aide des objets un <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="a3c36-117">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="a3c36-118">**DataRelation** objets peuvent ensuite être utilisés pour retourner les lignes connexes enfants ou parentes d’une ligne particulière.</span><span class="sxs-lookup"><span data-stu-id="a3c36-118">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="a3c36-119">Pour plus d’informations, consultez [Ajout de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="a3c36-119">For more information, see [Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3c36-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a3c36-120">In This Section</span></span>  
 [<span data-ttu-id="a3c36-121">Création d’un DataTable</span><span class="sxs-lookup"><span data-stu-id="a3c36-121">Creating a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 <span data-ttu-id="a3c36-122">Explique comment créer un **DataTable** et ajoutez-le à un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a3c36-122">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="a3c36-123">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="a3c36-123">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 <span data-ttu-id="a3c36-124">Fournit des informations sur la création et à l’aide de **DataColumn** contraintes et objets.</span><span class="sxs-lookup"><span data-stu-id="a3c36-124">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="a3c36-125">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="a3c36-125">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="a3c36-126">Explique comment ajouter, modifier et supprimer des données dans une table.</span><span class="sxs-lookup"><span data-stu-id="a3c36-126">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="a3c36-127">Explique comment utiliser **DataTable** événements pour examiner les modifications apportées aux données dans la table.</span><span class="sxs-lookup"><span data-stu-id="a3c36-127">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="a3c36-128">Gestion des événements de DataTable</span><span class="sxs-lookup"><span data-stu-id="a3c36-128">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 <span data-ttu-id="a3c36-129">Fournit des informations sur les événements disponibles pour une utilisation avec un **DataTable**, y compris les événements lorsque les valeurs de colonne sont modifiées et les lignes sont ajoutées ou supprimées.</span><span class="sxs-lookup"><span data-stu-id="a3c36-129">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a3c36-130">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a3c36-130">Related Sections</span></span>  
 [<span data-ttu-id="a3c36-131">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a3c36-131">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="a3c36-132">Décrit l'architecture et les composants d'ADO.NET ainsi que la façon de les utiliser pour accéder à des sources de données existantes et pour gérer des données d'application.</span><span class="sxs-lookup"><span data-stu-id="a3c36-132">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="a3c36-133">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="a3c36-133">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="a3c36-134">Fournit des informations sur l’ADO.NET **DataSet** , notamment comment créer des relations entre les tables.</span><span class="sxs-lookup"><span data-stu-id="a3c36-134">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="a3c36-135">Fournit des informations de référence sur les **contrainte** objet.</span><span class="sxs-lookup"><span data-stu-id="a3c36-135">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="a3c36-136">Fournit des informations de référence sur les **DataColumn** objet.</span><span class="sxs-lookup"><span data-stu-id="a3c36-136">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="a3c36-137">Fournit des informations de référence sur les **DataSet** objet.</span><span class="sxs-lookup"><span data-stu-id="a3c36-137">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="a3c36-138">Fournit des informations de référence sur les **DataTable** objet.</span><span class="sxs-lookup"><span data-stu-id="a3c36-138">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="a3c36-139">Présentation des bibliothèques de classes .NET</span><span class="sxs-lookup"><span data-stu-id="a3c36-139">Class Library Overview</span></span>](../../../../../docs/standard/class-library-overview.md)  
 <span data-ttu-id="a3c36-140">Fournit une vue d’ensemble de la bibliothèque de classes .NET Framework, y compris le **système** espace de noms, ainsi que son espace de noms de deuxième niveau, **System.Data**.</span><span class="sxs-lookup"><span data-stu-id="a3c36-140">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c36-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3c36-141">See Also</span></span>  
 [<span data-ttu-id="a3c36-142">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="a3c36-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
