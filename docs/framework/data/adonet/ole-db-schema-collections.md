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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33e794559abd7f619f7431683f06e59705b57d41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="dc318-102">Collections de schémas OLE DB</span><span class="sxs-lookup"><span data-stu-id="dc318-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="dc318-103">Cette section traite de la prise en charge des collections de schémas pour les fournisseurs OLE DB de Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="dc318-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="dc318-104">Fournisseur Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="dc318-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="dc318-105">Le pilote OLE DB Microsoft SQL Server prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="dc318-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dc318-106">Tables</span><span class="sxs-lookup"><span data-stu-id="dc318-106">Tables</span></span>  
  
-   <span data-ttu-id="dc318-107">Columns</span><span class="sxs-lookup"><span data-stu-id="dc318-107">Columns</span></span>  
  
-   <span data-ttu-id="dc318-108">Procédures</span><span class="sxs-lookup"><span data-stu-id="dc318-108">Procedures</span></span>  
  
-   <span data-ttu-id="dc318-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dc318-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="dc318-110">Catalogue</span><span class="sxs-lookup"><span data-stu-id="dc318-110">Catalog</span></span>  
  
-   <span data-ttu-id="dc318-111">Index</span><span class="sxs-lookup"><span data-stu-id="dc318-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="dc318-112">Tables</span><span class="sxs-lookup"><span data-stu-id="dc318-112">Tables</span></span>  
  
|<span data-ttu-id="dc318-113">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-113">ColumnName</span></span>|<span data-ttu-id="dc318-114">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-115">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-116">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-116">String</span></span>|  
|<span data-ttu-id="dc318-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-118">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-118">String</span></span>|  
|<span data-ttu-id="dc318-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-119">TABLE_NAME</span></span>|<span data-ttu-id="dc318-120">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-120">String</span></span>|  
|<span data-ttu-id="dc318-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-121">TABLE_TYPE</span></span>|<span data-ttu-id="dc318-122">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-122">String</span></span>|  
|<span data-ttu-id="dc318-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-123">TABLE_GUID</span></span>|<span data-ttu-id="dc318-124">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-124">Guid</span></span>|  
|<span data-ttu-id="dc318-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-125">DESCRIPTION</span></span>|<span data-ttu-id="dc318-126">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-126">String</span></span>|  
|<span data-ttu-id="dc318-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-127">TABLE_PROPID</span></span>|<span data-ttu-id="dc318-128">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-128">Int64</span></span>|  
|<span data-ttu-id="dc318-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="dc318-129">DATE_CREATED</span></span>|<span data-ttu-id="dc318-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-130">DateTime</span></span>|  
|<span data-ttu-id="dc318-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="dc318-131">DATE_MODIFIED</span></span>|<span data-ttu-id="dc318-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dc318-133">Columns</span><span class="sxs-lookup"><span data-stu-id="dc318-133">Columns</span></span>  
  
|<span data-ttu-id="dc318-134">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-134">ColumnName</span></span>|<span data-ttu-id="dc318-135">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-136">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-137">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-137">String</span></span>|  
|<span data-ttu-id="dc318-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-139">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-139">String</span></span>|  
|<span data-ttu-id="dc318-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-140">TABLE_NAME</span></span>|<span data-ttu-id="dc318-141">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-141">String</span></span>|  
|<span data-ttu-id="dc318-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-142">COLUMN_NAME</span></span>|<span data-ttu-id="dc318-143">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-143">String</span></span>|  
|<span data-ttu-id="dc318-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-144">COLUMN_GUID</span></span>|<span data-ttu-id="dc318-145">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-145">Guid</span></span>|  
|<span data-ttu-id="dc318-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-146">COLUMN_PROPID</span></span>|<span data-ttu-id="dc318-147">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-147">Int64</span></span>|  
|<span data-ttu-id="dc318-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dc318-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="dc318-149">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-149">Int64</span></span>|  
|<span data-ttu-id="dc318-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="dc318-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="dc318-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-151">Boolean</span></span>|  
|<span data-ttu-id="dc318-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="dc318-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="dc318-153">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-153">String</span></span>|  
|<span data-ttu-id="dc318-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="dc318-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="dc318-155">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-155">Int64</span></span>|  
|<span data-ttu-id="dc318-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dc318-156">IS_NULLABLE</span></span>|<span data-ttu-id="dc318-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-157">Boolean</span></span>|  
|<span data-ttu-id="dc318-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-158">DATA_TYPE</span></span>|<span data-ttu-id="dc318-159">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-159">Int32</span></span>|  
|<span data-ttu-id="dc318-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-160">TYPE_GUID</span></span>|<span data-ttu-id="dc318-161">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-161">Guid</span></span>|  
|<span data-ttu-id="dc318-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="dc318-163">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-163">Int64</span></span>|  
|<span data-ttu-id="dc318-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="dc318-165">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-165">Int64</span></span>|  
|<span data-ttu-id="dc318-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="dc318-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="dc318-167">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-167">Int32</span></span>|  
|<span data-ttu-id="dc318-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="dc318-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="dc318-169">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-169">Int16</span></span>|  
|<span data-ttu-id="dc318-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="dc318-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="dc318-171">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-171">Int64</span></span>|  
|<span data-ttu-id="dc318-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="dc318-173">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-173">String</span></span>|  
|<span data-ttu-id="dc318-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="dc318-175">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-175">String</span></span>|  
|<span data-ttu-id="dc318-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="dc318-177">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-177">String</span></span>|  
|<span data-ttu-id="dc318-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="dc318-179">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-179">String</span></span>|  
|<span data-ttu-id="dc318-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="dc318-181">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-181">String</span></span>|  
|<span data-ttu-id="dc318-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-182">COLLATION_NAME</span></span>|<span data-ttu-id="dc318-183">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-183">String</span></span>|  
|<span data-ttu-id="dc318-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="dc318-185">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-185">String</span></span>|  
|<span data-ttu-id="dc318-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="dc318-187">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-187">String</span></span>|  
|<span data-ttu-id="dc318-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-188">DOMAIN_NAME</span></span>|<span data-ttu-id="dc318-189">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-189">String</span></span>|  
|<span data-ttu-id="dc318-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-190">DESCRIPTION</span></span>|<span data-ttu-id="dc318-191">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-191">String</span></span>|  
|<span data-ttu-id="dc318-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="dc318-192">COLUMN_LCID</span></span>|<span data-ttu-id="dc318-193">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-193">Int32</span></span>|  
|<span data-ttu-id="dc318-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="dc318-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="dc318-195">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-195">Int32</span></span>|  
|<span data-ttu-id="dc318-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="dc318-196">COLUMN_SORTID</span></span>|<span data-ttu-id="dc318-197">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-197">Int32</span></span>|  
|<span data-ttu-id="dc318-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="dc318-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="dc318-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="dc318-199">Byte[]</span></span>|  
|<span data-ttu-id="dc318-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="dc318-200">IS_COMPUTED</span></span>|<span data-ttu-id="dc318-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dc318-202">Procédures</span><span class="sxs-lookup"><span data-stu-id="dc318-202">Procedures</span></span>  
  
