---
title: "Collections de schémas ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45cfed80decc2336c5a2bacf24fd075c2b81c531
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="dd1dc-102">Collections de schémas ODBC</span><span class="sxs-lookup"><span data-stu-id="dd1dc-102">ODBC Schema Collections</span></span>
<span data-ttu-id="dd1dc-103">Cette section traite de la prise en charge des collections de schémas pour les pilotes ODBC Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="dd1dc-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="dd1dc-104">Pilote Microsoft SQL Server ODBC</span><span class="sxs-lookup"><span data-stu-id="dd1dc-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="dd1dc-105">Le pilote ODBC de Microsoft SQL Server prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="dd1dc-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dd1dc-106">Tables</span><span class="sxs-lookup"><span data-stu-id="dd1dc-106">Tables</span></span>  
  
-   <span data-ttu-id="dd1dc-107">Index</span><span class="sxs-lookup"><span data-stu-id="dd1dc-107">Indexes</span></span>  
  
-   <span data-ttu-id="dd1dc-108">Columns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-108">Columns</span></span>  
  
-   <span data-ttu-id="dd1dc-109">Procédures</span><span class="sxs-lookup"><span data-stu-id="dd1dc-109">Procedures</span></span>  
  
-   <span data-ttu-id="dd1dc-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="dd1dc-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dd1dc-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="dd1dc-112">Vues</span><span class="sxs-lookup"><span data-stu-id="dd1dc-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="dd1dc-113">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="dd1dc-113">Tables and Views</span></span>  
  
|<span data-ttu-id="dd1dc-114">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-114">ColumnName</span></span>|<span data-ttu-id="dd1dc-115">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="dd1dc-116">TABLE_CAT</span></span>|<span data-ttu-id="dd1dc-117">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-117">String</span></span>|  
|<span data-ttu-id="dd1dc-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dd1dc-118">TABLE_SCHEM</span></span>|<span data-ttu-id="dd1dc-119">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-119">String</span></span>|  
|<span data-ttu-id="dd1dc-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-120">TABLE_NAME</span></span>|<span data-ttu-id="dd1dc-121">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-121">String</span></span>|  
|<span data-ttu-id="dd1dc-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-122">TABLE_TYPE</span></span>|<span data-ttu-id="dd1dc-123">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-123">String</span></span>|  
|<span data-ttu-id="dd1dc-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-124">REMARKS</span></span>|<span data-ttu-id="dd1dc-125">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="dd1dc-126">Index</span><span class="sxs-lookup"><span data-stu-id="dd1dc-126">Indexes</span></span>  
  
|<span data-ttu-id="dd1dc-127">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-127">ColumnName</span></span>|<span data-ttu-id="dd1dc-128">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="dd1dc-129">TABLE_CAT</span></span>|<span data-ttu-id="dd1dc-130">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-130">String</span></span>|  
|<span data-ttu-id="dd1dc-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dd1dc-131">TABLE_SCHEM</span></span>|<span data-ttu-id="dd1dc-132">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-132">String</span></span>|  
|<span data-ttu-id="dd1dc-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-133">TABLE_NAME</span></span>|<span data-ttu-id="dd1dc-134">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-134">String</span></span>|  
|<span data-ttu-id="dd1dc-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-135">NON_UNIQUE</span></span>|<span data-ttu-id="dd1dc-136">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-136">Int16</span></span>|  
|<span data-ttu-id="dd1dc-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-138">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-138">String</span></span>|  
|<span data-ttu-id="dd1dc-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-139">INDEX_NAME</span></span>|<span data-ttu-id="dd1dc-140">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-140">String</span></span>|  
|<span data-ttu-id="dd1dc-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-141">TYPE</span></span>|<span data-ttu-id="dd1dc-142">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-142">Int16</span></span>|  
|<span data-ttu-id="dd1dc-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-144">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-144">Int16</span></span>|  
|<span data-ttu-id="dd1dc-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-145">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-146">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-146">String</span></span>|  
|<span data-ttu-id="dd1dc-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="dd1dc-147">ASC_OR_DESC</span></span>|<span data-ttu-id="dd1dc-148">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-148">String</span></span>|  
|<span data-ttu-id="dd1dc-149">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="dd1dc-149">CARDINATLITY</span></span>|<span data-ttu-id="dd1dc-150">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-150">Int32</span></span>|  
|<span data-ttu-id="dd1dc-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="dd1dc-151">PAGES</span></span>|<span data-ttu-id="dd1dc-152">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-152">Int32</span></span>|  
|<span data-ttu-id="dd1dc-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-153">FILTER_CONDITION</span></span>|<span data-ttu-id="dd1dc-154">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-154">String</span></span>|  
|<span data-ttu-id="dd1dc-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dd1dc-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="dd1dc-156">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-156">String</span></span>|  
|<span data-ttu-id="dd1dc-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-158">Byte</span><span class="sxs-lookup"><span data-stu-id="dd1dc-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dd1dc-159">Columns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-159">Columns</span></span>  
  
