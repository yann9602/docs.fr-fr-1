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
# <a name="odbc-schema-collections"></a>Collections de schémas ODBC
Cette section traite de la prise en charge des collections de schémas pour les pilotes ODBC Microsoft SQL Server, Oracle et Microsoft Jet.  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Pilote Microsoft SQL Server ODBC  
 Le pilote ODBC de Microsoft SQL Server prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Index  
  
-   Columns  
  
-   Procédures  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Vues  
  
### <a name="tables-and-views"></a>Tables et vues  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|TABLE_CAT|Chaîne|  
|TABLE_SCHEM|Chaîne|  
|TABLE_NAME|Chaîne|  
|TABLE_TYPE|Chaîne|  
|REMARKS|Chaîne|  
  
### <a name="indexes"></a>Index  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|TABLE_CAT|Chaîne|  
|TABLE_SCHEM|Chaîne|  
|TABLE_NAME|Chaîne|  
|NON_UNIQUE|Int16|  
|INDEX_QUALIFIER|Chaîne|  
|INDEX_NAME|Chaîne|  
|TYPE|Int16|  
|ORDINAL_POSITION|Int16|  
|COLUMN_NAME|Chaîne|  
|ASC_OR_DESC|Chaîne|  
|CARDINALITY|Int32|  
|PAGES|Int32|  
|FILTER_CONDITION|Chaîne|  
|SS_TYPE_SCHEMA|Chaîne|  
|SS_DATA_TYPE|Byte|  
  
### <a name="columns"></a>Columns  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|TABLE_CAT|Chaîne|  
|TABLE_SCHEM|Chaîne|  
|TABLE_NAME|Chaîne|  
|COLUMN_NAME|Chaîne|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Chaîne|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|COLUMN_DEF|Chaîne|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Chaîne|  
|SS_TYPE_CATALOG|Chaîne|  
|SS_TYPE_SCHEMA|Chaîne|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedures"></a>Procédures  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|PROCEDURE_CAT|Chaîne|  
|PROCEDURE_SCHEM|Chaîne|  
|PROCEDURE_NAME|Chaîne|  
|NUM_INPUT_PARAMS|Int32|  
|NUM_OUTPUT_PARAMS|Int32|  
|NUM_RESULT_SETS|Int32|  
|REMARKS|Chaîne|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|PROCEDURE_CAT|Chaîne|  
|PROCEDURE_SCHEM|Chaîne|  
|PROCEDURE_NAME|Chaîne|  
|COLUMN_NAME|Chaîne|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Chaîne|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|COLUMN_DEF|Chaîne|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Chaîne|  
|SS_TYPE_CATALOG|Chaîne|  
|SS_TYPE_SCHEMA|Chaîne|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|PROCEDURE_CAT|Chaîne|  
|PROCEDURE_SCHEM|Chaîne|  
|PROCEDURE_NAME|Chaîne|  
|COLUMN_NAME|Chaîne|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Chaîne|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|COLUMN_DEF|Chaîne|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Chaîne|  
|SS_TYPE_CATALOG|Chaîne|  
|SS_TYPE_SCHEMA|Chaîne|  
|SS_DATA_TYPE|Byte|  
  
## <a name="microsoft-oracle-odbc-driver"></a>Pilote Microsoft Oracle ODBC  
 Le pilote Microsoft SQL Server Oracle ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Columns  
  
-   Procédures  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Vues  
  
-   Index  
  
### <a name="tables-and-views"></a>Tables et vues  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|TABLE_QUALIFIER|Chaîne|  
|TABLE_OWNER|Chaîne|  
|TABLE_NAME|Chaîne|  
|TABLE_TYPE|Chaîne|  
|REMARKS|Chaîne|  
  
### <a name="columns"></a>Columns  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|TABLE_QUALIFIER|Chaîne|  
|TABLE_OWNER|Chaîne|  
|TABLE_NAME|Chaîne|  
|COLUMN_NAME|Chaîne|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Chaîne|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procédures  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Chaîne|  
|PROCEDURE_OWNER|Chaîne|  
|PROCEDURE_NAME|Chaîne|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|REMARKS|Chaîne|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Chaîne|  
|PROCEDURE_OWNER|Chaîne|  
|PROCEDURE_NAME|Chaîne|  
|COLUMN_NAME|Chaîne|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Chaîne|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|OVERLOAD|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Pilote Microsoft Jet ODBC  
 Le pilote Microsoft Jet ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Index  
  
-   Columns  
  
-   Procédures  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Vues  
  
### <a name="tables-and-views"></a>Tables et vues  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|TABLE_QUALIFIER|Chaîne|  
|TABLE_OWNER|Chaîne|  
|TABLE_NAME|Chaîne|  
|TABLE_TYPE|Chaîne|  
|REMARKS|Chaîne|  
  
### <a name="columns"></a>Columns  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|TABLE_QUALIFIER|Chaîne|  
|TABLE_OWNER|Chaîne|  
|TABLE_NAME|Chaîne|  
|COLUMN_NAME|Chaîne|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Chaîne|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procédures  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Chaîne|  
|PROCEDURE_OWNER|Chaîne|  
|PROCEDURE_NAME|Chaîne|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|REMARKS|Chaîne|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Chaîne|  
|PROCEDURE_OWNER|Chaîne|  
|PROCEDURE_NAME|Chaîne|  
|COLUMN_NAME|Chaîne|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Chaîne|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|OVERLOAD|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Nom de colonne|Type de données|  
|----------------|--------------|  
|PROCEDURE_CAT|Chaîne|  
|PROCEDURE_SCHEM|Chaîne|  
|PROCEDURE_NAME|Chaîne|  
|COLUMN_NAME|Chaîne|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Chaîne|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|COLUMN_DEF|Chaîne|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Chaîne|  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
