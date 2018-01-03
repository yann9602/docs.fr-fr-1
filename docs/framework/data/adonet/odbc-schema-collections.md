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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b8c31f4e8b1463c184c9a8ff1cf64808783f030d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="81363-102">Collections de schémas ODBC</span><span class="sxs-lookup"><span data-stu-id="81363-102">ODBC Schema Collections</span></span>
<span data-ttu-id="81363-103">Cette section traite de la prise en charge des collections de schémas pour les pilotes ODBC Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="81363-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="81363-104">Pilote Microsoft SQL Server ODBC</span><span class="sxs-lookup"><span data-stu-id="81363-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="81363-105">Le pilote ODBC de Microsoft SQL Server prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="81363-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="81363-106">Tables</span><span class="sxs-lookup"><span data-stu-id="81363-106">Tables</span></span>  
  
-   <span data-ttu-id="81363-107">Index</span><span class="sxs-lookup"><span data-stu-id="81363-107">Indexes</span></span>  
  
-   <span data-ttu-id="81363-108">Columns</span><span class="sxs-lookup"><span data-stu-id="81363-108">Columns</span></span>  
  
-   <span data-ttu-id="81363-109">Procédures</span><span class="sxs-lookup"><span data-stu-id="81363-109">Procedures</span></span>  
  
-   <span data-ttu-id="81363-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="81363-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="81363-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="81363-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="81363-112">Vues</span><span class="sxs-lookup"><span data-stu-id="81363-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="81363-113">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="81363-113">Tables and Views</span></span>  
  
|<span data-ttu-id="81363-114">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-114">ColumnName</span></span>|<span data-ttu-id="81363-115">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="81363-116">TABLE_CAT</span></span>|<span data-ttu-id="81363-117">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-117">String</span></span>|  
|<span data-ttu-id="81363-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="81363-118">TABLE_SCHEM</span></span>|<span data-ttu-id="81363-119">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-119">String</span></span>|  
|<span data-ttu-id="81363-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-120">TABLE_NAME</span></span>|<span data-ttu-id="81363-121">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-121">String</span></span>|  
|<span data-ttu-id="81363-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-122">TABLE_TYPE</span></span>|<span data-ttu-id="81363-123">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-123">String</span></span>|  
|<span data-ttu-id="81363-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-124">REMARKS</span></span>|<span data-ttu-id="81363-125">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="81363-126">Index</span><span class="sxs-lookup"><span data-stu-id="81363-126">Indexes</span></span>  
  
|<span data-ttu-id="81363-127">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-127">ColumnName</span></span>|<span data-ttu-id="81363-128">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="81363-129">TABLE_CAT</span></span>|<span data-ttu-id="81363-130">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-130">String</span></span>|  
|<span data-ttu-id="81363-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="81363-131">TABLE_SCHEM</span></span>|<span data-ttu-id="81363-132">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-132">String</span></span>|  
|<span data-ttu-id="81363-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-133">TABLE_NAME</span></span>|<span data-ttu-id="81363-134">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-134">String</span></span>|  
|<span data-ttu-id="81363-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="81363-135">NON_UNIQUE</span></span>|<span data-ttu-id="81363-136">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-136">Int16</span></span>|  
|<span data-ttu-id="81363-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="81363-138">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-138">String</span></span>|  
|<span data-ttu-id="81363-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-139">INDEX_NAME</span></span>|<span data-ttu-id="81363-140">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-140">String</span></span>|  
|<span data-ttu-id="81363-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-141">TYPE</span></span>|<span data-ttu-id="81363-142">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-142">Int16</span></span>|  
|<span data-ttu-id="81363-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-144">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-144">Int16</span></span>|  
|<span data-ttu-id="81363-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-145">COLUMN_NAME</span></span>|<span data-ttu-id="81363-146">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-146">String</span></span>|  
|<span data-ttu-id="81363-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="81363-147">ASC_OR_DESC</span></span>|<span data-ttu-id="81363-148">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-148">String</span></span>|  
|<span data-ttu-id="81363-149">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="81363-149">CARDINATLITY</span></span>|<span data-ttu-id="81363-150">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-150">Int32</span></span>|  
|<span data-ttu-id="81363-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="81363-151">PAGES</span></span>|<span data-ttu-id="81363-152">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-152">Int32</span></span>|  
|<span data-ttu-id="81363-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="81363-153">FILTER_CONDITION</span></span>|<span data-ttu-id="81363-154">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-154">String</span></span>|  
|<span data-ttu-id="81363-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="81363-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="81363-156">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-156">String</span></span>|  
|<span data-ttu-id="81363-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="81363-158">Byte</span><span class="sxs-lookup"><span data-stu-id="81363-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="81363-159">Columns</span><span class="sxs-lookup"><span data-stu-id="81363-159">Columns</span></span>  
  