|<span data-ttu-id="dd1dc-160">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-160">ColumnName</span></span>|<span data-ttu-id="dd1dc-161">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="dd1dc-162">TABLE_CAT</span></span>|<span data-ttu-id="dd1dc-163">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-163">String</span></span>|  
|<span data-ttu-id="dd1dc-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dd1dc-164">TABLE_SCHEM</span></span>|<span data-ttu-id="dd1dc-165">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-165">String</span></span>|  
|<span data-ttu-id="dd1dc-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-166">TABLE_NAME</span></span>|<span data-ttu-id="dd1dc-167">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-167">String</span></span>|  
|<span data-ttu-id="dd1dc-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-168">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-169">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-169">String</span></span>|  
|<span data-ttu-id="dd1dc-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-170">DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-171">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-171">Int16</span></span>|  
|<span data-ttu-id="dd1dc-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-172">TYPE_NAME</span></span>|<span data-ttu-id="dd1dc-173">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-173">String</span></span>|  
|<span data-ttu-id="dd1dc-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-174">COLUMN_SIZE</span></span>|<span data-ttu-id="dd1dc-175">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-175">Int32</span></span>|  
|<span data-ttu-id="dd1dc-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="dd1dc-177">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-177">Int32</span></span>|  
|<span data-ttu-id="dd1dc-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="dd1dc-179">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-179">Int16</span></span>|  
|<span data-ttu-id="dd1dc-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="dd1dc-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="dd1dc-181">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-181">Int16</span></span>|  
|<span data-ttu-id="dd1dc-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-182">NULLABLE</span></span>|<span data-ttu-id="dd1dc-183">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-183">Int16</span></span>|  
|<span data-ttu-id="dd1dc-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-184">REMARKS</span></span>|<span data-ttu-id="dd1dc-185">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-185">String</span></span>|  
|<span data-ttu-id="dd1dc-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="dd1dc-186">COLUMN_DEF</span></span>|<span data-ttu-id="dd1dc-187">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-187">String</span></span>|  
|<span data-ttu-id="dd1dc-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-189">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-189">Int16</span></span>|  
|<span data-ttu-id="dd1dc-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="dd1dc-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="dd1dc-191">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-191">Int16</span></span>|  
|<span data-ttu-id="dd1dc-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="dd1dc-193">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-193">Int32</span></span>|  
|<span data-ttu-id="dd1dc-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-195">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-195">Int32</span></span>|  
|<span data-ttu-id="dd1dc-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-196">IS_NULLABLE</span></span>|<span data-ttu-id="dd1dc-197">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-197">String</span></span>|  
|<span data-ttu-id="dd1dc-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dd1dc-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="dd1dc-199">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-199">String</span></span>|  
|<span data-ttu-id="dd1dc-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dd1dc-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="dd1dc-201">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-201">String</span></span>|  
|<span data-ttu-id="dd1dc-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-203">Byte</span><span class="sxs-lookup"><span data-stu-id="dd1dc-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dd1dc-204">Procédures</span><span class="sxs-lookup"><span data-stu-id="dd1dc-204">Procedures</span></span>  
  
