---
title: "Mappages de types de donn&#233;es OLE&#160;DB | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Mappages de types de donn&#233;es OLE&#160;DB
Le tableau suivant présente le type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] déduit pour les types de données du fournisseur de données .NET Framework pour ADO et OLE DB \(<xref:System.Data.OleDb>\).  Les méthodes d'accesseur typé pour le <xref:System.Data.OleDb.OleDbDataReader> sont également répertoriées.  
  
|Type ADO|Type OLE DB|Type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|Accesseur typé [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE\_I8|Int64|GetInt64\(\)|  
|adBinary|DBTYPE\_BYTES|Byte\[\]|GetBytes\(\)|  
|adBoolean|DBTYPE\_BOOL|Boolean|GetBoolean\(\)|  
|adBSTR|DBTYPE\_BSTR|Chaîne|GetString\(\)|  
|adChapter|DBTYPE\_HCHAPTER|Pris en charge dans le `DataReader`.  Consultez [Extraction de données à l'aide d'un DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).|GetValue\(\)|  
|adChar|DBTYPE\_STR|Chaîne|GetString\(\)|  
|adCurrency|DBTYPE\_CY|Decimal|GetDecimal\(\)|  
|adDate|DBTYPE\_DATE|DateTime|GetDateTime\(\)|  
|adDBDate|DBTYPE\_DBDATE|DateTime|GetDateTime\(\)|  
|adDBTime|DBTYPE\_DBTIME|DateTime|GetDateTime\(\)|  
|adDBTimeStamp|DBTYPE\_DBTIMESTAMP|DateTime|GetDateTime\(\)|  
|adDecimal|DBTYPE\_DECIMAL|Decimal|GetDecimal\(\)|  
|adDouble|DBTYPE\_R8|Double|GetDouble\(\)|  
|adError|DBTYPE\_ERROR|ExternalException|GetValue\(\)|  
|adFileTime|DBTYPE\_FILETIME|DateTime|GetDateTime\(\)|  
|adGUID|DBTYPE\_GUID|Guid|GetGuid\(\)|  
|adIDispatch|DBTYPE\_IDISPATCH \*|Objet|GetValue\(\)|  
|adInteger|DBTYPE\_I4|Int32|GetInt32\(\)|  
|adIUnknown|DBTYPE\_IUNKNOWN \*|Objet|GetValue\(\)|  
|adNumeric|DBTYPE\_NUMERIC|Decimal|GetDecimal\(\)|  
|adPropVariant|DBTYPE\_PROPVARIANT|Objet|GetValue\(\)|  
|adSingle|DBTYPE\_R4|Single|GetFloat\(\)|  
|adSmallInt|DBTYPE\_I2|Int16|GetInt16\(\)|  
|adTinyInt|DBTYPE\_I1|Byte|GetByte\(\)|  
|adUnsignedBigInt|DBTYPE\_UI8|UInt64|GetValue\(\)|  
|adUnsignedInt|DBTYPE\_UI4|UInt32|GetValue\(\)|  
|adUnsignedSmallInt|DBTYPE\_UI2|UInt16|GetValue\(\)|  
|adUnsignedTinyInt|DBTYPE\_UI1|Byte|GetByte\(\)|  
|adVariant|DBTYPE\_VARIANT|Objet|GetValue\(\)|  
|adWChar|DBTYPE\_WSTR|Chaîne|GetString\(\)|  
|adUserDefined|DBTYPE\_UDT|non pris en charge||  
|adVarNumeric|DBTYPE\_VARNUMERIC|non pris en charge||  
  
 \* Pour les types OLE DB `DBTYPE_IUNKNOWN` et `DBTYPE_IDISPATCH`, la référence d'objet est une représentation marshalée du pointeur.  
  
## Voir aussi  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)