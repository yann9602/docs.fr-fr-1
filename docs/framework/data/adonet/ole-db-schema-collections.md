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
ms.openlocfilehash: 9b88308c5dad69ed1ba6f48f525931e94f13ef1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="0c1e6-102">Collections de schémas OLE DB</span><span class="sxs-lookup"><span data-stu-id="0c1e6-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="0c1e6-103">Cette section traite de la prise en charge des collections de schémas pour les fournisseurs OLE DB de Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="0c1e6-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="0c1e6-104">Fournisseur Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="0c1e6-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="0c1e6-105">Le pilote OLE DB Microsoft SQL Server prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0c1e6-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0c1e6-106">Tables</span><span class="sxs-lookup"><span data-stu-id="0c1e6-106">Tables</span></span>  
  
-   <span data-ttu-id="0c1e6-107">Columns</span><span class="sxs-lookup"><span data-stu-id="0c1e6-107">Columns</span></span>  
  
-   <span data-ttu-id="0c1e6-108">Procédures</span><span class="sxs-lookup"><span data-stu-id="0c1e6-108">Procedures</span></span>  
  
-   <span data-ttu-id="0c1e6-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0c1e6-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0c1e6-110">Catalogue</span><span class="sxs-lookup"><span data-stu-id="0c1e6-110">Catalog</span></span>  
  
-   <span data-ttu-id="0c1e6-111">Index</span><span class="sxs-lookup"><span data-stu-id="0c1e6-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0c1e6-112">Tables</span><span class="sxs-lookup"><span data-stu-id="0c1e6-112">Tables</span></span>  
  
|<span data-ttu-id="0c1e6-113">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-113">ColumnName</span></span>|<span data-ttu-id="0c1e6-114">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-115">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-116">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-116">String</span></span>|  
|<span data-ttu-id="0c1e6-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-118">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-118">String</span></span>|  
|<span data-ttu-id="0c1e6-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-119">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-120">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-120">String</span></span>|  
|<span data-ttu-id="0c1e6-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-121">TABLE_TYPE</span></span>|<span data-ttu-id="0c1e6-122">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-122">String</span></span>|  
|<span data-ttu-id="0c1e6-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-123">TABLE_GUID</span></span>|<span data-ttu-id="0c1e6-124">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-124">Guid</span></span>|  
|<span data-ttu-id="0c1e6-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-125">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-126">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-126">String</span></span>|  
|<span data-ttu-id="0c1e6-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-127">TABLE_PROPID</span></span>|<span data-ttu-id="0c1e6-128">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-128">Int64</span></span>|  
|<span data-ttu-id="0c1e6-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-129">DATE_CREATED</span></span>|<span data-ttu-id="0c1e6-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-130">DateTime</span></span>|  
|<span data-ttu-id="0c1e6-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-131">DATE_MODIFIED</span></span>|<span data-ttu-id="0c1e6-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0c1e6-133">Columns</span><span class="sxs-lookup"><span data-stu-id="0c1e6-133">Columns</span></span>  
  
|<span data-ttu-id="0c1e6-134">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-134">ColumnName</span></span>|<span data-ttu-id="0c1e6-135">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-136">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-137">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-137">String</span></span>|  
|<span data-ttu-id="0c1e6-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-139">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-139">String</span></span>|  
|<span data-ttu-id="0c1e6-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-140">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-141">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-141">String</span></span>|  
|<span data-ttu-id="0c1e6-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-142">COLUMN_NAME</span></span>|<span data-ttu-id="0c1e6-143">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-143">String</span></span>|  
|<span data-ttu-id="0c1e6-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-144">COLUMN_GUID</span></span>|<span data-ttu-id="0c1e6-145">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-145">Guid</span></span>|  
|<span data-ttu-id="0c1e6-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-146">COLUMN_PROPID</span></span>|<span data-ttu-id="0c1e6-147">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-147">Int64</span></span>|  
|<span data-ttu-id="0c1e6-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c1e6-149">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-149">Int64</span></span>|  
|<span data-ttu-id="0c1e6-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0c1e6-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0c1e6-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-151">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0c1e6-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0c1e6-153">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-153">String</span></span>|  
|<span data-ttu-id="0c1e6-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="0c1e6-155">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-155">Int64</span></span>|  
|<span data-ttu-id="0c1e6-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-156">IS_NULLABLE</span></span>|<span data-ttu-id="0c1e6-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-157">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-158">DATA_TYPE</span></span>|<span data-ttu-id="0c1e6-159">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-159">Int32</span></span>|  
|<span data-ttu-id="0c1e6-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-160">TYPE_GUID</span></span>|<span data-ttu-id="0c1e6-161">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-161">Guid</span></span>|  
|<span data-ttu-id="0c1e6-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0c1e6-163">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-163">Int64</span></span>|  
|<span data-ttu-id="0c1e6-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0c1e6-165">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-165">Int64</span></span>|  
|<span data-ttu-id="0c1e6-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0c1e6-167">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-167">Int32</span></span>|  
|<span data-ttu-id="0c1e6-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="0c1e6-169">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-169">Int16</span></span>|  
|<span data-ttu-id="0c1e6-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="0c1e6-171">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-171">Int64</span></span>|  
|<span data-ttu-id="0c1e6-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0c1e6-173">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-173">String</span></span>|  
|<span data-ttu-id="0c1e6-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0c1e6-175">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-175">String</span></span>|  
|<span data-ttu-id="0c1e6-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0c1e6-177">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-177">String</span></span>|  
|<span data-ttu-id="0c1e6-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="0c1e6-179">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-179">String</span></span>|  
|<span data-ttu-id="0c1e6-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0c1e6-181">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-181">String</span></span>|  
|<span data-ttu-id="0c1e6-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-182">COLLATION_NAME</span></span>|<span data-ttu-id="0c1e6-183">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-183">String</span></span>|  
|<span data-ttu-id="0c1e6-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0c1e6-185">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-185">String</span></span>|  
|<span data-ttu-id="0c1e6-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0c1e6-187">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-187">String</span></span>|  
|<span data-ttu-id="0c1e6-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-188">DOMAIN_NAME</span></span>|<span data-ttu-id="0c1e6-189">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-189">String</span></span>|  
|<span data-ttu-id="0c1e6-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-190">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-191">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-191">String</span></span>|  
|<span data-ttu-id="0c1e6-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-192">COLUMN_LCID</span></span>|<span data-ttu-id="0c1e6-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-193">Int32</span></span>|  
|<span data-ttu-id="0c1e6-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="0c1e6-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-195">Int32</span></span>|  
|<span data-ttu-id="0c1e6-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-196">COLUMN_SORTID</span></span>|<span data-ttu-id="0c1e6-197">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-197">Int32</span></span>|  
|<span data-ttu-id="0c1e6-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="0c1e6-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="0c1e6-199">Byte[]</span></span>|  
|<span data-ttu-id="0c1e6-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-200">IS_COMPUTED</span></span>|<span data-ttu-id="0c1e6-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0c1e6-202">Procédures</span><span class="sxs-lookup"><span data-stu-id="0c1e6-202">Procedures</span></span>  
  
