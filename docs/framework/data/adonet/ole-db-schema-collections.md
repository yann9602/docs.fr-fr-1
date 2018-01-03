---
title: "Collections de schémas OLE DB"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e120ea532b6da455e31ce7345b6c4b2be1ec975f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="9a3f8-102">Collections de schémas OLE DB</span><span class="sxs-lookup"><span data-stu-id="9a3f8-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="9a3f8-103">Cette section traite de la prise en charge des collections de schémas pour les fournisseurs OLE DB de Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="9a3f8-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="9a3f8-104">Fournisseur Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="9a3f8-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="9a3f8-105">Le pilote OLE DB Microsoft SQL Server prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="9a3f8-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9a3f8-106">Tables</span><span class="sxs-lookup"><span data-stu-id="9a3f8-106">Tables</span></span>  
  
-   <span data-ttu-id="9a3f8-107">Columns</span><span class="sxs-lookup"><span data-stu-id="9a3f8-107">Columns</span></span>  
  
-   <span data-ttu-id="9a3f8-108">Procédures</span><span class="sxs-lookup"><span data-stu-id="9a3f8-108">Procedures</span></span>  
  
-   <span data-ttu-id="9a3f8-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9a3f8-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9a3f8-110">Catalogue</span><span class="sxs-lookup"><span data-stu-id="9a3f8-110">Catalog</span></span>  
  
-   <span data-ttu-id="9a3f8-111">Index</span><span class="sxs-lookup"><span data-stu-id="9a3f8-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="9a3f8-112">Tables</span><span class="sxs-lookup"><span data-stu-id="9a3f8-112">Tables</span></span>  
  
|<span data-ttu-id="9a3f8-113">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-113">ColumnName</span></span>|<span data-ttu-id="9a3f8-114">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-115">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-116">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-116">String</span></span>|  
|<span data-ttu-id="9a3f8-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-118">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-118">String</span></span>|  
|<span data-ttu-id="9a3f8-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-119">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-120">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-120">String</span></span>|  
|<span data-ttu-id="9a3f8-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-121">TABLE_TYPE</span></span>|<span data-ttu-id="9a3f8-122">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-122">String</span></span>|  
|<span data-ttu-id="9a3f8-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-123">TABLE_GUID</span></span>|<span data-ttu-id="9a3f8-124">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-124">Guid</span></span>|  
|<span data-ttu-id="9a3f8-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-125">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-126">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-126">String</span></span>|  
|<span data-ttu-id="9a3f8-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-127">TABLE_PROPID</span></span>|<span data-ttu-id="9a3f8-128">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-128">Int64</span></span>|  
|<span data-ttu-id="9a3f8-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-129">DATE_CREATED</span></span>|<span data-ttu-id="9a3f8-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-130">DateTime</span></span>|  
|<span data-ttu-id="9a3f8-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-131">DATE_MODIFIED</span></span>|<span data-ttu-id="9a3f8-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9a3f8-133">Columns</span><span class="sxs-lookup"><span data-stu-id="9a3f8-133">Columns</span></span>  
  
|<span data-ttu-id="9a3f8-134">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-134">ColumnName</span></span>|<span data-ttu-id="9a3f8-135">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-136">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-137">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-137">String</span></span>|  
|<span data-ttu-id="9a3f8-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-139">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-139">String</span></span>|  
|<span data-ttu-id="9a3f8-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-140">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-141">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-141">String</span></span>|  
|<span data-ttu-id="9a3f8-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-142">COLUMN_NAME</span></span>|<span data-ttu-id="9a3f8-143">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-143">String</span></span>|  
|<span data-ttu-id="9a3f8-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-144">COLUMN_GUID</span></span>|<span data-ttu-id="9a3f8-145">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-145">Guid</span></span>|  
|<span data-ttu-id="9a3f8-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-146">COLUMN_PROPID</span></span>|<span data-ttu-id="9a3f8-147">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-147">Int64</span></span>|  
|<span data-ttu-id="9a3f8-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="9a3f8-149">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-149">Int64</span></span>|  
|<span data-ttu-id="9a3f8-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a3f8-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="9a3f8-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-151">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a3f8-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="9a3f8-153">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-153">String</span></span>|  
|<span data-ttu-id="9a3f8-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="9a3f8-155">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-155">Int64</span></span>|  
|<span data-ttu-id="9a3f8-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-156">IS_NULLABLE</span></span>|<span data-ttu-id="9a3f8-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-157">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-158">DATA_TYPE</span></span>|<span data-ttu-id="9a3f8-159">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-159">Int32</span></span>|  
|<span data-ttu-id="9a3f8-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-160">TYPE_GUID</span></span>|<span data-ttu-id="9a3f8-161">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-161">Guid</span></span>|  
|<span data-ttu-id="9a3f8-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9a3f8-163">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-163">Int64</span></span>|  
|<span data-ttu-id="9a3f8-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9a3f8-165">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-165">Int64</span></span>|  
|<span data-ttu-id="9a3f8-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9a3f8-167">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-167">Int32</span></span>|  
|<span data-ttu-id="9a3f8-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="9a3f8-169">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-169">Int16</span></span>|  
|<span data-ttu-id="9a3f8-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="9a3f8-171">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-171">Int64</span></span>|  
|<span data-ttu-id="9a3f8-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="9a3f8-173">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-173">String</span></span>|  
|<span data-ttu-id="9a3f8-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="9a3f8-175">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-175">String</span></span>|  
|<span data-ttu-id="9a3f8-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="9a3f8-177">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-177">String</span></span>|  
|<span data-ttu-id="9a3f8-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="9a3f8-179">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-179">String</span></span>|  
|<span data-ttu-id="9a3f8-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="9a3f8-181">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-181">String</span></span>|  
|<span data-ttu-id="9a3f8-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-182">COLLATION_NAME</span></span>|<span data-ttu-id="9a3f8-183">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-183">String</span></span>|  
|<span data-ttu-id="9a3f8-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="9a3f8-185">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-185">String</span></span>|  
|<span data-ttu-id="9a3f8-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="9a3f8-187">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-187">String</span></span>|  
|<span data-ttu-id="9a3f8-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-188">DOMAIN_NAME</span></span>|<span data-ttu-id="9a3f8-189">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-189">String</span></span>|  
|<span data-ttu-id="9a3f8-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-190">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-191">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-191">String</span></span>|  
|<span data-ttu-id="9a3f8-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-192">COLUMN_LCID</span></span>|<span data-ttu-id="9a3f8-193">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-193">Int32</span></span>|  
|<span data-ttu-id="9a3f8-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="9a3f8-195">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-195">Int32</span></span>|  
|<span data-ttu-id="9a3f8-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-196">COLUMN_SORTID</span></span>|<span data-ttu-id="9a3f8-197">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-197">Int32</span></span>|  
|<span data-ttu-id="9a3f8-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="9a3f8-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="9a3f8-199">Byte[]</span></span>|  
|<span data-ttu-id="9a3f8-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-200">IS_COMPUTED</span></span>|<span data-ttu-id="9a3f8-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9a3f8-202">Procédures</span><span class="sxs-lookup"><span data-stu-id="9a3f8-202">Procedures</span></span>  
  
