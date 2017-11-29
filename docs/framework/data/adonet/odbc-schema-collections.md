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
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="0fc9b-102">Collections de schémas ODBC</span><span class="sxs-lookup"><span data-stu-id="0fc9b-102">ODBC Schema Collections</span></span>
<span data-ttu-id="0fc9b-103">Cette section traite de la prise en charge des collections de schémas pour les pilotes ODBC Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="0fc9b-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="0fc9b-104">Pilote Microsoft SQL Server ODBC</span><span class="sxs-lookup"><span data-stu-id="0fc9b-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="0fc9b-105">Le pilote ODBC de Microsoft SQL Server prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0fc9b-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0fc9b-106">Tables</span><span class="sxs-lookup"><span data-stu-id="0fc9b-106">Tables</span></span>  
  
-   <span data-ttu-id="0fc9b-107">Index</span><span class="sxs-lookup"><span data-stu-id="0fc9b-107">Indexes</span></span>  
  
-   <span data-ttu-id="0fc9b-108">Columns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-108">Columns</span></span>  
  
-   <span data-ttu-id="0fc9b-109">Procédures</span><span class="sxs-lookup"><span data-stu-id="0fc9b-109">Procedures</span></span>  
  
-   <span data-ttu-id="0fc9b-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0fc9b-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0fc9b-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0fc9b-112">Vues</span><span class="sxs-lookup"><span data-stu-id="0fc9b-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="0fc9b-113">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="0fc9b-113">Tables and Views</span></span>  
  
|<span data-ttu-id="0fc9b-114">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-114">ColumnName</span></span>|<span data-ttu-id="0fc9b-115">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0fc9b-116">TABLE_CAT</span></span>|<span data-ttu-id="0fc9b-117">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-117">String</span></span>|  
|<span data-ttu-id="0fc9b-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0fc9b-118">TABLE_SCHEM</span></span>|<span data-ttu-id="0fc9b-119">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-119">String</span></span>|  
|<span data-ttu-id="0fc9b-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-120">TABLE_NAME</span></span>|<span data-ttu-id="0fc9b-121">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-121">String</span></span>|  
|<span data-ttu-id="0fc9b-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-122">TABLE_TYPE</span></span>|<span data-ttu-id="0fc9b-123">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-123">String</span></span>|  
|<span data-ttu-id="0fc9b-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-124">REMARKS</span></span>|<span data-ttu-id="0fc9b-125">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0fc9b-126">Index</span><span class="sxs-lookup"><span data-stu-id="0fc9b-126">Indexes</span></span>  
  
|<span data-ttu-id="0fc9b-127">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-127">ColumnName</span></span>|<span data-ttu-id="0fc9b-128">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0fc9b-129">TABLE_CAT</span></span>|<span data-ttu-id="0fc9b-130">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-130">String</span></span>|  
|<span data-ttu-id="0fc9b-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0fc9b-131">TABLE_SCHEM</span></span>|<span data-ttu-id="0fc9b-132">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-132">String</span></span>|  
|<span data-ttu-id="0fc9b-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-133">TABLE_NAME</span></span>|<span data-ttu-id="0fc9b-134">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-134">String</span></span>|  
|<span data-ttu-id="0fc9b-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-135">NON_UNIQUE</span></span>|<span data-ttu-id="0fc9b-136">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-136">Int16</span></span>|  
|<span data-ttu-id="0fc9b-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-138">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-138">String</span></span>|  
|<span data-ttu-id="0fc9b-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-139">INDEX_NAME</span></span>|<span data-ttu-id="0fc9b-140">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-140">String</span></span>|  
|<span data-ttu-id="0fc9b-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-141">TYPE</span></span>|<span data-ttu-id="0fc9b-142">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-142">Int16</span></span>|  
|<span data-ttu-id="0fc9b-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-144">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-144">Int16</span></span>|  
|<span data-ttu-id="0fc9b-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-145">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-146">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-146">String</span></span>|  
|<span data-ttu-id="0fc9b-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="0fc9b-147">ASC_OR_DESC</span></span>|<span data-ttu-id="0fc9b-148">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-148">String</span></span>|  
|<span data-ttu-id="0fc9b-149">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0fc9b-149">CARDINATLITY</span></span>|<span data-ttu-id="0fc9b-150">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-150">Int32</span></span>|  
|<span data-ttu-id="0fc9b-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="0fc9b-151">PAGES</span></span>|<span data-ttu-id="0fc9b-152">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-152">Int32</span></span>|  
|<span data-ttu-id="0fc9b-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-153">FILTER_CONDITION</span></span>|<span data-ttu-id="0fc9b-154">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-154">String</span></span>|  
|<span data-ttu-id="0fc9b-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0fc9b-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0fc9b-156">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-156">String</span></span>|  
|<span data-ttu-id="0fc9b-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-158">Byte</span><span class="sxs-lookup"><span data-stu-id="0fc9b-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0fc9b-159">Columns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-159">Columns</span></span>  
  