|<span data-ttu-id="dc318-203">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-203">ColumnName</span></span>|<span data-ttu-id="dc318-204">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="dc318-206">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-206">String</span></span>|  
|<span data-ttu-id="dc318-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="dc318-208">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-208">String</span></span>|  
|<span data-ttu-id="dc318-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="dc318-210">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-210">String</span></span>|  
|<span data-ttu-id="dc318-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dc318-212">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-212">Int16</span></span>|  
|<span data-ttu-id="dc318-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="dc318-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="dc318-214">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-214">String</span></span>|  
|<span data-ttu-id="dc318-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-215">DESCRIPTION</span></span>|<span data-ttu-id="dc318-216">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-216">String</span></span>|  
|<span data-ttu-id="dc318-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="dc318-217">DATE_CREATED</span></span>|<span data-ttu-id="dc318-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-218">DateTime</span></span>|  
|<span data-ttu-id="dc318-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="dc318-219">DATE_MODIFIED</span></span>|<span data-ttu-id="dc318-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="dc318-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dc318-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="dc318-222">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-222">ColumnName</span></span>|<span data-ttu-id="dc318-223">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="dc318-225">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-225">String</span></span>|  
|<span data-ttu-id="dc318-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="dc318-227">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-227">String</span></span>|  
|<span data-ttu-id="dc318-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="dc318-229">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-229">String</span></span>|  
|<span data-ttu-id="dc318-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-230">PARAMETER_NAME</span></span>|<span data-ttu-id="dc318-231">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-231">String</span></span>|  
|<span data-ttu-id="dc318-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dc318-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="dc318-233">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-233">Int32</span></span>|  
|<span data-ttu-id="dc318-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="dc318-235">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-235">Int32</span></span>|  
|<span data-ttu-id="dc318-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="dc318-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="dc318-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-237">Boolean</span></span>|  
|<span data-ttu-id="dc318-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="dc318-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="dc318-239">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-239">String</span></span>|  
|<span data-ttu-id="dc318-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dc318-240">IS_NULLABLE</span></span>|<span data-ttu-id="dc318-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-241">Boolean</span></span>|  
|<span data-ttu-id="dc318-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-242">DATA_TYPE</span></span>|<span data-ttu-id="dc318-243">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-243">Int32</span></span>|  
|<span data-ttu-id="dc318-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="dc318-245">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-245">Int64</span></span>|  
|<span data-ttu-id="dc318-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="dc318-247">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-247">Int64</span></span>|  
|<span data-ttu-id="dc318-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="dc318-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="dc318-249">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-249">Int32</span></span>|  
|<span data-ttu-id="dc318-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="dc318-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="dc318-251">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-251">Int16</span></span>|  
|<span data-ttu-id="dc318-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-252">DESCRIPTION</span></span>|<span data-ttu-id="dc318-253">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-253">String</span></span>|  
|<span data-ttu-id="dc318-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-254">TYPE_NAME</span></span>|<span data-ttu-id="dc318-255">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-255">String</span></span>|  
|<span data-ttu-id="dc318-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="dc318-257">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="dc318-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="dc318-258">Catalog</span></span>  
  
|<span data-ttu-id="dc318-259">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-259">ColumnName</span></span>|<span data-ttu-id="dc318-260">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-261">CATALOG_NAME</span></span>|<span data-ttu-id="dc318-262">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-262">String</span></span>|  
|<span data-ttu-id="dc318-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-263">DESCRIPTION</span></span>|<span data-ttu-id="dc318-264">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="dc318-265">Index</span><span class="sxs-lookup"><span data-stu-id="dc318-265">Indexes</span></span>  
  