|<span data-ttu-id="9a3f8-203">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-203">ColumnName</span></span>|<span data-ttu-id="9a3f8-204">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9a3f8-206">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-206">String</span></span>|  
|<span data-ttu-id="9a3f8-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-208">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-208">String</span></span>|  
|<span data-ttu-id="9a3f8-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="9a3f8-210">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-210">String</span></span>|  
|<span data-ttu-id="9a3f8-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9a3f8-212">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-212">Int16</span></span>|  
|<span data-ttu-id="9a3f8-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="9a3f8-214">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-214">String</span></span>|  
|<span data-ttu-id="9a3f8-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-215">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-216">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-216">String</span></span>|  
|<span data-ttu-id="9a3f8-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-217">DATE_CREATED</span></span>|<span data-ttu-id="9a3f8-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-218">DateTime</span></span>|  
|<span data-ttu-id="9a3f8-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-219">DATE_MODIFIED</span></span>|<span data-ttu-id="9a3f8-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="9a3f8-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9a3f8-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="9a3f8-222">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-222">ColumnName</span></span>|<span data-ttu-id="9a3f8-223">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9a3f8-225">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-225">String</span></span>|  
|<span data-ttu-id="9a3f8-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-227">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-227">String</span></span>|  
|<span data-ttu-id="9a3f8-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="9a3f8-229">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-229">String</span></span>|  
|<span data-ttu-id="9a3f8-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-230">PARAMETER_NAME</span></span>|<span data-ttu-id="9a3f8-231">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-231">String</span></span>|  
|<span data-ttu-id="9a3f8-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="9a3f8-233">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-233">Int32</span></span>|  
|<span data-ttu-id="9a3f8-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="9a3f8-235">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-235">Int32</span></span>|  
|<span data-ttu-id="9a3f8-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a3f8-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="9a3f8-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-237">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a3f8-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="9a3f8-239">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-239">String</span></span>|  
|<span data-ttu-id="9a3f8-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-240">IS_NULLABLE</span></span>|<span data-ttu-id="9a3f8-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-241">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-242">DATA_TYPE</span></span>|<span data-ttu-id="9a3f8-243">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-243">Int32</span></span>|  
|<span data-ttu-id="9a3f8-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9a3f8-245">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-245">Int64</span></span>|  
|<span data-ttu-id="9a3f8-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9a3f8-247">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-247">Int64</span></span>|  
|<span data-ttu-id="9a3f8-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9a3f8-249">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-249">Int32</span></span>|  
|<span data-ttu-id="9a3f8-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="9a3f8-251">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-251">Int16</span></span>|  
|<span data-ttu-id="9a3f8-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-252">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-253">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-253">String</span></span>|  
|<span data-ttu-id="9a3f8-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-254">TYPE_NAME</span></span>|<span data-ttu-id="9a3f8-255">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-255">String</span></span>|  
|<span data-ttu-id="9a3f8-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="9a3f8-257">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="9a3f8-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="9a3f8-258">Catalog</span></span>  
  