|<span data-ttu-id="0fc9b-160">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-160">ColumnName</span></span>|<span data-ttu-id="0fc9b-161">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0fc9b-162">TABLE_CAT</span></span>|<span data-ttu-id="0fc9b-163">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-163">String</span></span>|  
|<span data-ttu-id="0fc9b-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0fc9b-164">TABLE_SCHEM</span></span>|<span data-ttu-id="0fc9b-165">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-165">String</span></span>|  
|<span data-ttu-id="0fc9b-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-166">TABLE_NAME</span></span>|<span data-ttu-id="0fc9b-167">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-167">String</span></span>|  
|<span data-ttu-id="0fc9b-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-168">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-169">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-169">String</span></span>|  
|<span data-ttu-id="0fc9b-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-170">DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-171">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-171">Int16</span></span>|  
|<span data-ttu-id="0fc9b-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-172">TYPE_NAME</span></span>|<span data-ttu-id="0fc9b-173">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-173">String</span></span>|  
|<span data-ttu-id="0fc9b-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-174">COLUMN_SIZE</span></span>|<span data-ttu-id="0fc9b-175">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-175">Int32</span></span>|  
|<span data-ttu-id="0fc9b-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="0fc9b-177">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-177">Int32</span></span>|  
|<span data-ttu-id="0fc9b-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0fc9b-179">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-179">Int16</span></span>|  
|<span data-ttu-id="0fc9b-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0fc9b-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0fc9b-181">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-181">Int16</span></span>|  
|<span data-ttu-id="0fc9b-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-182">NULLABLE</span></span>|<span data-ttu-id="0fc9b-183">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-183">Int16</span></span>|  
|<span data-ttu-id="0fc9b-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-184">REMARKS</span></span>|<span data-ttu-id="0fc9b-185">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-185">String</span></span>|  
|<span data-ttu-id="0fc9b-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0fc9b-186">COLUMN_DEF</span></span>|<span data-ttu-id="0fc9b-187">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-187">String</span></span>|  
|<span data-ttu-id="0fc9b-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-189">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-189">Int16</span></span>|  
|<span data-ttu-id="0fc9b-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0fc9b-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0fc9b-191">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-191">Int16</span></span>|  
|<span data-ttu-id="0fc9b-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0fc9b-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-193">Int32</span></span>|  
|<span data-ttu-id="0fc9b-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-195">Int32</span></span>|  
|<span data-ttu-id="0fc9b-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-196">IS_NULLABLE</span></span>|<span data-ttu-id="0fc9b-197">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-197">String</span></span>|  
|<span data-ttu-id="0fc9b-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0fc9b-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0fc9b-199">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-199">String</span></span>|  
|<span data-ttu-id="0fc9b-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0fc9b-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0fc9b-201">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-201">String</span></span>|  
|<span data-ttu-id="0fc9b-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-203">Byte</span><span class="sxs-lookup"><span data-stu-id="0fc9b-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0fc9b-204">Procédures</span><span class="sxs-lookup"><span data-stu-id="0fc9b-204">Procedures</span></span>  
  