|<span data-ttu-id="dc318-266">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-266">ColumnName</span></span>|<span data-ttu-id="dc318-267">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-268">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-269">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-269">String</span></span>|  
|<span data-ttu-id="dc318-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-271">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-271">String</span></span>|  
|<span data-ttu-id="dc318-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-272">TABLE_NAME</span></span>|<span data-ttu-id="dc318-273">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-273">String</span></span>|  
|<span data-ttu-id="dc318-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-274">INDEX_CATALOG</span></span>|<span data-ttu-id="dc318-275">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-275">String</span></span>|  
|<span data-ttu-id="dc318-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="dc318-277">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-277">String</span></span>|  
|<span data-ttu-id="dc318-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-278">INDEX_NAME</span></span>|<span data-ttu-id="dc318-279">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-279">String</span></span>|  
|<span data-ttu-id="dc318-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="dc318-280">PRIMARY_KEY</span></span>|<span data-ttu-id="dc318-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-281">Boolean</span></span>|  
|<span data-ttu-id="dc318-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="dc318-282">UNIQUE</span></span>|<span data-ttu-id="dc318-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-283">Boolean</span></span>|  
|<span data-ttu-id="dc318-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="dc318-284">CLUSTERED</span></span>|<span data-ttu-id="dc318-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-285">Boolean</span></span>|  
|<span data-ttu-id="dc318-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-286">TYPE</span></span>|<span data-ttu-id="dc318-287">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-287">Int32</span></span>|  
|<span data-ttu-id="dc318-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="dc318-288">FILL_FACTOR</span></span>|<span data-ttu-id="dc318-289">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-289">Int32</span></span>|  
|<span data-ttu-id="dc318-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="dc318-290">INITIAL_SIZE</span></span>|<span data-ttu-id="dc318-291">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-291">Int32</span></span>|  
|<span data-ttu-id="dc318-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="dc318-292">NULLS</span></span>|<span data-ttu-id="dc318-293">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-293">Int32</span></span>|  
|<span data-ttu-id="dc318-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="dc318-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="dc318-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-295">Boolean</span></span>|  
|<span data-ttu-id="dc318-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="dc318-296">AUTO_UPDATE</span></span>|<span data-ttu-id="dc318-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-297">Boolean</span></span>|  
|<span data-ttu-id="dc318-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="dc318-298">NULL_COLLATION</span></span>|<span data-ttu-id="dc318-299">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-299">Int32</span></span>|  
|<span data-ttu-id="dc318-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dc318-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="dc318-301">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-301">Int64</span></span>|  
|<span data-ttu-id="dc318-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-302">COLUMN_NAME</span></span>|<span data-ttu-id="dc318-303">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-303">String</span></span>|  
|<span data-ttu-id="dc318-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-304">COLUMN_GUID</span></span>|<span data-ttu-id="dc318-305">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-305">Guid</span></span>|  
|<span data-ttu-id="dc318-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-306">COLUMN_PROPID</span></span>|<span data-ttu-id="dc318-307">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-307">Int64</span></span>|  
|<span data-ttu-id="dc318-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="dc318-308">COLLATION</span></span>|<span data-ttu-id="dc318-309">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-309">Int16</span></span>|  
|<span data-ttu-id="dc318-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="dc318-310">CARDINALITY</span></span>|<span data-ttu-id="dc318-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="dc318-311">Decimal</span></span>|  
|<span data-ttu-id="dc318-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="dc318-312">PAGES</span></span>|<span data-ttu-id="dc318-313">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-313">Int32</span></span>|  
|<span data-ttu-id="dc318-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="dc318-314">FILTER_CONDITION</span></span>|<span data-ttu-id="dc318-315">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-315">String</span></span>|  
|<span data-ttu-id="dc318-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="dc318-316">INTEGRATED</span></span>|<span data-ttu-id="dc318-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="dc318-318">Fournisseur Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="dc318-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="dc318-319">Le pilote Microsoft Oracle OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="dc318-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dc318-320">Tables</span><span class="sxs-lookup"><span data-stu-id="dc318-320">Tables</span></span>  
  
-   <span data-ttu-id="dc318-321">Columns</span><span class="sxs-lookup"><span data-stu-id="dc318-321">Columns</span></span>  
  
-   <span data-ttu-id="dc318-322">Procédures</span><span class="sxs-lookup"><span data-stu-id="dc318-322">Procedures</span></span>  
  
-   <span data-ttu-id="dc318-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dc318-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="dc318-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dc318-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="dc318-325">Vues</span><span class="sxs-lookup"><span data-stu-id="dc318-325">Views</span></span>  
  
-   <span data-ttu-id="dc318-326">Index</span><span class="sxs-lookup"><span data-stu-id="dc318-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="dc318-327">Tables</span><span class="sxs-lookup"><span data-stu-id="dc318-327">Tables</span></span>  
  
