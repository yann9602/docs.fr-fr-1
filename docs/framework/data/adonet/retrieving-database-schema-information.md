---
title: "R&#233;cup&#233;ration d&#39;informations de sch&#233;ma de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# R&#233;cup&#233;ration d&#39;informations de sch&#233;ma de base de donn&#233;es
L'obtention des informations de schéma à partir d'une base de données est effectuée avec le processus de découverte de schéma.  La découverte de schéma permet à des applications de demander que des fournisseurs managés trouvent et retournent des informations sur le schéma de base de données, également appelées *métadonnées*, d'une base de données déterminée.  Différents éléments de schéma de base de données tels que des tables, des colonnes et des procédures stockées, sont exposés à l'aide de collections de schémas.  Chaque collection de schémas contient une série d'informations de schéma spécifiques au fournisseur utilisé.  
  
 Chacun des fournisseurs .NET Framework managés implémente la méthode **GetSchema** dans la classe **Connection** et les informations de schéma retournées par la méthode **GetSchema** viennent sous la forme d'un <xref:System.Data.DataTable>.  La méthode **GetSchema** est une méthode surchargée qui fournit des paramètres facultatifs pour spécifier la collection de schémas à retourner et restreindre la quantité d'informations retournées.  
  
 Les fournisseurs de données .NET Framework pour OLE DB, ODBC, Oracle et SqlClient offrent une méthode **GetSchemaTable** qui retourne un objet DataTable décrivant les métadonnées des colonnes de **DataReader**.  
  
 Le fournisseur de données .NET Framework pour OLE DB expose également des informations de schéma à l'aide de la méthode <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> de l'objet <xref:System.Data.OleDb.OleDbConnection>.  **GetOleDbSchemaTable** prend comme arguments un <xref:System.Data.OleDb.OleDbSchemaGuid> qui identifie les informations de schéma à retourner et un tableau de restrictions sur ces colonnes retournées.  **GetOleDbSchemaTable** retourne un <xref:System.Data.DataTable> rempli d'informations de schéma requises.  
  
## Dans cette section  
 [GetSchema et collections de schémas](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 Décrit la méthode **GetSchema** et la manière dont il est possible de l'utiliser pour extraire et restreindre les informations de schéma d'une base de données.  
  
 Restrictions de schéma  
 Décrit les restrictions de schéma qui peuvent être utilisées avec **GetSchema**.  
  
 [Collections de schémas communes](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 Décrit toutes les collections de schémas communes prises en charge par tous les fournisseurs .NET Framework managés.  
  
 [Collections de schémas SQL Server](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 Décrit la collection de schémas prise en charge par le fournisseur .NET Framework pour SQL Server.  
  
 [Collections de schémas Oracle](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 Décrit la collection de schémas prise en charge par le fournisseur .NET Framework pour Oracle.  
  
 [Collections de schémas ODBC](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 Décrit les collections de schémas pour les pilotes ODBC.  
  
 [Collections de schémas OLE DB](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 Décrit les collections de schémas pour les fournisseurs OLE DB.  
  
## Référence  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la classe <xref:System.Data.Common.DbConnection>.  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la classe <xref:System.Data.Odbc.OdbcConnection>.  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la classe <xref:System.Data.OleDb.OleDbConnection>.  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la classe <xref:System.Data.OracleClient.OracleConnection>.  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 Décrit la méthode **GetSchema** de la classe <xref:System.Data.SqlClient.SqlConnection>.  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la classe <xref:System.Data.Common.DbDataReader>.  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la classe <xref:System.Data.Odbc.OdbcDataReader>.  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la classe <xref:System.Data.OleDb.OleDbDataReader>.  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la classe <xref:System.Data.OracleClient.OracleDataReader>.  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 Décrit la méthode **GetSchemaTable** de la classe <xref:System.Data.SqlClient.SqlDataReader>.  
  
## Voir aussi  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)