|<span data-ttu-id="81363-160">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-160">ColumnName</span></span>|<span data-ttu-id="81363-161">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="81363-162">TABLE_CAT</span></span>|<span data-ttu-id="81363-163">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-163">String</span></span>|  
|<span data-ttu-id="81363-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="81363-164">TABLE_SCHEM</span></span>|<span data-ttu-id="81363-165">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-165">String</span></span>|  
|<span data-ttu-id="81363-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-166">TABLE_NAME</span></span>|<span data-ttu-id="81363-167">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-167">String</span></span>|  
|<span data-ttu-id="81363-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-168">COLUMN_NAME</span></span>|<span data-ttu-id="81363-169">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-169">String</span></span>|  
|<span data-ttu-id="81363-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-170">DATA_TYPE</span></span>|<span data-ttu-id="81363-171">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-171">Int16</span></span>|  
|<span data-ttu-id="81363-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-172">TYPE_NAME</span></span>|<span data-ttu-id="81363-173">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-173">String</span></span>|  
|<span data-ttu-id="81363-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="81363-174">COLUMN_SIZE</span></span>|<span data-ttu-id="81363-175">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-175">Int32</span></span>|  
|<span data-ttu-id="81363-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="81363-177">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-177">Int32</span></span>|  
|<span data-ttu-id="81363-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="81363-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="81363-179">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-179">Int16</span></span>|  
|<span data-ttu-id="81363-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="81363-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="81363-181">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-181">Int16</span></span>|  
|<span data-ttu-id="81363-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-182">NULLABLE</span></span>|<span data-ttu-id="81363-183">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-183">Int16</span></span>|  
|<span data-ttu-id="81363-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-184">REMARKS</span></span>|<span data-ttu-id="81363-185">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-185">String</span></span>|  
|<span data-ttu-id="81363-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="81363-186">COLUMN_DEF</span></span>|<span data-ttu-id="81363-187">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-187">String</span></span>|  
|<span data-ttu-id="81363-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="81363-189">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-189">Int16</span></span>|  
|<span data-ttu-id="81363-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="81363-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="81363-191">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-191">Int16</span></span>|  
|<span data-ttu-id="81363-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="81363-193">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-193">Int32</span></span>|  
|<span data-ttu-id="81363-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-195">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-195">Int32</span></span>|  
|<span data-ttu-id="81363-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-196">IS_NULLABLE</span></span>|<span data-ttu-id="81363-197">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-197">String</span></span>|  
|<span data-ttu-id="81363-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="81363-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="81363-199">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-199">String</span></span>|  
|<span data-ttu-id="81363-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="81363-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="81363-201">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-201">String</span></span>|  
|<span data-ttu-id="81363-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="81363-203">Byte</span><span class="sxs-lookup"><span data-stu-id="81363-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="81363-204">Procédures</span><span class="sxs-lookup"><span data-stu-id="81363-204">Procedures</span></span>  
  