|<span data-ttu-id="dc318-328">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-328">ColumnName</span></span>|<span data-ttu-id="dc318-329">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-330">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-331">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-331">String</span></span>|  
|<span data-ttu-id="dc318-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-333">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-333">String</span></span>|  
|<span data-ttu-id="dc318-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-334">TABLE_NAME</span></span>|<span data-ttu-id="dc318-335">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-335">String</span></span>|  
|<span data-ttu-id="dc318-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-336">TABLE_TYPE</span></span>|<span data-ttu-id="dc318-337">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-337">String</span></span>|  
|<span data-ttu-id="dc318-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-338">TABLE_GUID</span></span>|<span data-ttu-id="dc318-339">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-339">Guid</span></span>|  
|<span data-ttu-id="dc318-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-340">DESCRIPTION</span></span>|<span data-ttu-id="dc318-341">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-341">String</span></span>|  
|<span data-ttu-id="dc318-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-342">TABLE_PROPID</span></span>|<span data-ttu-id="dc318-343">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-343">Int64</span></span>|  
|<span data-ttu-id="dc318-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="dc318-344">DATE_CREATED</span></span>|<span data-ttu-id="dc318-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-345">DateTime</span></span>|  
|<span data-ttu-id="dc318-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="dc318-346">DATE_MODIFIED</span></span>|<span data-ttu-id="dc318-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dc318-348">Columns</span><span class="sxs-lookup"><span data-stu-id="dc318-348">Columns</span></span>  
  
|<span data-ttu-id="dc318-349">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-349">ColumnName</span></span>|<span data-ttu-id="dc318-350">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-351">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-352">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-352">String</span></span>|  
|<span data-ttu-id="dc318-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-354">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-354">String</span></span>|  
|<span data-ttu-id="dc318-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-355">TABLE_NAME</span></span>|<span data-ttu-id="dc318-356">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-356">String</span></span>|  
|<span data-ttu-id="dc318-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-357">COLUMN_NAME</span></span>|<span data-ttu-id="dc318-358">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-358">String</span></span>|  
|<span data-ttu-id="dc318-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-359">COLUMN_GUID</span></span>|<span data-ttu-id="dc318-360">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-360">Guid</span></span>|  
|<span data-ttu-id="dc318-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-361">COLUMN_PROPID</span></span>|<span data-ttu-id="dc318-362">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-362">Int64</span></span>|  
|<span data-ttu-id="dc318-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dc318-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="dc318-364">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-364">Int64</span></span>|  
|<span data-ttu-id="dc318-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="dc318-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="dc318-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-366">Boolean</span></span>|  
|<span data-ttu-id="dc318-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="dc318-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="dc318-368">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-368">String</span></span>|  
|<span data-ttu-id="dc318-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="dc318-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="dc318-370">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-370">Int64</span></span>|  
|<span data-ttu-id="dc318-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dc318-371">IS_NULLABLE</span></span>|<span data-ttu-id="dc318-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-372">Boolean</span></span>|  
|<span data-ttu-id="dc318-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-373">DATA_TYPE</span></span>|<span data-ttu-id="dc318-374">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-374">Int32</span></span>|  
|<span data-ttu-id="dc318-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-375">TYPE_GUID</span></span>|<span data-ttu-id="dc318-376">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-376">Guid</span></span>|  
|<span data-ttu-id="dc318-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="dc318-378">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-378">Int64</span></span>|  
|<span data-ttu-id="dc318-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="dc318-380">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-380">Int64</span></span>|  
|<span data-ttu-id="dc318-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="dc318-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="dc318-382">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-382">Int32</span></span>|  
|<span data-ttu-id="dc318-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="dc318-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="dc318-384">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-384">Int16</span></span>|  
|<span data-ttu-id="dc318-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="dc318-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="dc318-386">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-386">Int64</span></span>|  
|<span data-ttu-id="dc318-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="dc318-388">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-388">String</span></span>|  
|<span data-ttu-id="dc318-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="dc318-390">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-390">String</span></span>|  
|<span data-ttu-id="dc318-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="dc318-392">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-392">String</span></span>|  
|<span data-ttu-id="dc318-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="dc318-394">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-394">String</span></span>|  
|<span data-ttu-id="dc318-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="dc318-396">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-396">String</span></span>|  
|<span data-ttu-id="dc318-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-397">COLLATION_NAME</span></span>|<span data-ttu-id="dc318-398">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-398">String</span></span>|  
|<span data-ttu-id="dc318-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="dc318-400">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-400">String</span></span>|  
|<span data-ttu-id="dc318-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="dc318-402">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-402">String</span></span>|  
|<span data-ttu-id="dc318-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-403">DOMAIN_NAME</span></span>|<span data-ttu-id="dc318-404">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-404">String</span></span>|  
|<span data-ttu-id="dc318-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-405">DESCRIPTION</span></span>|<span data-ttu-id="dc318-406">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dc318-407">Procédures</span><span class="sxs-lookup"><span data-stu-id="dc318-407">Procedures</span></span>  
  
