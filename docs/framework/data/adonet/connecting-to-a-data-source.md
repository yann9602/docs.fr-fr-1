---
title: "Connexion &#224; une source de donn&#233;es dans ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Connexion &#224; une source de donn&#233;es dans ADO.NET
Dans ADO.NET, vous utilisez un objet **Connection** pour vous connecter à une source de données spécifique en fournissant les informations d'authentification nécessaires dans une chaîne de connexion.  L'objet **Connection** que vous utilisez dépend du type de la source de données.  
  
 Chaque fournisseur de données .NET Framework inclut dans le .NET Framework comprend un objet <xref:System.Data.Common.DbConnection> : le fournisseur de données .ENT Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbConnection>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlConnection>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcConnection> et le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleConnection>.  
  
## Dans cette section  
 [Établissement de la connexion](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Décrit comment utiliser un objet **Connection** pour établir une connexion à une source de données.  
  
 [Événements de connexion](../../../../docs/framework/data/adonet/connection-events.md)  
 Décrit comment utiliser un événement **InfoMessage** pour extraire des messages d'information d'une source de données.  
  
## Voir aussi  
 [Chaînes de connexion](../../../../docs/framework/data/adonet/connection-strings.md)   
 [Regroupement de connexions](../../../../docs/framework/data/adonet/connection-pooling.md)   
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [Transactions et concurrence](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)