|<span data-ttu-id="81363-205">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-205">ColumnName</span></span>|<span data-ttu-id="81363-206">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="81363-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="81363-208">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-208">String</span></span>|  
|<span data-ttu-id="81363-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="81363-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="81363-210">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-210">String</span></span>|  
|<span data-ttu-id="81363-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="81363-212">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-212">String</span></span>|  
|<span data-ttu-id="81363-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="81363-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="81363-214">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-214">Int32</span></span>|  
|<span data-ttu-id="81363-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="81363-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="81363-216">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-216">Int32</span></span>|  
|<span data-ttu-id="81363-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="81363-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="81363-218">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-218">Int32</span></span>|  
|<span data-ttu-id="81363-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-219">REMARKS</span></span>|<span data-ttu-id="81363-220">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-220">String</span></span>|  
|<span data-ttu-id="81363-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="81363-222">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="81363-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="81363-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="81363-224">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-224">ColumnName</span></span>|<span data-ttu-id="81363-225">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="81363-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="81363-227">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-227">String</span></span>|  
|<span data-ttu-id="81363-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="81363-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="81363-229">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-229">String</span></span>|  
|<span data-ttu-id="81363-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="81363-231">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-231">String</span></span>|  
|<span data-ttu-id="81363-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-232">COLUMN_NAME</span></span>|<span data-ttu-id="81363-233">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-233">String</span></span>|  
|<span data-ttu-id="81363-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-234">COLUMN_TYPE</span></span>|<span data-ttu-id="81363-235">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-235">Int16</span></span>|  
|<span data-ttu-id="81363-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-236">DATA_TYPE</span></span>|<span data-ttu-id="81363-237">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-237">Int16</span></span>|  
|<span data-ttu-id="81363-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-238">TYPE_NAME</span></span>|<span data-ttu-id="81363-239">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-239">String</span></span>|  
|<span data-ttu-id="81363-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="81363-240">COLUMN_SIZE</span></span>|<span data-ttu-id="81363-241">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-241">Int32</span></span>|  
|<span data-ttu-id="81363-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="81363-243">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-243">Int32</span></span>|  
|<span data-ttu-id="81363-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="81363-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="81363-245">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-245">Int16</span></span>|  
|<span data-ttu-id="81363-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="81363-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="81363-247">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-247">Int16</span></span>|  
|<span data-ttu-id="81363-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-248">NULLABLE</span></span>|<span data-ttu-id="81363-249">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-249">Int16</span></span>|  
|<span data-ttu-id="81363-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-250">REMARKS</span></span>|<span data-ttu-id="81363-251">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-251">String</span></span>|  
|<span data-ttu-id="81363-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="81363-252">COLUMN_DEF</span></span>|<span data-ttu-id="81363-253">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-253">String</span></span>|  
|<span data-ttu-id="81363-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="81363-255">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-255">Int16</span></span>|  
|<span data-ttu-id="81363-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="81363-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="81363-257">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-257">Int16</span></span>|  
|<span data-ttu-id="81363-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="81363-259">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-259">Int32</span></span>|  
|<span data-ttu-id="81363-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-261">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-261">Int32</span></span>|  
|<span data-ttu-id="81363-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-262">IS_NULLABLE</span></span>|<span data-ttu-id="81363-263">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-263">String</span></span>|  
|<span data-ttu-id="81363-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="81363-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="81363-265">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-265">String</span></span>|  
|<span data-ttu-id="81363-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="81363-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="81363-267">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-267">String</span></span>|  
|<span data-ttu-id="81363-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="81363-269">Byte</span><span class="sxs-lookup"><span data-stu-id="81363-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="81363-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="81363-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="81363-271">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-271">ColumnName</span></span>|<span data-ttu-id="81363-272">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="81363-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="81363-274">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-274">String</span></span>|  
|<span data-ttu-id="81363-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="81363-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="81363-276">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-276">String</span></span>|  
|<span data-ttu-id="81363-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="81363-278">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-278">String</span></span>|  
|<span data-ttu-id="81363-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-279">COLUMN_NAME</span></span>|<span data-ttu-id="81363-280">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-280">String</span></span>|  
|<span data-ttu-id="81363-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-281">COLUMN_TYPE</span></span>|<span data-ttu-id="81363-282">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-282">Int16</span></span>|  
|<span data-ttu-id="81363-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-283">DATA_TYPE</span></span>|<span data-ttu-id="81363-284">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-284">Int16</span></span>|  
|<span data-ttu-id="81363-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-285">TYPE_NAME</span></span>|<span data-ttu-id="81363-286">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-286">String</span></span>|  
|<span data-ttu-id="81363-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="81363-287">COLUMN_SIZE</span></span>|<span data-ttu-id="81363-288">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-288">Int32</span></span>|  
|<span data-ttu-id="81363-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="81363-290">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-290">Int32</span></span>|  
|<span data-ttu-id="81363-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="81363-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="81363-292">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-292">Int16</span></span>|  
|<span data-ttu-id="81363-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="81363-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="81363-294">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-294">Int16</span></span>|  
|<span data-ttu-id="81363-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-295">NULLABLE</span></span>|<span data-ttu-id="81363-296">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-296">Int16</span></span>|  
|<span data-ttu-id="81363-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-297">REMARKS</span></span>|<span data-ttu-id="81363-298">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-298">String</span></span>|  
|<span data-ttu-id="81363-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="81363-299">COLUMN_DEF</span></span>|<span data-ttu-id="81363-300">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-300">String</span></span>|  
|<span data-ttu-id="81363-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="81363-302">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-302">Int16</span></span>|  
|<span data-ttu-id="81363-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="81363-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="81363-304">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-304">Int16</span></span>|  
|<span data-ttu-id="81363-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="81363-306">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-306">Int32</span></span>|  
|<span data-ttu-id="81363-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-308">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-308">Int32</span></span>|  
|<span data-ttu-id="81363-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-309">IS_NULLABLE</span></span>|<span data-ttu-id="81363-310">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-310">String</span></span>|  
|<span data-ttu-id="81363-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="81363-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="81363-312">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-312">String</span></span>|  
|<span data-ttu-id="81363-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="81363-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="81363-314">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-314">String</span></span>|  
|<span data-ttu-id="81363-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="81363-316">Byte</span><span class="sxs-lookup"><span data-stu-id="81363-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="81363-317">Pilote Microsoft Oracle ODBC</span><span class="sxs-lookup"><span data-stu-id="81363-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="81363-318">Le pilote Microsoft SQL Server Oracle ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="81363-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="81363-319">Tables</span><span class="sxs-lookup"><span data-stu-id="81363-319">Tables</span></span>  
  
