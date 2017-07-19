---
title: "Obtention d&#39;une valeur unique &#224; partir d&#39;une base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Obtention d&#39;une valeur unique &#224; partir d&#39;une base de donn&#233;es
Vous aurez peut\-être besoin de retourner des informations de base de données qui sont simplement une valeur unique plutôt qu'une table ou un flux de données.  Par exemple, vous souhaitez éventuellement retourner le résultat d'une fonction d'agrégation telle que COUNT\(\*\), SUM\(Price\) ou AVG\(Quantity\).  L'objet **Command** fournit la fonctionnalité permettant de retourner des valeurs uniques à l'aide de la méthode **ExecuteScalar**.  La méthode **ExecuteScalar** retourne sous forme de valeur scalaire la valeur de la première colonne de la première ligne du jeu de résultats.  
  
 L'exemple de code suivant insère une nouvelle valeur dans la base de données en utilisant un objet <xref:System.Data.SqlClient.SqlCommand>.  La méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> est utilisée pour retourner la valeur de la colonne d'identité de l'enregistrement inséré.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## Voir aussi  
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [Exécution d'une commande](../../../../docs/framework/data/adonet/executing-a-command.md)   
 [DbConnection, DbCommand et DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)