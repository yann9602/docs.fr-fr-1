---
title: "Mappings1 de Type de données Oracle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: adb0fc332e00e766a62d0af1c110c5a7ce2d42c3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-data-type-mappings"></a>Mappages des types de données Oracle
La table suivante répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Type de données Oracle|Type de données .NET Framework retourné par OracleDataReader.GetValue|Type de données OracleClient retourné par OracleDataReader.GetOracleValue|Notes|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le **nombre** type de données et est conçu afin que les <xref:System.Data.OracleClient.OracleDataReader> retourne un **System.Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur à virgule flottante. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le **Number (38)** type de données et est conçu afin que les <xref:System.Data.OracleClient.OracleDataReader> retourne un **System.Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur entière. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**INTERVALLE ANNÉE MOIS**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**DEUXIÈME INTERVALLE JOUR**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR** type de données n’est pas pris en charge par le <xref:System.Data.OracleClient.OracleDataReader> objet.|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**HORODATEUR AVEC FUSEAU HORAIRE LOCAL**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**HORODATEUR AVEC FUSEAU HORAIRE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ENTIER NON SIGNÉ**|**Nombre**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le **Number (38)** type de données et est conçu afin que les <xref:System.Data.OracleClient.OracleDataReader> retourne un **System.Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur entière non signée. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 Le tableau suivant répertorie les types de données Oracle et les types de données .NET Framework (**System.Data.DbType** et <xref:System.Data.OracleClient.OracleType>) à utiliser pour les lier comme paramètres.  
  
|Type de données Oracle|Énumération DbType à lier comme paramètre|Énumération OracleType à lier comme paramètre|Notes|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle n’autorise la liaison un **BFILE** comme un **BFILE** paramètre. Le fournisseur de données .NET pour Oracle ne construit pas automatiquement un pour vous si vous tentez de lier un non -**BFILE** de valeurs, tels que **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle n’autorise la liaison un **BLOB** comme un **BLOB** paramètre. Le fournisseur de données .NET pour Oracle ne construit pas automatiquement un pour vous si vous tentez de lier un non -**BLOB** de valeurs, tels que **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle n’autorise la liaison un **CLOB** comme un **CLOB** paramètre. Le fournisseur de données .NET pour Oracle ne construit pas automatiquement un pour vous si vous tentez de lier un non -**CLOB** de valeurs, tels que **System.String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single, Double, Decimal**|**Float, Double, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Détermine la **System.Data.DBType** et <xref:System.Data.OracleClient.OracleType>.|  
|**INTEGER**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Détermine la **System.Data.DBType** et <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVALLE ANNÉE MOIS**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**DEUXIÈME INTERVALLE JOUR**|**Objet**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle n’autorise la liaison un **NCLOB** comme un **NCLOB** paramètre. Le fournisseur de données .NET pour Oracle ne construit pas automatiquement un pour vous si vous tentez de lier un non -**NCLOB** de valeurs, tels que **System.String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**NUMBER**|**VarNumeric**|**Nombre**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**Binary**|**Raw**||  
|**REF CURSOR**||**Cursor**|Pour plus d’informations, consultez [REF CURSOR Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**Horodatage**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**HORODATEUR AVEC FUSEAU HORAIRE LOCAL**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**HORODATEUR AVEC FUSEAU HORAIRE**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**ENTIER NON SIGNÉ**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Détermine la **System.Data.DBType** et <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 Le **InputOutput**, **sortie**, et **ReturnValue** **ParameterDirection** valeurs utilisées par le <xref:System.Data.OracleClient.OracleParameter.Value%2A> propriété de la <xref:System.Data.OracleClient.OracleParameter> objet sont des types de données .NET Framework, à moins que la valeur d’entrée est un type de données Oracle (par exemple, <xref:System.Data.OracleClient.OracleNumber> ou <xref:System.Data.OracleClient.OracleString>). Cela ne s’applique pas aux **REF CURSOR**, **BFILE**, ou **LOB** des types de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