-   <span data-ttu-id="81363-320">Columns</span><span class="sxs-lookup"><span data-stu-id="81363-320">Columns</span></span>  
  
-   <span data-ttu-id="81363-321">Procédures</span><span class="sxs-lookup"><span data-stu-id="81363-321">Procedures</span></span>  
  
-   <span data-ttu-id="81363-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="81363-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="81363-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="81363-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="81363-324">Vues</span><span class="sxs-lookup"><span data-stu-id="81363-324">Views</span></span>  
  
-   <span data-ttu-id="81363-325">Index</span><span class="sxs-lookup"><span data-stu-id="81363-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="81363-326">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="81363-326">Tables and Views</span></span>  
  
|<span data-ttu-id="81363-327">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-327">ColumnName</span></span>|<span data-ttu-id="81363-328">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="81363-330">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-330">String</span></span>|  
|<span data-ttu-id="81363-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="81363-331">TABLE_OWNER</span></span>|<span data-ttu-id="81363-332">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-332">String</span></span>|  
|<span data-ttu-id="81363-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-333">TABLE_NAME</span></span>|<span data-ttu-id="81363-334">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-334">String</span></span>|  
|<span data-ttu-id="81363-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-335">TABLE_TYPE</span></span>|<span data-ttu-id="81363-336">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-336">String</span></span>|  
|<span data-ttu-id="81363-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-337">REMARKS</span></span>|<span data-ttu-id="81363-338">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="81363-339">Columns</span><span class="sxs-lookup"><span data-stu-id="81363-339">Columns</span></span>  
  
|<span data-ttu-id="81363-340">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-340">ColumnName</span></span>|<span data-ttu-id="81363-341">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="81363-343">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-343">String</span></span>|  
|<span data-ttu-id="81363-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="81363-344">TABLE_OWNER</span></span>|<span data-ttu-id="81363-345">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-345">String</span></span>|  
|<span data-ttu-id="81363-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-346">TABLE_NAME</span></span>|<span data-ttu-id="81363-347">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-347">String</span></span>|  
|<span data-ttu-id="81363-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-348">COLUMN_NAME</span></span>|<span data-ttu-id="81363-349">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-349">String</span></span>|  
|<span data-ttu-id="81363-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-350">DATA_TYPE</span></span>|<span data-ttu-id="81363-351">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-351">Int16</span></span>|  
|<span data-ttu-id="81363-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-352">TYPE_NAME</span></span>|<span data-ttu-id="81363-353">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-353">String</span></span>|  
|<span data-ttu-id="81363-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="81363-354">PRECISION</span></span>|<span data-ttu-id="81363-355">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-355">Int32</span></span>|  
|<span data-ttu-id="81363-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-356">LENGTH</span></span>|<span data-ttu-id="81363-357">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-357">Int32</span></span>|  
|<span data-ttu-id="81363-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="81363-358">SCALE</span></span>|<span data-ttu-id="81363-359">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-359">Int16</span></span>|  
|<span data-ttu-id="81363-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="81363-360">RADIX</span></span>|<span data-ttu-id="81363-361">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-361">Int16</span></span>|  
|<span data-ttu-id="81363-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-362">NULLABLE</span></span>|<span data-ttu-id="81363-363">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-363">Int16</span></span>|  
|<span data-ttu-id="81363-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-364">REMARKS</span></span>|<span data-ttu-id="81363-365">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-365">String</span></span>|  
|<span data-ttu-id="81363-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-367">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="81363-368">Procédures</span><span class="sxs-lookup"><span data-stu-id="81363-368">Procedures</span></span>  
  