|<span data-ttu-id="0fc9b-205">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-205">ColumnName</span></span>|<span data-ttu-id="0fc9b-206">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0fc9b-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="0fc9b-208">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-208">String</span></span>|  
|<span data-ttu-id="0fc9b-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0fc9b-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0fc9b-210">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-210">String</span></span>|  
|<span data-ttu-id="0fc9b-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="0fc9b-212">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-212">String</span></span>|  
|<span data-ttu-id="0fc9b-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0fc9b-214">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-214">Int32</span></span>|  
|<span data-ttu-id="0fc9b-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0fc9b-216">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-216">Int32</span></span>|  
|<span data-ttu-id="0fc9b-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0fc9b-218">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-218">Int32</span></span>|  
|<span data-ttu-id="0fc9b-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-219">REMARKS</span></span>|<span data-ttu-id="0fc9b-220">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-220">String</span></span>|  
|<span data-ttu-id="0fc9b-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0fc9b-222">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0fc9b-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0fc9b-224">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-224">ColumnName</span></span>|<span data-ttu-id="0fc9b-225">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0fc9b-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="0fc9b-227">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-227">String</span></span>|  
|<span data-ttu-id="0fc9b-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0fc9b-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0fc9b-229">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-229">String</span></span>|  
|<span data-ttu-id="0fc9b-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="0fc9b-231">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-231">String</span></span>|  
|<span data-ttu-id="0fc9b-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-232">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-233">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-233">String</span></span>|  
|<span data-ttu-id="0fc9b-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-234">COLUMN_TYPE</span></span>|<span data-ttu-id="0fc9b-235">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-235">Int16</span></span>|  
|<span data-ttu-id="0fc9b-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-236">DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-237">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-237">Int16</span></span>|  
|<span data-ttu-id="0fc9b-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-238">TYPE_NAME</span></span>|<span data-ttu-id="0fc9b-239">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-239">String</span></span>|  
|<span data-ttu-id="0fc9b-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-240">COLUMN_SIZE</span></span>|<span data-ttu-id="0fc9b-241">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-241">Int32</span></span>|  
|<span data-ttu-id="0fc9b-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="0fc9b-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-243">Int32</span></span>|  
|<span data-ttu-id="0fc9b-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0fc9b-245">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-245">Int16</span></span>|  
|<span data-ttu-id="0fc9b-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0fc9b-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0fc9b-247">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-247">Int16</span></span>|  
|<span data-ttu-id="0fc9b-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-248">NULLABLE</span></span>|<span data-ttu-id="0fc9b-249">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-249">Int16</span></span>|  
|<span data-ttu-id="0fc9b-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-250">REMARKS</span></span>|<span data-ttu-id="0fc9b-251">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-251">String</span></span>|  
|<span data-ttu-id="0fc9b-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0fc9b-252">COLUMN_DEF</span></span>|<span data-ttu-id="0fc9b-253">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-253">String</span></span>|  
|<span data-ttu-id="0fc9b-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-255">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-255">Int16</span></span>|  
|<span data-ttu-id="0fc9b-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0fc9b-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0fc9b-257">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-257">Int16</span></span>|  
|<span data-ttu-id="0fc9b-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0fc9b-259">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-259">Int32</span></span>|  
|<span data-ttu-id="0fc9b-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-261">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-261">Int32</span></span>|  
|<span data-ttu-id="0fc9b-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-262">IS_NULLABLE</span></span>|<span data-ttu-id="0fc9b-263">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-263">String</span></span>|  
|<span data-ttu-id="0fc9b-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0fc9b-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0fc9b-265">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-265">String</span></span>|  
|<span data-ttu-id="0fc9b-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0fc9b-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0fc9b-267">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-267">String</span></span>|  
|<span data-ttu-id="0fc9b-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-269">Byte</span><span class="sxs-lookup"><span data-stu-id="0fc9b-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0fc9b-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0fc9b-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0fc9b-271">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-271">ColumnName</span></span>|<span data-ttu-id="0fc9b-272">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0fc9b-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="0fc9b-274">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-274">String</span></span>|  
|<span data-ttu-id="0fc9b-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0fc9b-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0fc9b-276">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-276">String</span></span>|  
|<span data-ttu-id="0fc9b-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="0fc9b-278">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-278">String</span></span>|  
|<span data-ttu-id="0fc9b-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-279">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-280">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-280">String</span></span>|  
|<span data-ttu-id="0fc9b-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-281">COLUMN_TYPE</span></span>|<span data-ttu-id="0fc9b-282">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-282">Int16</span></span>|  
|<span data-ttu-id="0fc9b-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-283">DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-284">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-284">Int16</span></span>|  
|<span data-ttu-id="0fc9b-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-285">TYPE_NAME</span></span>|<span data-ttu-id="0fc9b-286">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-286">String</span></span>|  
|<span data-ttu-id="0fc9b-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-287">COLUMN_SIZE</span></span>|<span data-ttu-id="0fc9b-288">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-288">Int32</span></span>|  
|<span data-ttu-id="0fc9b-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="0fc9b-290">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-290">Int32</span></span>|  
|<span data-ttu-id="0fc9b-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0fc9b-292">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-292">Int16</span></span>|  
|<span data-ttu-id="0fc9b-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0fc9b-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0fc9b-294">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-294">Int16</span></span>|  
|<span data-ttu-id="0fc9b-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-295">NULLABLE</span></span>|<span data-ttu-id="0fc9b-296">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-296">Int16</span></span>|  
|<span data-ttu-id="0fc9b-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-297">REMARKS</span></span>|<span data-ttu-id="0fc9b-298">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-298">String</span></span>|  
|<span data-ttu-id="0fc9b-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0fc9b-299">COLUMN_DEF</span></span>|<span data-ttu-id="0fc9b-300">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-300">String</span></span>|  
|<span data-ttu-id="0fc9b-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-302">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-302">Int16</span></span>|  
|<span data-ttu-id="0fc9b-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0fc9b-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0fc9b-304">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-304">Int16</span></span>|  
|<span data-ttu-id="0fc9b-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0fc9b-306">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-306">Int32</span></span>|  
|<span data-ttu-id="0fc9b-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-308">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-308">Int32</span></span>|  
|<span data-ttu-id="0fc9b-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-309">IS_NULLABLE</span></span>|<span data-ttu-id="0fc9b-310">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-310">String</span></span>|  
|<span data-ttu-id="0fc9b-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0fc9b-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0fc9b-312">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-312">String</span></span>|  
|<span data-ttu-id="0fc9b-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0fc9b-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0fc9b-314">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-314">String</span></span>|  
|<span data-ttu-id="0fc9b-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-316">Byte</span><span class="sxs-lookup"><span data-stu-id="0fc9b-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="0fc9b-317">Pilote Microsoft Oracle ODBC</span><span class="sxs-lookup"><span data-stu-id="0fc9b-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="0fc9b-318">Le pilote Microsoft SQL Server Oracle ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0fc9b-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0fc9b-319">Tables</span><span class="sxs-lookup"><span data-stu-id="0fc9b-319">Tables</span></span>  
  
