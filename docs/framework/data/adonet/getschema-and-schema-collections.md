---
title: "GetSchema et collections de sch&#233;mas | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# GetSchema et collections de sch&#233;mas
Les classes **Connection** dans chacun des fournisseurs .NET Framework managés implémentent une méthode **GetSchema** qui est utilisée pour extraire des informations de schéma sur la base de données actuellement connectée, et les informations de schéma retournées par la méthode **GetSchema** se présentent sous la forme d'un <xref:System.Data.DataTable>.  La méthode **GetSchema** est une méthode surchargée qui fournit des paramètres facultatifs pour spécifier la collection de schémas à retourner et restreindre la quantité d'informations retournées.  
  
## Spécification des collections de schémas  
 Le premier paramètre facultatif de la méthode **GetSchema** est le nom de collection spécifié comme chaîne.  Il y a deux types de collection de schémas : les collections de schémas communes qui sont communes à tous les fournisseurs et les collections de schémas spécifiques qui sont spécifiques à chaque fournisseur.  
  
 Vous pouvez interroger un fournisseur .NET Framework managé afin d'établir la liste des collections de schémas prises en charge en appelant la méthode **GetSchema** sans argument ou avec le nom de collection de schémas « MetaDataCollections ».  Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu'elles prennent en charge et le nombre d'éléments d'identification qu'elles utilisent.  
  
### Exemple d'extraction de collections de schémas  
 Les exemples suivants montrent comment utiliser la méthode <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> du fournisseur de données .NET Framework pour la classe SQL Server <xref:System.Data.SqlClient.SqlConnection> afin d'extraire des informations de schéma sur toutes les tables contenues dans l'exemple de base de données **AdventureWorks** :  
  
 \[Visual Basic\]  
  
```  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,    
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
   End Sub  
End Module  
```  
  
 \[C\#\]  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
   Console.WriteLine("Press any key to continue.");  
   Console.ReadKey();  
   }  
 }  
  
  private static string GetConnectionString()  
  {  
   // To avoid storing the connection string in your code,  
   // you can retrieve it from a configuration file.  
   return "Data Source=(local);Database=AdventureWorks;" +  
      "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## Voir aussi  
 [Récupération d'informations de schéma de base de données](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)