|<span data-ttu-id="dc318-408">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-408">ColumnName</span></span>|<span data-ttu-id="dc318-409">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="dc318-411">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-411">String</span></span>|  
|<span data-ttu-id="dc318-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="dc318-413">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-413">String</span></span>|  
|<span data-ttu-id="dc318-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="dc318-415">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-415">String</span></span>|  
|<span data-ttu-id="dc318-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dc318-417">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-417">Int16</span></span>|  
|<span data-ttu-id="dc318-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="dc318-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="dc318-419">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-419">String</span></span>|  
|<span data-ttu-id="dc318-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-420">DESCRIPTION</span></span>|<span data-ttu-id="dc318-421">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-421">String</span></span>|  
|<span data-ttu-id="dc318-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="dc318-422">DATE_CREATED</span></span>|<span data-ttu-id="dc318-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-423">DateTime</span></span>|  
|<span data-ttu-id="dc318-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="dc318-424">DATE_MODIFIED</span></span>|<span data-ttu-id="dc318-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="dc318-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dc318-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="dc318-427">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-427">ColumnName</span></span>|<span data-ttu-id="dc318-428">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="dc318-430">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-430">String</span></span>|  
|<span data-ttu-id="dc318-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="dc318-432">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-432">String</span></span>|  
|<span data-ttu-id="dc318-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="dc318-434">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-434">String</span></span>|  
|<span data-ttu-id="dc318-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-435">COLUMN_NAME</span></span>|<span data-ttu-id="dc318-436">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-436">String</span></span>|  
|<span data-ttu-id="dc318-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-437">COLUMN_GUID</span></span>|<span data-ttu-id="dc318-438">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-438">Guid</span></span>|  
|<span data-ttu-id="dc318-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-439">COLUMN_PROPID</span></span>|<span data-ttu-id="dc318-440">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-440">Int64</span></span>|  
|<span data-ttu-id="dc318-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="dc318-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="dc318-442">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-442">Int64</span></span>|  
|<span data-ttu-id="dc318-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dc318-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="dc318-444">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-444">Int64</span></span>|  
|<span data-ttu-id="dc318-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dc318-445">IS_NULLABLE</span></span>|<span data-ttu-id="dc318-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-446">Boolean</span></span>|  
|<span data-ttu-id="dc318-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-447">DATA_TYPE</span></span>|<span data-ttu-id="dc318-448">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-448">Int32</span></span>|  
|<span data-ttu-id="dc318-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-449">TYPE_GUID</span></span>|<span data-ttu-id="dc318-450">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-450">Guid</span></span>|  
|<span data-ttu-id="dc318-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="dc318-452">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-452">Int64</span></span>|  
|<span data-ttu-id="dc318-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="dc318-454">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-454">Int64</span></span>|  
|<span data-ttu-id="dc318-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="dc318-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="dc318-456">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-456">Int32</span></span>|  
|<span data-ttu-id="dc318-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="dc318-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="dc318-458">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-458">Int16</span></span>|  
|<span data-ttu-id="dc318-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-459">DESCRIPTION</span></span>|<span data-ttu-id="dc318-460">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-460">String</span></span>|  
|<span data-ttu-id="dc318-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="dc318-461">OVERLOAD</span></span>|<span data-ttu-id="dc318-462">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="dc318-463">Vues</span><span class="sxs-lookup"><span data-stu-id="dc318-463">Views</span></span>  
  
|<span data-ttu-id="dc318-464">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-464">ColumnName</span></span>|<span data-ttu-id="dc318-465">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-466">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-467">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-467">String</span></span>|  
|<span data-ttu-id="dc318-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-469">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-469">String</span></span>|  
|<span data-ttu-id="dc318-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-470">TABLE_NAME</span></span>|<span data-ttu-id="dc318-471">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-471">String</span></span>|  
|<span data-ttu-id="dc318-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="dc318-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="dc318-473">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-473">String</span></span>|  
|<span data-ttu-id="dc318-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-474">CHECK_OPTION</span></span>|<span data-ttu-id="dc318-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-475">Boolean</span></span>|  
|<span data-ttu-id="dc318-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="dc318-476">IS_UPDATABLE</span></span>|<span data-ttu-id="dc318-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-477">Boolean</span></span>|  
|<span data-ttu-id="dc318-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-478">DESCRIPTION</span></span>|<span data-ttu-id="dc318-479">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-479">String</span></span>|  
|<span data-ttu-id="dc318-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="dc318-480">DATE_CREATED</span></span>|<span data-ttu-id="dc318-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-481">DateTime</span></span>|  
|<span data-ttu-id="dc318-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="dc318-482">DATE_MODIFIED</span></span>|<span data-ttu-id="dc318-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="dc318-484">Index</span><span class="sxs-lookup"><span data-stu-id="dc318-484">Indexes</span></span>  
  