|<span data-ttu-id="0c1e6-203">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-203">ColumnName</span></span>|<span data-ttu-id="0c1e6-204">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0c1e6-206">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-206">String</span></span>|  
|<span data-ttu-id="0c1e6-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-208">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-208">String</span></span>|  
|<span data-ttu-id="0c1e6-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c1e6-210">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-210">String</span></span>|  
|<span data-ttu-id="0c1e6-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0c1e6-212">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-212">Int16</span></span>|  
|<span data-ttu-id="0c1e6-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0c1e6-214">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-214">String</span></span>|  
|<span data-ttu-id="0c1e6-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-215">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-216">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-216">String</span></span>|  
|<span data-ttu-id="0c1e6-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-217">DATE_CREATED</span></span>|<span data-ttu-id="0c1e6-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-218">DateTime</span></span>|  
|<span data-ttu-id="0c1e6-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-219">DATE_MODIFIED</span></span>|<span data-ttu-id="0c1e6-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0c1e6-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0c1e6-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0c1e6-222">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-222">ColumnName</span></span>|<span data-ttu-id="0c1e6-223">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0c1e6-225">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-225">String</span></span>|  
|<span data-ttu-id="0c1e6-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-227">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-227">String</span></span>|  
|<span data-ttu-id="0c1e6-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c1e6-229">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-229">String</span></span>|  
|<span data-ttu-id="0c1e6-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-230">PARAMETER_NAME</span></span>|<span data-ttu-id="0c1e6-231">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-231">String</span></span>|  
|<span data-ttu-id="0c1e6-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c1e6-233">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-233">Int32</span></span>|  
|<span data-ttu-id="0c1e6-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="0c1e6-235">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-235">Int32</span></span>|  
|<span data-ttu-id="0c1e6-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0c1e6-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="0c1e6-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-237">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0c1e6-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="0c1e6-239">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-239">String</span></span>|  
|<span data-ttu-id="0c1e6-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-240">IS_NULLABLE</span></span>|<span data-ttu-id="0c1e6-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-241">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-242">DATA_TYPE</span></span>|<span data-ttu-id="0c1e6-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-243">Int32</span></span>|  
|<span data-ttu-id="0c1e6-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0c1e6-245">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-245">Int64</span></span>|  
|<span data-ttu-id="0c1e6-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0c1e6-247">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-247">Int64</span></span>|  
|<span data-ttu-id="0c1e6-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0c1e6-249">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-249">Int32</span></span>|  
|<span data-ttu-id="0c1e6-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="0c1e6-251">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-251">Int16</span></span>|  
|<span data-ttu-id="0c1e6-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-252">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-253">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-253">String</span></span>|  
|<span data-ttu-id="0c1e6-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-254">TYPE_NAME</span></span>|<span data-ttu-id="0c1e6-255">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-255">String</span></span>|  
|<span data-ttu-id="0c1e6-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="0c1e6-257">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="0c1e6-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="0c1e6-258">Catalog</span></span>  
  
