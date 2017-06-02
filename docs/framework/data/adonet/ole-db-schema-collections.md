---
title: "Collections de sch&#233;mas OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Collections de sch&#233;mas OLE DB
Cette section traite de la prise en charge des collections de schémas pour les fournisseurs OLE DB de Microsoft SQL Server, Oracle et Microsoft Jet.  
  
## Fournisseur Microsoft SQL Server OLE DB  
 Le pilote Microsoft SQL Server OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Columns  
  
-   Procédures  
  
-   ProcedureParameters  
  
-   Catalogue  
  
-   Index  
  
### Tables  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|TABLE\_TYPE|Chaîne|  
|TABLE\_GUID|Guid|  
|DESCRIPTION|Chaîne|  
|TABLE\_PROPID|Int64|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### Columns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_HASDEFAULT|Boolean|  
|COLUMN\_DEFAULT|Chaîne|  
|COLUMN\_FLAGS|Int64|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|TYPE\_GUID|Guid|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DATETIME\_PRECISION|Int64|  
|CHARACTER\_SET\_CATALOG|Chaîne|  
|CHARACTER\_SET\_SCHEMA|Chaîne|  
|CHARACTER\_SET\_NAME|Chaîne|  
|COLLATION\_CATALOG|Chaîne|  
|COLLATION\_SCHEMA|Chaîne|  
|COLLATION\_NAME|Chaîne|  
|DOMAIN\_CATALOG|Chaîne|  
|DOMAIN\_SCHEMA|Chaîne|  
|DOMAIN\_NAME|Chaîne|  
|DESCRIPTION|Chaîne|  
|COLUMN\_LCID|Int32|  
|COLUMN\_COMPFLAGS|Int32|  
|COLUMN\_SORTID|Int32|  
|COLUMN\_TDSCOLLATION|Byte\[\]|  
|IS\_COMPUTED|Boolean|  
  
### Procédures  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CATALOG|Chaîne|  
|PROCEDURE\_SCHEMA|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|PROCEDURE\_TYPE|Int16|  
|PROCEDURE\_DEFINITION|Chaîne|  
|DESCRIPTION|Chaîne|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### ProcedureParameters  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CATALOG|Chaîne|  
|PROCEDURE\_SCHEMA|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|PARAMETER\_NAME|Chaîne|  
|ORDINAL\_POSITION|Int32|  
|PARAMETER\_TYPE|Int32|  
|PARAMETER\_HASDEFAULT|Boolean|  
|PARAMETER\_DEFAULT|Chaîne|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DESCRIPTION|Chaîne|  
|TYPE\_NAME|Chaîne|  
|LOCAL\_TYPE\_NAME|Chaîne|  
  
### Catalogue  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|CATALOG\_NAME|Chaîne|  
|DESCRIPTION|Chaîne|  
  
### Index  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|INDEX\_CATALOG|Chaîne|  
|INDEX\_SCHEMA|Chaîne|  
|INDEX\_NAME|Chaîne|  
|PRIMARY\_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYPE|Int32|  
|FILL\_FACTOR|Int32|  
|INITIAL\_SIZE|Int32|  
|NULLS|Int32|  
|SORT\_BOOKMARKS|Boolean|  
|AUTO\_UPDATE|Boolean|  
|NULL\_COLLATION|Int32|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|COLLATION|Int16|  
|CARDINALITY|Decimal|  
|PAGES|Int32|  
|FILTER\_CONDITION|Chaîne|  
|INTEGRATED|Boolean|  
  
## Fournisseur Microsoft Oracle OLE DB  
 Le pilote Microsoft Oracle OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Columns  
  
-   Procédures  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Vues  
  
-   Index  
  
### Tables  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|TABLE\_TYPE|Chaîne|  
|TABLE\_GUID|Guid|  
|DESCRIPTION|Chaîne|  
|TABLE\_PROPID|Int64|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### Columns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_HASDEFAULT|Boolean|  
|COLUMN\_DEFAULT|Chaîne|  
|COLUMN\_FLAGS|Int64|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|TYPE\_GUID|Guid|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DATETIME\_PRECISION|Int64|  
|CHARACTER\_SET\_CATALOG|Chaîne|  
|CHARACTER\_SET\_SCHEMA|Chaîne|  
|CHARACTER\_SET\_NAME|Chaîne|  
|COLLATION\_CATALOG|Chaîne|  
|COLLATION\_SCHEMA|Chaîne|  
|COLLATION\_NAME|Chaîne|  
|DOMAIN\_CATALOG|Chaîne|  
|DOMAIN\_SCHEMA|Chaîne|  
|DOMAIN\_NAME|Chaîne|  
|DESCRIPTION|Chaîne|  
  