-   <span data-ttu-id="0fc9b-320">Columns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-320">Columns</span></span>  
  
-   <span data-ttu-id="0fc9b-321">Procédures</span><span class="sxs-lookup"><span data-stu-id="0fc9b-321">Procedures</span></span>  
  
-   <span data-ttu-id="0fc9b-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0fc9b-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0fc9b-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0fc9b-324">Vues</span><span class="sxs-lookup"><span data-stu-id="0fc9b-324">Views</span></span>  
  
-   <span data-ttu-id="0fc9b-325">Index</span><span class="sxs-lookup"><span data-stu-id="0fc9b-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="0fc9b-326">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="0fc9b-326">Tables and Views</span></span>  
  
|<span data-ttu-id="0fc9b-327">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-327">ColumnName</span></span>|<span data-ttu-id="0fc9b-328">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-330">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-330">String</span></span>|  
|<span data-ttu-id="0fc9b-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-331">TABLE_OWNER</span></span>|<span data-ttu-id="0fc9b-332">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-332">String</span></span>|  
|<span data-ttu-id="0fc9b-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-333">TABLE_NAME</span></span>|<span data-ttu-id="0fc9b-334">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-334">String</span></span>|  
|<span data-ttu-id="0fc9b-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-335">TABLE_TYPE</span></span>|<span data-ttu-id="0fc9b-336">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-336">String</span></span>|  
|<span data-ttu-id="0fc9b-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-337">REMARKS</span></span>|<span data-ttu-id="0fc9b-338">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0fc9b-339">Columns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-339">Columns</span></span>  
  