|<span data-ttu-id="dd1dc-205">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-205">ColumnName</span></span>|<span data-ttu-id="dd1dc-206">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="dd1dc-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="dd1dc-208">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-208">String</span></span>|  
|<span data-ttu-id="dd1dc-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dd1dc-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="dd1dc-210">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-210">String</span></span>|  
|<span data-ttu-id="dd1dc-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="dd1dc-212">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-212">String</span></span>|  
|<span data-ttu-id="dd1dc-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="dd1dc-214">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-214">Int32</span></span>|  
|<span data-ttu-id="dd1dc-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="dd1dc-216">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-216">Int32</span></span>|  
|<span data-ttu-id="dd1dc-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="dd1dc-218">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-218">Int32</span></span>|  
|<span data-ttu-id="dd1dc-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-219">REMARKS</span></span>|<span data-ttu-id="dd1dc-220">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-220">String</span></span>|  
|<span data-ttu-id="dd1dc-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dd1dc-222">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="dd1dc-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="dd1dc-224">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-224">ColumnName</span></span>|<span data-ttu-id="dd1dc-225">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="dd1dc-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="dd1dc-227">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-227">String</span></span>|  
|<span data-ttu-id="dd1dc-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dd1dc-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="dd1dc-229">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-229">String</span></span>|  
|<span data-ttu-id="dd1dc-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="dd1dc-231">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-231">String</span></span>|  
|<span data-ttu-id="dd1dc-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-232">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-233">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-233">String</span></span>|  
|<span data-ttu-id="dd1dc-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-234">COLUMN_TYPE</span></span>|<span data-ttu-id="dd1dc-235">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-235">Int16</span></span>|  
|<span data-ttu-id="dd1dc-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-236">DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-237">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-237">Int16</span></span>|  
|<span data-ttu-id="dd1dc-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-238">TYPE_NAME</span></span>|<span data-ttu-id="dd1dc-239">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-239">String</span></span>|  
|<span data-ttu-id="dd1dc-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-240">COLUMN_SIZE</span></span>|<span data-ttu-id="dd1dc-241">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-241">Int32</span></span>|  
|<span data-ttu-id="dd1dc-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="dd1dc-243">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-243">Int32</span></span>|  
|<span data-ttu-id="dd1dc-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="dd1dc-245">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-245">Int16</span></span>|  
|<span data-ttu-id="dd1dc-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="dd1dc-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="dd1dc-247">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-247">Int16</span></span>|  
|<span data-ttu-id="dd1dc-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-248">NULLABLE</span></span>|<span data-ttu-id="dd1dc-249">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-249">Int16</span></span>|  
|<span data-ttu-id="dd1dc-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-250">REMARKS</span></span>|<span data-ttu-id="dd1dc-251">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-251">String</span></span>|  
|<span data-ttu-id="dd1dc-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="dd1dc-252">COLUMN_DEF</span></span>|<span data-ttu-id="dd1dc-253">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-253">String</span></span>|  
|<span data-ttu-id="dd1dc-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-255">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-255">Int16</span></span>|  
|<span data-ttu-id="dd1dc-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="dd1dc-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="dd1dc-257">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-257">Int16</span></span>|  
|<span data-ttu-id="dd1dc-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="dd1dc-259">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-259">Int32</span></span>|  
|<span data-ttu-id="dd1dc-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-261">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-261">Int32</span></span>|  
|<span data-ttu-id="dd1dc-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-262">IS_NULLABLE</span></span>|<span data-ttu-id="dd1dc-263">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-263">String</span></span>|  
|<span data-ttu-id="dd1dc-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dd1dc-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="dd1dc-265">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-265">String</span></span>|  
|<span data-ttu-id="dd1dc-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dd1dc-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="dd1dc-267">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-267">String</span></span>|  
|<span data-ttu-id="dd1dc-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-269">Byte</span><span class="sxs-lookup"><span data-stu-id="dd1dc-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="dd1dc-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dd1dc-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="dd1dc-271">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-271">ColumnName</span></span>|<span data-ttu-id="dd1dc-272">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="dd1dc-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="dd1dc-274">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-274">String</span></span>|  
|<span data-ttu-id="dd1dc-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dd1dc-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="dd1dc-276">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-276">String</span></span>|  
|<span data-ttu-id="dd1dc-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="dd1dc-278">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-278">String</span></span>|  
|<span data-ttu-id="dd1dc-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-279">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-280">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-280">String</span></span>|  
|<span data-ttu-id="dd1dc-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-281">COLUMN_TYPE</span></span>|<span data-ttu-id="dd1dc-282">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-282">Int16</span></span>|  
|<span data-ttu-id="dd1dc-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-283">DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-284">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-284">Int16</span></span>|  
|<span data-ttu-id="dd1dc-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-285">TYPE_NAME</span></span>|<span data-ttu-id="dd1dc-286">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-286">String</span></span>|  
|<span data-ttu-id="dd1dc-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-287">COLUMN_SIZE</span></span>|<span data-ttu-id="dd1dc-288">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-288">Int32</span></span>|  
|<span data-ttu-id="dd1dc-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="dd1dc-290">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-290">Int32</span></span>|  
|<span data-ttu-id="dd1dc-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="dd1dc-292">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-292">Int16</span></span>|  
|<span data-ttu-id="dd1dc-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="dd1dc-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="dd1dc-294">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-294">Int16</span></span>|  
|<span data-ttu-id="dd1dc-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-295">NULLABLE</span></span>|<span data-ttu-id="dd1dc-296">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-296">Int16</span></span>|  
|<span data-ttu-id="dd1dc-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-297">REMARKS</span></span>|<span data-ttu-id="dd1dc-298">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-298">String</span></span>|  
|<span data-ttu-id="dd1dc-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="dd1dc-299">COLUMN_DEF</span></span>|<span data-ttu-id="dd1dc-300">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-300">String</span></span>|  
|<span data-ttu-id="dd1dc-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-302">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-302">Int16</span></span>|  
|<span data-ttu-id="dd1dc-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="dd1dc-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="dd1dc-304">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-304">Int16</span></span>|  
|<span data-ttu-id="dd1dc-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="dd1dc-306">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-306">Int32</span></span>|  
|<span data-ttu-id="dd1dc-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-308">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-308">Int32</span></span>|  
|<span data-ttu-id="dd1dc-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-309">IS_NULLABLE</span></span>|<span data-ttu-id="dd1dc-310">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-310">String</span></span>|  
|<span data-ttu-id="dd1dc-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dd1dc-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="dd1dc-312">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-312">String</span></span>|  
|<span data-ttu-id="dd1dc-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dd1dc-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="dd1dc-314">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-314">String</span></span>|  
|<span data-ttu-id="dd1dc-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-316">Byte</span><span class="sxs-lookup"><span data-stu-id="dd1dc-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="dd1dc-317">Pilote Microsoft Oracle ODBC</span><span class="sxs-lookup"><span data-stu-id="dd1dc-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="dd1dc-318">Le pilote Microsoft SQL Server Oracle ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="dd1dc-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dd1dc-319">Tables</span><span class="sxs-lookup"><span data-stu-id="dd1dc-319">Tables</span></span>  
  
