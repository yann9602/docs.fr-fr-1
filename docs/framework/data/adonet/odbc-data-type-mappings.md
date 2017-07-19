---
title: "Mappages de types de donn&#233;es ODBC | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Mappages de types de donn&#233;es ODBC
Le tableau suivant présente le type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] déduit pour les types de données du fournisseur de données .NET Framework pour ODBC \(<xref:System.Data.Odbc>\).  Les méthodes d'accesseur typé pour le <xref:System.Data.Odbc.OdbcDataReader> sont également répertoriées.  
  
|Type ODBC|Type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|Accesseur typé [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL\_BIGINT|Int64|GetInt64\(\)|  
|SQL\_BINARY|Byte\[\]|GetBytes\(\)|  
|SQL\_BIT|Boolean|GetBoolean\(\)|  
|SQL\_CHAR|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
|SQL\_DECIMAL|Decimal|GetDecimal\(\)|  
|SQL\_DOUBLE|Double|GetDouble\(\)|  
|SQL\_GUID|Guid|GetGuid\(\)|  
|SQL\_INTEGER|Int32|GetInt32\(\)|  
|SQL\_LONG\_VARCHAR|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
|SQL\_LONGVARBINARY|Byte\[\]|GetBytes\(\)|  
|SQL\_NUMERIC|Decimal|GetDecimal\(\)|  
|SQL\_REAL|Single|GetFloat\(\)|  
|SQL\_SMALLINT|Int16|GetInt16\(\)|  
|SQL\_TINYINT|Byte|GetByte\(\)|  
|SQL\_TYPE\_TIMES|DateTime|GetDateTime\(\)|  
|SQL\_TYPE\_TIMESTAMP|DateTime|GetDateTime\(\)|  
|SQL\_VARBINARY|Byte\[\]|GetBytes\(\)|  
|SQL\_WCHAR|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
|SQL\_WLONGVARCHAR|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
|SQL\_WVARCHAR|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
  
## Voir aussi  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)