|<span data-ttu-id="9a3f8-259">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-259">ColumnName</span></span>|<span data-ttu-id="9a3f8-260">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-261">CATALOG_NAME</span></span>|<span data-ttu-id="9a3f8-262">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-262">String</span></span>|  
|<span data-ttu-id="9a3f8-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-263">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-264">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9a3f8-265">Index</span><span class="sxs-lookup"><span data-stu-id="9a3f8-265">Indexes</span></span>  
  
|<span data-ttu-id="9a3f8-266">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-266">ColumnName</span></span>|<span data-ttu-id="9a3f8-267">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-268">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-269">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-269">String</span></span>|  
|<span data-ttu-id="9a3f8-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-271">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-271">String</span></span>|  
|<span data-ttu-id="9a3f8-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-272">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-273">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-273">String</span></span>|  
|<span data-ttu-id="9a3f8-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-274">INDEX_CATALOG</span></span>|<span data-ttu-id="9a3f8-275">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-275">String</span></span>|  
|<span data-ttu-id="9a3f8-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="9a3f8-277">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-277">String</span></span>|  
|<span data-ttu-id="9a3f8-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-278">INDEX_NAME</span></span>|<span data-ttu-id="9a3f8-279">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-279">String</span></span>|  
|<span data-ttu-id="9a3f8-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="9a3f8-280">PRIMARY_KEY</span></span>|<span data-ttu-id="9a3f8-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-281">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-282">UNIQUE</span></span>|<span data-ttu-id="9a3f8-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-283">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-284">CLUSTERED</span></span>|<span data-ttu-id="9a3f8-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-285">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-286">TYPE</span></span>|<span data-ttu-id="9a3f8-287">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-287">Int32</span></span>|  
|<span data-ttu-id="9a3f8-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="9a3f8-288">FILL_FACTOR</span></span>|<span data-ttu-id="9a3f8-289">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-289">Int32</span></span>|  
|<span data-ttu-id="9a3f8-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-290">INITIAL_SIZE</span></span>|<span data-ttu-id="9a3f8-291">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-291">Int32</span></span>|  
|<span data-ttu-id="9a3f8-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-292">NULLS</span></span>|<span data-ttu-id="9a3f8-293">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-293">Int32</span></span>|  
|<span data-ttu-id="9a3f8-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="9a3f8-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-295">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-296">AUTO_UPDATE</span></span>|<span data-ttu-id="9a3f8-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-297">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-298">NULL_COLLATION</span></span>|<span data-ttu-id="9a3f8-299">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-299">Int32</span></span>|  
|<span data-ttu-id="9a3f8-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="9a3f8-301">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-301">Int64</span></span>|  
|<span data-ttu-id="9a3f8-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-302">COLUMN_NAME</span></span>|<span data-ttu-id="9a3f8-303">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-303">String</span></span>|  
|<span data-ttu-id="9a3f8-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-304">COLUMN_GUID</span></span>|<span data-ttu-id="9a3f8-305">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-305">Guid</span></span>|  
|<span data-ttu-id="9a3f8-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-306">COLUMN_PROPID</span></span>|<span data-ttu-id="9a3f8-307">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-307">Int64</span></span>|  
|<span data-ttu-id="9a3f8-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-308">COLLATION</span></span>|<span data-ttu-id="9a3f8-309">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-309">Int16</span></span>|  
|<span data-ttu-id="9a3f8-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="9a3f8-310">CARDINALITY</span></span>|<span data-ttu-id="9a3f8-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="9a3f8-311">Decimal</span></span>|  
|<span data-ttu-id="9a3f8-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="9a3f8-312">PAGES</span></span>|<span data-ttu-id="9a3f8-313">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-313">Int32</span></span>|  
|<span data-ttu-id="9a3f8-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-314">FILTER_CONDITION</span></span>|<span data-ttu-id="9a3f8-315">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-315">String</span></span>|  
|<span data-ttu-id="9a3f8-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-316">INTEGRATED</span></span>|<span data-ttu-id="9a3f8-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="9a3f8-318">Fournisseur Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="9a3f8-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="9a3f8-319">Le pilote Microsoft Oracle OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="9a3f8-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9a3f8-320">Tables</span><span class="sxs-lookup"><span data-stu-id="9a3f8-320">Tables</span></span>  
  
-   <span data-ttu-id="9a3f8-321">Columns</span><span class="sxs-lookup"><span data-stu-id="9a3f8-321">Columns</span></span>  
  
-   <span data-ttu-id="9a3f8-322">Procédures</span><span class="sxs-lookup"><span data-stu-id="9a3f8-322">Procedures</span></span>  
  
-   <span data-ttu-id="9a3f8-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9a3f8-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="9a3f8-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9a3f8-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9a3f8-325">Vues</span><span class="sxs-lookup"><span data-stu-id="9a3f8-325">Views</span></span>  
  
-   <span data-ttu-id="9a3f8-326">Index</span><span class="sxs-lookup"><span data-stu-id="9a3f8-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="9a3f8-327">Tables</span><span class="sxs-lookup"><span data-stu-id="9a3f8-327">Tables</span></span>  
  