-   <span data-ttu-id="dd1dc-320">Columns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-320">Columns</span></span>  
  
-   <span data-ttu-id="dd1dc-321">Procédures</span><span class="sxs-lookup"><span data-stu-id="dd1dc-321">Procedures</span></span>  
  
-   <span data-ttu-id="dd1dc-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="dd1dc-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dd1dc-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="dd1dc-324">Vues</span><span class="sxs-lookup"><span data-stu-id="dd1dc-324">Views</span></span>  
  
-   <span data-ttu-id="dd1dc-325">Index</span><span class="sxs-lookup"><span data-stu-id="dd1dc-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="dd1dc-326">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="dd1dc-326">Tables and Views</span></span>  
  
|<span data-ttu-id="dd1dc-327">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-327">ColumnName</span></span>|<span data-ttu-id="dd1dc-328">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-330">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-330">String</span></span>|  
|<span data-ttu-id="dd1dc-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-331">TABLE_OWNER</span></span>|<span data-ttu-id="dd1dc-332">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-332">String</span></span>|  
|<span data-ttu-id="dd1dc-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-333">TABLE_NAME</span></span>|<span data-ttu-id="dd1dc-334">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-334">String</span></span>|  
|<span data-ttu-id="dd1dc-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-335">TABLE_TYPE</span></span>|<span data-ttu-id="dd1dc-336">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-336">String</span></span>|  
|<span data-ttu-id="dd1dc-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-337">REMARKS</span></span>|<span data-ttu-id="dd1dc-338">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dd1dc-339">Columns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-339">Columns</span></span>  
  