|<span data-ttu-id="81363-369">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-369">ColumnName</span></span>|<span data-ttu-id="81363-370">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="81363-372">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-372">String</span></span>|  
|<span data-ttu-id="81363-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="81363-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="81363-374">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-374">String</span></span>|  
|<span data-ttu-id="81363-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="81363-376">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-376">String</span></span>|  
|<span data-ttu-id="81363-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="81363-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="81363-378">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-378">Int16</span></span>|  
|<span data-ttu-id="81363-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="81363-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="81363-380">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-380">Int16</span></span>|  
|<span data-ttu-id="81363-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="81363-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="81363-382">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-382">Int16</span></span>|  
|<span data-ttu-id="81363-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-383">REMARKS</span></span>|<span data-ttu-id="81363-384">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-384">String</span></span>|  
|<span data-ttu-id="81363-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="81363-386">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="81363-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="81363-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="81363-388">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-388">ColumnName</span></span>|<span data-ttu-id="81363-389">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="81363-391">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-391">String</span></span>|  
|<span data-ttu-id="81363-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="81363-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="81363-393">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-393">String</span></span>|  
|<span data-ttu-id="81363-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="81363-395">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-395">String</span></span>|  
|<span data-ttu-id="81363-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-396">COLUMN_NAME</span></span>|<span data-ttu-id="81363-397">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-397">String</span></span>|  
|<span data-ttu-id="81363-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-398">COLUMN_TYPE</span></span>|<span data-ttu-id="81363-399">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-399">Int16</span></span>|  
|<span data-ttu-id="81363-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-400">DATA_TYPE</span></span>|<span data-ttu-id="81363-401">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-401">Int16</span></span>|  
|<span data-ttu-id="81363-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-402">TYPE_NAME</span></span>|<span data-ttu-id="81363-403">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-403">String</span></span>|  
|<span data-ttu-id="81363-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="81363-404">PRECISION</span></span>|<span data-ttu-id="81363-405">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-405">Int32</span></span>|  
|<span data-ttu-id="81363-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-406">LENGTH</span></span>|<span data-ttu-id="81363-407">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-407">Int32</span></span>|  
|<span data-ttu-id="81363-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="81363-408">SCALE</span></span>|<span data-ttu-id="81363-409">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-409">Int16</span></span>|  
|<span data-ttu-id="81363-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="81363-410">RADIX</span></span>|<span data-ttu-id="81363-411">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-411">Int16</span></span>|  
|<span data-ttu-id="81363-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-412">NULLABLE</span></span>|<span data-ttu-id="81363-413">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-413">Int16</span></span>|  
|<span data-ttu-id="81363-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-414">REMARKS</span></span>|<span data-ttu-id="81363-415">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-415">String</span></span>|  
|<span data-ttu-id="81363-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="81363-416">OVERLOAD</span></span>|<span data-ttu-id="81363-417">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-417">Int32</span></span>|  
|<span data-ttu-id="81363-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-419">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="81363-420">Pilote Microsoft Jet ODBC</span><span class="sxs-lookup"><span data-stu-id="81363-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="81363-421">Le pilote Microsoft Jet ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="81363-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="81363-422">Tables</span><span class="sxs-lookup"><span data-stu-id="81363-422">Tables</span></span>  
  
-   <span data-ttu-id="81363-423">Index</span><span class="sxs-lookup"><span data-stu-id="81363-423">Indexes</span></span>  
  
-   <span data-ttu-id="81363-424">Columns</span><span class="sxs-lookup"><span data-stu-id="81363-424">Columns</span></span>  
  
-   <span data-ttu-id="81363-425">Procédures</span><span class="sxs-lookup"><span data-stu-id="81363-425">Procedures</span></span>  
  
-   <span data-ttu-id="81363-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="81363-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="81363-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="81363-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="81363-428">Vues</span><span class="sxs-lookup"><span data-stu-id="81363-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="81363-429">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="81363-429">Tables and Views</span></span>  
  