|<span data-ttu-id="0fc9b-340">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-340">ColumnName</span></span>|<span data-ttu-id="0fc9b-341">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-343">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-343">String</span></span>|  
|<span data-ttu-id="0fc9b-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-344">TABLE_OWNER</span></span>|<span data-ttu-id="0fc9b-345">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-345">String</span></span>|  
|<span data-ttu-id="0fc9b-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-346">TABLE_NAME</span></span>|<span data-ttu-id="0fc9b-347">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-347">String</span></span>|  
|<span data-ttu-id="0fc9b-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-348">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-349">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-349">String</span></span>|  
|<span data-ttu-id="0fc9b-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-350">DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-351">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-351">Int16</span></span>|  
|<span data-ttu-id="0fc9b-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-352">TYPE_NAME</span></span>|<span data-ttu-id="0fc9b-353">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-353">String</span></span>|  
|<span data-ttu-id="0fc9b-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-354">PRECISION</span></span>|<span data-ttu-id="0fc9b-355">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-355">Int32</span></span>|  
|<span data-ttu-id="0fc9b-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-356">LENGTH</span></span>|<span data-ttu-id="0fc9b-357">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-357">Int32</span></span>|  
|<span data-ttu-id="0fc9b-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-358">SCALE</span></span>|<span data-ttu-id="0fc9b-359">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-359">Int16</span></span>|  
|<span data-ttu-id="0fc9b-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="0fc9b-360">RADIX</span></span>|<span data-ttu-id="0fc9b-361">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-361">Int16</span></span>|  
|<span data-ttu-id="0fc9b-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-362">NULLABLE</span></span>|<span data-ttu-id="0fc9b-363">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-363">Int16</span></span>|  
|<span data-ttu-id="0fc9b-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-364">REMARKS</span></span>|<span data-ttu-id="0fc9b-365">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-365">String</span></span>|  
|<span data-ttu-id="0fc9b-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-367">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0fc9b-368">Procédures</span><span class="sxs-lookup"><span data-stu-id="0fc9b-368">Procedures</span></span>  
  
