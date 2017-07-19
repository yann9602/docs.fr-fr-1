---
title: "Modification de donn&#233;es &#224; l&#39;aide de proc&#233;dures stock&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Modification de donn&#233;es &#224; l&#39;aide de proc&#233;dures stock&#233;es)
Les procédures stockées peuvent accepter des données en tant que paramètres d'entrée et retourner des données en tant que paramètres de sortie, jeux de résultats et valeurs de retour.  L'exemple ci\-dessous montre comment ADO.NET envoie et reçoit des paramètres d'entrée, des paramètres de sortie et des valeurs de retour.  L'exemple insère un nouvel enregistrement dans une table où la colonne de clé primaire est une colonne d'identité dans une base de données SQL Server.  
  
> [!NOTE]
>  Si vous utilisez des procédures stockées SQL Server pour modifier ou supprimer des données à l'aide de <xref:System.Data.SqlClient.SqlDataAdapter>, assurez\-vous que vous n'utilisez pas SET NOCOUNT ON dans la définition de procédure stockée.  En effet, le nombre de lignes affectées retourné serait alors la valeur zéro, ce que `DataAdapter` interprète comme un conflit d'accès concurrentiel.  Dans ce cas, l'exception <xref:System.Data.DBConcurrencyException> est levée.  
  
## Exemple  
 L'exemple utilise la procédure stockée suivante pour insérer une nouvelle catégorie dans la table **Northwind** **Categories**.  La procédure stockée prend la valeur dans la colonne **CategoryName** en tant que paramètre d'entrée et utilise la fonction SCOPE\_IDENTITY\(\) pour récupérer la nouvelle valeur du champ d'identité **CategoryID** et la retourner dans un paramètre de sortie.  L'instruction RETURN utilise la fonction @@ROWCOUNT pour retourner le nombre de lignes insérées.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 L'exemple de code suivant utilise la procédure stockée `InsertCategory` présentée ci\-dessus comme source pour <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> de <xref:System.Data.SqlClient.SqlDataAdapter>.  Le paramètre de sortie `@Identity` se reflète dans <xref:System.Data.DataSet> après que l'enregistrement a été inséré dans la base de données lors de l'appel de la méthode `Update` de <xref:System.Data.SqlClient.SqlDataAdapter>.  Le code récupère également la valeur de retour.  
  
> [!NOTE]
>  Lors de l'utilisation du <xref:System.Data.OleDb.OleDbDataAdapter>, vous devez spécifier des paramètres avec un <xref:System.Data.ParameterDirection> de **ReturnValue** avant les autres paramètres.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## Voir aussi  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [Exécution d'une commande](../../../../docs/framework/data/adonet/executing-a-command.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)