|<span data-ttu-id="9a3f8-328">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-328">ColumnName</span></span>|<span data-ttu-id="9a3f8-329">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-330">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-331">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-331">String</span></span>|  
|<span data-ttu-id="9a3f8-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-333">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-333">String</span></span>|  
|<span data-ttu-id="9a3f8-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-334">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-335">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-335">String</span></span>|  
|<span data-ttu-id="9a3f8-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-336">TABLE_TYPE</span></span>|<span data-ttu-id="9a3f8-337">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-337">String</span></span>|  
|<span data-ttu-id="9a3f8-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-338">TABLE_GUID</span></span>|<span data-ttu-id="9a3f8-339">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-339">Guid</span></span>|  
|<span data-ttu-id="9a3f8-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-340">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-341">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-341">String</span></span>|  
|<span data-ttu-id="9a3f8-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-342">TABLE_PROPID</span></span>|<span data-ttu-id="9a3f8-343">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-343">Int64</span></span>|  
|<span data-ttu-id="9a3f8-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-344">DATE_CREATED</span></span>|<span data-ttu-id="9a3f8-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-345">DateTime</span></span>|  
|<span data-ttu-id="9a3f8-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-346">DATE_MODIFIED</span></span>|<span data-ttu-id="9a3f8-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9a3f8-348">Columns</span><span class="sxs-lookup"><span data-stu-id="9a3f8-348">Columns</span></span>  
  
|<span data-ttu-id="9a3f8-349">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-349">ColumnName</span></span>|<span data-ttu-id="9a3f8-350">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-351">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-352">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-352">String</span></span>|  
|<span data-ttu-id="9a3f8-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-354">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-354">String</span></span>|  
|<span data-ttu-id="9a3f8-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-355">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-356">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-356">String</span></span>|  
|<span data-ttu-id="9a3f8-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-357">COLUMN_NAME</span></span>|<span data-ttu-id="9a3f8-358">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-358">String</span></span>|  
|<span data-ttu-id="9a3f8-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-359">COLUMN_GUID</span></span>|<span data-ttu-id="9a3f8-360">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-360">Guid</span></span>|  
|<span data-ttu-id="9a3f8-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-361">COLUMN_PROPID</span></span>|<span data-ttu-id="9a3f8-362">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-362">Int64</span></span>|  
|<span data-ttu-id="9a3f8-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="9a3f8-364">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-364">Int64</span></span>|  
|<span data-ttu-id="9a3f8-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a3f8-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="9a3f8-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-366">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a3f8-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="9a3f8-368">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-368">String</span></span>|  
|<span data-ttu-id="9a3f8-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="9a3f8-370">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-370">Int64</span></span>|  
|<span data-ttu-id="9a3f8-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-371">IS_NULLABLE</span></span>|<span data-ttu-id="9a3f8-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-372">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-373">DATA_TYPE</span></span>|<span data-ttu-id="9a3f8-374">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-374">Int32</span></span>|  
|<span data-ttu-id="9a3f8-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-375">TYPE_GUID</span></span>|<span data-ttu-id="9a3f8-376">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-376">Guid</span></span>|  
|<span data-ttu-id="9a3f8-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9a3f8-378">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-378">Int64</span></span>|  
|<span data-ttu-id="9a3f8-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9a3f8-380">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-380">Int64</span></span>|  
|<span data-ttu-id="9a3f8-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9a3f8-382">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-382">Int32</span></span>|  
|<span data-ttu-id="9a3f8-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="9a3f8-384">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-384">Int16</span></span>|  
|<span data-ttu-id="9a3f8-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="9a3f8-386">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-386">Int64</span></span>|  
|<span data-ttu-id="9a3f8-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="9a3f8-388">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-388">String</span></span>|  
|<span data-ttu-id="9a3f8-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="9a3f8-390">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-390">String</span></span>|  
|<span data-ttu-id="9a3f8-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="9a3f8-392">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-392">String</span></span>|  
|<span data-ttu-id="9a3f8-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="9a3f8-394">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-394">String</span></span>|  
|<span data-ttu-id="9a3f8-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="9a3f8-396">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-396">String</span></span>|  
|<span data-ttu-id="9a3f8-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-397">COLLATION_NAME</span></span>|<span data-ttu-id="9a3f8-398">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-398">String</span></span>|  
|<span data-ttu-id="9a3f8-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="9a3f8-400">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-400">String</span></span>|  
|<span data-ttu-id="9a3f8-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="9a3f8-402">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-402">String</span></span>|  
|<span data-ttu-id="9a3f8-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-403">DOMAIN_NAME</span></span>|<span data-ttu-id="9a3f8-404">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-404">String</span></span>|  
|<span data-ttu-id="9a3f8-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-405">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-406">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9a3f8-407">Procédures</span><span class="sxs-lookup"><span data-stu-id="9a3f8-407">Procedures</span></span>  
  