|<span data-ttu-id="81363-430">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-430">ColumnName</span></span>|<span data-ttu-id="81363-431">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="81363-433">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-433">String</span></span>|  
|<span data-ttu-id="81363-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="81363-434">TABLE_OWNER</span></span>|<span data-ttu-id="81363-435">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-435">String</span></span>|  
|<span data-ttu-id="81363-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-436">TABLE_NAME</span></span>|<span data-ttu-id="81363-437">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-437">String</span></span>|  
|<span data-ttu-id="81363-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-438">TABLE_TYPE</span></span>|<span data-ttu-id="81363-439">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-439">String</span></span>|  
|<span data-ttu-id="81363-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-440">REMARKS</span></span>|<span data-ttu-id="81363-441">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="81363-442">Columns</span><span class="sxs-lookup"><span data-stu-id="81363-442">Columns</span></span>  
  
|<span data-ttu-id="81363-443">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-443">ColumnName</span></span>|<span data-ttu-id="81363-444">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="81363-446">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-446">String</span></span>|  
|<span data-ttu-id="81363-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="81363-447">TABLE_OWNER</span></span>|<span data-ttu-id="81363-448">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-448">String</span></span>|  
|<span data-ttu-id="81363-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-449">TABLE_NAME</span></span>|<span data-ttu-id="81363-450">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-450">String</span></span>|  
|<span data-ttu-id="81363-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-451">COLUMN_NAME</span></span>|<span data-ttu-id="81363-452">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-452">String</span></span>|  
|<span data-ttu-id="81363-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-453">DATA_TYPE</span></span>|<span data-ttu-id="81363-454">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-454">Int16</span></span>|  
|<span data-ttu-id="81363-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-455">TYPE_NAME</span></span>|<span data-ttu-id="81363-456">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-456">String</span></span>|  
|<span data-ttu-id="81363-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="81363-457">PRECISION</span></span>|<span data-ttu-id="81363-458">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-458">Int32</span></span>|  
|<span data-ttu-id="81363-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-459">LENGTH</span></span>|<span data-ttu-id="81363-460">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-460">Int32</span></span>|  
|<span data-ttu-id="81363-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="81363-461">SCALE</span></span>|<span data-ttu-id="81363-462">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-462">Int16</span></span>|  
|<span data-ttu-id="81363-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="81363-463">RADIX</span></span>|<span data-ttu-id="81363-464">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-464">Int16</span></span>|  
|<span data-ttu-id="81363-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-465">NULLABLE</span></span>|<span data-ttu-id="81363-466">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-466">Int16</span></span>|  
|<span data-ttu-id="81363-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-467">REMARKS</span></span>|<span data-ttu-id="81363-468">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-468">String</span></span>|  
|<span data-ttu-id="81363-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-470">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="81363-471">Procédures</span><span class="sxs-lookup"><span data-stu-id="81363-471">Procedures</span></span>  
  