|<span data-ttu-id="0c1e6-259">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-259">ColumnName</span></span>|<span data-ttu-id="0c1e6-260">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-261">CATALOG_NAME</span></span>|<span data-ttu-id="0c1e6-262">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-262">String</span></span>|  
|<span data-ttu-id="0c1e6-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-263">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-264">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0c1e6-265">Index</span><span class="sxs-lookup"><span data-stu-id="0c1e6-265">Indexes</span></span>  
  
|<span data-ttu-id="0c1e6-266">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-266">ColumnName</span></span>|<span data-ttu-id="0c1e6-267">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-268">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-269">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-269">String</span></span>|  
|<span data-ttu-id="0c1e6-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-271">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-271">String</span></span>|  
|<span data-ttu-id="0c1e6-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-272">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-273">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-273">String</span></span>|  
|<span data-ttu-id="0c1e6-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-274">INDEX_CATALOG</span></span>|<span data-ttu-id="0c1e6-275">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-275">String</span></span>|  
|<span data-ttu-id="0c1e6-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="0c1e6-277">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-277">String</span></span>|  
|<span data-ttu-id="0c1e6-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-278">INDEX_NAME</span></span>|<span data-ttu-id="0c1e6-279">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-279">String</span></span>|  
|<span data-ttu-id="0c1e6-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0c1e6-280">PRIMARY_KEY</span></span>|<span data-ttu-id="0c1e6-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-281">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-282">UNIQUE</span></span>|<span data-ttu-id="0c1e6-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-283">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-284">CLUSTERED</span></span>|<span data-ttu-id="0c1e6-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-285">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-286">TYPE</span></span>|<span data-ttu-id="0c1e6-287">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-287">Int32</span></span>|  
|<span data-ttu-id="0c1e6-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0c1e6-288">FILL_FACTOR</span></span>|<span data-ttu-id="0c1e6-289">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-289">Int32</span></span>|  
|<span data-ttu-id="0c1e6-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-290">INITIAL_SIZE</span></span>|<span data-ttu-id="0c1e6-291">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-291">Int32</span></span>|  
|<span data-ttu-id="0c1e6-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-292">NULLS</span></span>|<span data-ttu-id="0c1e6-293">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-293">Int32</span></span>|  
|<span data-ttu-id="0c1e6-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0c1e6-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-295">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-296">AUTO_UPDATE</span></span>|<span data-ttu-id="0c1e6-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-297">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-298">NULL_COLLATION</span></span>|<span data-ttu-id="0c1e6-299">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-299">Int32</span></span>|  
|<span data-ttu-id="0c1e6-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c1e6-301">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-301">Int64</span></span>|  
|<span data-ttu-id="0c1e6-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-302">COLUMN_NAME</span></span>|<span data-ttu-id="0c1e6-303">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-303">String</span></span>|  
|<span data-ttu-id="0c1e6-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-304">COLUMN_GUID</span></span>|<span data-ttu-id="0c1e6-305">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-305">Guid</span></span>|  
|<span data-ttu-id="0c1e6-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-306">COLUMN_PROPID</span></span>|<span data-ttu-id="0c1e6-307">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-307">Int64</span></span>|  
|<span data-ttu-id="0c1e6-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-308">COLLATION</span></span>|<span data-ttu-id="0c1e6-309">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-309">Int16</span></span>|  
|<span data-ttu-id="0c1e6-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0c1e6-310">CARDINALITY</span></span>|<span data-ttu-id="0c1e6-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="0c1e6-311">Decimal</span></span>|  
|<span data-ttu-id="0c1e6-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="0c1e6-312">PAGES</span></span>|<span data-ttu-id="0c1e6-313">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-313">Int32</span></span>|  
|<span data-ttu-id="0c1e6-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-314">FILTER_CONDITION</span></span>|<span data-ttu-id="0c1e6-315">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-315">String</span></span>|  
|<span data-ttu-id="0c1e6-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-316">INTEGRATED</span></span>|<span data-ttu-id="0c1e6-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="0c1e6-318">Fournisseur Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="0c1e6-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="0c1e6-319">Le pilote Microsoft Oracle OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0c1e6-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0c1e6-320">Tables</span><span class="sxs-lookup"><span data-stu-id="0c1e6-320">Tables</span></span>  
  
-   <span data-ttu-id="0c1e6-321">Columns</span><span class="sxs-lookup"><span data-stu-id="0c1e6-321">Columns</span></span>  
  
-   <span data-ttu-id="0c1e6-322">Procédures</span><span class="sxs-lookup"><span data-stu-id="0c1e6-322">Procedures</span></span>  
  
-   <span data-ttu-id="0c1e6-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0c1e6-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0c1e6-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0c1e6-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0c1e6-325">Vues</span><span class="sxs-lookup"><span data-stu-id="0c1e6-325">Views</span></span>  
  
-   <span data-ttu-id="0c1e6-326">Index</span><span class="sxs-lookup"><span data-stu-id="0c1e6-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0c1e6-327">Tables</span><span class="sxs-lookup"><span data-stu-id="0c1e6-327">Tables</span></span>  
  