|<span data-ttu-id="dd1dc-340">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-340">ColumnName</span></span>|<span data-ttu-id="dd1dc-341">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-343">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-343">String</span></span>|  
|<span data-ttu-id="dd1dc-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-344">TABLE_OWNER</span></span>|<span data-ttu-id="dd1dc-345">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-345">String</span></span>|  
|<span data-ttu-id="dd1dc-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-346">TABLE_NAME</span></span>|<span data-ttu-id="dd1dc-347">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-347">String</span></span>|  
|<span data-ttu-id="dd1dc-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-348">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-349">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-349">String</span></span>|  
|<span data-ttu-id="dd1dc-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-350">DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-351">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-351">Int16</span></span>|  
|<span data-ttu-id="dd1dc-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-352">TYPE_NAME</span></span>|<span data-ttu-id="dd1dc-353">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-353">String</span></span>|  
|<span data-ttu-id="dd1dc-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-354">PRECISION</span></span>|<span data-ttu-id="dd1dc-355">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-355">Int32</span></span>|  
|<span data-ttu-id="dd1dc-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-356">LENGTH</span></span>|<span data-ttu-id="dd1dc-357">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-357">Int32</span></span>|  
|<span data-ttu-id="dd1dc-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-358">SCALE</span></span>|<span data-ttu-id="dd1dc-359">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-359">Int16</span></span>|  
|<span data-ttu-id="dd1dc-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="dd1dc-360">RADIX</span></span>|<span data-ttu-id="dd1dc-361">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-361">Int16</span></span>|  
|<span data-ttu-id="dd1dc-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-362">NULLABLE</span></span>|<span data-ttu-id="dd1dc-363">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-363">Int16</span></span>|  
|<span data-ttu-id="dd1dc-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-364">REMARKS</span></span>|<span data-ttu-id="dd1dc-365">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-365">String</span></span>|  
|<span data-ttu-id="dd1dc-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-367">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dd1dc-368">Procédures</span><span class="sxs-lookup"><span data-stu-id="dd1dc-368">Procedures</span></span>  
  
