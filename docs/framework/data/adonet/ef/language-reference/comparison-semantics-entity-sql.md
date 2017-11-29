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
ms.openlocfilehash: f1fd1c21fc4f156bfe7a5abf9f76bd341e2d0f10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="82498-102">Sémantique de comparaison (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="82498-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="82498-103">L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :</span><span class="sxs-lookup"><span data-stu-id="82498-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="82498-104">Comparaison explicite</span><span class="sxs-lookup"><span data-stu-id="82498-104">Explicit comparison</span></span>  
 <span data-ttu-id="82498-105">Opérations d'égalité :</span><span class="sxs-lookup"><span data-stu-id="82498-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="82498-106">!=</span><span class="sxs-lookup"><span data-stu-id="82498-106">!=</span></span>  
  
 <span data-ttu-id="82498-107">Opérations de classement :</span><span class="sxs-lookup"><span data-stu-id="82498-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="82498-108">Opérations relatives à la possibilité de valeurs NULL :</span><span class="sxs-lookup"><span data-stu-id="82498-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="82498-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="82498-109">IS NULL</span></span>  
  
-   <span data-ttu-id="82498-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="82498-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="82498-111">Distinction explicite</span><span class="sxs-lookup"><span data-stu-id="82498-111">Explicit distinction</span></span>  
 <span data-ttu-id="82498-112">Distinction d'égalité :</span><span class="sxs-lookup"><span data-stu-id="82498-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="82498-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="82498-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="82498-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="82498-114">GROUP BY</span></span>  
  
 <span data-ttu-id="82498-115">Distinction de classement :</span><span class="sxs-lookup"><span data-stu-id="82498-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="82498-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="82498-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="82498-117">Distinction implicite</span><span class="sxs-lookup"><span data-stu-id="82498-117">Implicit distinction</span></span>  
 <span data-ttu-id="82498-118">Opérations et prédicats de définition (égalité) :</span><span class="sxs-lookup"><span data-stu-id="82498-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="82498-119">UNION</span><span class="sxs-lookup"><span data-stu-id="82498-119">UNION</span></span>  
  
-   <span data-ttu-id="82498-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="82498-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="82498-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="82498-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="82498-122">SET</span><span class="sxs-lookup"><span data-stu-id="82498-122">SET</span></span>  
  
-   <span data-ttu-id="82498-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="82498-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="82498-124">Prédicats d'élément (égalité) :</span><span class="sxs-lookup"><span data-stu-id="82498-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="82498-125">IN</span><span class="sxs-lookup"><span data-stu-id="82498-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="82498-126">Combinaisons prises en charge</span><span class="sxs-lookup"><span data-stu-id="82498-126">Supported Combinations</span></span>  
 <span data-ttu-id="82498-127">Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :</span><span class="sxs-lookup"><span data-stu-id="82498-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="82498-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="82498-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="82498-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="82498-129">**!=**</span></span>|<span data-ttu-id="82498-130">**REGROUPER PAR**</span><span class="sxs-lookup"><span data-stu-id="82498-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="82498-131">**DISTINCTES**</span><span class="sxs-lookup"><span data-stu-id="82498-131">**DISTINCT**</span></span>|<span data-ttu-id="82498-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="82498-132">**UNION**</span></span><br /><br /> <span data-ttu-id="82498-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="82498-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="82498-134">**À L’EXCEPTION**</span><span class="sxs-lookup"><span data-stu-id="82498-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="82498-135">**ENSEMBLE**</span><span class="sxs-lookup"><span data-stu-id="82498-135">**SET**</span></span><br /><br /> <span data-ttu-id="82498-136">**CHEVAUCHEMENTS**</span><span class="sxs-lookup"><span data-stu-id="82498-136">**OVERLAPS**</span></span>|<span data-ttu-id="82498-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="82498-137">**IN**</span></span>|<span data-ttu-id="82498-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="82498-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="82498-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="82498-139">**>   >=**</span></span>|<span data-ttu-id="82498-140">**TRIER PAR**</span><span class="sxs-lookup"><span data-stu-id="82498-140">**ORDER BY**</span></span>|<span data-ttu-id="82498-141">**A LA VALEUR NULL**</span><span class="sxs-lookup"><span data-stu-id="82498-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="82498-142">**N’EST PAS NULL**</span><span class="sxs-lookup"><span data-stu-id="82498-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="82498-143">Type d'entité</span><span class="sxs-lookup"><span data-stu-id="82498-143">Entity type</span></span>|<span data-ttu-id="82498-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="82498-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="82498-145">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="82498-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="82498-146">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="82498-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="82498-147">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="82498-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="82498-148">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-149">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="82498-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="82498-151">Type complexe</span><span class="sxs-lookup"><span data-stu-id="82498-151">Complex type</span></span>|<span data-ttu-id="82498-152">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-153">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-154">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-155">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-156">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-157">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-158">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="82498-159">Ligne</span><span class="sxs-lookup"><span data-stu-id="82498-159">Row</span></span>|<span data-ttu-id="82498-160">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="82498-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="82498-161">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="82498-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="82498-162">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="82498-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="82498-163">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-164">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-165">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="82498-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="82498-166">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="82498-167">Type primitif</span><span class="sxs-lookup"><span data-stu-id="82498-167">Primitive type</span></span>|<span data-ttu-id="82498-168">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="82498-168">Provider-specific</span></span>|<span data-ttu-id="82498-169">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="82498-169">Provider-specific</span></span>|<span data-ttu-id="82498-170">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="82498-170">Provider-specific</span></span>|<span data-ttu-id="82498-171">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="82498-171">Provider-specific</span></span>|<span data-ttu-id="82498-172">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="82498-172">Provider-specific</span></span>|<span data-ttu-id="82498-173">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="82498-173">Provider-specific</span></span>|<span data-ttu-id="82498-174">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="82498-174">Provider-specific</span></span>|  
|<span data-ttu-id="82498-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="82498-175">Multiset</span></span>|<span data-ttu-id="82498-176">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-177">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-178">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-179">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-180">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-181">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-182">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="82498-183">Ref</span><span class="sxs-lookup"><span data-stu-id="82498-183">Ref</span></span>|<span data-ttu-id="82498-184">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="82498-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="82498-185">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="82498-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="82498-186">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="82498-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="82498-187">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="82498-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="82498-188">Throw</span><span class="sxs-lookup"><span data-stu-id="82498-188">Throw</span></span>|<span data-ttu-id="82498-189">Throw</span><span class="sxs-lookup"><span data-stu-id="82498-189">Throw</span></span>|<span data-ttu-id="82498-190">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="82498-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="82498-191">Association</span><span class="sxs-lookup"><span data-stu-id="82498-191">Association</span></span><br /><br /> <span data-ttu-id="82498-192">type</span><span class="sxs-lookup"><span data-stu-id="82498-192">type</span></span>|<span data-ttu-id="82498-193">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-194">Throw</span><span class="sxs-lookup"><span data-stu-id="82498-194">Throw</span></span>|<span data-ttu-id="82498-195">Throw</span><span class="sxs-lookup"><span data-stu-id="82498-195">Throw</span></span>|<span data-ttu-id="82498-196">Throw</span><span class="sxs-lookup"><span data-stu-id="82498-196">Throw</span></span>|<span data-ttu-id="82498-197">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-198">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="82498-199">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="82498-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="82498-200"><sup>1</sup>les références des instances du type d’entité donnée sont comparées implicitement, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="82498-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="82498-201">Une instance d'entité ne peut pas être comparée à une référence explicite.</span><span class="sxs-lookup"><span data-stu-id="82498-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="82498-202">Lors d'une telle tentative, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="82498-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="82498-203">Par exemple, la requête suivante lève une exception :</span><span class="sxs-lookup"><span data-stu-id="82498-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="82498-204"><sup>2</sup>propriétés de types complexes sont aplanies avant d’être envoyées au magasin, afin de pouvoir être comparées (tant que toutes leurs propriétés peuvent être comparées).</span><span class="sxs-lookup"><span data-stu-id="82498-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="82498-205">Consultez également <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="82498-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="82498-206"><sup>3</sup>exécution d’Entity Framework détecte le cas non pris en charge et lève une exception explicite sans engager le fournisseur/magasin.</span><span class="sxs-lookup"><span data-stu-id="82498-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="82498-207"><sup>4</sup>une tentative est faite pour comparer toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="82498-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="82498-208">Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.</span><span class="sxs-lookup"><span data-stu-id="82498-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="82498-209"><sup>5</sup>tous les éléments individuels des références sont comparés (Cela inclut le nom de jeu d’entités et de toutes les propriétés de clé du type d’entité).</span><span class="sxs-lookup"><span data-stu-id="82498-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82498-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82498-210">See Also</span></span>  
 [<span data-ttu-id="82498-211">Vue d’ensemble de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="82498-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
