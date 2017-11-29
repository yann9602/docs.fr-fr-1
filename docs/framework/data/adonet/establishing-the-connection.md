---
title: "Établissement de la connexion"
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
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3d391796d42a4303db16ee01ceba57bac2e3fc84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="establishing-the-connection"></a>Établissement de la connexion
Pour vous connecter à Microsoft SQL Server, utilisez l'objet <xref:System.Data.SqlClient.SqlConnection> du fournisseur de données .NET Framework pour SQL Server. Pour vous connecter à une source de données OLE DB, utilisez l'objet <xref:System.Data.OleDb.OleDbConnection> du fournisseur de données .NET Framework pour OLE DB. Pour vous connecter à une source de données ODBC, utilisez l'objet <xref:System.Data.Odbc.OdbcConnection> du fournisseur de données .NET Framework pour ODBC. Pour vous connecter à une source de données Oracle, utilisez l'objet <xref:System.Data.OracleClient.OracleConnection> du fournisseur de données .NET Framework pour Oracle. Pour stocker de façon sécurisée et l’extraction des chaînes de connexion, consultez [protéger les informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Fermeture de connexions  
 Nous vous recommandons de toujours fermer la connexion lorsque vous avez fini de l'utiliser, de façon à ce qu'elle puisse être retournée au pool. Le bloc `Using` dans Visual Basic ou C# supprime automatiquement la connexion lorsque le code quitte le bloc, même dans le cas d'une exception non traitée. Consultez [à l’aide d’instruction](~/docs/csharp/language-reference/keywords/using-statement.md) et [à l’aide de l’instruction](~/docs/visual-basic/language-reference/statements/using-statement.md) pour plus d’informations.  
  
 Vous pouvez également utiliser la méthode `Close` ou `Dispose` de l'objet de connexion pour le fournisseur que vous utilisez. Les connexions qui ne sont pas explicitement fermées risquent de ne pas être ajoutées ni retournées au pool. Par exemple, une connexion devenue hors de portée mais qui n'a pas été explicitement fermée sera retournée au pool de connexion seulement si la taille maximale de celui-ci a été atteinte et si la connexion est toujours valide. Pour plus d’informations, consultez [OLE DB, ODBC et le regroupement de connexions Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
>  N’appelez pas `Close` ou `Dispose` sur un **connexion**, un **DataReader**, ou tout autre objet managé dans le `Finalize` méthode de votre classe. Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement. Si votre classe ne possède pas de ressource non managée, n'incluez pas une méthode `Finalize` dans la définition de classe. Pour plus d’informations, consultez [le Garbage Collection](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Les événements de connexion et de déconnexion ne seront pas déclenchés sur le serveur si une connexion est récupérée depuis le pool de connexions ou qu’elle est retournée au pool, car elle n’est pas réellement fermée lorsqu’elle est retournée au pool. Pour plus d’informations, consultez [le regroupement de connexion SQL Server (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Connexion à SQL Server  
 Le fournisseur de données .NET Framework pour SQL Server prend en charge un format de chaîne de connexion similaire à celui de la chaîne de connexion OLE DB (ADO). Pour obtenir les noms et les valeurs de format de chaîne valides, voir la propriété <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection>. Vous pouvez également utiliser la classe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer des chaînes de connexion valides du point de vue de la syntaxe au moment de l'exécution. Pour plus d’informations, consultez [générateurs de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une base de données SQL Server.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a>Sécurité intégrée et ASP.NET  
 La sécurité intégrée SQL Server (également appelée « connexions approuvées ») fournit une protection lors de la connexion à SQL Server car elle n'expose pas d'ID utilisateur et de mot de passe dans la chaîne de connexion, et elle est la méthode recommandée pour l'authentification d'une connexion. La sécurité intégrée utilise l'identité de sécurité active, ou jeton, du processus en cours d'exécution. Dans les applications bureautiques, il s'agit généralement de l'identité de l'utilisateur actuellement connecté.  
  
 Dans les applications ASP.NET, l'identité de sécurité peut être définie à l'aide d'une option parmi plusieurs options différentes. Pour mieux comprendre l’identité de sécurité qu’une application ASP.NET utilise lors de la connexion à SQL Server, consultez [emprunt d’identité ASP.NET](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [l’authentification ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), et [Comment : accès SQL La sécurité intégrée de serveur à l’aide de Windows](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Connexion à une source de données OLE DB  
 Le fournisseur de données .NET Framework pour OLE DB assure la connectivité aux sources de données exposées à l’aide de OLE DB (via SQLOLEDB, le fournisseur OLE DB pour SQL Server), à l’aide de la **OleDbConnection** objet.  
  
 Pour le fournisseur de données .NET Framework pour OLE DB, le format de chaîne de connexion est identique à celui utilisé dans ADO, avec les exceptions suivantes :  
  
-   Le **fournisseur** mot clé est obligatoire.  
  
-   Le **URL**, **fournisseur distant**, et **serveur distant** mots clés ne sont pas pris en charge.  
  
 Pour plus d'informations sur les chaînes de connexion OLE DB, voir la rubrique <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>. Vous pouvez également utiliser <xref:System.Data.OleDb.OleDbConnectionStringBuilder> pour créer des chaînes de connexion au moment de l'exécution.  
  
> [!NOTE]
>  Le **OleDbConnection** objet ne prend pas en charge la définition ou la récupération des propriétés dynamiques spécifiques à un fournisseur OLE DB. Seules les propriétés pouvant être passées dans la chaîne de connexion du fournisseur OLE DB sont prises en charge.  
  
 L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données OLE DB.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a>N'utilisez pas de fichiers UDL (Universal Data Link)  
 Il est possible de fournir des informations de connexion pour un **OleDbConnection** dans un fichier lien UDL (Universal Data) ; toutefois vous devez éviter cela. Les fichiers UDL n'étant pas chiffrés, ils exposent les informations de chaîne de connexion en texte brut. Comme un fichier UDL est une ressource basée sur un fichier externe pour votre application, il n'est pas possible de le sécuriser à l'aide du .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Connexion à une source de données ODBC  
 Le fournisseur de données .NET Framework pour ODBC assure la connectivité aux sources de données exposées via ODBC à l’aide du **OdbcConnection** objet.  
  
 Pour le fournisseur de données .NET Framework pour ODBC, le format de la chaîne de connexion est conçu pour être aussi proche que possible du format de la chaîne de connexion ODBC. Vous pouvez également fournir un nom de source de données ODBC (DSN). Pour plus d’informations sur la **OdbcConnection** , consultez le <xref:System.Data.Odbc.OdbcConnection>.  
  
 L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données ODBC.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a>Connexion à une source de données Oracle  
 Le fournisseur de données .NET Framework pour Oracle assure la connectivité aux sources de données Oracle à l’aide de la **OracleConnection** objet.  
  
 Pour le fournisseur de données .NET Framework pour Oracle, le format de la chaîne de connexion est conçu pour être aussi proche que possible du format de la chaîne de connexion du fournisseur de données OLE DB pour Oracle (MSDAORA). Pour plus d’informations sur la **OracleConnection**, consultez le <xref:System.Data.OracleClient.OracleConnection>.  
  
 L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données Oracle.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à une source de données](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Chaînes de connexion](../../../../docs/framework/data/adonet/connection-strings.md)  
 [OLE DB, ODBC et Oracle Connection le regroupement](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