|<span data-ttu-id="9a3f8-408">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-408">ColumnName</span></span>|<span data-ttu-id="9a3f8-409">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9a3f8-411">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-411">String</span></span>|  
|<span data-ttu-id="9a3f8-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-413">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-413">String</span></span>|  
|<span data-ttu-id="9a3f8-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="9a3f8-415">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-415">String</span></span>|  
|<span data-ttu-id="9a3f8-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9a3f8-417">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-417">Int16</span></span>|  
|<span data-ttu-id="9a3f8-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="9a3f8-419">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-419">String</span></span>|  
|<span data-ttu-id="9a3f8-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-420">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-421">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-421">String</span></span>|  
|<span data-ttu-id="9a3f8-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-422">DATE_CREATED</span></span>|<span data-ttu-id="9a3f8-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-423">DateTime</span></span>|  
|<span data-ttu-id="9a3f8-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-424">DATE_MODIFIED</span></span>|<span data-ttu-id="9a3f8-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="9a3f8-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9a3f8-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="9a3f8-427">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-427">ColumnName</span></span>|<span data-ttu-id="9a3f8-428">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9a3f8-430">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-430">String</span></span>|  
|<span data-ttu-id="9a3f8-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-432">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-432">String</span></span>|  
|<span data-ttu-id="9a3f8-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="9a3f8-434">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-434">String</span></span>|  
|<span data-ttu-id="9a3f8-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-435">COLUMN_NAME</span></span>|<span data-ttu-id="9a3f8-436">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-436">String</span></span>|  
|<span data-ttu-id="9a3f8-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-437">COLUMN_GUID</span></span>|<span data-ttu-id="9a3f8-438">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-438">Guid</span></span>|  
|<span data-ttu-id="9a3f8-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-439">COLUMN_PROPID</span></span>|<span data-ttu-id="9a3f8-440">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-440">Int64</span></span>|  
|<span data-ttu-id="9a3f8-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="9a3f8-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="9a3f8-442">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-442">Int64</span></span>|  
|<span data-ttu-id="9a3f8-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="9a3f8-444">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-444">Int64</span></span>|  
|<span data-ttu-id="9a3f8-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-445">IS_NULLABLE</span></span>|<span data-ttu-id="9a3f8-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-446">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-447">DATA_TYPE</span></span>|<span data-ttu-id="9a3f8-448">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-448">Int32</span></span>|  
|<span data-ttu-id="9a3f8-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-449">TYPE_GUID</span></span>|<span data-ttu-id="9a3f8-450">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-450">Guid</span></span>|  
|<span data-ttu-id="9a3f8-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9a3f8-452">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-452">Int64</span></span>|  
|<span data-ttu-id="9a3f8-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9a3f8-454">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-454">Int64</span></span>|  
|<span data-ttu-id="9a3f8-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9a3f8-456">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-456">Int32</span></span>|  
|<span data-ttu-id="9a3f8-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="9a3f8-458">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-458">Int16</span></span>|  
|<span data-ttu-id="9a3f8-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-459">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-460">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-460">String</span></span>|  
|<span data-ttu-id="9a3f8-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="9a3f8-461">OVERLOAD</span></span>|<span data-ttu-id="9a3f8-462">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="9a3f8-463">Vues</span><span class="sxs-lookup"><span data-stu-id="9a3f8-463">Views</span></span>  
  
|<span data-ttu-id="9a3f8-464">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-464">ColumnName</span></span>|<span data-ttu-id="9a3f8-465">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-466">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-467">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-467">String</span></span>|  
|<span data-ttu-id="9a3f8-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-469">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-469">String</span></span>|  
|<span data-ttu-id="9a3f8-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-470">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-471">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-471">String</span></span>|  
|<span data-ttu-id="9a3f8-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="9a3f8-473">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-473">String</span></span>|  
|<span data-ttu-id="9a3f8-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-474">CHECK_OPTION</span></span>|<span data-ttu-id="9a3f8-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-475">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-476">IS_UPDATABLE</span></span>|<span data-ttu-id="9a3f8-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-477">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-478">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-479">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-479">String</span></span>|  
|<span data-ttu-id="9a3f8-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-480">DATE_CREATED</span></span>|<span data-ttu-id="9a3f8-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-481">DateTime</span></span>|  
|<span data-ttu-id="9a3f8-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-482">DATE_MODIFIED</span></span>|<span data-ttu-id="9a3f8-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9a3f8-484">Index</span><span class="sxs-lookup"><span data-stu-id="9a3f8-484">Indexes</span></span>  
  