|<span data-ttu-id="81363-472">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-472">ColumnName</span></span>|<span data-ttu-id="81363-473">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="81363-475">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-475">String</span></span>|  
|<span data-ttu-id="81363-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="81363-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="81363-477">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-477">String</span></span>|  
|<span data-ttu-id="81363-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="81363-479">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-479">String</span></span>|  
|<span data-ttu-id="81363-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="81363-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="81363-481">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-481">Int16</span></span>|  
|<span data-ttu-id="81363-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="81363-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="81363-483">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-483">Int16</span></span>|  
|<span data-ttu-id="81363-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="81363-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="81363-485">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-485">Int16</span></span>|  
|<span data-ttu-id="81363-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-486">REMARKS</span></span>|<span data-ttu-id="81363-487">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-487">String</span></span>|  
|<span data-ttu-id="81363-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="81363-489">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="81363-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="81363-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="81363-491">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-491">ColumnName</span></span>|<span data-ttu-id="81363-492">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="81363-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="81363-494">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-494">String</span></span>|  
|<span data-ttu-id="81363-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="81363-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="81363-496">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-496">String</span></span>|  
|<span data-ttu-id="81363-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="81363-498">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-498">String</span></span>|  
|<span data-ttu-id="81363-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-499">COLUMN_NAME</span></span>|<span data-ttu-id="81363-500">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-500">String</span></span>|  
|<span data-ttu-id="81363-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-501">COLUMN_TYPE</span></span>|<span data-ttu-id="81363-502">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-502">Int16</span></span>|  
|<span data-ttu-id="81363-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-503">DATA_TYPE</span></span>|<span data-ttu-id="81363-504">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-504">Int16</span></span>|  
|<span data-ttu-id="81363-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-505">TYPE_NAME</span></span>|<span data-ttu-id="81363-506">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-506">String</span></span>|  
|<span data-ttu-id="81363-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="81363-507">PRECISION</span></span>|<span data-ttu-id="81363-508">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-508">Int32</span></span>|  
|<span data-ttu-id="81363-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-509">LENGTH</span></span>|<span data-ttu-id="81363-510">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-510">Int32</span></span>|  
|<span data-ttu-id="81363-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="81363-511">SCALE</span></span>|<span data-ttu-id="81363-512">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-512">Int16</span></span>|  
|<span data-ttu-id="81363-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="81363-513">RADIX</span></span>|<span data-ttu-id="81363-514">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-514">Int16</span></span>|  
|<span data-ttu-id="81363-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-515">NULLABLE</span></span>|<span data-ttu-id="81363-516">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-516">Int16</span></span>|  
|<span data-ttu-id="81363-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-517">REMARKS</span></span>|<span data-ttu-id="81363-518">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-518">String</span></span>|  
|<span data-ttu-id="81363-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="81363-519">OVERLOAD</span></span>|<span data-ttu-id="81363-520">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-520">Int32</span></span>|  
|<span data-ttu-id="81363-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-522">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="81363-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="81363-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="81363-524">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="81363-524">ColumnName</span></span>|<span data-ttu-id="81363-525">Type de données</span><span class="sxs-lookup"><span data-stu-id="81363-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="81363-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="81363-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="81363-527">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-527">String</span></span>|  
|<span data-ttu-id="81363-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="81363-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="81363-529">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-529">String</span></span>|  
|<span data-ttu-id="81363-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="81363-531">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-531">String</span></span>|  
|<span data-ttu-id="81363-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-532">COLUMN_NAME</span></span>|<span data-ttu-id="81363-533">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-533">String</span></span>|  
|<span data-ttu-id="81363-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-534">COLUMN_TYPE</span></span>|<span data-ttu-id="81363-535">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-535">Int16</span></span>|  
|<span data-ttu-id="81363-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-536">DATA_TYPE</span></span>|<span data-ttu-id="81363-537">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-537">Int16</span></span>|  
|<span data-ttu-id="81363-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="81363-538">TYPE_NAME</span></span>|<span data-ttu-id="81363-539">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-539">String</span></span>|  
|<span data-ttu-id="81363-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="81363-540">COLUMN_SIZE</span></span>|<span data-ttu-id="81363-541">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-541">Int32</span></span>|  
|<span data-ttu-id="81363-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="81363-543">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-543">Int32</span></span>|  
|<span data-ttu-id="81363-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="81363-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="81363-545">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-545">Int16</span></span>|  
|<span data-ttu-id="81363-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="81363-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="81363-547">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-547">Int16</span></span>|  
|<span data-ttu-id="81363-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-548">NULLABLE</span></span>|<span data-ttu-id="81363-549">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-549">Int16</span></span>|  
|<span data-ttu-id="81363-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="81363-550">REMARKS</span></span>|<span data-ttu-id="81363-551">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-551">String</span></span>|  
|<span data-ttu-id="81363-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="81363-552">COLUMN_DEF</span></span>|<span data-ttu-id="81363-553">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-553">String</span></span>|  
|<span data-ttu-id="81363-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="81363-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="81363-555">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-555">Int16</span></span>|  
|<span data-ttu-id="81363-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="81363-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="81363-557">Int16</span><span class="sxs-lookup"><span data-stu-id="81363-557">Int16</span></span>|  
|<span data-ttu-id="81363-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="81363-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="81363-559">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-559">Int32</span></span>|  
|<span data-ttu-id="81363-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="81363-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="81363-561">Int32</span><span class="sxs-lookup"><span data-stu-id="81363-561">Int32</span></span>|  
|<span data-ttu-id="81363-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="81363-562">IS_NULLABLE</span></span>|<span data-ttu-id="81363-563">Chaîne</span><span class="sxs-lookup"><span data-stu-id="81363-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81363-564">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81363-564">See Also</span></span>  
 [<span data-ttu-id="81363-565">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="81363-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