|<span data-ttu-id="0c1e6-328">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-328">ColumnName</span></span>|<span data-ttu-id="0c1e6-329">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-330">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-331">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-331">String</span></span>|  
|<span data-ttu-id="0c1e6-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-333">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-333">String</span></span>|  
|<span data-ttu-id="0c1e6-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-334">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-335">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-335">String</span></span>|  
|<span data-ttu-id="0c1e6-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-336">TABLE_TYPE</span></span>|<span data-ttu-id="0c1e6-337">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-337">String</span></span>|  
|<span data-ttu-id="0c1e6-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-338">TABLE_GUID</span></span>|<span data-ttu-id="0c1e6-339">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-339">Guid</span></span>|  
|<span data-ttu-id="0c1e6-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-340">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-341">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-341">String</span></span>|  
|<span data-ttu-id="0c1e6-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-342">TABLE_PROPID</span></span>|<span data-ttu-id="0c1e6-343">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-343">Int64</span></span>|  
|<span data-ttu-id="0c1e6-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-344">DATE_CREATED</span></span>|<span data-ttu-id="0c1e6-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-345">DateTime</span></span>|  
|<span data-ttu-id="0c1e6-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-346">DATE_MODIFIED</span></span>|<span data-ttu-id="0c1e6-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0c1e6-348">Columns</span><span class="sxs-lookup"><span data-stu-id="0c1e6-348">Columns</span></span>  
  
|<span data-ttu-id="0c1e6-349">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-349">ColumnName</span></span>|<span data-ttu-id="0c1e6-350">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-351">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-352">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-352">String</span></span>|  
|<span data-ttu-id="0c1e6-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-354">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-354">String</span></span>|  
|<span data-ttu-id="0c1e6-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-355">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-356">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-356">String</span></span>|  
|<span data-ttu-id="0c1e6-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-357">COLUMN_NAME</span></span>|<span data-ttu-id="0c1e6-358">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-358">String</span></span>|  
|<span data-ttu-id="0c1e6-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-359">COLUMN_GUID</span></span>|<span data-ttu-id="0c1e6-360">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-360">Guid</span></span>|  
|<span data-ttu-id="0c1e6-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-361">COLUMN_PROPID</span></span>|<span data-ttu-id="0c1e6-362">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-362">Int64</span></span>|  
|<span data-ttu-id="0c1e6-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c1e6-364">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-364">Int64</span></span>|  
|<span data-ttu-id="0c1e6-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0c1e6-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0c1e6-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-366">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0c1e6-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0c1e6-368">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-368">String</span></span>|  
|<span data-ttu-id="0c1e6-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="0c1e6-370">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-370">Int64</span></span>|  
|<span data-ttu-id="0c1e6-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-371">IS_NULLABLE</span></span>|<span data-ttu-id="0c1e6-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-372">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-373">DATA_TYPE</span></span>|<span data-ttu-id="0c1e6-374">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-374">Int32</span></span>|  
|<span data-ttu-id="0c1e6-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-375">TYPE_GUID</span></span>|<span data-ttu-id="0c1e6-376">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-376">Guid</span></span>|  
|<span data-ttu-id="0c1e6-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0c1e6-378">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-378">Int64</span></span>|  
|<span data-ttu-id="0c1e6-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0c1e6-380">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-380">Int64</span></span>|  
|<span data-ttu-id="0c1e6-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0c1e6-382">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-382">Int32</span></span>|  
|<span data-ttu-id="0c1e6-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="0c1e6-384">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-384">Int16</span></span>|  
|<span data-ttu-id="0c1e6-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="0c1e6-386">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-386">Int64</span></span>|  
|<span data-ttu-id="0c1e6-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0c1e6-388">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-388">String</span></span>|  
|<span data-ttu-id="0c1e6-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0c1e6-390">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-390">String</span></span>|  
|<span data-ttu-id="0c1e6-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0c1e6-392">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-392">String</span></span>|  
|<span data-ttu-id="0c1e6-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="0c1e6-394">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-394">String</span></span>|  
|<span data-ttu-id="0c1e6-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0c1e6-396">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-396">String</span></span>|  
|<span data-ttu-id="0c1e6-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-397">COLLATION_NAME</span></span>|<span data-ttu-id="0c1e6-398">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-398">String</span></span>|  
|<span data-ttu-id="0c1e6-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0c1e6-400">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-400">String</span></span>|  
|<span data-ttu-id="0c1e6-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0c1e6-402">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-402">String</span></span>|  
|<span data-ttu-id="0c1e6-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-403">DOMAIN_NAME</span></span>|<span data-ttu-id="0c1e6-404">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-404">String</span></span>|  
|<span data-ttu-id="0c1e6-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-405">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-406">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0c1e6-407">Procédures</span><span class="sxs-lookup"><span data-stu-id="0c1e6-407">Procedures</span></span>  
  