|<span data-ttu-id="dd1dc-369">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-369">ColumnName</span></span>|<span data-ttu-id="dd1dc-370">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-372">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-372">String</span></span>|  
|<span data-ttu-id="dd1dc-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="dd1dc-374">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-374">String</span></span>|  
|<span data-ttu-id="dd1dc-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="dd1dc-376">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-376">String</span></span>|  
|<span data-ttu-id="dd1dc-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="dd1dc-378">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-378">Int16</span></span>|  
|<span data-ttu-id="dd1dc-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="dd1dc-380">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-380">Int16</span></span>|  
|<span data-ttu-id="dd1dc-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="dd1dc-382">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-382">Int16</span></span>|  
|<span data-ttu-id="dd1dc-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-383">REMARKS</span></span>|<span data-ttu-id="dd1dc-384">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-384">String</span></span>|  
|<span data-ttu-id="dd1dc-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dd1dc-386">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="dd1dc-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="dd1dc-388">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-388">ColumnName</span></span>|<span data-ttu-id="dd1dc-389">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-391">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-391">String</span></span>|  
|<span data-ttu-id="dd1dc-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="dd1dc-393">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-393">String</span></span>|  
|<span data-ttu-id="dd1dc-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="dd1dc-395">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-395">String</span></span>|  
|<span data-ttu-id="dd1dc-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-396">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-397">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-397">String</span></span>|  
|<span data-ttu-id="dd1dc-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-398">COLUMN_TYPE</span></span>|<span data-ttu-id="dd1dc-399">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-399">Int16</span></span>|  
|<span data-ttu-id="dd1dc-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-400">DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-401">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-401">Int16</span></span>|  
|<span data-ttu-id="dd1dc-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-402">TYPE_NAME</span></span>|<span data-ttu-id="dd1dc-403">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-403">String</span></span>|  
|<span data-ttu-id="dd1dc-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-404">PRECISION</span></span>|<span data-ttu-id="dd1dc-405">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-405">Int32</span></span>|  
|<span data-ttu-id="dd1dc-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-406">LENGTH</span></span>|<span data-ttu-id="dd1dc-407">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-407">Int32</span></span>|  
|<span data-ttu-id="dd1dc-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-408">SCALE</span></span>|<span data-ttu-id="dd1dc-409">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-409">Int16</span></span>|  
|<span data-ttu-id="dd1dc-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="dd1dc-410">RADIX</span></span>|<span data-ttu-id="dd1dc-411">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-411">Int16</span></span>|  
|<span data-ttu-id="dd1dc-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-412">NULLABLE</span></span>|<span data-ttu-id="dd1dc-413">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-413">Int16</span></span>|  
|<span data-ttu-id="dd1dc-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-414">REMARKS</span></span>|<span data-ttu-id="dd1dc-415">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-415">String</span></span>|  
|<span data-ttu-id="dd1dc-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="dd1dc-416">OVERLOAD</span></span>|<span data-ttu-id="dd1dc-417">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-417">Int32</span></span>|  
|<span data-ttu-id="dd1dc-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-419">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="dd1dc-420">Pilote Microsoft Jet ODBC</span><span class="sxs-lookup"><span data-stu-id="dd1dc-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="dd1dc-421">Le pilote Microsoft Jet ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="dd1dc-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dd1dc-422">Tables</span><span class="sxs-lookup"><span data-stu-id="dd1dc-422">Tables</span></span>  
  
-   <span data-ttu-id="dd1dc-423">Index</span><span class="sxs-lookup"><span data-stu-id="dd1dc-423">Indexes</span></span>  
  
-   <span data-ttu-id="dd1dc-424">Columns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-424">Columns</span></span>  
  
-   <span data-ttu-id="dd1dc-425">Procédures</span><span class="sxs-lookup"><span data-stu-id="dd1dc-425">Procedures</span></span>  
  
-   <span data-ttu-id="dd1dc-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="dd1dc-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dd1dc-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="dd1dc-428">Vues</span><span class="sxs-lookup"><span data-stu-id="dd1dc-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="dd1dc-429">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="dd1dc-429">Tables and Views</span></span>  
  
|<span data-ttu-id="dd1dc-430">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-430">ColumnName</span></span>|<span data-ttu-id="dd1dc-431">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-433">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-433">String</span></span>|  
|<span data-ttu-id="dd1dc-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-434">TABLE_OWNER</span></span>|<span data-ttu-id="dd1dc-435">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-435">String</span></span>|  
|<span data-ttu-id="dd1dc-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-436">TABLE_NAME</span></span>|<span data-ttu-id="dd1dc-437">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-437">String</span></span>|  
|<span data-ttu-id="dd1dc-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-438">TABLE_TYPE</span></span>|<span data-ttu-id="dd1dc-439">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-439">String</span></span>|  
|<span data-ttu-id="dd1dc-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-440">REMARKS</span></span>|<span data-ttu-id="dd1dc-441">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dd1dc-442">Columns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-442">Columns</span></span>  
  
