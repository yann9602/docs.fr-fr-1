---
title: "Opérations uniques de copie en bloc"
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
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 001bd24d46d0106887ad693534c51d152eedfb1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="single-bulk-copy-operations"></a>Opérations uniques de copie en bloc
L'approche la plus simple de l'exécution d'une opération de copie en bloc SQL Server consiste à exécuter une opération unique sur une base de données. Par défaut, une opération de copie en bloc s'effectue comme une opération isolée : l'opération de copie se produit de façon non traitée, sans possibilité de restauration.  
  
> [!NOTE]
>  Si vous devez restaurer tout ou partie de la copie en bloc en cas d'erreur, vous pouvez soit utiliser une transaction <xref:System.Data.SqlClient.SqlBulkCopy> managée, soit effectuer une opération de copie en bloc à l'intérieur d'une transaction existante. **SqlBulkCopy** fonctionne également avec <xref:System.Transactions> si la connexion est inscrite (implicitement ou explicitement) dans un **System.Transactions** transaction.  
>   
>  Pour plus d’informations, consultez [Transaction et opérations de copie en bloc](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 Les étapes générales pour l'exécution d'une opération de copie en bloc sont les suivantes :  
  
1.  Connectez-vous au serveur source et obtenez les données à copier. Les données peuvent également provenir d'autres sources si elles peuvent être extraites d'un objet <xref:System.Data.IDataReader> ou <xref:System.Data.DataTable>.  
  
2.  Se connecter au serveur de destination (à moins que vous souhaitiez **SqlBulkCopy** pour établir une connexion pour vous).  
  
3.  Créez un objet <xref:System.Data.SqlClient.SqlBulkCopy> en définissant toutes les propriétés nécessaires.  
  
4.  Définir le **DestinationTableName** opération d’insertion de propriété pour indiquer la table cible pour le bloc.  
  
5.  Appelez l’une de le **WriteToServer** méthodes.  
  
6.  Si vous le souhaitez, mettre à jour les propriétés et appelez **WriteToServer** si nécessaire.  
  
7.  Appelez <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A> ou enveloppez les opérations de copie en bloc dans une instruction `Using`.  
  
> [!CAUTION]
>  Il est recommandé que les types de données des colonnes source et cible correspondent. Si les types de données ne correspondent pas, **SqlBulkCopy** tente de convertir chaque valeur source pour le type de données cible, en utilisant les règles employées par <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Les conversions peuvent affecter les performances et générer des erreurs inattendues. Par exemple, un type de données `Double` peut généralement être converti en un type de données `Decimal`, mais pas toujours.  
  
## <a name="example"></a>Exemple  
 L'application console suivante montre comment charger des données à l'aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy>. Dans cet exemple, un <xref:System.Data.SqlClient.SqlDataReader> est utilisé pour copier des données à partir de la **Production.Product** de table dans le [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] **AdventureWorks** base de données dans une table semblable dans la même base de données.  
  
> [!IMPORTANT]
>  Cet exemple ne s’exécutera pas à moins que vous ayez créé les tables de travail comme décrit dans [configuration exemple de copie en bloc](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ce code est fourni pour illustrer la syntaxe pour l’utilisation de **SqlBulkCopy** uniquement. Si les tables sources et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d'utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Exécution d'une opération de copie en bloc à l'aide de Transact-SQL et de la classe Command  
 L'exemple suivant illustre la manière d'utiliser la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> pour exécuter l'instruction BULK INSERT.  
  
> [!NOTE]
>  Le chemin d'accès au fichier de la source de données est relatif par rapport au serveur. Le processus serveur doit avoir accès à ce chemin d’accès pour que l’opération de copie en bloc réussisse.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Opérations de copie en bloc dans SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