### Procédures  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CATALOG|Chaîne|  
|PROCEDURE\_SCHEMA|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|PROCEDURE\_TYPE|Int16|  
|PROCEDURE\_DEFINITION|Chaîne|  
|DESCRIPTION|Chaîne|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### ProcedureColumns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CATALOG|Chaîne|  
|PROCEDURE\_SCHEMA|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|ROWSET\_NUMBER|Int64|  
|ORDINAL\_POSITION|Int64|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|TYPE\_GUID|Guid|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DESCRIPTION|Chaîne|  
|OVERLOAD|Int16|  
  
### Vues  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|VIEW\_DEFINITION|Chaîne|  
|CHECK\_OPTION|Boolean|  
|IS\_UPDATABLE|Boolean|  
|DESCRIPTION|Chaîne|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### Index  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|INDEX\_CATALOG|Chaîne|  
|INDEX\_SCHEMA|Chaîne|  
|INDEX\_NAME|Chaîne|  
|PRIMARY\_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYPE|Int32|  
|FILL\_FACTOR|Int32|  
|INITIAL\_SIZE|Int32|  
|NULLS|Int32|  
|SORT\_BOOKMARKS|Boolean|  
|AUTO\_UPDATE|Boolean|  
|NULL\_COLLATION|Int32|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|COLLATION|Int16|  
|CARDINALITY|Decimal|  
|PAGES|Int32|  
|FILTER\_CONDITION|Chaîne|  
|INTEGRATED|Boolean|  
  
## Fournisseur Microsoft Jet OLE DB  
 Le pilote Microsoft Jet OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :  
  
-   Tables  
  
-   Columns  
  
-   Procédures  
  
-   Vues  
  
-   Index  
  
### Tables  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|TABLE\_TYPE|Chaîne|  
|TABLE\_GUID|Guid|  
|DESCRIPTION|Chaîne|  
|TABLE\_PROPID|Int64|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### Columns  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_HASDEFAULT|Boolean|  
|COLUMN\_DEFAULT|Chaîne|  
|COLUMN\_FLAGS|Int64|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|TYPE\_GUID|Guid|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DATETIME\_PRECISION|Int64|  
|CHARACTER\_SET\_CATALOG|Chaîne|  
|CHARACTER\_SET\_SCHEMA|Chaîne|  
|CHARACTER\_SET\_NAME|Chaîne|  
|COLLATION\_CATALOG|Chaîne|  
|COLLATION\_SCHEMA|Chaîne|  
|COLLATION\_NAME|Chaîne|  
|DOMAIN\_CATALOG|Chaîne|  
|DOMAIN\_SCHEMA|Chaîne|  
|DOMAIN\_NAME|Chaîne|  
|DESCRIPTION|Chaîne|  
  
### Procédures  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|PROCEDURE\_CATALOG|Chaîne|  
|PROCEDURE\_SCHEMA|Chaîne|  
|PROCEDURE\_NAME|Chaîne|  
|PROCEDURE\_TYPE|Int16|  
|PROCEDURE\_DEFINITION|Chaîne|  
|DESCRIPTION|Chaîne|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### Vues  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|VIEW\_DEFINITION|Chaîne|  
|CHECK\_OPTION|Boolean|  
|IS\_UPDATABLE|Boolean|  
|DESCRIPTION|Chaîne|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### Index  
  
|Nom de colonne|Type de données|  
|--------------------|---------------------|  
|TABLE\_CATALOG|Chaîne|  
|TABLE\_SCHEMA|Chaîne|  
|TABLE\_NAME|Chaîne|  
|INDEX\_CATALOG|Chaîne|  
|INDEX\_SCHEMA|Chaîne|  
|INDEX\_NAME|Chaîne|  
|PRIMARY\_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYPE|Int32|  
|FILL\_FACTOR|Int32|  
|INITIAL\_SIZE|Int32|  
|NULLS|Int32|  
|SORT\_BOOKMARKS|Boolean|  
|AUTO\_UPDATE|Boolean|  
|NULL\_COLLATION|Int32|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_NAME|Chaîne|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|COLLATION|Int16|  
|CARDINALITY|Decimal|  
|PAGES|Int32|  
|FILTER\_CONDITION|Chaîne|  
|INTEGRATED|Boolean|  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)