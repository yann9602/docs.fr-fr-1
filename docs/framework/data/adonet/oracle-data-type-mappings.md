---
title: "Mappages de types de donn&#233;es Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Mappages de types de donn&#233;es Oracle
La table suivante répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Type de données Oracle|Type de données .NET Framework retourné par OracleDataReader.GetValue|Type de données OracleClient retourné par OracleDataReader.GetOracleValue|Notes|  
|----------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------------|-----------|  
|**BFILE**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Chaîne**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias du type de données **NUMBER** et est conçu de façon à ce que le <xref:System.Data.OracleClient.OracleDataReader> retourne un **System.Decimal** ou un <xref:System.Data.OracleClient.OracleNumber> au lieu d'une valeur en virgule flottante.  L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias du type de données **NUMBER\(38\)** et est conçu de façon à ce que le <xref:System.Data.OracleClient.OracleDataReader> retourne un **System.Decimal** ou un <xref:System.Data.OracleClient.OracleNumber> au lieu d'une valeur entière.  L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO SECOND**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Chaîne**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**NVARCHAR2**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||La type de données Oracle **REF CURSOR** n'est pas pris en charge par l'objet <xref:System.Data.OracleClient.OracleDataReader>.|  
|**ROWID**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**UNSIGNED INTEGER**|**Nombre**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias du type de données **NUMBER\(38\)** et est conçu de façon à ce que le <xref:System.Data.OracleClient.OracleDataReader> retourne un **System.Decimal** ou un <xref:System.Data.OracleClient.OracleNumber> au lieu d'une valeur entière non signée.  L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**VARCHAR2**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
  
 La table suivante répertorie les types de données Oracle et les types de données .NET Framework \(**System.Data.DbType** et <xref:System.Data.OracleClient.OracleType>\) à utiliser pour les lier comme paramètres.  
  
|Type de données Oracle|Énumération DbType à lier comme paramètre|Énumération OracleType à lier comme paramètre|Notes|  
|----------------------------|-----------------------------------------------|---------------------------------------------------|-----------|  
|**BFILE**||**BFile**|Oracle n'autorise la liaison d'un **BFILE** que comme paramètre **BFILE**.  Le fournisseur de données .NET pour Oracle n'en construit pas automatiquement un pour vous si vous tentez de lier une valeur non **BFILE**, telle que **byte\[\]** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle n'autorise la liaison d'un **BLOB** que comme paramètre **BLOB**.  Le fournisseur de données .NET pour Oracle n'en construit pas automatiquement un pour vous si vous tentez de lier une valeur non **BLOB**, telle que **byte\[\]** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle n'autorise la liaison d'un **CLOB** que comme paramètre **CLOB**.  Le fournisseur de données .NET pour Oracle n'en construit pas automatiquement un pour vous si vous tentez de lier une valeur non **CLOB**, telle que **System.String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Simple, Double, Decimal**|**Float, Double, Number**|[Size](frlrfSystemDataOracleClientOracleParameterClassSizeTopic) détermine le **System.Data.DBType** et le <xref:System.Data.OracleClient.OracleType>.|  
|**INTEGER**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, Number**|[Size](frlrfSystemDataOracleClientOracleParameterClassSizeTopic) détermine le **System.Data.DBType** et le <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**INTERVAL DAY TO SECOND**|**Objet**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binaire**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle n'autorise la liaison d'un **NCLOB** que comme paramètre **NCLOB**.  Le fournisseur de données .NET pour Oracle n'en construit pas automatiquement un pour vous si vous tentez de lier une valeur non **NCLOB**, telle que **System.String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**NUMBER**|**VarNumeric**|**Nombre**||  
|**NVARCHAR2**|**Chaîne**|**NVarChar**||  
|**RAW**|**Binaire**|**Raw**||  
|**REF CURSOR**||**Curseur**|Pour plus d'informations, consultez [REF CURSOR Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**Horodateur**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**UNSIGNED INTEGER**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, Number**|[Size](frlrfSystemDataOracleClientOracleParameterClassSizeTopic) détermine le **System.Data.DBType** et le <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 Les valeurs **InputOutput**, **Output** et **ReturnValue** **ParameterDirection** utilisées par la propriété <xref:System.Data.OracleClient.OracleParameter.Value%2A> de l'objet <xref:System.Data.OracleClient.OracleParameter> sont des types de données .NET Framework, à moins que la valeur d'entrée ne soit un type de données Oracle \(par exemple, <xref:System.Data.OracleClient.OracleNumber> ou <xref:System.Data.OracleClient.OracleString>\).  Cela ne s'applique pas aux types de données **REF CURSOR**, **BFILE** ou **LOB**.  
  
## Voir aussi  
 [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)