|<span data-ttu-id="9a3f8-485">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-485">ColumnName</span></span>|<span data-ttu-id="9a3f8-486">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-487">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-488">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-488">String</span></span>|  
|<span data-ttu-id="9a3f8-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-490">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-490">String</span></span>|  
|<span data-ttu-id="9a3f8-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-491">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-492">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-492">String</span></span>|  
|<span data-ttu-id="9a3f8-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-493">INDEX_CATALOG</span></span>|<span data-ttu-id="9a3f8-494">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-494">String</span></span>|  
|<span data-ttu-id="9a3f8-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="9a3f8-496">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-496">String</span></span>|  
|<span data-ttu-id="9a3f8-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-497">INDEX_NAME</span></span>|<span data-ttu-id="9a3f8-498">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-498">String</span></span>|  
|<span data-ttu-id="9a3f8-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="9a3f8-499">PRIMARY_KEY</span></span>|<span data-ttu-id="9a3f8-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-500">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-501">UNIQUE</span></span>|<span data-ttu-id="9a3f8-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-502">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-503">CLUSTERED</span></span>|<span data-ttu-id="9a3f8-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-504">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-505">TYPE</span></span>|<span data-ttu-id="9a3f8-506">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-506">Int32</span></span>|  
|<span data-ttu-id="9a3f8-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="9a3f8-507">FILL_FACTOR</span></span>|<span data-ttu-id="9a3f8-508">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-508">Int32</span></span>|  
|<span data-ttu-id="9a3f8-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-509">INITIAL_SIZE</span></span>|<span data-ttu-id="9a3f8-510">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-510">Int32</span></span>|  
|<span data-ttu-id="9a3f8-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-511">NULLS</span></span>|<span data-ttu-id="9a3f8-512">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-512">Int32</span></span>|  
|<span data-ttu-id="9a3f8-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="9a3f8-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-514">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-515">AUTO_UPDATE</span></span>|<span data-ttu-id="9a3f8-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-516">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-517">NULL_COLLATION</span></span>|<span data-ttu-id="9a3f8-518">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-518">Int32</span></span>|  
|<span data-ttu-id="9a3f8-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="9a3f8-520">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-520">Int64</span></span>|  
|<span data-ttu-id="9a3f8-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-521">COLUMN_NAME</span></span>|<span data-ttu-id="9a3f8-522">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-522">String</span></span>|  
|<span data-ttu-id="9a3f8-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-523">COLUMN_GUID</span></span>|<span data-ttu-id="9a3f8-524">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-524">Guid</span></span>|  
|<span data-ttu-id="9a3f8-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-525">COLUMN_PROPID</span></span>|<span data-ttu-id="9a3f8-526">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-526">Int64</span></span>|  
|<span data-ttu-id="9a3f8-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-527">COLLATION</span></span>|<span data-ttu-id="9a3f8-528">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-528">Int16</span></span>|  
|<span data-ttu-id="9a3f8-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="9a3f8-529">CARDINALITY</span></span>|<span data-ttu-id="9a3f8-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="9a3f8-530">Decimal</span></span>|  
|<span data-ttu-id="9a3f8-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="9a3f8-531">PAGES</span></span>|<span data-ttu-id="9a3f8-532">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-532">Int32</span></span>|  
|<span data-ttu-id="9a3f8-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-533">FILTER_CONDITION</span></span>|<span data-ttu-id="9a3f8-534">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-534">String</span></span>|  
|<span data-ttu-id="9a3f8-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-535">INTEGRATED</span></span>|<span data-ttu-id="9a3f8-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="9a3f8-537">Fournisseur Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="9a3f8-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="9a3f8-538">Le pilote Microsoft Jet OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="9a3f8-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9a3f8-539">Tables</span><span class="sxs-lookup"><span data-stu-id="9a3f8-539">Tables</span></span>  
  
-   <span data-ttu-id="9a3f8-540">Columns</span><span class="sxs-lookup"><span data-stu-id="9a3f8-540">Columns</span></span>  
  
-   <span data-ttu-id="9a3f8-541">Procédures</span><span class="sxs-lookup"><span data-stu-id="9a3f8-541">Procedures</span></span>  
  
-   <span data-ttu-id="9a3f8-542">Vues</span><span class="sxs-lookup"><span data-stu-id="9a3f8-542">Views</span></span>  
  
-   <span data-ttu-id="9a3f8-543">Index</span><span class="sxs-lookup"><span data-stu-id="9a3f8-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="9a3f8-544">Tables</span><span class="sxs-lookup"><span data-stu-id="9a3f8-544">Tables</span></span>  
  
|<span data-ttu-id="9a3f8-545">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-545">ColumnName</span></span>|<span data-ttu-id="9a3f8-546">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-547">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-548">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-548">String</span></span>|  
|<span data-ttu-id="9a3f8-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-550">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-550">String</span></span>|  
|<span data-ttu-id="9a3f8-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-551">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-552">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-552">String</span></span>|  
|<span data-ttu-id="9a3f8-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-553">TABLE_TYPE</span></span>|<span data-ttu-id="9a3f8-554">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-554">String</span></span>|  
|<span data-ttu-id="9a3f8-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-555">TABLE_GUID</span></span>|<span data-ttu-id="9a3f8-556">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-556">Guid</span></span>|  
|<span data-ttu-id="9a3f8-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-557">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-558">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-558">String</span></span>|  
|<span data-ttu-id="9a3f8-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-559">TABLE_PROPID</span></span>|<span data-ttu-id="9a3f8-560">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-560">Int64</span></span>|  
|<span data-ttu-id="9a3f8-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-561">DATE_CREATED</span></span>|<span data-ttu-id="9a3f8-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-562">DateTime</span></span>|  
|<span data-ttu-id="9a3f8-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-563">DATE_MODIFIED</span></span>|<span data-ttu-id="9a3f8-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9a3f8-565">Columns</span><span class="sxs-lookup"><span data-stu-id="9a3f8-565">Columns</span></span>  
  
