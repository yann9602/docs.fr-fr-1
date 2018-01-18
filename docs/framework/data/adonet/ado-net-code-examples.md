---
title: Exemples de code ADO.NET
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-ado
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ea26b4297f587a449b8484947257081e0d11906c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-code-examples"></a>Exemples de code ADO.NET
Les listings de code dans cette rubrique montrent comment récupérer des données d'une base de données à l'aide des technologies ADO.NET suivantes :

- Fournisseurs de données ADO.NET :

  - [SqlClient](#sqlclient) (`System.Data.SqlClient`)

  - [OleDb](#oledb) (`System.Data.OleDb`)

  - [Odbc](#odbc) (`System.Data.Odbc`)

  - [OracleClient](#oracleclient) (`System.Data.OracleClient`)

- ADO.NET Entity Framework :

  - [LINQ to Entities](#linq-to-entities)

  - [ObjectQuery typé](#typed-objectquery)

  - [EntityClient](#entityclient) (`System.Data.EntityClient`)

- [LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>Exemples de fournisseurs de données ADO.NET
Les listings de code suivants montrent comment récupérer des données d'une base de données à l'aide des fournisseurs de données ADO.NET. Les données sont retournées dans un `DataReader`. Pour plus d’informations, consultez [la récupération des données à l’aide d’un DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).

### <a name="sqlclient"></a>SqlClient
Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données `Northwind` Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Le code crée une <xref:System.Data.SqlClient.SqlCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.SqlClient.SqlParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5. Le <xref:System.Data.SqlClient.SqlConnection> est ouvert dans un `using` bloc, ce qui garantit que les ressources sont fermés et supprimés lorsque le code s’arrête. Le code exécute la commande à l'aide d'un <xref:System.Data.SqlClient.SqlDataReader> et affiche les résultats dans la fenêtre de console.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OleDb
Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données Northwind Microsoft Access. Le code crée une <xref:System.Data.OleDb.OleDbCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.OleDb.OleDbParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5. <xref:System.Data.OleDb.OleDbConnection> s'ouvre dans un bloc `using`, ce qui garantit la fermeture et la suppression des ressources lorsque le code s'arrête. Le code exécute la commande à l'aide d'un <xref:System.Data.OleDb.OleDbDataReader> et affiche les résultats dans la fenêtre de console.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données Northwind Microsoft Access. Le code crée une <xref:System.Data.Odbc.OdbcCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.Odbc.OdbcParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5. Le <xref:System.Data.Odbc.OdbcConnection> est ouvert dans un `using` bloc, ce qui garantit que les ressources sont fermés et supprimés lorsque le code s’arrête. Le code exécute la commande à l'aide d'un <xref:System.Data.Odbc.OdbcDataReader> et affiche les résultats dans la fenêtre de console.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a>OracleClient
Le code de cet exemple suppose une connexion à DEMO.CUSTOMER sur un serveur Oracle. Vous devez également ajouter une référence au fichier System.Data.OracleClient.dll. Ce code retourne les données dans un objet <xref:System.Data.OracleClient.OracleDataReader>.

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Exemples d’Entity Framework
Les listings de code suivants montrent comment récupérer des données d'une source de données en interrogeant des entités d'un modèle de données d'entité (EDM, Entity Data Model). Ces exemples utilisent la [modèle Northwind](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638). Pour plus d’informations, consultez [présentation d’Entity Framework](../../../../docs/framework/data/adonet/ef/overview.md).

### <a name="linq-to-entities"></a>LINQ to Entities
Le code dans cet exemple utilise une requête LINQ pour retourner des données en tant qu'objets Categories, qui sont projetés comme type anonyme contenant uniquement les propriétés CategoryID et CategoryName. Pour plus d’informations, consultez [LINQ pour une vue d’ensemble des entités](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a>ObjectQuery typé
Le code dans cet exemple utilise un <xref:System.Data.Objects.ObjectQuery%601> pour retourner des données en tant qu'objets Categories. Pour plus d’informations, consultez [requêtes d’objet](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in 
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a>EntityClient
Le code dans cet exemple utilise une <xref:System.Data.EntityClient.EntityCommand> pour exécuter une requête Entity SQL. Cette requête retourne une liste d'enregistrements représentant des instances du type d'entité Categories. Un <xref:System.Data.EntityClient.EntityDataReader> est utilisé pour accéder aux enregistrements de données du jeu de résultats. Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName 
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr = 
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using 
    End Sub
End Class
```

## <a name="linq-to-sql"></a>LINQ to SQL
Le code dans cet exemple utilise une requête LINQ pour retourner des données en tant qu'objets Categories, qui sont projetés comme type anonyme contenant uniquement les propriétés CategoryID et CategoryName. Cet exemple est basé sur le contexte de données Northwind. Pour plus d’informations, consultez [Bien commencer avec le .NET Framework](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using 
    End Sub
End Class
```

## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble d’ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Création d’applications de données](http://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [Interrogation d’un Entity Data Model (tâches Entity Framework)](http://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [Comment : exécuter une requête qui retourne des objets de Type anonyme](http://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)  