|<span data-ttu-id="dd1dc-443">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-443">ColumnName</span></span>|<span data-ttu-id="dd1dc-444">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-446">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-446">String</span></span>|  
|<span data-ttu-id="dd1dc-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-447">TABLE_OWNER</span></span>|<span data-ttu-id="dd1dc-448">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-448">String</span></span>|  
|<span data-ttu-id="dd1dc-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-449">TABLE_NAME</span></span>|<span data-ttu-id="dd1dc-450">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-450">String</span></span>|  
|<span data-ttu-id="dd1dc-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-451">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-452">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-452">String</span></span>|  
|<span data-ttu-id="dd1dc-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-453">DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-454">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-454">Int16</span></span>|  
|<span data-ttu-id="dd1dc-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-455">TYPE_NAME</span></span>|<span data-ttu-id="dd1dc-456">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-456">String</span></span>|  
|<span data-ttu-id="dd1dc-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-457">PRECISION</span></span>|<span data-ttu-id="dd1dc-458">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-458">Int32</span></span>|  
|<span data-ttu-id="dd1dc-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-459">LENGTH</span></span>|<span data-ttu-id="dd1dc-460">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-460">Int32</span></span>|  
|<span data-ttu-id="dd1dc-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-461">SCALE</span></span>|<span data-ttu-id="dd1dc-462">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-462">Int16</span></span>|  
|<span data-ttu-id="dd1dc-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="dd1dc-463">RADIX</span></span>|<span data-ttu-id="dd1dc-464">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-464">Int16</span></span>|  
|<span data-ttu-id="dd1dc-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-465">NULLABLE</span></span>|<span data-ttu-id="dd1dc-466">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-466">Int16</span></span>|  
|<span data-ttu-id="dd1dc-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-467">REMARKS</span></span>|<span data-ttu-id="dd1dc-468">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-468">String</span></span>|  
|<span data-ttu-id="dd1dc-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-470">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dd1dc-471">Procédures</span><span class="sxs-lookup"><span data-stu-id="dd1dc-471">Procedures</span></span>  
  
