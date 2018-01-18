---
title: Obtention d'un DbProviderFactory
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
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a018447b790dde047bd76e1319a13aa3f77ffc61
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="obtaining-a-dbproviderfactory"></a>Obtention d'un DbProviderFactory
Le processus d'obtention d'un objet <xref:System.Data.Common.DbProviderFactory> implique de passer des informations à propos d'un fournisseur de données à la classe <xref:System.Data.Common.DbProviderFactories>. En fonction de ces informations, la méthode <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> crée une fabrique de fournisseurs fortement typée. Par exemple, pour créer un objet <xref:System.Data.SqlClient.SqlClientFactory>, vous pouvez passer à `GetFactory` une chaîne avec le nom du fournisseur spécifié comme « System.Data.SqlClient ». L'autre surcharge de `GetFactory` prend un objet <xref:System.Data.DataRow>. Une fois que vous avez créé la fabrique de fournisseurs, vous pouvez ensuite utiliser ses méthodes pour créer des objets supplémentaires. Parmi les méthodes d'un `SqlClientFactory`, citons <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> et <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
>  Les objets <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory> .NET Framework et les classes <xref:System.Data.OleDb.OleDbFactory> fournissent des fonctionnalités similaires.  
  
## <a name="registering-dbproviderfactories"></a>Inscription de DbProviderFactories  
 Chaque fournisseur de données .NET Framework qui prend en charge une classe de fabrique enregistre les informations de configuration dans le **DbProviderFactories** section de la **machine.config** fichier sur l’ordinateur local. Le fragment de fichier de configuration suivant montre la syntaxe et le format de <xref:System.Data.SqlClient>.  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 Le **invariant** attribut identifie le fournisseur de données sous-jacent. Cette syntaxe d'attribution de nom en trois parties est également utilisée lors de la création d'une fabrique et pour l'identification du fournisseur dans un fichier de configuration d'application de manière à ce que le nom du fournisseur, ainsi que sa chaîne de connexion associée, puissent être récupérés au moment de l'exécution.  
  
## <a name="retrieving-provider-information"></a>Récupération des informations relatives aux fournisseurs  
 Vous pouvez récupérer les informations relatives à tous les fournisseurs de données installés sur l'ordinateur local à l'aide de la méthode <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A>. Elle retourne un <xref:System.Data.DataTable> nommé **DbProviderFactories** qui contient les colonnes décrites dans le tableau suivant.  
  
|Numéro de colonne|Nom de la colonne|Résultat de l'exemple|Description|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Name**|Fournisseur de données SqlClient|Nom lisible pour le fournisseur de données|  
|1|**Description**|Fournisseur de données .NET Framework pour SqlServer|Description lisible pour le fournisseur de données|  
|2|**InvariantName**|System.Data.SqlClient|Nom qui peut être utilisé de façon programmée pour faire référence au fournisseur de données|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|Nom qualifié complet de la classe de fabrique, contenant suffisamment d'informations pour instancier l'objet|  
  
 Cette `DataTable` peuvent servir à autoriser un utilisateur à sélectionner un objet <xref:System.Data.DataRow> au moment de l'exécution. La `DataRow` sélectionnée puis peut être passée à la méthode <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> pour créer un objet <xref:System.Data.Common.DbProviderFactory> fortement typé. Un objet <xref:System.Data.DataRow> sélectionné peut être passé à la méthode `GetFactory` pour créer l'objet `DbProviderFactory` souhaité.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Liste des classes de fabrique de fournisseurs installées  
 Cet exemple montre comment utiliser la méthode <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> pour retourner un objet <xref:System.Data.DataTable> contenant des informations sur les fournisseurs installés. Le code itère au sein de chaque ligne dans la `DataTable`, en affichant des informations pour chaque fournisseur installé dans la fenêtre de console.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Utilisation de fichiers de configuration d'application pour stocker des informations sur les fabriques  
 Le modèle de conception permettant d’utiliser des fabriques implique de stocker des informations de chaîne de fournisseur et de connexion dans un fichier de configuration d’application, tel que **app.config** pour une application Windows, et **web.config**  pour une application ASP.NET.  
  
 Le fragment de fichier de configuration suivant montre comment enregistrer deux chaînes de connexion nommées : « NorthwindSQL » pour une connexion dans la base de données Northwind dans SQL Server, et « NorthwindAccess » pour une connexion dans la base de données Northwind dans Access/Jet. Le **invariant** nom est utilisé pour le **providerName** attribut.  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Récupération d'une chaîne de connexion à l'aide du nom du fournisseur  
 Pour créer une fabrique de fournisseurs, vous devez fournir une chaîne de connexion ainsi que le nom du fournisseur. Cet exemple montre comment extraire une chaîne de connexion à partir d’un fichier de configuration en passant le nom du fournisseur dans le format invariant «*System.Data.ProviderName*». Le code itère au sein de l'objet <xref:System.Configuration.ConnectionStringSettingsCollection>. Il retourne la propriété <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> en cas de réussite; sinon `null` (`Nothing` dans Visual Basic). S'il existe plusieurs entrées pour un fournisseur, la première occurrence trouvée est retournée. Pour plus d’informations et des exemples de la récupération des chaînes de connexion à partir des fichiers de configuration, consultez [les chaînes de connexion et les fichiers de Configuration](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
>  Une référence à `System.Configuration.dll` est requise pour que le code s'exécute.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Création des objets DbProviderFactory et DbConnection  
 Cet exemple montre comment créer un <xref:System.Data.Common.DbProviderFactory> et <xref:System.Data.Common.DbConnection> objet en lui passant le nom du fournisseur dans le format «*System.Data.ProviderName*» et une chaîne de connexion. Un objet `DbConnection` est retourné en cas de réussite ; `null` (`Nothing` dans Visual Basic) en cas d'erreur.  
  
 Le code obtient `DbProviderFactory` en appelant <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. La méthode <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> crée ensuite l'objet <xref:System.Data.Common.DbConnection> et la propriété <xref:System.Data.Common.DbConnection.ConnectionString%2A> prend la valeur de la chaîne de connexion.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Chaînes de connexion](../../../../docs/framework/data/adonet/connection-strings.md)  
 [À l’aide des Classes de Configuration](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
