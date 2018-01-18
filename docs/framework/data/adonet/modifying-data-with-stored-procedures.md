---
title: "Modification des données avec les procédures stockées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: dbc928e70ee7762b494d7efe60bc52b9f9783013
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="modifying-data-with-stored-procedures"></a>Modification des données avec les procédures stockées
Les procédures stockées peuvent accepter des données en tant que paramètres d'entrée et retourner des données en tant que paramètres de sortie, jeux de résultats et valeurs de retour. L'exemple ci-dessous montre comment ADO.NET envoie et reçoit des paramètres d'entrée, des paramètres de sortie et des valeurs de retour. L'exemple insère un nouvel enregistrement dans une table où la colonne de clé primaire est une colonne d'identité dans une base de données SQL Server.  
  
> [!NOTE]
>  Si vous utilisez des procédures stockées SQL Server pour modifier ou supprimer des données à l'aide de <xref:System.Data.SqlClient.SqlDataAdapter>, assurez-vous que vous n'utilisez pas SET NOCOUNT ON dans la définition de procédure stockée. En effet, le nombre de lignes affectées retourné serait alors la valeur zéro, ce que `DataAdapter` interprète comme un conflit d'accès concurrentiel. Dans ce cas, l'exception <xref:System.Data.DBConcurrencyException> est levée.  
  
## <a name="example"></a>Exemple  
 L’exemple utilise la procédure stockée suivante pour insérer une nouvelle catégorie dans le **Northwind** **catégories** table. La procédure stockée prend la valeur de la **CategoryName** colonne en tant que paramètre d’entrée et utilise le SCOPE_IDENTITY() à récupérer la nouvelle valeur du champ d’identité, la fonction **CategoryID**et le retourner dans un paramètre de sortie. L’instruction RETURN utilise la @@ROWCOUNT fonction pour retourner le nombre de lignes insérées.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 L'exemple de code suivant utilise la procédure stockée `InsertCategory` présentée ci-dessus comme source pour <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> de <xref:System.Data.SqlClient.SqlDataAdapter>. Le paramètre de sortie `@Identity` se reflète dans <xref:System.Data.DataSet> après que l'enregistrement a été inséré dans la base de données lors de l'appel de la méthode `Update` de <xref:System.Data.SqlClient.SqlDataAdapter>. Le code récupère également la valeur de retour.  
  
> [!NOTE]
>  Lorsque vous utilisez la <xref:System.Data.OleDb.OleDbDataAdapter>, vous devez spécifier des paramètres avec un <xref:System.Data.ParameterDirection> de **ReturnValue** avant les autres paramètres.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Exécution d’une commande](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
