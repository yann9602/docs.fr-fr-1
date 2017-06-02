---
title: "Exemples de code ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Exemples de code ADO.NET
Les listings de code dans cette rubrique montrent comment récupérer des données d'une base de données à l'aide des technologies ADO.NET suivantes :  
  
-   Fournisseurs de données ADO.NET :  
  
    -   [SqlClient](#_SqlClient) (`System.Data.SqlClient`)  
  
    -   [OleDb](#_OleDb) (`System.Data.OleDb`)  
  
    -   [Odbc](#_Odbc) (`System.Data.Odbc`)  
  
    -   [OracleClient](#_OracleClient) (`System.Data.OracleClient`)  
  
-   ADO.NET Entity Framework :  
  
    -   [LINQ to Entities](#_LINQ)  
  
    -   [ObjectQuery typé](#_QBM)  
  
    -   [EntityClient](#_EntityClient) (`System.Data.EntityClient`)  
  
-   [LINQ to SQL](#_LINQ2SQL)  
  
## <a name="adonet-data-provider-examples"></a>Exemples de fournisseurs de données ADO.NET  
 Les listings de code suivants montrent comment récupérer des données d'une base de données à l'aide des fournisseurs de données ADO.NET. Les données sont retournées dans un `DataReader`. Pour plus d’informations, consultez [extraction de données à l’aide d’un DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).  
  
<a name="_SqlClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données `Northwind` Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Le code crée un <xref:System.Data.SqlClient.SqlCommand> pour sélectionner les lignes de la table Products, ajout d’un <xref:System.Data.SqlClient.SqlParameter> pour limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur du paramètre spécifié, dans ce cas 5. Le <xref:System.Data.SqlClient.SqlConnection> s’ouvre dans un `using` bloc, ce qui garantit que les ressources sont fermés et supprimés lorsque le code s’arrête. Le code exécute la commande en utilisant un <xref:System.Data.SqlClient.SqlDataReader>et affiche les résultats dans la fenêtre de console.  
  
  [DataWorks SampleApp.SqlClient#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient#1)]  
  
 [[Début]](#_TOP)  
  
<a name="_OleDb"></a>   
### <a name="oledb"></a>OleDb  
 Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données Northwind Microsoft Access. Le code crée un <xref:System.Data.OleDb.OleDbCommand> pour sélectionner les lignes de la table Products, ajout d’un <xref:System.Data.OleDb.OleDbParameter> pour limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur du paramètre spécifié, dans ce cas 5. Le <xref:System.Data.OleDb.OleDbConnection> s’ouvre dans un `using` bloc, ce qui garantit que les ressources sont fermés et supprimés lorsque le code s’arrête. Le code exécute la commande en utilisant un <xref:System.Data.OleDb.OleDbDataReader>et affiche les résultats dans la fenêtre de console.  
  
  [DataWorks SampleApp.OleDb#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb#1)]  
  
 [[Début]](#_TOP)  
  
<a name="_Odbc"></a>   
### <a name="odbc"></a>Odbc  
 Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données Northwind Microsoft Access. Le code crée un <xref:System.Data.Odbc.OdbcCommand> pour sélectionner les lignes de la table Products, ajout d’un <xref:System.Data.Odbc.OdbcParameter> pour limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur du paramètre spécifié, dans ce cas 5. Le <xref:System.Data.Odbc.OdbcConnection> s’ouvre dans un `using` bloc, ce qui garantit que les ressources sont fermés et supprimés lorsque le code s’arrête. L’exécute la commande en utilisant un <xref:System.Data.Odbc.OdbcDataReader>et affiche les résultats dans la fenêtre de console.  
  
<!-- TODO: review snippet reference  [!CODE [DataWorksSampleApp.Odbc#1](DataWorksSampleApp.Odbc#1)]  -->  
  
 [[Début]](#_TOP)  
  
<a name="_OracleClient"></a>   
### <a name="oracleclient"></a>OracleClient  
 Le code de cet exemple suppose une connexion à DEMO.CUSTOMER sur un serveur Oracle. Vous devez également ajouter une référence au fichier System.Data.OracleClient.dll. Le code retourne les données dans un <xref:System.Data.OracleClient.OracleDataReader>.  
  
  [DataWorks SampleApp.Oracle#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle#1)]  
  
 [[Début]](#_TOP)  
  
## <a name="entity-framework-examples"></a>Exemples d’Entity Framework  
 Les listings de code suivants montrent comment récupérer des données d'une source de données en interrogeant des entités d'un modèle de données d'entité (EDM, Entity Data Model). Ces exemples utilisent la [modèle Northwind](http://msdn.microsoft.com/fr-fr/74521f8c-e974-48cb-8858-c08deff52638). Pour plus d’informations, consultez [présentation d’Entity Framework](../../../../docs/framework/data/adonet/ef/overview.md).  
  
<a name="_LINQ"></a>   
### <a name="linq-to-entities"></a>LINQ to Entities  
 Le code dans cet exemple utilise une requête LINQ pour retourner des données en tant qu'objets Categories, qui sont projetés comme type anonyme contenant uniquement les propriétés CategoryID et CategoryName. Pour plus d’informations, consultez [LINQ to Entities présentation](http://msdn.microsoft.com/fr-fr/86d87a27-c17a-45ac-b28d-72c8500333c6).  
  
```  
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
  
 En C# :  
  
```  
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
  
 [[Début]](#_TOP)  
  
<a name="_QBM"></a>   
### <a name="typed-objectquery"></a>ObjectQuery typé  
 Le code de cet exemple utilise un <xref:System.Data.Objects.ObjectQuery%601> pour retourner des données en tant qu’objets Categories. Pour plus d’informations, consultez [requêtes d’objet](http://msdn.microsoft.com/fr-fr/0768033c-876f-471d-85d5-264884349276).  
  
```  
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
  
 En C# :  
  
```  
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
  
 [[Début]](#_TOP)  
  
<a name="_EntityClient"></a>   
### <a name="entityclient"></a>EntityClient  
 Le code de cet exemple utilise un <xref:System.Data.EntityClient.EntityCommand> pour exécuter une requête Entity SQL. Cette requête retourne une liste d'enregistrements représentant des instances du type d'entité Categories. Un <xref:System.Data.EntityClient.EntityDataReader> est utilisé pour accéder aux enregistrements de données dans le jeu de résultats. Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
```  
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
  
 En C#  
  
```  
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
  
 [[Début]](#_TOP)  
  
<a name="_LINQ2SQL"></a>   
## <a name="linq-to-sql"></a>LINQ to SQL  
 Le code dans cet exemple utilise une requête LINQ pour retourner des données en tant qu'objets Categories, qui sont projetés comme type anonyme contenant uniquement les propriétés CategoryID et CategoryName. Cet exemple est basé sur le contexte de données Northwind. Pour plus d’informations, consultez [mise en route](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).  
  
```  
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
  
 En C# :  
  
```  
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
  
 [[Début]](#_TOP)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble d’ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)   
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Création d’Applications de données](../Topic/Creating%20Data%20Applications.md)   
 [Interrogation d’un modèle EDM (tâches Entity Framework)](http://msdn.microsoft.com/fr-fr/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)   
 [Comment : exécuter une requête qui retourne des objets de Type anonyme](http://msdn.microsoft.com/fr-fr/3b264025-e911-4d73-90ce-992d2b9d189d)   
 [Fournisseurs managés ADO.NET et centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)