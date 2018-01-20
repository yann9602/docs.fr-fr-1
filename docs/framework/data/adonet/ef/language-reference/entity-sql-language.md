---
title: Langage d'Entity SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a0caf2670a90db0e44ad1f51689b6086313de274
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="entity-sql-language"></a><span data-ttu-id="a25a5-102">Langage d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a25a5-102">Entity SQL Language</span></span>
<span data-ttu-id="a25a5-103">Entity SQL est un langage de requête indépendant du stockage et semblable à SQL.</span><span class="sxs-lookup"><span data-stu-id="a25a5-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="a25a5-104">Entity SQL vous permet d'interroger des données d'entité, en tant qu'objets ou sous une forme tabulaire.</span><span class="sxs-lookup"><span data-stu-id="a25a5-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="a25a5-105">Vous devez envisager d'utiliser Entity SQL dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="a25a5-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="a25a5-106">Lorsqu'une requête doit être construite dynamiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a25a5-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="a25a5-107">Dans ce cas, vous devez également envisager d'utiliser les méthodes du Générateur de requêtes d'<xref:System.Data.Objects.ObjectQuery%601> au lieu de construire une chaîne de requête Entity SQL au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a25a5-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="a25a5-108">Lorsque vous voulez définir une requête dans le cadre de la définition du modèle.</span><span class="sxs-lookup"><span data-stu-id="a25a5-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="a25a5-109">Seul Entity SQL est pris en charge dans un modèle de données.</span><span class="sxs-lookup"><span data-stu-id="a25a5-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="a25a5-110">Pour plus d’informations, consultez [élément QueryView (MSL)](http://msdn.microsoft.com/library/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span><span class="sxs-lookup"><span data-stu-id="a25a5-110">For more information, see [QueryView Element (MSL)](http://msdn.microsoft.com/library/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span></span>  
  
-   <span data-ttu-id="a25a5-111">Lorsque vous utilisez EntityClient pour retourner des données d'entité en lecture seule sous la forme d'ensembles de lignes à l'aide d'un <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a25a5-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="a25a5-112">Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="a25a5-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="a25a5-113">Si vous êtes déjà un expert des langages de requête basés sur SQL, Entity SQL peut vous sembler le choix le plus naturel.</span><span class="sxs-lookup"><span data-stu-id="a25a5-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="a25a5-114">Utilisation de Entity SQL avec le fournisseur EntityClient</span><span class="sxs-lookup"><span data-stu-id="a25a5-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="a25a5-115">Pour plus d'informations sur l'utilisation de Entity SQL avec le fournisseur EntityClient, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="a25a5-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="a25a5-116">Fournisseur EntityClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a25a5-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="a25a5-117">Guide pratique pour créer une chaîne de connexion EntityConnection</span><span class="sxs-lookup"><span data-stu-id="a25a5-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="a25a5-118">Guide pratique pour exécuter une requête qui retourne les résultats PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="a25a5-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="a25a5-119">Guide pratique pour exécuter une requête qui retourne les résultats StructuralType</span><span class="sxs-lookup"><span data-stu-id="a25a5-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="a25a5-120">Guide pratique pour exécuter une requête qui retourne les résultats RefType</span><span class="sxs-lookup"><span data-stu-id="a25a5-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="a25a5-121">Guide pratique pour exécuter une requête qui retourne les types complexes</span><span class="sxs-lookup"><span data-stu-id="a25a5-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="a25a5-122">Guide pratique pour exécuter une requête qui retourne les collections imbriquées</span><span class="sxs-lookup"><span data-stu-id="a25a5-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="a25a5-123">Guide pratique pour exécuter une requête paramétrée Entity SQL avec EntityCommand</span><span class="sxs-lookup"><span data-stu-id="a25a5-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="a25a5-124">Guide pratique pour exécuter une procédure stockée paramétrée utilisant EntityCommand</span><span class="sxs-lookup"><span data-stu-id="a25a5-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="a25a5-125">Guide pratique pour exécuter une requête polymorphe</span><span class="sxs-lookup"><span data-stu-id="a25a5-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="a25a5-126">Guide pratique pour naviguer parmi les relations avec l’opérateur Navigate</span><span class="sxs-lookup"><span data-stu-id="a25a5-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="a25a5-127">Utilisation de Entity SQL avec des requêtes d'objet</span><span class="sxs-lookup"><span data-stu-id="a25a5-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="a25a5-128">Pour plus d'informations sur l'utilisation de Entity SQL avec des requêtes d'objet, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="a25a5-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="a25a5-129">Comment : exécuter une requête qui retourne des objets de Type d’entité</span><span class="sxs-lookup"><span data-stu-id="a25a5-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](http://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="a25a5-130">Comment : exécuter une requête paramétrable</span><span class="sxs-lookup"><span data-stu-id="a25a5-130">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="a25a5-131">Comment : parcourir les relations à l’aide des propriétés de Navigation</span><span class="sxs-lookup"><span data-stu-id="a25a5-131">How to: Navigate Relationships Using Navigation Properties</span></span>](http://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="a25a5-132">Comment : appeler une fonction définie par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="a25a5-132">How to: Call a User-Defined Function</span></span>](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="a25a5-133">Comment : filtrer des données</span><span class="sxs-lookup"><span data-stu-id="a25a5-133">How to: Filter Data</span></span>](http://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="a25a5-134">Comment : trier des données</span><span class="sxs-lookup"><span data-stu-id="a25a5-134">How to: Sort Data</span></span>](http://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="a25a5-135">Comment : regrouper des données</span><span class="sxs-lookup"><span data-stu-id="a25a5-135">How to: Group Data</span></span>](http://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="a25a5-136">Comment : regrouper des données</span><span class="sxs-lookup"><span data-stu-id="a25a5-136">How to: Aggregate Data</span></span>](http://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="a25a5-137">Comment : exécuter une requête qui retourne des objets de Type anonyme</span><span class="sxs-lookup"><span data-stu-id="a25a5-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="a25a5-138">Comment : exécuter une requête qui retourne une Collection de Types primitifs</span><span class="sxs-lookup"><span data-stu-id="a25a5-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](http://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="a25a5-139">Comment : interroger les objets connexes d’un EntityCollection</span><span class="sxs-lookup"><span data-stu-id="a25a5-139">How to: Query Related Objects in an EntityCollection</span></span>](http://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="a25a5-140">Comment : classer l’Union de deux requêtes</span><span class="sxs-lookup"><span data-stu-id="a25a5-140">How to: Order the Union of Two Queries</span></span>](http://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="a25a5-141">Comment : résultats de la Page via la requête</span><span class="sxs-lookup"><span data-stu-id="a25a5-141">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="a25a5-142">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a25a5-142">In This Section</span></span>  
 [<span data-ttu-id="a25a5-143">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a25a5-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="a25a5-144">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a25a5-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="a25a5-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a25a5-145">See Also</span></span>  
 [<span data-ttu-id="a25a5-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a25a5-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="a25a5-147">Informations de référence sur le langage</span><span class="sxs-lookup"><span data-stu-id="a25a5-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
