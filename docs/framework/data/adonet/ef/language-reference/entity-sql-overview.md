---
title: Vue d'ensemble d'Entity SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f77e3a5d0073cb13d1904f802c4d6760fc52caa9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="entity-sql-overview"></a><span data-ttu-id="92a0a-102">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="92a0a-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="92a0a-103"> est un langage similaire à SQL qui vous permet d'interroger des modèles conceptuels dans [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92a0a-103"> is a SQL-like language that enables you to query conceptual models in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="92a0a-104">Des modèles conceptuels représentent des données en tant qu’entités et de relations, et [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vous permet d’interroger les entités et les relations dans un format familier pour ceux qui ont utilisé SQL.</span><span class="sxs-lookup"><span data-stu-id="92a0a-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
  
 <span data-ttu-id="92a0a-105">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] utilise des fournisseurs de données de stockage pour traduire le langage [!INCLUDE[esql](../../../../../../includes/esql-md.md)] générique en requêtes de stockage.</span><span class="sxs-lookup"><span data-stu-id="92a0a-105">The [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="92a0a-106">Le fournisseur EntityClient fournit une méthode pour exécuter une commande [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sur un modèle d'entité et retourner des types de données enrichis, y compris des résultats scalaires, des jeux de résultats et des graphiques d'objets.</span><span class="sxs-lookup"><span data-stu-id="92a0a-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="92a0a-107">Lorsque vous construisez des objets <xref:System.Data.EntityClient.EntityCommand>, vous pouvez spécifier un nom de procédure stockée ou le texte d'une requête en assignant une chaîne de requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à sa propriété <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92a0a-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="92a0a-108"><xref:System.Data.EntityClient.EntityDataReader> expose les résultats de l'exécution d'un <xref:System.Data.EntityClient.EntityCommand> sur un modèle EDM.</span><span class="sxs-lookup"><span data-stu-id="92a0a-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="92a0a-109">Pour exécuter la commande qui retourne l'objet <xref:System.Data.EntityClient.EntityDataReader>, appelez la méthode <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="92a0a-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="92a0a-110">Outre le fournisseur EntityClient, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] vous permet d'utiliser [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour exécuter des requêtes sur un modèle conceptuel et retourner des données sous forme d'objets CLR fortement typés qui sont des instances de types d'entités.</span><span class="sxs-lookup"><span data-stu-id="92a0a-110">In addition to the EntityClient provider, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="92a0a-111">Pour plus d’informations, consultez [utilisation des objets](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="92a0a-111">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="92a0a-112">Cette section fournit des informations conceptuelles sur [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92a0a-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92a0a-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="92a0a-113">In This Section</span></span>  
 [<span data-ttu-id="92a0a-114">Différences entre Entity SQL et Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="92a0a-114">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="92a0a-115">Aide-mémoire Entity SQL</span><span class="sxs-lookup"><span data-stu-id="92a0a-115">Entity SQL Quick Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="92a0a-116">Système de type</span><span class="sxs-lookup"><span data-stu-id="92a0a-116">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-117">Définitions de type</span><span class="sxs-lookup"><span data-stu-id="92a0a-117">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-118">Construction de types</span><span class="sxs-lookup"><span data-stu-id="92a0a-118">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-119">Mise en cache d’un plan de requête</span><span class="sxs-lookup"><span data-stu-id="92a0a-119">Query Plan Caching</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-120">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="92a0a-120">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-121">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="92a0a-121">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-122">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92a0a-122">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-123">Variables</span><span class="sxs-lookup"><span data-stu-id="92a0a-123">Variables</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-124">Expressions non prises en charge</span><span class="sxs-lookup"><span data-stu-id="92a0a-124">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-125">Littéraux</span><span class="sxs-lookup"><span data-stu-id="92a0a-125">Literals</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-126">Littéraux null et inférence de type</span><span class="sxs-lookup"><span data-stu-id="92a0a-126">Null Literals and Type Inference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-127">Jeu de caractères en entrée</span><span class="sxs-lookup"><span data-stu-id="92a0a-127">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-128">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="92a0a-128">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-129">Fonctions</span><span class="sxs-lookup"><span data-stu-id="92a0a-129">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-130">Priorité des opérateurs</span><span class="sxs-lookup"><span data-stu-id="92a0a-130">Operator Precedence</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-131">Pagination</span><span class="sxs-lookup"><span data-stu-id="92a0a-131">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-132">Sémantique de comparaison</span><span class="sxs-lookup"><span data-stu-id="92a0a-132">Comparison Semantics</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="92a0a-133">Composition de requêtes Entity SQL imbriquées</span><span class="sxs-lookup"><span data-stu-id="92a0a-133">Composing Nested Entity SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="92a0a-134">Types structurés autorisant la valeur null</span><span class="sxs-lookup"><span data-stu-id="92a0a-134">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="92a0a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92a0a-135">See Also</span></span>  
 [<span data-ttu-id="92a0a-136">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="92a0a-136">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="92a0a-137">Langage Entity SQL</span><span class="sxs-lookup"><span data-stu-id="92a0a-137">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [<span data-ttu-id="92a0a-138">Spécifications CSDL, SSDL et MSL</span><span class="sxs-lookup"><span data-stu-id="92a0a-138">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