|<span data-ttu-id="dd1dc-472">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-472">ColumnName</span></span>|<span data-ttu-id="dd1dc-473">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-475">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-475">String</span></span>|  
|<span data-ttu-id="dd1dc-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="dd1dc-477">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-477">String</span></span>|  
|<span data-ttu-id="dd1dc-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="dd1dc-479">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-479">String</span></span>|  
|<span data-ttu-id="dd1dc-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="dd1dc-481">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-481">Int16</span></span>|  
|<span data-ttu-id="dd1dc-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="dd1dc-483">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-483">Int16</span></span>|  
|<span data-ttu-id="dd1dc-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="dd1dc-485">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-485">Int16</span></span>|  
|<span data-ttu-id="dd1dc-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-486">REMARKS</span></span>|<span data-ttu-id="dd1dc-487">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-487">String</span></span>|  
|<span data-ttu-id="dd1dc-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dd1dc-489">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="dd1dc-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dd1dc-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="dd1dc-491">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-491">ColumnName</span></span>|<span data-ttu-id="dd1dc-492">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="dd1dc-494">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-494">String</span></span>|  
|<span data-ttu-id="dd1dc-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1dc-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="dd1dc-496">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-496">String</span></span>|  
|<span data-ttu-id="dd1dc-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="dd1dc-498">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-498">String</span></span>|  
|<span data-ttu-id="dd1dc-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-499">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-500">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-500">String</span></span>|  
|<span data-ttu-id="dd1dc-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-501">COLUMN_TYPE</span></span>|<span data-ttu-id="dd1dc-502">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-502">Int16</span></span>|  
|<span data-ttu-id="dd1dc-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-503">DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-504">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-504">Int16</span></span>|  
|<span data-ttu-id="dd1dc-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-505">TYPE_NAME</span></span>|<span data-ttu-id="dd1dc-506">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-506">String</span></span>|  
|<span data-ttu-id="dd1dc-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-507">PRECISION</span></span>|<span data-ttu-id="dd1dc-508">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-508">Int32</span></span>|  
|<span data-ttu-id="dd1dc-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-509">LENGTH</span></span>|<span data-ttu-id="dd1dc-510">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-510">Int32</span></span>|  
|<span data-ttu-id="dd1dc-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-511">SCALE</span></span>|<span data-ttu-id="dd1dc-512">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-512">Int16</span></span>|  
|<span data-ttu-id="dd1dc-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="dd1dc-513">RADIX</span></span>|<span data-ttu-id="dd1dc-514">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-514">Int16</span></span>|  
|<span data-ttu-id="dd1dc-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-515">NULLABLE</span></span>|<span data-ttu-id="dd1dc-516">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-516">Int16</span></span>|  
|<span data-ttu-id="dd1dc-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-517">REMARKS</span></span>|<span data-ttu-id="dd1dc-518">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-518">String</span></span>|  
|<span data-ttu-id="dd1dc-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="dd1dc-519">OVERLOAD</span></span>|<span data-ttu-id="dd1dc-520">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-520">Int32</span></span>|  
|<span data-ttu-id="dd1dc-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-522">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="dd1dc-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dd1dc-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="dd1dc-524">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-524">ColumnName</span></span>|<span data-ttu-id="dd1dc-525">Type de données</span><span class="sxs-lookup"><span data-stu-id="dd1dc-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dd1dc-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="dd1dc-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="dd1dc-527">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-527">String</span></span>|  
|<span data-ttu-id="dd1dc-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dd1dc-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="dd1dc-529">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-529">String</span></span>|  
|<span data-ttu-id="dd1dc-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="dd1dc-531">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-531">String</span></span>|  
|<span data-ttu-id="dd1dc-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-532">COLUMN_NAME</span></span>|<span data-ttu-id="dd1dc-533">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-533">String</span></span>|  
|<span data-ttu-id="dd1dc-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-534">COLUMN_TYPE</span></span>|<span data-ttu-id="dd1dc-535">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-535">Int16</span></span>|  
|<span data-ttu-id="dd1dc-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-536">DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-537">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-537">Int16</span></span>|  
|<span data-ttu-id="dd1dc-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dd1dc-538">TYPE_NAME</span></span>|<span data-ttu-id="dd1dc-539">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-539">String</span></span>|  
|<span data-ttu-id="dd1dc-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-540">COLUMN_SIZE</span></span>|<span data-ttu-id="dd1dc-541">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-541">Int32</span></span>|  
|<span data-ttu-id="dd1dc-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="dd1dc-543">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-543">Int32</span></span>|  
|<span data-ttu-id="dd1dc-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="dd1dc-545">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-545">Int16</span></span>|  
|<span data-ttu-id="dd1dc-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="dd1dc-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="dd1dc-547">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-547">Int16</span></span>|  
|<span data-ttu-id="dd1dc-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-548">NULLABLE</span></span>|<span data-ttu-id="dd1dc-549">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-549">Int16</span></span>|  
|<span data-ttu-id="dd1dc-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="dd1dc-550">REMARKS</span></span>|<span data-ttu-id="dd1dc-551">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-551">String</span></span>|  
|<span data-ttu-id="dd1dc-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="dd1dc-552">COLUMN_DEF</span></span>|<span data-ttu-id="dd1dc-553">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-553">String</span></span>|  
|<span data-ttu-id="dd1dc-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="dd1dc-555">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-555">Int16</span></span>|  
|<span data-ttu-id="dd1dc-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="dd1dc-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="dd1dc-557">Int16</span><span class="sxs-lookup"><span data-stu-id="dd1dc-557">Int16</span></span>|  
|<span data-ttu-id="dd1dc-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dd1dc-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="dd1dc-559">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-559">Int32</span></span>|  
|<span data-ttu-id="dd1dc-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dd1dc-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="dd1dc-561">Int32</span><span class="sxs-lookup"><span data-stu-id="dd1dc-561">Int32</span></span>|  
|<span data-ttu-id="dd1dc-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dd1dc-562">IS_NULLABLE</span></span>|<span data-ttu-id="dd1dc-563">Chaîne</span><span class="sxs-lookup"><span data-stu-id="dd1dc-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd1dc-564">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd1dc-564">See Also</span></span>  
 [<span data-ttu-id="dd1dc-565">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="dd1dc-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