|<span data-ttu-id="dc318-485">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-485">ColumnName</span></span>|<span data-ttu-id="dc318-486">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-487">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-488">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-488">String</span></span>|  
|<span data-ttu-id="dc318-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-490">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-490">String</span></span>|  
|<span data-ttu-id="dc318-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-491">TABLE_NAME</span></span>|<span data-ttu-id="dc318-492">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-492">String</span></span>|  
|<span data-ttu-id="dc318-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-493">INDEX_CATALOG</span></span>|<span data-ttu-id="dc318-494">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-494">String</span></span>|  
|<span data-ttu-id="dc318-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="dc318-496">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-496">String</span></span>|  
|<span data-ttu-id="dc318-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-497">INDEX_NAME</span></span>|<span data-ttu-id="dc318-498">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-498">String</span></span>|  
|<span data-ttu-id="dc318-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="dc318-499">PRIMARY_KEY</span></span>|<span data-ttu-id="dc318-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-500">Boolean</span></span>|  
|<span data-ttu-id="dc318-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="dc318-501">UNIQUE</span></span>|<span data-ttu-id="dc318-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-502">Boolean</span></span>|  
|<span data-ttu-id="dc318-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="dc318-503">CLUSTERED</span></span>|<span data-ttu-id="dc318-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-504">Boolean</span></span>|  
|<span data-ttu-id="dc318-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-505">TYPE</span></span>|<span data-ttu-id="dc318-506">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-506">Int32</span></span>|  
|<span data-ttu-id="dc318-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="dc318-507">FILL_FACTOR</span></span>|<span data-ttu-id="dc318-508">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-508">Int32</span></span>|  
|<span data-ttu-id="dc318-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="dc318-509">INITIAL_SIZE</span></span>|<span data-ttu-id="dc318-510">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-510">Int32</span></span>|  
|<span data-ttu-id="dc318-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="dc318-511">NULLS</span></span>|<span data-ttu-id="dc318-512">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-512">Int32</span></span>|  
|<span data-ttu-id="dc318-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="dc318-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="dc318-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-514">Boolean</span></span>|  
|<span data-ttu-id="dc318-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="dc318-515">AUTO_UPDATE</span></span>|<span data-ttu-id="dc318-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-516">Boolean</span></span>|  
|<span data-ttu-id="dc318-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="dc318-517">NULL_COLLATION</span></span>|<span data-ttu-id="dc318-518">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-518">Int32</span></span>|  
|<span data-ttu-id="dc318-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dc318-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="dc318-520">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-520">Int64</span></span>|  
|<span data-ttu-id="dc318-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-521">COLUMN_NAME</span></span>|<span data-ttu-id="dc318-522">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-522">String</span></span>|  
|<span data-ttu-id="dc318-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-523">COLUMN_GUID</span></span>|<span data-ttu-id="dc318-524">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-524">Guid</span></span>|  
|<span data-ttu-id="dc318-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-525">COLUMN_PROPID</span></span>|<span data-ttu-id="dc318-526">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-526">Int64</span></span>|  
|<span data-ttu-id="dc318-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="dc318-527">COLLATION</span></span>|<span data-ttu-id="dc318-528">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-528">Int16</span></span>|  
|<span data-ttu-id="dc318-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="dc318-529">CARDINALITY</span></span>|<span data-ttu-id="dc318-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="dc318-530">Decimal</span></span>|  
|<span data-ttu-id="dc318-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="dc318-531">PAGES</span></span>|<span data-ttu-id="dc318-532">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-532">Int32</span></span>|  
|<span data-ttu-id="dc318-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="dc318-533">FILTER_CONDITION</span></span>|<span data-ttu-id="dc318-534">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-534">String</span></span>|  
|<span data-ttu-id="dc318-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="dc318-535">INTEGRATED</span></span>|<span data-ttu-id="dc318-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="dc318-537">Fournisseur Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="dc318-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="dc318-538">Le pilote Microsoft Jet OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="dc318-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dc318-539">Tables</span><span class="sxs-lookup"><span data-stu-id="dc318-539">Tables</span></span>  
  
-   <span data-ttu-id="dc318-540">Columns</span><span class="sxs-lookup"><span data-stu-id="dc318-540">Columns</span></span>  
  
-   <span data-ttu-id="dc318-541">Procédures</span><span class="sxs-lookup"><span data-stu-id="dc318-541">Procedures</span></span>  
  
-   <span data-ttu-id="dc318-542">Vues</span><span class="sxs-lookup"><span data-stu-id="dc318-542">Views</span></span>  
  
-   <span data-ttu-id="dc318-543">Index</span><span class="sxs-lookup"><span data-stu-id="dc318-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="dc318-544">Tables</span><span class="sxs-lookup"><span data-stu-id="dc318-544">Tables</span></span>  
  
|<span data-ttu-id="dc318-545">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-545">ColumnName</span></span>|<span data-ttu-id="dc318-546">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-547">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-548">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-548">String</span></span>|  
|<span data-ttu-id="dc318-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-550">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-550">String</span></span>|  
|<span data-ttu-id="dc318-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-551">TABLE_NAME</span></span>|<span data-ttu-id="dc318-552">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-552">String</span></span>|  
|<span data-ttu-id="dc318-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-553">TABLE_TYPE</span></span>|<span data-ttu-id="dc318-554">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-554">String</span></span>|  
|<span data-ttu-id="dc318-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-555">TABLE_GUID</span></span>|<span data-ttu-id="dc318-556">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-556">Guid</span></span>|  
|<span data-ttu-id="dc318-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-557">DESCRIPTION</span></span>|<span data-ttu-id="dc318-558">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-558">String</span></span>|  
|<span data-ttu-id="dc318-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-559">TABLE_PROPID</span></span>|<span data-ttu-id="dc318-560">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-560">Int64</span></span>|  
|<span data-ttu-id="dc318-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="dc318-561">DATE_CREATED</span></span>|<span data-ttu-id="dc318-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-562">DateTime</span></span>|  
|<span data-ttu-id="dc318-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="dc318-563">DATE_MODIFIED</span></span>|<span data-ttu-id="dc318-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dc318-565">Columns</span><span class="sxs-lookup"><span data-stu-id="dc318-565">Columns</span></span>  
  