|<span data-ttu-id="0c1e6-408">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-408">ColumnName</span></span>|<span data-ttu-id="0c1e6-409">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0c1e6-411">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-411">String</span></span>|  
|<span data-ttu-id="0c1e6-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-413">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-413">String</span></span>|  
|<span data-ttu-id="0c1e6-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c1e6-415">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-415">String</span></span>|  
|<span data-ttu-id="0c1e6-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0c1e6-417">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-417">Int16</span></span>|  
|<span data-ttu-id="0c1e6-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0c1e6-419">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-419">String</span></span>|  
|<span data-ttu-id="0c1e6-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-420">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-421">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-421">String</span></span>|  
|<span data-ttu-id="0c1e6-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-422">DATE_CREATED</span></span>|<span data-ttu-id="0c1e6-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-423">DateTime</span></span>|  
|<span data-ttu-id="0c1e6-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-424">DATE_MODIFIED</span></span>|<span data-ttu-id="0c1e6-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0c1e6-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0c1e6-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0c1e6-427">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-427">ColumnName</span></span>|<span data-ttu-id="0c1e6-428">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0c1e6-430">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-430">String</span></span>|  
|<span data-ttu-id="0c1e6-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-432">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-432">String</span></span>|  
|<span data-ttu-id="0c1e6-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c1e6-434">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-434">String</span></span>|  
|<span data-ttu-id="0c1e6-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-435">COLUMN_NAME</span></span>|<span data-ttu-id="0c1e6-436">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-436">String</span></span>|  
|<span data-ttu-id="0c1e6-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-437">COLUMN_GUID</span></span>|<span data-ttu-id="0c1e6-438">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-438">Guid</span></span>|  
|<span data-ttu-id="0c1e6-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-439">COLUMN_PROPID</span></span>|<span data-ttu-id="0c1e6-440">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-440">Int64</span></span>|  
|<span data-ttu-id="0c1e6-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="0c1e6-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="0c1e6-442">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-442">Int64</span></span>|  
|<span data-ttu-id="0c1e6-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c1e6-444">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-444">Int64</span></span>|  
|<span data-ttu-id="0c1e6-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-445">IS_NULLABLE</span></span>|<span data-ttu-id="0c1e6-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-446">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-447">DATA_TYPE</span></span>|<span data-ttu-id="0c1e6-448">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-448">Int32</span></span>|  
|<span data-ttu-id="0c1e6-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-449">TYPE_GUID</span></span>|<span data-ttu-id="0c1e6-450">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-450">Guid</span></span>|  
|<span data-ttu-id="0c1e6-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0c1e6-452">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-452">Int64</span></span>|  
|<span data-ttu-id="0c1e6-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0c1e6-454">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-454">Int64</span></span>|  
|<span data-ttu-id="0c1e6-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0c1e6-456">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-456">Int32</span></span>|  
|<span data-ttu-id="0c1e6-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="0c1e6-458">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-458">Int16</span></span>|  
|<span data-ttu-id="0c1e6-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-459">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-460">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-460">String</span></span>|  
|<span data-ttu-id="0c1e6-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="0c1e6-461">OVERLOAD</span></span>|<span data-ttu-id="0c1e6-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0c1e6-463">Vues</span><span class="sxs-lookup"><span data-stu-id="0c1e6-463">Views</span></span>  
  
|<span data-ttu-id="0c1e6-464">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-464">ColumnName</span></span>|<span data-ttu-id="0c1e6-465">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-466">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-467">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-467">String</span></span>|  
|<span data-ttu-id="0c1e6-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-469">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-469">String</span></span>|  
|<span data-ttu-id="0c1e6-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-470">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-471">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-471">String</span></span>|  
|<span data-ttu-id="0c1e6-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="0c1e6-473">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-473">String</span></span>|  
|<span data-ttu-id="0c1e6-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-474">CHECK_OPTION</span></span>|<span data-ttu-id="0c1e6-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-475">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-476">IS_UPDATABLE</span></span>|<span data-ttu-id="0c1e6-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-477">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-478">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-479">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-479">String</span></span>|  
|<span data-ttu-id="0c1e6-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-480">DATE_CREATED</span></span>|<span data-ttu-id="0c1e6-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-481">DateTime</span></span>|  
|<span data-ttu-id="0c1e6-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-482">DATE_MODIFIED</span></span>|<span data-ttu-id="0c1e6-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0c1e6-484">Index</span><span class="sxs-lookup"><span data-stu-id="0c1e6-484">Indexes</span></span>  
  
