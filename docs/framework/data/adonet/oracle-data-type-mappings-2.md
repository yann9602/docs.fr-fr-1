---
title: "Mappages des types de donn&#233;es Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2521bcc-0051-4f35-8be3-e8723edeaf6f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Mappages des types de donn&#233;es Oracle
Le tableau suivant présente le type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] déduit pour les types de données du fournisseur de données .NET Framework pour Oracle \(<xref:System.Data.OracleClient>\). Les méthodes d'accesseur typé pour le <xref:System.Data.OracleClient.OracleDataReader> sont également répertoriées.  
  
|Type Oracle|Type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|Accesseur typé [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|Accesseur typé OracleType|  
|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|-------------------------------|  
|BFILE|Byte\[\]|GetBytes\(\)|GetOracleBFile\(\)|  
|BLOB|Byte\[\]|GetBytes\(\)|GetOracleLob\(\)|  
|CHAR|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|CLOB|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleLob\(\)|  
|DATE|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|FLOAT|Decimal|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|INTEGER|Decimal|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|INTERVAL YEAR TO MONTH \*|Int32|GetInt32\(\)|GetOracleMonthSpan\(\)|  
|INTERVAL DAY TO SECOND \*|TimeSpan|GetTimeSpan\(\)|GetOracleTimeSpan\(\)|  
|LONG|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|LONG RAW|Byte\[\]|GetBytes\(\)|GetOracleBinary\(\)|  
|NCHAR|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|NCLOB|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleLob\(\)|  
|NUMBER|Decimal|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|NVARCHAR2|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|RAW|Byte\[\]|GetBytes\(\)|GetOracleBinary\(\)|  
|REF CURSOR||||  
|ROWID|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|TIMESTAMP \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|TIMESTAMP WITH LOCAL TIME ZONE \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|TIMESTAMP WITH TIME ZONE \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|UNSIGNED INTEGER|Decimal|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|VARCHAR2|Chaîne<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
  
 \* Le type Oracle spécifié est uniquement disponible si vous utilisez le logiciel Oracle 9i pour le client et le serveur.  
  
 \*\* Un type NUMBER Oracle peut avoir un nombre maximal de 38 chiffres significatifs. Le type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` est limité à 28 chiffres. La lecture d'un type NUMBER Oracle dans un type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` lève une exception `OverflowException` pour les valeurs NUMBER qui dépassent 28 chiffres. Si vous lisez une valeur NUMBER Oracle à partir d'un `OracleDataReader`, il est recommandé d'appeler la méthode d'accesseur typé `GetOracleNumber` pour retourner les valeurs NUMBER Oracle en tant que `OracleNumber`. Si vous remplissez un `DataSet`, vous pouvez utiliser l'événement `FillError` pour déterminer si une exception `OverflowException` s'est produite et, le cas échéant, effectuer l'action appropriée. Pour plus d’informations sur l’événement `FillError`, consultez [Gestion des événements DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## Voir aussi  
 [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)