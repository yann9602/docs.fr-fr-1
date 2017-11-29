---
title: Fonctions canoniques
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b80eeedc67678d703664eb705408a72b7e4a2274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="canonical-functions"></a><span data-ttu-id="4156c-102">Fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="4156c-102">Canonical Functions</span></span>
<span data-ttu-id="4156c-103">Cette section décrit les fonctions canoniques qui sont prises en charge par tous les fournisseurs de données et qui peuvent être utilisée par toutes les technologies de requête.</span><span class="sxs-lookup"><span data-stu-id="4156c-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="4156c-104">Les fonctions canoniques ne peuvent pas être étendues par un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4156c-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="4156c-105">Ces fonctions canoniques seront traduites en fonctionnalités de source de données correspondantes pour le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4156c-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="4156c-106">De ce fait, les appels de fonction peuvent être exprimés sous une forme commune dans toutes les sources de données.</span><span class="sxs-lookup"><span data-stu-id="4156c-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="4156c-107">Ces fonctions canoniques étant indépendantes des sources de données, les types d'arguments et de retour des fonctions canoniques sont définis par rapport aux types du modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="4156c-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="4156c-108">Toutefois, il est possible que certaines sources de données ne puissent pas prendre en charge tous les types du modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="4156c-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="4156c-109">Lorsque des fonctions canoniques sont utilisées dans une requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)], la fonction appropriée est appelée au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="4156c-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="4156c-110">Le comportement en cas d'entrée null et les conditions d'erreurs sont explicitement spécifiées pour toutes les fonctions canoniques.</span><span class="sxs-lookup"><span data-stu-id="4156c-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="4156c-111">Les fournisseurs de magasins doivent respecter ce comportement, mais [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ne l'applique pas de force.</span><span class="sxs-lookup"><span data-stu-id="4156c-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="4156c-112">Pour les scénarios LINQ, les requêtes sur le [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] impliquent le mappage de méthodes CLR aux méthodes dans la source de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="4156c-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="4156c-113">Les méthodes CLR sont mappées aux fonctions canoniques, ce qui garantit qu'un ensemble spécifique de méthodes sera correctement mappé, quelle que soit la source de données.</span><span class="sxs-lookup"><span data-stu-id="4156c-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="4156c-114">Espace de noms des fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="4156c-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="4156c-115">L'espace de noms des fonctions canoniques est <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="4156c-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="4156c-116">L'espace de noms <xref:System.Data.Metadata.Edm> est automatiquement inclus dans toutes les requêtes.</span><span class="sxs-lookup"><span data-stu-id="4156c-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="4156c-117">Toutefois, si un autre espace de noms est importé et que celui-ci contient une fonction de même nom qu'une fonction canonique (dans l'espace de noms <xref:System.Data.Metadata.Edm>), vous devez spécifier l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4156c-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4156c-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4156c-118">In This Section</span></span>  
 [<span data-ttu-id="4156c-119">Fonctions canoniques d’agrégation</span><span class="sxs-lookup"><span data-stu-id="4156c-119">Aggregate Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 <span data-ttu-id="4156c-120">Décrit les fonctions canoniques d'agrégation [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4156c-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4156c-121">Fonctions canoniques mathématiques</span><span class="sxs-lookup"><span data-stu-id="4156c-121">Math Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 <span data-ttu-id="4156c-122">Décrit les fonctions canoniques mathématiques [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4156c-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4156c-123">Fonctions canoniques de chaîne</span><span class="sxs-lookup"><span data-stu-id="4156c-123">String Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 <span data-ttu-id="4156c-124">Décrit les fonctions canoniques de chaîne [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4156c-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4156c-125">Fonctions canoniques de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="4156c-125">Date and Time Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 <span data-ttu-id="4156c-126">Décrit les fonctions canoniques de date et d'heure [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4156c-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4156c-127">Au niveau du bit des fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="4156c-127">Bitwise Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 <span data-ttu-id="4156c-128">Décrit les fonctions canoniques au niveau du bit [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4156c-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4156c-129">Fonctions spatiales</span><span class="sxs-lookup"><span data-stu-id="4156c-129">Spatial Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 <span data-ttu-id="4156c-130">Décrit les fonctions canoniques spatiales [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4156c-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="4156c-131">Les autres fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="4156c-131">Other Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 <span data-ttu-id="4156c-132">Décrit les fonctions qui ne sont pas considérées comme des fonctions au niveau du bit, des fonctions de date/heure, des fonctions de chaîne, des fonctions mathématiques ni des fonctions d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="4156c-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4156c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4156c-133">See Also</span></span>  
 [<span data-ttu-id="4156c-134">Vue d’ensemble de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4156c-134">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="4156c-135">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4156c-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="4156c-136">Mappage des fonctions de modèle conceptuel canonique à SQL Server</span><span class="sxs-lookup"><span data-stu-id="4156c-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [<span data-ttu-id="4156c-137">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="4156c-137">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