|<span data-ttu-id="0c1e6-485">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-485">ColumnName</span></span>|<span data-ttu-id="0c1e6-486">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-487">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-488">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-488">String</span></span>|  
|<span data-ttu-id="0c1e6-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-490">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-490">String</span></span>|  
|<span data-ttu-id="0c1e6-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-491">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-492">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-492">String</span></span>|  
|<span data-ttu-id="0c1e6-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-493">INDEX_CATALOG</span></span>|<span data-ttu-id="0c1e6-494">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-494">String</span></span>|  
|<span data-ttu-id="0c1e6-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="0c1e6-496">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-496">String</span></span>|  
|<span data-ttu-id="0c1e6-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-497">INDEX_NAME</span></span>|<span data-ttu-id="0c1e6-498">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-498">String</span></span>|  
|<span data-ttu-id="0c1e6-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0c1e6-499">PRIMARY_KEY</span></span>|<span data-ttu-id="0c1e6-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-500">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-501">UNIQUE</span></span>|<span data-ttu-id="0c1e6-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-502">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-503">CLUSTERED</span></span>|<span data-ttu-id="0c1e6-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-504">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-505">TYPE</span></span>|<span data-ttu-id="0c1e6-506">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-506">Int32</span></span>|  
|<span data-ttu-id="0c1e6-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0c1e6-507">FILL_FACTOR</span></span>|<span data-ttu-id="0c1e6-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-508">Int32</span></span>|  
|<span data-ttu-id="0c1e6-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-509">INITIAL_SIZE</span></span>|<span data-ttu-id="0c1e6-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-510">Int32</span></span>|  
|<span data-ttu-id="0c1e6-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-511">NULLS</span></span>|<span data-ttu-id="0c1e6-512">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-512">Int32</span></span>|  
|<span data-ttu-id="0c1e6-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0c1e6-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-514">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-515">AUTO_UPDATE</span></span>|<span data-ttu-id="0c1e6-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-516">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-517">NULL_COLLATION</span></span>|<span data-ttu-id="0c1e6-518">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-518">Int32</span></span>|  
|<span data-ttu-id="0c1e6-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c1e6-520">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-520">Int64</span></span>|  
|<span data-ttu-id="0c1e6-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-521">COLUMN_NAME</span></span>|<span data-ttu-id="0c1e6-522">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-522">String</span></span>|  
|<span data-ttu-id="0c1e6-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-523">COLUMN_GUID</span></span>|<span data-ttu-id="0c1e6-524">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-524">Guid</span></span>|  
|<span data-ttu-id="0c1e6-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-525">COLUMN_PROPID</span></span>|<span data-ttu-id="0c1e6-526">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-526">Int64</span></span>|  
|<span data-ttu-id="0c1e6-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-527">COLLATION</span></span>|<span data-ttu-id="0c1e6-528">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-528">Int16</span></span>|  
|<span data-ttu-id="0c1e6-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0c1e6-529">CARDINALITY</span></span>|<span data-ttu-id="0c1e6-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="0c1e6-530">Decimal</span></span>|  
|<span data-ttu-id="0c1e6-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="0c1e6-531">PAGES</span></span>|<span data-ttu-id="0c1e6-532">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-532">Int32</span></span>|  
|<span data-ttu-id="0c1e6-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-533">FILTER_CONDITION</span></span>|<span data-ttu-id="0c1e6-534">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-534">String</span></span>|  
|<span data-ttu-id="0c1e6-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-535">INTEGRATED</span></span>|<span data-ttu-id="0c1e6-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="0c1e6-537">Fournisseur Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="0c1e6-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="0c1e6-538">Le pilote Microsoft Jet OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0c1e6-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0c1e6-539">Tables</span><span class="sxs-lookup"><span data-stu-id="0c1e6-539">Tables</span></span>  
  
-   <span data-ttu-id="0c1e6-540">Columns</span><span class="sxs-lookup"><span data-stu-id="0c1e6-540">Columns</span></span>  
  
-   <span data-ttu-id="0c1e6-541">Procédures</span><span class="sxs-lookup"><span data-stu-id="0c1e6-541">Procedures</span></span>  
  
-   <span data-ttu-id="0c1e6-542">Vues</span><span class="sxs-lookup"><span data-stu-id="0c1e6-542">Views</span></span>  
  
-   <span data-ttu-id="0c1e6-543">Index</span><span class="sxs-lookup"><span data-stu-id="0c1e6-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0c1e6-544">Tables</span><span class="sxs-lookup"><span data-stu-id="0c1e6-544">Tables</span></span>  
  
|<span data-ttu-id="0c1e6-545">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-545">ColumnName</span></span>|<span data-ttu-id="0c1e6-546">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-547">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-548">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-548">String</span></span>|  
|<span data-ttu-id="0c1e6-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-550">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-550">String</span></span>|  
|<span data-ttu-id="0c1e6-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-551">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-552">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-552">String</span></span>|  
|<span data-ttu-id="0c1e6-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-553">TABLE_TYPE</span></span>|<span data-ttu-id="0c1e6-554">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-554">String</span></span>|  
|<span data-ttu-id="0c1e6-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-555">TABLE_GUID</span></span>|<span data-ttu-id="0c1e6-556">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-556">Guid</span></span>|  
|<span data-ttu-id="0c1e6-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-557">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-558">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-558">String</span></span>|  
|<span data-ttu-id="0c1e6-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-559">TABLE_PROPID</span></span>|<span data-ttu-id="0c1e6-560">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-560">Int64</span></span>|  
|<span data-ttu-id="0c1e6-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-561">DATE_CREATED</span></span>|<span data-ttu-id="0c1e6-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-562">DateTime</span></span>|  
|<span data-ttu-id="0c1e6-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-563">DATE_MODIFIED</span></span>|<span data-ttu-id="0c1e6-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0c1e6-565">Columns</span><span class="sxs-lookup"><span data-stu-id="0c1e6-565">Columns</span></span>  
  