|<span data-ttu-id="0fc9b-369">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-369">ColumnName</span></span>|<span data-ttu-id="0fc9b-370">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-372">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-372">String</span></span>|  
|<span data-ttu-id="0fc9b-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0fc9b-374">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-374">String</span></span>|  
|<span data-ttu-id="0fc9b-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="0fc9b-376">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-376">String</span></span>|  
|<span data-ttu-id="0fc9b-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0fc9b-378">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-378">Int16</span></span>|  
|<span data-ttu-id="0fc9b-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0fc9b-380">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-380">Int16</span></span>|  
|<span data-ttu-id="0fc9b-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0fc9b-382">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-382">Int16</span></span>|  
|<span data-ttu-id="0fc9b-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-383">REMARKS</span></span>|<span data-ttu-id="0fc9b-384">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-384">String</span></span>|  
|<span data-ttu-id="0fc9b-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0fc9b-386">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0fc9b-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0fc9b-388">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-388">ColumnName</span></span>|<span data-ttu-id="0fc9b-389">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-391">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-391">String</span></span>|  
|<span data-ttu-id="0fc9b-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0fc9b-393">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-393">String</span></span>|  
|<span data-ttu-id="0fc9b-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="0fc9b-395">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-395">String</span></span>|  
|<span data-ttu-id="0fc9b-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-396">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-397">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-397">String</span></span>|  
|<span data-ttu-id="0fc9b-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-398">COLUMN_TYPE</span></span>|<span data-ttu-id="0fc9b-399">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-399">Int16</span></span>|  
|<span data-ttu-id="0fc9b-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-400">DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-401">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-401">Int16</span></span>|  
|<span data-ttu-id="0fc9b-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-402">TYPE_NAME</span></span>|<span data-ttu-id="0fc9b-403">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-403">String</span></span>|  
|<span data-ttu-id="0fc9b-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-404">PRECISION</span></span>|<span data-ttu-id="0fc9b-405">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-405">Int32</span></span>|  
|<span data-ttu-id="0fc9b-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-406">LENGTH</span></span>|<span data-ttu-id="0fc9b-407">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-407">Int32</span></span>|  
|<span data-ttu-id="0fc9b-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-408">SCALE</span></span>|<span data-ttu-id="0fc9b-409">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-409">Int16</span></span>|  
|<span data-ttu-id="0fc9b-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="0fc9b-410">RADIX</span></span>|<span data-ttu-id="0fc9b-411">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-411">Int16</span></span>|  
|<span data-ttu-id="0fc9b-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-412">NULLABLE</span></span>|<span data-ttu-id="0fc9b-413">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-413">Int16</span></span>|  
|<span data-ttu-id="0fc9b-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-414">REMARKS</span></span>|<span data-ttu-id="0fc9b-415">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-415">String</span></span>|  
|<span data-ttu-id="0fc9b-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="0fc9b-416">OVERLOAD</span></span>|<span data-ttu-id="0fc9b-417">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-417">Int32</span></span>|  
|<span data-ttu-id="0fc9b-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-419">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="0fc9b-420">Pilote Microsoft Jet ODBC</span><span class="sxs-lookup"><span data-stu-id="0fc9b-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="0fc9b-421">Le pilote Microsoft Jet ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0fc9b-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0fc9b-422">Tables</span><span class="sxs-lookup"><span data-stu-id="0fc9b-422">Tables</span></span>  
  
-   <span data-ttu-id="0fc9b-423">Index</span><span class="sxs-lookup"><span data-stu-id="0fc9b-423">Indexes</span></span>  
  
-   <span data-ttu-id="0fc9b-424">Columns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-424">Columns</span></span>  
  
-   <span data-ttu-id="0fc9b-425">Procédures</span><span class="sxs-lookup"><span data-stu-id="0fc9b-425">Procedures</span></span>  
  
-   <span data-ttu-id="0fc9b-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0fc9b-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0fc9b-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0fc9b-428">Vues</span><span class="sxs-lookup"><span data-stu-id="0fc9b-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="0fc9b-429">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="0fc9b-429">Tables and Views</span></span>  
  
|<span data-ttu-id="0fc9b-430">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-430">ColumnName</span></span>|<span data-ttu-id="0fc9b-431">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-433">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-433">String</span></span>|  
|<span data-ttu-id="0fc9b-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-434">TABLE_OWNER</span></span>|<span data-ttu-id="0fc9b-435">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-435">String</span></span>|  
|<span data-ttu-id="0fc9b-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-436">TABLE_NAME</span></span>|<span data-ttu-id="0fc9b-437">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-437">String</span></span>|  
|<span data-ttu-id="0fc9b-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-438">TABLE_TYPE</span></span>|<span data-ttu-id="0fc9b-439">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-439">String</span></span>|  
|<span data-ttu-id="0fc9b-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-440">REMARKS</span></span>|<span data-ttu-id="0fc9b-441">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0fc9b-442">Columns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-442">Columns</span></span>  
  
