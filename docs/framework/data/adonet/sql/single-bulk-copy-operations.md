---
title: "Op&#233;ration de copie en bloc uniques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Op&#233;ration de copie en bloc uniques
L'approche la plus simple de l'exécution d'une opération de copie en bloc SQL Server consiste à exécuter une opération unique sur une base de données.  Par défaut, une opération de copie en bloc s'effectue comme une opération isolée : l'opération de copie se produit de façon non traitée, sans possibilité de restauration.  
  
> [!NOTE]
>  Si vous devez restaurer tout ou partie de la copie en bloc en cas d'erreur, vous pouvez soit utiliser une transaction <xref:System.Data.SqlClient.SqlBulkCopy> managée, soit effectuer une opération de copie en bloc à l'intérieur d'une transaction existante.  **SqlBulkCopy** fonctionne également avec <xref:System.Transactions> si la connexion est inscrite \(implicitement ou explicitement\) dans une transaction **System.Transactions**.  
>   
>  Pour plus d'informations, consultez [Transaction et opérations de copie en bloc](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 Les étapes générales pour l'exécution d'une opération de copie en bloc sont les suivantes :  
  
1.  Connectez\-vous au serveur source et obtenez les données à copier.  Les données peuvent également provenir d'autres sources si elles peuvent être extraites d'un objet <xref:System.Data.IDataReader> ou <xref:System.Data.DataTable>.  
  
2.  Connectez\-vous au serveur de destination \(à moins que vous souhaitiez que **SqlBulkCopy** établisse une connexion à votre place\).  
  
3.  Créez un objet <xref:System.Data.SqlClient.SqlBulkCopy> en définissant toutes les propriétés nécessaires.  
  
4.  Définissez la propriété **DestinationTableName** pour indiquer la table cible pour l'opération d'insertion en bloc.  
  
5.  Appelez l'une des méthodes **WriteToServer**.  
  
6.  À titre facultatif, mettez à jour les propriétés et appelez de nouveau la méthode **WriteToServer** si nécessaire.  
  
7.  Appelez <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A> ou enveloppez les opérations de copie en bloc dans une instruction `Using`.  
  
> [!CAUTION]
>  Il est recommandé que les types de données des colonnes source et cible correspondent.  Si les types de données ne correspondent pas, **SqlBulkCopy** tente de convertir chaque valeur source vers le type de données cible en utilisant les règles employées par <xref:System.Data.SqlClient.SqlParameter.Value%2A>.  Les conversions peuvent affecter les performances et générer des erreurs inattendues.  Par exemple, un type de données `Double` peut généralement être converti en un type de données `Decimal`, mais pas toujours.  
  
## Exemple  
 L'application console suivante montre comment charger des données à l'aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy>.  Dans cet exemple, <xref:System.Data.SqlClient.SqlDataReader> est utilisé pour copier des données de la table **Production.Product** dans la base de données **AdventureWorks** [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] vers une table semblable dans la même base de données.  
  
> [!IMPORTANT]
>  Cet exemple ne s'exécutera pas à moins que vous ayez créé les tables de travail comme décrit dans la rubrique [Configuration de l'exemple de copie en bloc](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).  Ce code est fourni uniquement pour illustrer la syntaxe de l'utilisation de **SqlBulkCopy**.  Si les tables sources et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact\-SQL `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## Exécution d'une opération de copie en bloc à l'aide de Transact\-SQL et de la classe Command  
 L'exemple suivant illustre la manière d'utiliser la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> pour exécuter l'instruction BULK INSERT.  
  
> [!NOTE]
>  Le chemin d'accès au fichier de la source de données est relatif par rapport au serveur.  Le processus serveur doit avoir accès à ce chemin d'accès pour que l'opération de copie en bloc réussisse.  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## Voir aussi  
 [Opérations de copie en bloc dans SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)