|<span data-ttu-id="9a3f8-566">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-566">ColumnName</span></span>|<span data-ttu-id="9a3f8-567">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-568">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-569">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-569">String</span></span>|  
|<span data-ttu-id="9a3f8-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-571">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-571">String</span></span>|  
|<span data-ttu-id="9a3f8-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-572">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-573">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-573">String</span></span>|  
|<span data-ttu-id="9a3f8-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-574">COLUMN_NAME</span></span>|<span data-ttu-id="9a3f8-575">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-575">String</span></span>|  
|<span data-ttu-id="9a3f8-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-576">COLUMN_GUID</span></span>|<span data-ttu-id="9a3f8-577">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-577">Guid</span></span>|  
|<span data-ttu-id="9a3f8-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-578">COLUMN_PROPID</span></span>|<span data-ttu-id="9a3f8-579">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-579">Int64</span></span>|  
|<span data-ttu-id="9a3f8-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="9a3f8-581">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-581">Int64</span></span>|  
|<span data-ttu-id="9a3f8-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a3f8-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="9a3f8-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-583">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9a3f8-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="9a3f8-585">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-585">String</span></span>|  
|<span data-ttu-id="9a3f8-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="9a3f8-587">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-587">Int64</span></span>|  
|<span data-ttu-id="9a3f8-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-588">IS_NULLABLE</span></span>|<span data-ttu-id="9a3f8-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-589">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-590">DATA_TYPE</span></span>|<span data-ttu-id="9a3f8-591">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-591">Int32</span></span>|  
|<span data-ttu-id="9a3f8-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-592">TYPE_GUID</span></span>|<span data-ttu-id="9a3f8-593">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-593">Guid</span></span>|  
|<span data-ttu-id="9a3f8-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="9a3f8-595">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-595">Int64</span></span>|  
|<span data-ttu-id="9a3f8-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9a3f8-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="9a3f8-597">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-597">Int64</span></span>|  
|<span data-ttu-id="9a3f8-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="9a3f8-599">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-599">Int32</span></span>|  
|<span data-ttu-id="9a3f8-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="9a3f8-601">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-601">Int16</span></span>|  
|<span data-ttu-id="9a3f8-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="9a3f8-603">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-603">Int64</span></span>|  
|<span data-ttu-id="9a3f8-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="9a3f8-605">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-605">String</span></span>|  
|<span data-ttu-id="9a3f8-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="9a3f8-607">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-607">String</span></span>|  
|<span data-ttu-id="9a3f8-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="9a3f8-609">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-609">String</span></span>|  
|<span data-ttu-id="9a3f8-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="9a3f8-611">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-611">String</span></span>|  
|<span data-ttu-id="9a3f8-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="9a3f8-613">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-613">String</span></span>|  
|<span data-ttu-id="9a3f8-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-614">COLLATION_NAME</span></span>|<span data-ttu-id="9a3f8-615">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-615">String</span></span>|  
|<span data-ttu-id="9a3f8-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="9a3f8-617">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-617">String</span></span>|  
|<span data-ttu-id="9a3f8-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="9a3f8-619">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-619">String</span></span>|  
|<span data-ttu-id="9a3f8-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-620">DOMAIN_NAME</span></span>|<span data-ttu-id="9a3f8-621">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-621">String</span></span>|  
|<span data-ttu-id="9a3f8-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-622">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-623">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9a3f8-624">Procédures</span><span class="sxs-lookup"><span data-stu-id="9a3f8-624">Procedures</span></span>  
  
|<span data-ttu-id="9a3f8-625">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-625">ColumnName</span></span>|<span data-ttu-id="9a3f8-626">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="9a3f8-628">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-628">String</span></span>|  
|<span data-ttu-id="9a3f8-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-630">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-630">String</span></span>|  
|<span data-ttu-id="9a3f8-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="9a3f8-632">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-632">String</span></span>|  
|<span data-ttu-id="9a3f8-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9a3f8-634">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-634">Int16</span></span>|  
|<span data-ttu-id="9a3f8-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="9a3f8-636">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-636">String</span></span>|  
|<span data-ttu-id="9a3f8-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-637">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-638">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-638">String</span></span>|  
|<span data-ttu-id="9a3f8-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-639">DATE_CREATED</span></span>|<span data-ttu-id="9a3f8-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-640">DateTime</span></span>|  
|<span data-ttu-id="9a3f8-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-641">DATE_MODIFIED</span></span>|<span data-ttu-id="9a3f8-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="9a3f8-643">Vues</span><span class="sxs-lookup"><span data-stu-id="9a3f8-643">Views</span></span>  
  
|<span data-ttu-id="9a3f8-644">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-644">ColumnName</span></span>|<span data-ttu-id="9a3f8-645">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-646">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-647">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-647">String</span></span>|  
|<span data-ttu-id="9a3f8-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-649">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-649">String</span></span>|  
|<span data-ttu-id="9a3f8-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-650">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-651">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-651">String</span></span>|  
|<span data-ttu-id="9a3f8-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="9a3f8-653">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-653">String</span></span>|  
|<span data-ttu-id="9a3f8-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-654">CHECK_OPTION</span></span>|<span data-ttu-id="9a3f8-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-655">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-656">IS_UPDATABLE</span></span>|<span data-ttu-id="9a3f8-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-657">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-658">DESCRIPTION</span></span>|<span data-ttu-id="9a3f8-659">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-659">String</span></span>|  
|<span data-ttu-id="9a3f8-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-660">DATE_CREATED</span></span>|<span data-ttu-id="9a3f8-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-661">DateTime</span></span>|  
|<span data-ttu-id="9a3f8-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-662">DATE_MODIFIED</span></span>|<span data-ttu-id="9a3f8-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a3f8-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9a3f8-664">Index</span><span class="sxs-lookup"><span data-stu-id="9a3f8-664">Indexes</span></span>  
  