|<span data-ttu-id="0fc9b-443">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-443">ColumnName</span></span>|<span data-ttu-id="0fc9b-444">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-446">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-446">String</span></span>|  
|<span data-ttu-id="0fc9b-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-447">TABLE_OWNER</span></span>|<span data-ttu-id="0fc9b-448">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-448">String</span></span>|  
|<span data-ttu-id="0fc9b-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-449">TABLE_NAME</span></span>|<span data-ttu-id="0fc9b-450">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-450">String</span></span>|  
|<span data-ttu-id="0fc9b-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-451">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-452">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-452">String</span></span>|  
|<span data-ttu-id="0fc9b-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-453">DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-454">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-454">Int16</span></span>|  
|<span data-ttu-id="0fc9b-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-455">TYPE_NAME</span></span>|<span data-ttu-id="0fc9b-456">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-456">String</span></span>|  
|<span data-ttu-id="0fc9b-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-457">PRECISION</span></span>|<span data-ttu-id="0fc9b-458">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-458">Int32</span></span>|  
|<span data-ttu-id="0fc9b-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-459">LENGTH</span></span>|<span data-ttu-id="0fc9b-460">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-460">Int32</span></span>|  
|<span data-ttu-id="0fc9b-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-461">SCALE</span></span>|<span data-ttu-id="0fc9b-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-462">Int16</span></span>|  
|<span data-ttu-id="0fc9b-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="0fc9b-463">RADIX</span></span>|<span data-ttu-id="0fc9b-464">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-464">Int16</span></span>|  
|<span data-ttu-id="0fc9b-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-465">NULLABLE</span></span>|<span data-ttu-id="0fc9b-466">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-466">Int16</span></span>|  
|<span data-ttu-id="0fc9b-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-467">REMARKS</span></span>|<span data-ttu-id="0fc9b-468">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-468">String</span></span>|  
|<span data-ttu-id="0fc9b-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-470">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0fc9b-471">Procédures</span><span class="sxs-lookup"><span data-stu-id="0fc9b-471">Procedures</span></span>  
  
