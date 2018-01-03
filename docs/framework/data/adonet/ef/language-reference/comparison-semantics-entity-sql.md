---
title: "Sémantique de comparaison (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2835d2064f1845b55dd3a33abb086c5af0fb9e6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="af50f-102">Sémantique de comparaison (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="af50f-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="af50f-103">L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :</span><span class="sxs-lookup"><span data-stu-id="af50f-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="af50f-104">Comparaison explicite</span><span class="sxs-lookup"><span data-stu-id="af50f-104">Explicit comparison</span></span>  
 <span data-ttu-id="af50f-105">Opérations d'égalité :</span><span class="sxs-lookup"><span data-stu-id="af50f-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="af50f-106">!=</span><span class="sxs-lookup"><span data-stu-id="af50f-106">!=</span></span>  
  
 <span data-ttu-id="af50f-107">Opérations de classement :</span><span class="sxs-lookup"><span data-stu-id="af50f-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="af50f-108">Opérations relatives à la possibilité de valeurs NULL :</span><span class="sxs-lookup"><span data-stu-id="af50f-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="af50f-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="af50f-109">IS NULL</span></span>  
  
-   <span data-ttu-id="af50f-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="af50f-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="af50f-111">Distinction explicite</span><span class="sxs-lookup"><span data-stu-id="af50f-111">Explicit distinction</span></span>  
 <span data-ttu-id="af50f-112">Distinction d'égalité :</span><span class="sxs-lookup"><span data-stu-id="af50f-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="af50f-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="af50f-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="af50f-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="af50f-114">GROUP BY</span></span>  
  
 <span data-ttu-id="af50f-115">Distinction de classement :</span><span class="sxs-lookup"><span data-stu-id="af50f-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="af50f-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="af50f-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="af50f-117">Distinction implicite</span><span class="sxs-lookup"><span data-stu-id="af50f-117">Implicit distinction</span></span>  
 <span data-ttu-id="af50f-118">Opérations et prédicats de définition (égalité) :</span><span class="sxs-lookup"><span data-stu-id="af50f-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="af50f-119">UNION</span><span class="sxs-lookup"><span data-stu-id="af50f-119">UNION</span></span>  
  
-   <span data-ttu-id="af50f-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="af50f-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="af50f-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="af50f-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="af50f-122">SET</span><span class="sxs-lookup"><span data-stu-id="af50f-122">SET</span></span>  
  
-   <span data-ttu-id="af50f-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="af50f-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="af50f-124">Prédicats d'élément (égalité) :</span><span class="sxs-lookup"><span data-stu-id="af50f-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="af50f-125">IN</span><span class="sxs-lookup"><span data-stu-id="af50f-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="af50f-126">Combinaisons prises en charge</span><span class="sxs-lookup"><span data-stu-id="af50f-126">Supported Combinations</span></span>  
 <span data-ttu-id="af50f-127">Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :</span><span class="sxs-lookup"><span data-stu-id="af50f-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="af50f-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="af50f-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="af50f-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="af50f-129">**!=**</span></span>|<span data-ttu-id="af50f-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="af50f-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="af50f-131">**DISTINCTES**</span><span class="sxs-lookup"><span data-stu-id="af50f-131">**DISTINCT**</span></span>|<span data-ttu-id="af50f-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="af50f-132">**UNION**</span></span><br /><br /> <span data-ttu-id="af50f-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="af50f-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="af50f-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="af50f-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="af50f-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="af50f-135">**SET**</span></span><br /><br /> <span data-ttu-id="af50f-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="af50f-136">**OVERLAPS**</span></span>|<span data-ttu-id="af50f-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="af50f-137">**IN**</span></span>|<span data-ttu-id="af50f-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="af50f-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="af50f-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="af50f-139">**>   >=**</span></span>|<span data-ttu-id="af50f-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="af50f-140">**ORDER BY**</span></span>|<span data-ttu-id="af50f-141">**A LA VALEUR NULL**</span><span class="sxs-lookup"><span data-stu-id="af50f-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="af50f-142">**N’EST PAS NULL**</span><span class="sxs-lookup"><span data-stu-id="af50f-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="af50f-143">Type d'entité</span><span class="sxs-lookup"><span data-stu-id="af50f-143">Entity type</span></span>|<span data-ttu-id="af50f-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="af50f-145">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="af50f-146">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="af50f-147">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="af50f-148">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-149">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="af50f-151">Type complexe</span><span class="sxs-lookup"><span data-stu-id="af50f-151">Complex type</span></span>|<span data-ttu-id="af50f-152">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-153">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-154">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-155">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-156">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-157">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-158">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="af50f-159">Ligne</span><span class="sxs-lookup"><span data-stu-id="af50f-159">Row</span></span>|<span data-ttu-id="af50f-160">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="af50f-161">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="af50f-162">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="af50f-163">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-164">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-165">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="af50f-166">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="af50f-167">Type primitif</span><span class="sxs-lookup"><span data-stu-id="af50f-167">Primitive type</span></span>|<span data-ttu-id="af50f-168">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="af50f-168">Provider-specific</span></span>|<span data-ttu-id="af50f-169">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="af50f-169">Provider-specific</span></span>|<span data-ttu-id="af50f-170">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="af50f-170">Provider-specific</span></span>|<span data-ttu-id="af50f-171">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="af50f-171">Provider-specific</span></span>|<span data-ttu-id="af50f-172">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="af50f-172">Provider-specific</span></span>|<span data-ttu-id="af50f-173">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="af50f-173">Provider-specific</span></span>|<span data-ttu-id="af50f-174">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="af50f-174">Provider-specific</span></span>|  