|<span data-ttu-id="9a3f8-665">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-665">ColumnName</span></span>|<span data-ttu-id="9a3f8-666">Type de données</span><span class="sxs-lookup"><span data-stu-id="9a3f8-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9a3f8-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-667">TABLE_CATALOG</span></span>|<span data-ttu-id="9a3f8-668">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-668">String</span></span>|  
|<span data-ttu-id="9a3f8-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="9a3f8-670">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-670">String</span></span>|  
|<span data-ttu-id="9a3f8-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-671">TABLE_NAME</span></span>|<span data-ttu-id="9a3f8-672">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-672">String</span></span>|  
|<span data-ttu-id="9a3f8-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9a3f8-673">INDEX_CATALOG</span></span>|<span data-ttu-id="9a3f8-674">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-674">String</span></span>|  
|<span data-ttu-id="9a3f8-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9a3f8-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="9a3f8-676">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-676">String</span></span>|  
|<span data-ttu-id="9a3f8-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-677">INDEX_NAME</span></span>|<span data-ttu-id="9a3f8-678">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-678">String</span></span>|  
|<span data-ttu-id="9a3f8-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="9a3f8-679">PRIMARY_KEY</span></span>|<span data-ttu-id="9a3f8-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-680">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-681">UNIQUE</span></span>|<span data-ttu-id="9a3f8-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-682">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-683">CLUSTERED</span></span>|<span data-ttu-id="9a3f8-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-684">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-685">TYPE</span></span>|<span data-ttu-id="9a3f8-686">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-686">Int32</span></span>|  
|<span data-ttu-id="9a3f8-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="9a3f8-687">FILL_FACTOR</span></span>|<span data-ttu-id="9a3f8-688">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-688">Int32</span></span>|  
|<span data-ttu-id="9a3f8-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-689">INITIAL_SIZE</span></span>|<span data-ttu-id="9a3f8-690">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-690">Int32</span></span>|  
|<span data-ttu-id="9a3f8-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-691">NULLS</span></span>|<span data-ttu-id="9a3f8-692">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-692">Int32</span></span>|  
|<span data-ttu-id="9a3f8-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="9a3f8-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="9a3f8-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-694">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="9a3f8-695">AUTO_UPDATE</span></span>|<span data-ttu-id="9a3f8-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="9a3f8-696">Boolean</span></span>|  
|<span data-ttu-id="9a3f8-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-697">NULL_COLLATION</span></span>|<span data-ttu-id="9a3f8-698">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-698">Int32</span></span>|  
|<span data-ttu-id="9a3f8-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="9a3f8-700">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-700">Int64</span></span>|  
|<span data-ttu-id="9a3f8-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9a3f8-701">COLUMN_NAME</span></span>|<span data-ttu-id="9a3f8-702">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-702">String</span></span>|  
|<span data-ttu-id="9a3f8-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-703">COLUMN_GUID</span></span>|<span data-ttu-id="9a3f8-704">Guid</span><span class="sxs-lookup"><span data-stu-id="9a3f8-704">Guid</span></span>|  
|<span data-ttu-id="9a3f8-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="9a3f8-705">COLUMN_PROPID</span></span>|<span data-ttu-id="9a3f8-706">Int64</span><span class="sxs-lookup"><span data-stu-id="9a3f8-706">Int64</span></span>|  
|<span data-ttu-id="9a3f8-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-707">COLLATION</span></span>|<span data-ttu-id="9a3f8-708">Int16</span><span class="sxs-lookup"><span data-stu-id="9a3f8-708">Int16</span></span>|  
|<span data-ttu-id="9a3f8-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="9a3f8-709">CARDINALITY</span></span>|<span data-ttu-id="9a3f8-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="9a3f8-710">Decimal</span></span>|  
|<span data-ttu-id="9a3f8-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="9a3f8-711">PAGES</span></span>|<span data-ttu-id="9a3f8-712">Int32</span><span class="sxs-lookup"><span data-stu-id="9a3f8-712">Int32</span></span>|  
|<span data-ttu-id="9a3f8-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="9a3f8-713">FILTER_CONDITION</span></span>|<span data-ttu-id="9a3f8-714">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9a3f8-714">String</span></span>|  
|<span data-ttu-id="9a3f8-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="9a3f8-715">INTEGRATED</span></span>|<span data-ttu-id="9a3f8-716">Booléen</span><span class="sxs-lookup"><span data-stu-id="9a3f8-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a3f8-717">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a3f8-717">See Also</span></span>  
 [<span data-ttu-id="9a3f8-718">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="9a3f8-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
