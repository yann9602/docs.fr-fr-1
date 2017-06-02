---
title: "Mappages de types de donn&#233;es SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fafdc31a-f435-4cd3-883f-1dfadd971277
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Mappages de types de donn&#233;es SQL&#160;Server
SQL Server et le .NET Framework sont basés sur des systèmes de types différents.  Par exemple, la structure <xref:System.Decimal> du .NET Framework a une échelle maximale de 28, tandis que l'échelle maximale des types de données décimal et numérique de SQL Server est de 38.  Pour préserver l'intégrité des données lors des opérations de lecture et d'écriture, le <xref:System.Data.SqlClient.SqlDataReader> expose des méthodes d'accesseur typé spécifiques à SQL Server qui retournent des objets de <xref:System.Data.SqlTypes>, ainsi que des méthodes d'accesseur qui retournent des types .NET Framework.  Les types SQL Server et les types .NET Framework sont également représentés par des énumérations dans les classes <xref:System.Data.DbType> et <xref:System.Data.SqlDbType>, que vous pouvez utiliser pour spécifier des types de données <xref:System.Data.SqlClient.SqlParameter>.  
  
 Le tableau suivant répertorie le type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] déduit, les énumérations <xref:System.Data.DbType> et <xref:System.Data.SqlDbType>, ainsi que les méthodes d'accesseur pour le <xref:System.Data.SqlClient.SqlDataReader>.  
  
|Type du moteur de base de données SQL Server|Type .NET Framework|Énumération SqlDbType|Accesseur typé SqlTypes SqlDataReader|Énumération DbType|Accesseur typé DbType SqlDataReader|  
|--------------------------------------------------|-------------------------|---------------------------|-------------------------------------------|------------------------|-----------------------------------------|  
|bigint|Int64|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt64%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt64%2A>|  
|binaire|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|de bits|Boolean|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBoolean%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBoolean%2A>|  
|char|Chaîne<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>,<br /><br /> <xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|date<br /><br /> \(SQL Server 2008 et versions ultérieures\)|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime2<br /><br /> \(SQL Server 2008 et versions ultérieures\)|DateTime|<xref:System.Data.SqlDbType>|None|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetimeoffset<br /><br /> \(SQL Server 2008 et versions ultérieures\)|DateTimeOffset|<xref:System.Data.SqlDbType>|aucun|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|  
|decimal|Decimal|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|Attribut FILESTREAM \(varbinary\(max\)\)|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|float|Double|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDouble%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDouble%2A>|  
|image|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|int|Int32|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt32%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt32%2A>|  
|money|Decimal|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nchar|Chaîne<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|ntext|Chaîne<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|numériques|Decimal|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nvarchar|Chaîne<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|réels|Single|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlSingle%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetFloat%2A>|  
|rowversion|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|smalldatetime|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|smallint|Int16|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt16%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt16%2A>|  
|smallmoney|Decimal|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|sql\_variant|Object\*|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A> \*|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A> \*|  
|texte|Chaîne<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|heure<br /><br /> \(SQL Server 2008 et versions ultérieures\)|TimeSpan|<xref:System.Data.SqlDbType>|aucun|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|horodatage|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|tinyint|Byte|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlByte%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetByte%2A>|  
|uniqueidentifier|Guid|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlGuid%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetGuid%2A>|  
|varbinary|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|varchar|Chaîne<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>, <xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|xml|Xml|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A>|<xref:System.Data.DbType>|aucun|  
  
 \* Utilisez un accesseur typé spécifique si vous connaissez le type sous\-jacent de `sql_variant`.  
  
## Référence à la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]  
 Pour plus d'informations sur les types de données [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], consultez [Types de données \(Moteur de base de données\)](http://go.microsoft.com/fwlink/?LinkID=107468).  
  
## Voir aussi  
 [Types de données SQL Server et ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)   
 [Données binaires et de valeur élevée SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)   
 [Mappages de types de données dans ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [Configuration des paramètres et des types de données des paramètres](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)