|<span data-ttu-id="0c1e6-566">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-566">ColumnName</span></span>|<span data-ttu-id="0c1e6-567">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-568">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-569">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-569">String</span></span>|  
|<span data-ttu-id="0c1e6-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-571">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-571">String</span></span>|  
|<span data-ttu-id="0c1e6-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-572">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-573">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-573">String</span></span>|  
|<span data-ttu-id="0c1e6-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-574">COLUMN_NAME</span></span>|<span data-ttu-id="0c1e6-575">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-575">String</span></span>|  
|<span data-ttu-id="0c1e6-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-576">COLUMN_GUID</span></span>|<span data-ttu-id="0c1e6-577">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-577">Guid</span></span>|  
|<span data-ttu-id="0c1e6-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-578">COLUMN_PROPID</span></span>|<span data-ttu-id="0c1e6-579">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-579">Int64</span></span>|  
|<span data-ttu-id="0c1e6-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c1e6-581">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-581">Int64</span></span>|  
|<span data-ttu-id="0c1e6-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0c1e6-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0c1e6-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-583">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0c1e6-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0c1e6-585">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-585">String</span></span>|  
|<span data-ttu-id="0c1e6-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="0c1e6-587">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-587">Int64</span></span>|  
|<span data-ttu-id="0c1e6-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-588">IS_NULLABLE</span></span>|<span data-ttu-id="0c1e6-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-589">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-590">DATA_TYPE</span></span>|<span data-ttu-id="0c1e6-591">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-591">Int32</span></span>|  
|<span data-ttu-id="0c1e6-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-592">TYPE_GUID</span></span>|<span data-ttu-id="0c1e6-593">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-593">Guid</span></span>|  
|<span data-ttu-id="0c1e6-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0c1e6-595">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-595">Int64</span></span>|  
|<span data-ttu-id="0c1e6-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c1e6-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0c1e6-597">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-597">Int64</span></span>|  
|<span data-ttu-id="0c1e6-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0c1e6-599">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-599">Int32</span></span>|  
|<span data-ttu-id="0c1e6-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="0c1e6-601">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-601">Int16</span></span>|  
|<span data-ttu-id="0c1e6-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="0c1e6-603">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-603">Int64</span></span>|  
|<span data-ttu-id="0c1e6-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0c1e6-605">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-605">String</span></span>|  
|<span data-ttu-id="0c1e6-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0c1e6-607">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-607">String</span></span>|  
|<span data-ttu-id="0c1e6-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0c1e6-609">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-609">String</span></span>|  
|<span data-ttu-id="0c1e6-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="0c1e6-611">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-611">String</span></span>|  
|<span data-ttu-id="0c1e6-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0c1e6-613">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-613">String</span></span>|  
|<span data-ttu-id="0c1e6-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-614">COLLATION_NAME</span></span>|<span data-ttu-id="0c1e6-615">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-615">String</span></span>|  
|<span data-ttu-id="0c1e6-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0c1e6-617">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-617">String</span></span>|  
|<span data-ttu-id="0c1e6-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0c1e6-619">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-619">String</span></span>|  
|<span data-ttu-id="0c1e6-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-620">DOMAIN_NAME</span></span>|<span data-ttu-id="0c1e6-621">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-621">String</span></span>|  
|<span data-ttu-id="0c1e6-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-622">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-623">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0c1e6-624">Procédures</span><span class="sxs-lookup"><span data-stu-id="0c1e6-624">Procedures</span></span>  
  
|<span data-ttu-id="0c1e6-625">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-625">ColumnName</span></span>|<span data-ttu-id="0c1e6-626">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0c1e6-628">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-628">String</span></span>|  
|<span data-ttu-id="0c1e6-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-630">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-630">String</span></span>|  
|<span data-ttu-id="0c1e6-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c1e6-632">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-632">String</span></span>|  
|<span data-ttu-id="0c1e6-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0c1e6-634">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-634">Int16</span></span>|  
|<span data-ttu-id="0c1e6-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0c1e6-636">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-636">String</span></span>|  
|<span data-ttu-id="0c1e6-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-637">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-638">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-638">String</span></span>|  
|<span data-ttu-id="0c1e6-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-639">DATE_CREATED</span></span>|<span data-ttu-id="0c1e6-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-640">DateTime</span></span>|  
|<span data-ttu-id="0c1e6-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-641">DATE_MODIFIED</span></span>|<span data-ttu-id="0c1e6-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0c1e6-643">Vues</span><span class="sxs-lookup"><span data-stu-id="0c1e6-643">Views</span></span>  
  
|<span data-ttu-id="0c1e6-644">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-644">ColumnName</span></span>|<span data-ttu-id="0c1e6-645">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-646">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-647">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-647">String</span></span>|  
|<span data-ttu-id="0c1e6-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-649">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-649">String</span></span>|  
|<span data-ttu-id="0c1e6-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-650">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-651">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-651">String</span></span>|  
|<span data-ttu-id="0c1e6-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="0c1e6-653">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-653">String</span></span>|  
|<span data-ttu-id="0c1e6-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-654">CHECK_OPTION</span></span>|<span data-ttu-id="0c1e6-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-655">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-656">IS_UPDATABLE</span></span>|<span data-ttu-id="0c1e6-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-657">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-658">DESCRIPTION</span></span>|<span data-ttu-id="0c1e6-659">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-659">String</span></span>|  
|<span data-ttu-id="0c1e6-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-660">DATE_CREATED</span></span>|<span data-ttu-id="0c1e6-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-661">DateTime</span></span>|  
|<span data-ttu-id="0c1e6-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-662">DATE_MODIFIED</span></span>|<span data-ttu-id="0c1e6-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="0c1e6-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0c1e6-664">Index</span><span class="sxs-lookup"><span data-stu-id="0c1e6-664">Indexes</span></span>  
  
