---
title: "Collections de sch&#233;mas ODBC | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Collections de sch&#233;mas ODBC
Cette section traite de la prise en charge des collections de schémas pour les pilotes ODBC Microsoft SQL Server, Oracle et Microsoft Jet.  
  
## Pilote Microsoft SQL Server ODBC  
 Le pilote Microsoft SQL Server ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Index  
  
-   Columns  
  
-   Procédures  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Vues  
  
### Tables et vues  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CAT|Chaîne|  
|TABLE\_SCHEM|Chaîne|  
|TABLE\_NAME|Chaîne|  
|TABLE\_TYPE|Chaîne|  
|REMARKS|Chaîne|  
  
### Index  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CAT|Chaîne|  
|TABLE\_SCHEM|Chaîne|  
|TABLE\_NAME|Chaîne|  
|NON\_UNIQUE|Int16|  
|INDEX\_QUALIFIER|Chaîne|  
|INDEX\_NAME|Chaîne|  
|TYPE|Int16|  
|ORDINAL\_POSITION|Int16|  
|COLUMN\_NAME|Chaîne|  
|ASC\_OR\_DESC|Chaîne|  
|CARDINALITY|Int32|  
|PAGES|Int32|  
|FILTER\_CONDITION|Chaîne|  
|SS\_TYPE\_SCHEMA|Chaîne|  
|SS\_DATA\_TYPE|Byte|  
  
### Columns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CAT|Chaîne|  
|TABLE\_SCHEM|Chaîne|  
|TABLE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|Chaîne|  
|COLUMN\_SIZE|Int32|  
|BUFFER\_LENGTH|Int32|  
|DECIMAL\_DIGITS|Int16|  
|NUM\_PREC\_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|COLUMN\_DEF|Chaîne|  
|SQL\_DATA\_TYPE|Int16|  
|SQL\_DATETIME\_SUB|Int16|  
|CHAR\_OCTET\_LENGTH|Int32|  
|ORDINAL\_POSITION|Int32|  
|IS\_NULLABLE|Chaîne|  
|SS\_TYPE\_CATALOG|Chaîne|  
|SS\_TYPE\_SCHEMA|Chaîne|  
|SS\_DATA\_TYPE|Byte|  
  
### Procédures  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CAT|Chaîne|  
|PROCEDURE\_SCHEM|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|NUM\_INPUT\_PARAMS|Int32|  
|NUM\_OUTPUT\_PARAMS|Int32|  
|NUM\_RESULT\_SETS|Int32|  
|REMARKS|Chaîne|  
|PROCEDURE\_TYPE|Int16|  
  
### ProcedureColumns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CAT|Chaîne|  
|PROCEDURE\_SCHEM|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|Chaîne|  
|COLUMN\_SIZE|Int32|  
|BUFFER\_LENGTH|Int32|  
|DECIMAL\_DIGITS|Int16|  
|NUM\_PREC\_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|COLUMN\_DEF|Chaîne|  
|SQL\_DATA\_TYPE|Int16|  
|SQL\_DATETIME\_SUB|Int16|  
|CHAR\_OCTET\_LENGTH|Int32|  
|ORDINAL\_POSITION|Int32|  
|IS\_NULLABLE|Chaîne|  
|SS\_TYPE\_CATALOG|Chaîne|  
|SS\_TYPE\_SCHEMA|Chaîne|  
|SS\_DATA\_TYPE|Byte|  
  
### ProcedureParameters  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CAT|Chaîne|  
|PROCEDURE\_SCHEM|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|Chaîne|  
|COLUMN\_SIZE|Int32|  
|BUFFER\_LENGTH|Int32|  
|DECIMAL\_DIGITS|Int16|  
|NUM\_PREC\_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|COLUMN\_DEF|Chaîne|  
|SQL\_DATA\_TYPE|Int16|  
|SQL\_DATETIME\_SUB|Int16|  
|CHAR\_OCTET\_LENGTH|Int32|  
|ORDINAL\_POSITION|Int32|  
|IS\_NULLABLE|Chaîne|  
|SS\_TYPE\_CATALOG|Chaîne|  
|SS\_TYPE\_SCHEMA|Chaîne|  
|SS\_DATA\_TYPE|Byte|  
  
## Pilote Microsoft Oracle ODBC  
 Le pilote Microsoft SQL Server Oracle ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Columns  
  
-   Procédures  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Vues  
  
-   Index  
  
### Tables et vues  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_QUALIFIER|Chaîne|  
|TABLE\_OWNER|Chaîne|  
|TABLE\_NAME|Chaîne|  
|TABLE\_TYPE|Chaîne|  
|REMARKS|Chaîne|  
  
### Columns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_QUALIFIER|Chaîne|  
|TABLE\_OWNER|Chaîne|  
|TABLE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|Chaîne|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|ORDINAL\_POSITION|Int32|  
  
### Procédures  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_QUALIFIER|Chaîne|  
|PROCEDURE\_OWNER|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|NUM\_INPUT\_PARAMS|Int16|  
|NUM\_OUTPUT\_PARAMS|Int16|  
|NUM\_RESULT\_SETS|Int16|  
|REMARKS|Chaîne|  
|PROCEDURE\_TYPE|Int16|  
  
### ProcedureColumns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_QUALIFIER|Chaîne|  
|PROCEDURE\_OWNER|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|Chaîne|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|OVERLOAD|Int32|  
|ORDINAL\_POSITION|Int32|  
  
## Pilote Microsoft Jet ODBC  
 Le pilote Microsoft Jet ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Index  
  
-   Columns  
  
-   Procédures  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Vues  
  
### Tables et vues  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_QUALIFIER|Chaîne|  
|TABLE\_OWNER|Chaîne|  
|TABLE\_NAME|Chaîne|  
|TABLE\_TYPE|Chaîne|  
|REMARKS|Chaîne|  
  
### Columns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_QUALIFIER|Chaîne|  
|TABLE\_OWNER|Chaîne|  
|TABLE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|Chaîne|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|ORDINAL\_POSITION|Int32|  
  
### Procédures  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_QUALIFIER|Chaîne|  
|PROCEDURE\_OWNER|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|NUM\_INPUT\_PARAMS|Int16|  
|NUM\_OUTPUT\_PARAMS|Int16|  
|NUM\_RESULT\_SETS|Int16|  
|REMARKS|Chaîne|  
|PROCEDURE\_TYPE|Int16|  
  
### ProcedureColumns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_QUALIFIER|Chaîne|  
|PROCEDURE\_OWNER|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|Chaîne|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|OVERLOAD|Int32|  
|ORDINAL\_POSITION|Int32|  
  
### ProcedureParameters  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CAT|Chaîne|  
|PROCEDURE\_SCHEM|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|Chaîne|  
|COLUMN\_SIZE|Int32|  
|BUFFER\_LENGTH|Int32|  
|DECIMAL\_DIGITS|Int16|  
|NUM\_PREC\_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|Chaîne|  
|COLUMN\_DEF|Chaîne|  
|SQL\_DATA\_TYPE|Int16|  
|SQL\_DATETIME\_SUB|Int16|  
|CHAR\_OCTET\_LENGTH|Int32|  
|ORDINAL\_POSITION|Int32|  
|IS\_NULLABLE|Chaîne|  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)