|<span data-ttu-id="0fc9b-472">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-472">ColumnName</span></span>|<span data-ttu-id="0fc9b-473">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-475">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-475">String</span></span>|  
|<span data-ttu-id="0fc9b-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0fc9b-477">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-477">String</span></span>|  
|<span data-ttu-id="0fc9b-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="0fc9b-479">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-479">String</span></span>|  
|<span data-ttu-id="0fc9b-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0fc9b-481">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-481">Int16</span></span>|  
|<span data-ttu-id="0fc9b-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0fc9b-483">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-483">Int16</span></span>|  
|<span data-ttu-id="0fc9b-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0fc9b-485">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-485">Int16</span></span>|  
|<span data-ttu-id="0fc9b-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-486">REMARKS</span></span>|<span data-ttu-id="0fc9b-487">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-487">String</span></span>|  
|<span data-ttu-id="0fc9b-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0fc9b-489">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0fc9b-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0fc9b-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0fc9b-491">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-491">ColumnName</span></span>|<span data-ttu-id="0fc9b-492">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0fc9b-494">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-494">String</span></span>|  
|<span data-ttu-id="0fc9b-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc9b-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0fc9b-496">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-496">String</span></span>|  
|<span data-ttu-id="0fc9b-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="0fc9b-498">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-498">String</span></span>|  
|<span data-ttu-id="0fc9b-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-499">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-500">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-500">String</span></span>|  
|<span data-ttu-id="0fc9b-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-501">COLUMN_TYPE</span></span>|<span data-ttu-id="0fc9b-502">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-502">Int16</span></span>|  
|<span data-ttu-id="0fc9b-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-503">DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-504">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-504">Int16</span></span>|  
|<span data-ttu-id="0fc9b-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-505">TYPE_NAME</span></span>|<span data-ttu-id="0fc9b-506">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-506">String</span></span>|  
|<span data-ttu-id="0fc9b-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-507">PRECISION</span></span>|<span data-ttu-id="0fc9b-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-508">Int32</span></span>|  
|<span data-ttu-id="0fc9b-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-509">LENGTH</span></span>|<span data-ttu-id="0fc9b-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-510">Int32</span></span>|  
|<span data-ttu-id="0fc9b-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-511">SCALE</span></span>|<span data-ttu-id="0fc9b-512">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-512">Int16</span></span>|  
|<span data-ttu-id="0fc9b-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="0fc9b-513">RADIX</span></span>|<span data-ttu-id="0fc9b-514">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-514">Int16</span></span>|  
|<span data-ttu-id="0fc9b-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-515">NULLABLE</span></span>|<span data-ttu-id="0fc9b-516">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-516">Int16</span></span>|  
|<span data-ttu-id="0fc9b-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-517">REMARKS</span></span>|<span data-ttu-id="0fc9b-518">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-518">String</span></span>|  
|<span data-ttu-id="0fc9b-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="0fc9b-519">OVERLOAD</span></span>|<span data-ttu-id="0fc9b-520">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-520">Int32</span></span>|  
|<span data-ttu-id="0fc9b-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-522">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0fc9b-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0fc9b-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0fc9b-524">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-524">ColumnName</span></span>|<span data-ttu-id="0fc9b-525">Type de données</span><span class="sxs-lookup"><span data-stu-id="0fc9b-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0fc9b-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0fc9b-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="0fc9b-527">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-527">String</span></span>|  
|<span data-ttu-id="0fc9b-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0fc9b-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0fc9b-529">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-529">String</span></span>|  
|<span data-ttu-id="0fc9b-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="0fc9b-531">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-531">String</span></span>|  
|<span data-ttu-id="0fc9b-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-532">COLUMN_NAME</span></span>|<span data-ttu-id="0fc9b-533">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-533">String</span></span>|  
|<span data-ttu-id="0fc9b-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-534">COLUMN_TYPE</span></span>|<span data-ttu-id="0fc9b-535">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-535">Int16</span></span>|  
|<span data-ttu-id="0fc9b-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-536">DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-537">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-537">Int16</span></span>|  
|<span data-ttu-id="0fc9b-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0fc9b-538">TYPE_NAME</span></span>|<span data-ttu-id="0fc9b-539">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-539">String</span></span>|  
|<span data-ttu-id="0fc9b-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-540">COLUMN_SIZE</span></span>|<span data-ttu-id="0fc9b-541">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-541">Int32</span></span>|  
|<span data-ttu-id="0fc9b-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="0fc9b-543">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-543">Int32</span></span>|  
|<span data-ttu-id="0fc9b-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0fc9b-545">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-545">Int16</span></span>|  
|<span data-ttu-id="0fc9b-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0fc9b-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0fc9b-547">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-547">Int16</span></span>|  
|<span data-ttu-id="0fc9b-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-548">NULLABLE</span></span>|<span data-ttu-id="0fc9b-549">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-549">Int16</span></span>|  
|<span data-ttu-id="0fc9b-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0fc9b-550">REMARKS</span></span>|<span data-ttu-id="0fc9b-551">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-551">String</span></span>|  
|<span data-ttu-id="0fc9b-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0fc9b-552">COLUMN_DEF</span></span>|<span data-ttu-id="0fc9b-553">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-553">String</span></span>|  
|<span data-ttu-id="0fc9b-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0fc9b-555">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-555">Int16</span></span>|  
|<span data-ttu-id="0fc9b-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0fc9b-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0fc9b-557">Int16</span><span class="sxs-lookup"><span data-stu-id="0fc9b-557">Int16</span></span>|  
|<span data-ttu-id="0fc9b-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0fc9b-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0fc9b-559">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-559">Int32</span></span>|  
|<span data-ttu-id="0fc9b-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0fc9b-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="0fc9b-561">Int32</span><span class="sxs-lookup"><span data-stu-id="0fc9b-561">Int32</span></span>|  
|<span data-ttu-id="0fc9b-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0fc9b-562">IS_NULLABLE</span></span>|<span data-ttu-id="0fc9b-563">Chaîne</span><span class="sxs-lookup"><span data-stu-id="0fc9b-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fc9b-564">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fc9b-564">See Also</span></span>  
 [<span data-ttu-id="0fc9b-565">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="0fc9b-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