|<span data-ttu-id="dc318-566">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-566">ColumnName</span></span>|<span data-ttu-id="dc318-567">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-568">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-569">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-569">String</span></span>|  
|<span data-ttu-id="dc318-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-571">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-571">String</span></span>|  
|<span data-ttu-id="dc318-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-572">TABLE_NAME</span></span>|<span data-ttu-id="dc318-573">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-573">String</span></span>|  
|<span data-ttu-id="dc318-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-574">COLUMN_NAME</span></span>|<span data-ttu-id="dc318-575">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-575">String</span></span>|  
|<span data-ttu-id="dc318-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-576">COLUMN_GUID</span></span>|<span data-ttu-id="dc318-577">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-577">Guid</span></span>|  
|<span data-ttu-id="dc318-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-578">COLUMN_PROPID</span></span>|<span data-ttu-id="dc318-579">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-579">Int64</span></span>|  
|<span data-ttu-id="dc318-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dc318-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="dc318-581">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-581">Int64</span></span>|  
|<span data-ttu-id="dc318-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="dc318-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="dc318-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-583">Boolean</span></span>|  
|<span data-ttu-id="dc318-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="dc318-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="dc318-585">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-585">String</span></span>|  
|<span data-ttu-id="dc318-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="dc318-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="dc318-587">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-587">Int64</span></span>|  
|<span data-ttu-id="dc318-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dc318-588">IS_NULLABLE</span></span>|<span data-ttu-id="dc318-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-589">Boolean</span></span>|  
|<span data-ttu-id="dc318-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-590">DATA_TYPE</span></span>|<span data-ttu-id="dc318-591">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-591">Int32</span></span>|  
|<span data-ttu-id="dc318-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-592">TYPE_GUID</span></span>|<span data-ttu-id="dc318-593">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-593">Guid</span></span>|  
|<span data-ttu-id="dc318-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="dc318-595">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-595">Int64</span></span>|  
|<span data-ttu-id="dc318-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dc318-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="dc318-597">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-597">Int64</span></span>|  
|<span data-ttu-id="dc318-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="dc318-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="dc318-599">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-599">Int32</span></span>|  
|<span data-ttu-id="dc318-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="dc318-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="dc318-601">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-601">Int16</span></span>|  
|<span data-ttu-id="dc318-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="dc318-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="dc318-603">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-603">Int64</span></span>|  
|<span data-ttu-id="dc318-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="dc318-605">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-605">String</span></span>|  
|<span data-ttu-id="dc318-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="dc318-607">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-607">String</span></span>|  
|<span data-ttu-id="dc318-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="dc318-609">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-609">String</span></span>|  
|<span data-ttu-id="dc318-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="dc318-611">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-611">String</span></span>|  
|<span data-ttu-id="dc318-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="dc318-613">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-613">String</span></span>|  
|<span data-ttu-id="dc318-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-614">COLLATION_NAME</span></span>|<span data-ttu-id="dc318-615">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-615">String</span></span>|  
|<span data-ttu-id="dc318-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="dc318-617">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-617">String</span></span>|  
|<span data-ttu-id="dc318-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="dc318-619">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-619">String</span></span>|  
|<span data-ttu-id="dc318-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-620">DOMAIN_NAME</span></span>|<span data-ttu-id="dc318-621">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-621">String</span></span>|  
|<span data-ttu-id="dc318-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-622">DESCRIPTION</span></span>|<span data-ttu-id="dc318-623">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dc318-624">Procédures</span><span class="sxs-lookup"><span data-stu-id="dc318-624">Procedures</span></span>  
  
|<span data-ttu-id="dc318-625">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-625">ColumnName</span></span>|<span data-ttu-id="dc318-626">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="dc318-628">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-628">String</span></span>|  
|<span data-ttu-id="dc318-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="dc318-630">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-630">String</span></span>|  
|<span data-ttu-id="dc318-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="dc318-632">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-632">String</span></span>|  
|<span data-ttu-id="dc318-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dc318-634">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-634">Int16</span></span>|  
|<span data-ttu-id="dc318-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="dc318-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="dc318-636">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-636">String</span></span>|  
|<span data-ttu-id="dc318-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-637">DESCRIPTION</span></span>|<span data-ttu-id="dc318-638">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-638">String</span></span>|  
|<span data-ttu-id="dc318-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="dc318-639">DATE_CREATED</span></span>|<span data-ttu-id="dc318-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-640">DateTime</span></span>|  
|<span data-ttu-id="dc318-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="dc318-641">DATE_MODIFIED</span></span>|<span data-ttu-id="dc318-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="dc318-643">Vues</span><span class="sxs-lookup"><span data-stu-id="dc318-643">Views</span></span>  
  