|<span data-ttu-id="af50f-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="af50f-175">Multiset</span></span>|<span data-ttu-id="af50f-176">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-177">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-178">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-179">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-180">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-181">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-182">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="af50f-183">Ref</span><span class="sxs-lookup"><span data-stu-id="af50f-183">Ref</span></span>|<span data-ttu-id="af50f-184">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="af50f-185">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="af50f-186">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="af50f-187">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="af50f-188">Throw</span><span class="sxs-lookup"><span data-stu-id="af50f-188">Throw</span></span>|<span data-ttu-id="af50f-189">Throw</span><span class="sxs-lookup"><span data-stu-id="af50f-189">Throw</span></span>|<span data-ttu-id="af50f-190">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="af50f-191">Association</span><span class="sxs-lookup"><span data-stu-id="af50f-191">Association</span></span><br /><br /> <span data-ttu-id="af50f-192">type</span><span class="sxs-lookup"><span data-stu-id="af50f-192">type</span></span>|<span data-ttu-id="af50f-193">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-194">Throw</span><span class="sxs-lookup"><span data-stu-id="af50f-194">Throw</span></span>|<span data-ttu-id="af50f-195">Throw</span><span class="sxs-lookup"><span data-stu-id="af50f-195">Throw</span></span>|<span data-ttu-id="af50f-196">Throw</span><span class="sxs-lookup"><span data-stu-id="af50f-196">Throw</span></span>|<span data-ttu-id="af50f-197">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-198">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="af50f-199">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="af50f-200"><sup>1</sup>les références des instances du type d’entité donnée sont comparées implicitement, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="af50f-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="af50f-201">Une instance d'entité ne peut pas être comparée à une référence explicite.</span><span class="sxs-lookup"><span data-stu-id="af50f-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="af50f-202">Lors d'une telle tentative, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="af50f-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="af50f-203">Par exemple, la requête suivante lève une exception :</span><span class="sxs-lookup"><span data-stu-id="af50f-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="af50f-204"><sup>2</sup>propriétés de types complexes sont aplanies avant d’être envoyées au magasin, afin de pouvoir être comparées (tant que toutes leurs propriétés peuvent être comparées).</span><span class="sxs-lookup"><span data-stu-id="af50f-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="af50f-205">Consultez également <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="af50f-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="af50f-206"><sup>3</sup>exécution d’Entity Framework détecte le cas non pris en charge et lève une exception explicite sans engager le fournisseur/magasin.</span><span class="sxs-lookup"><span data-stu-id="af50f-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="af50f-207"><sup>4</sup>une tentative est faite pour comparer toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="af50f-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="af50f-208">Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.</span><span class="sxs-lookup"><span data-stu-id="af50f-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="af50f-209"><sup>5</sup>tous les éléments individuels des références sont comparés (Cela inclut le nom de jeu d’entités et de toutes les propriétés de clé du type d’entité).</span><span class="sxs-lookup"><span data-stu-id="af50f-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af50f-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af50f-210">See Also</span></span>  
 [<span data-ttu-id="af50f-211">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="af50f-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