|<span data-ttu-id="0c1e6-665">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-665">ColumnName</span></span>|<span data-ttu-id="0c1e6-666">Type de données</span><span class="sxs-lookup"><span data-stu-id="0c1e6-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c1e6-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-667">TABLE_CATALOG</span></span>|<span data-ttu-id="0c1e6-668">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-668">String</span></span>|  
|<span data-ttu-id="0c1e6-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="0c1e6-670">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-670">String</span></span>|  
|<span data-ttu-id="0c1e6-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-671">TABLE_NAME</span></span>|<span data-ttu-id="0c1e6-672">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-672">String</span></span>|  
|<span data-ttu-id="0c1e6-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c1e6-673">INDEX_CATALOG</span></span>|<span data-ttu-id="0c1e6-674">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-674">String</span></span>|  
|<span data-ttu-id="0c1e6-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c1e6-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="0c1e6-676">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-676">String</span></span>|  
|<span data-ttu-id="0c1e6-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-677">INDEX_NAME</span></span>|<span data-ttu-id="0c1e6-678">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-678">String</span></span>|  
|<span data-ttu-id="0c1e6-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0c1e6-679">PRIMARY_KEY</span></span>|<span data-ttu-id="0c1e6-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-680">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-681">UNIQUE</span></span>|<span data-ttu-id="0c1e6-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-682">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-683">CLUSTERED</span></span>|<span data-ttu-id="0c1e6-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-684">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-685">TYPE</span></span>|<span data-ttu-id="0c1e6-686">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-686">Int32</span></span>|  
|<span data-ttu-id="0c1e6-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0c1e6-687">FILL_FACTOR</span></span>|<span data-ttu-id="0c1e6-688">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-688">Int32</span></span>|  
|<span data-ttu-id="0c1e6-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-689">INITIAL_SIZE</span></span>|<span data-ttu-id="0c1e6-690">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-690">Int32</span></span>|  
|<span data-ttu-id="0c1e6-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-691">NULLS</span></span>|<span data-ttu-id="0c1e6-692">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-692">Int32</span></span>|  
|<span data-ttu-id="0c1e6-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0c1e6-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0c1e6-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-694">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0c1e6-695">AUTO_UPDATE</span></span>|<span data-ttu-id="0c1e6-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="0c1e6-696">Boolean</span></span>|  
|<span data-ttu-id="0c1e6-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-697">NULL_COLLATION</span></span>|<span data-ttu-id="0c1e6-698">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-698">Int32</span></span>|  
|<span data-ttu-id="0c1e6-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c1e6-700">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-700">Int64</span></span>|  
|<span data-ttu-id="0c1e6-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c1e6-701">COLUMN_NAME</span></span>|<span data-ttu-id="0c1e6-702">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-702">String</span></span>|  
|<span data-ttu-id="0c1e6-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-703">COLUMN_GUID</span></span>|<span data-ttu-id="0c1e6-704">Guid</span><span class="sxs-lookup"><span data-stu-id="0c1e6-704">Guid</span></span>|  
|<span data-ttu-id="0c1e6-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0c1e6-705">COLUMN_PROPID</span></span>|<span data-ttu-id="0c1e6-706">Int64</span><span class="sxs-lookup"><span data-stu-id="0c1e6-706">Int64</span></span>|  
|<span data-ttu-id="0c1e6-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-707">COLLATION</span></span>|<span data-ttu-id="0c1e6-708">Int16</span><span class="sxs-lookup"><span data-stu-id="0c1e6-708">Int16</span></span>|  
|<span data-ttu-id="0c1e6-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0c1e6-709">CARDINALITY</span></span>|<span data-ttu-id="0c1e6-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="0c1e6-710">Decimal</span></span>|  
|<span data-ttu-id="0c1e6-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="0c1e6-711">PAGES</span></span>|<span data-ttu-id="0c1e6-712">Int32</span><span class="sxs-lookup"><span data-stu-id="0c1e6-712">Int32</span></span>|  
|<span data-ttu-id="0c1e6-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0c1e6-713">FILTER_CONDITION</span></span>|<span data-ttu-id="0c1e6-714">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0c1e6-714">String</span></span>|  
|<span data-ttu-id="0c1e6-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0c1e6-715">INTEGRATED</span></span>|<span data-ttu-id="0c1e6-716">Booléen</span><span class="sxs-lookup"><span data-stu-id="0c1e6-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c1e6-717">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c1e6-717">See Also</span></span>  
 [<span data-ttu-id="0c1e6-718">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="0c1e6-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