|<span data-ttu-id="dc318-644">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-644">ColumnName</span></span>|<span data-ttu-id="dc318-645">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-646">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-647">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-647">String</span></span>|  
|<span data-ttu-id="dc318-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-649">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-649">String</span></span>|  
|<span data-ttu-id="dc318-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-650">TABLE_NAME</span></span>|<span data-ttu-id="dc318-651">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-651">String</span></span>|  
|<span data-ttu-id="dc318-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="dc318-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="dc318-653">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-653">String</span></span>|  
|<span data-ttu-id="dc318-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-654">CHECK_OPTION</span></span>|<span data-ttu-id="dc318-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-655">Boolean</span></span>|  
|<span data-ttu-id="dc318-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="dc318-656">IS_UPDATABLE</span></span>|<span data-ttu-id="dc318-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-657">Boolean</span></span>|  
|<span data-ttu-id="dc318-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc318-658">DESCRIPTION</span></span>|<span data-ttu-id="dc318-659">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-659">String</span></span>|  
|<span data-ttu-id="dc318-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="dc318-660">DATE_CREATED</span></span>|<span data-ttu-id="dc318-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-661">DateTime</span></span>|  
|<span data-ttu-id="dc318-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="dc318-662">DATE_MODIFIED</span></span>|<span data-ttu-id="dc318-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="dc318-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="dc318-664">Index</span><span class="sxs-lookup"><span data-stu-id="dc318-664">Indexes</span></span>  
  
|<span data-ttu-id="dc318-665">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dc318-665">ColumnName</span></span>|<span data-ttu-id="dc318-666">Type de données</span><span class="sxs-lookup"><span data-stu-id="dc318-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dc318-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-667">TABLE_CATALOG</span></span>|<span data-ttu-id="dc318-668">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-668">String</span></span>|  
|<span data-ttu-id="dc318-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc318-670">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-670">String</span></span>|  
|<span data-ttu-id="dc318-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-671">TABLE_NAME</span></span>|<span data-ttu-id="dc318-672">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-672">String</span></span>|  
|<span data-ttu-id="dc318-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc318-673">INDEX_CATALOG</span></span>|<span data-ttu-id="dc318-674">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-674">String</span></span>|  
|<span data-ttu-id="dc318-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc318-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="dc318-676">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-676">String</span></span>|  
|<span data-ttu-id="dc318-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-677">INDEX_NAME</span></span>|<span data-ttu-id="dc318-678">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-678">String</span></span>|  
|<span data-ttu-id="dc318-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="dc318-679">PRIMARY_KEY</span></span>|<span data-ttu-id="dc318-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-680">Boolean</span></span>|  
|<span data-ttu-id="dc318-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="dc318-681">UNIQUE</span></span>|<span data-ttu-id="dc318-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-682">Boolean</span></span>|  
|<span data-ttu-id="dc318-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="dc318-683">CLUSTERED</span></span>|<span data-ttu-id="dc318-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-684">Boolean</span></span>|  
|<span data-ttu-id="dc318-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="dc318-685">TYPE</span></span>|<span data-ttu-id="dc318-686">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-686">Int32</span></span>|  
|<span data-ttu-id="dc318-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="dc318-687">FILL_FACTOR</span></span>|<span data-ttu-id="dc318-688">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-688">Int32</span></span>|  
|<span data-ttu-id="dc318-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="dc318-689">INITIAL_SIZE</span></span>|<span data-ttu-id="dc318-690">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-690">Int32</span></span>|  
|<span data-ttu-id="dc318-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="dc318-691">NULLS</span></span>|<span data-ttu-id="dc318-692">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-692">Int32</span></span>|  
|<span data-ttu-id="dc318-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="dc318-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="dc318-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-694">Boolean</span></span>|  
|<span data-ttu-id="dc318-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="dc318-695">AUTO_UPDATE</span></span>|<span data-ttu-id="dc318-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="dc318-696">Boolean</span></span>|  
|<span data-ttu-id="dc318-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="dc318-697">NULL_COLLATION</span></span>|<span data-ttu-id="dc318-698">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-698">Int32</span></span>|  
|<span data-ttu-id="dc318-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dc318-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="dc318-700">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-700">Int64</span></span>|  
|<span data-ttu-id="dc318-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc318-701">COLUMN_NAME</span></span>|<span data-ttu-id="dc318-702">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-702">String</span></span>|  
|<span data-ttu-id="dc318-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="dc318-703">COLUMN_GUID</span></span>|<span data-ttu-id="dc318-704">Guid</span><span class="sxs-lookup"><span data-stu-id="dc318-704">Guid</span></span>|  
|<span data-ttu-id="dc318-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="dc318-705">COLUMN_PROPID</span></span>|<span data-ttu-id="dc318-706">Int64</span><span class="sxs-lookup"><span data-stu-id="dc318-706">Int64</span></span>|  
|<span data-ttu-id="dc318-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="dc318-707">COLLATION</span></span>|<span data-ttu-id="dc318-708">Int16</span><span class="sxs-lookup"><span data-stu-id="dc318-708">Int16</span></span>|  
|<span data-ttu-id="dc318-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="dc318-709">CARDINALITY</span></span>|<span data-ttu-id="dc318-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="dc318-710">Decimal</span></span>|  
|<span data-ttu-id="dc318-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="dc318-711">PAGES</span></span>|<span data-ttu-id="dc318-712">Int32</span><span class="sxs-lookup"><span data-stu-id="dc318-712">Int32</span></span>|  
|<span data-ttu-id="dc318-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="dc318-713">FILTER_CONDITION</span></span>|<span data-ttu-id="dc318-714">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dc318-714">String</span></span>|  
|<span data-ttu-id="dc318-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="dc318-715">INTEGRATED</span></span>|<span data-ttu-id="dc318-716">Booléen</span><span class="sxs-lookup"><span data-stu-id="dc318-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc318-717">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc318-717">See Also</span></span>  
 [<span data-ttu-id="dc318-718">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="dc318-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
