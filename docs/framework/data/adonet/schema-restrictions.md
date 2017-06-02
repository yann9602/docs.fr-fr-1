---
title: "Restrictions de sch&#233;ma | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Restrictions de sch&#233;ma
Le second paramètre facultatif de la méthode **GetSchema** est constitué par les restrictions utilisées pour limiter la quantité d'informations de schéma retournées ; il est passé à la méthode **GetSchema** sous la forme d'un tableau de chaînes.  La position dans le tableau détermine les valeurs que vous pouvez passer et équivaut au numéro de restriction.  
  
 Par exemple, le tableau suivant décrit les restrictions prises en charge par la collection de schémas « Tables » utilisant le fournisseur de données .NET Framework pour SQL Server.  Des restrictions supplémentaires pour les collections de schémas SQL Server figurent à la fin de cette rubrique.  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|TABLE\_CATALOG|1|  
|Propriétaire|@Owner|TABLE\_SCHEMA|2|  
|Table|@Name|TABLE\_NAME|3|  
|TableType|@TableType|TABLE\_TYPE|4|  
  
## Spécification des valeurs de restriction  
 Pour utiliser l'une des restrictions de la collection de schémas « Tables », créez simplement un tableau de chaînes contenant quatre éléments, puis placez une valeur dans l'élément correspondant au numéro de restriction.  Par exemple, pour restreindre les tables retournées par la méthode **GetSchema** uniquement à celles du schéma « Sales », définissez le second élément du tableau sur « Sales » avant de le passer à la méthode **GetSchema**.  
  
> [!NOTE]
>  Les collections de restrictions pour `SqlClient` et `OracleClient` comportent une colonne `ParameterName` supplémentaire.  La colonne par défaut de la restriction est encore là pour la compatibilité ascendante, mais est désormais ignorée.  Il convient d'utiliser des requêtes paramétrées plutôt qu'un remplacement de chaîne afin de minimiser le risque d'attaque par injection SQL lors de la spécification de valeurs de restriction.  
  
> [!NOTE]
>  Le nombre d'éléments du tableau doit être inférieur ou égal au nombre de restrictions prises en charge pour la collection de schémas spécifiée, sans quoi une exception <xref:System.ArgumentException> est levée.  Il peut y avoir moins de restrictions que le nombre maximal de restrictions.  Les restrictions manquantes sont supposées avoir la valeur null \(aucune restriction\).  
  
 Vous pouvez interroger un fournisseur .NET Framework managé afin d'établir la liste des restrictions prises en charge en appelant la méthode **GetSchema** avec le nom de la collection de schémas de restrictions, « Restrictions ».  Cette opération retourne un <xref:System.Data.DataTable> contenant une liste des noms de collections, des noms de restriction, des valeurs de restriction par défaut et des numéros de restriction.  
  
### Exemple  
 Les exemples suivants montrent comment utiliser la méthode <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> du fournisseur de données .NET Framework pour la classe SQL Server <xref:System.Data.SqlClient.SqlConnection> afin d'extraire des informations de schéma sur toutes les tables contenues dans l'exemple de base de données **AdventureWorks** et de restreindre les informations retournées exclusivement aux tables du schéma « Sales » :  
  
 \[Visual Basic\]  
  
```  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
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
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
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
  
## Restrictions de schéma SQL Server  
 Les tableaux suivants énumèrent les restrictions pour les collections de schémas SQL Server.  
  
### Utilisateurs  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|User\_Name|@Name|name|1|  
  
### Bases de données  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Nom|@Name|Nom|1|  
  
### Tables  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|TABLE\_CATALOG|1|  
|Propriétaire|@Owner|TABLE\_SCHEMA|2|  
|Table|@Name|TABLE\_NAME|3|  
|TableType|@TableType|TABLE\_TYPE|4|  
  
### Columns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|TABLE\_CATALOG|1|  
|Propriétaire|@Owner|TABLE\_SCHEMA|2|  
|Table|@Table|TABLE\_NAME|3|  
|Colonne|@Column|COLUMN\_NAME|4|  
  
### StructuredTypeMembers  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|TABLE\_CATALOG|1|  
|Propriétaire|@Owner|TABLE\_SCHEMA|2|  
|Table|@Table|TABLE\_NAME|3|  
|Colonne|@Column|COLUMN\_NAME|4|  
  
### Vues  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|TABLE\_CATALOG|1|  
|Propriétaire|@Owner|TABLE\_SCHEMA|2|  
|Table|@Table|TABLE\_NAME|3|  
  
### ViewColumns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|VIEW\_CATALOG|1|  
|Propriétaire|@Owner|VIEW\_SCHEMA|2|  
|Table|@Table|VIEW\_NAME|3|  
|Colonne|@Column|COLUMN\_NAME|4|  
  
### ProcedureParameters  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|SPECIFIC\_CATALOG|1|  
|Propriétaire|@Owner|SPECIFIC\_SCHEMA|2|  
|Nom|@Name|SPECIFIC\_NAME|3|  
|Paramètre|@Parameter|PARAMETER\_NAME|4|  
  
### Procédures  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|SPECIFIC\_CATALOG|1|  
|Propriétaire|@Owner|SPECIFIC\_SCHEMA|2|  
|Nom|@Name|SPECIFIC\_NAME|3|  
|Type|@Type|ROUTINE\_TYPE|4|  
  
### IndexColumns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|db\_name\(\)|1|  
|Propriétaire|@Owner|user\_name\(\)|2|  
|Table|@Table|o.  name|3|  
|ConstraintName|@ConstraintName|x.  name|4|  
|Colonne|@Column|c.  name|5|  
  
### Index  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|db\_name\(\)|1|  
|Propriétaire|@Owner|user\_name\(\)|2|  
|Table|@Table|o.  name|3|  
  
### UserDefinedTypes  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|assembly\_name|@AssemblyName|assemblys.  name|1|  
|udt\_name|@UDTName|types.assembly\_class|2|  
  
### ForeignKeys  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|CONSTRAINT\_CATALOG|1|  
|Propriétaire|@Owner|CONSTRAINT\_SCHEMA|2|  
|Table|@Table|TABLE\_NAME|3|  
|Nom|@Name|CONSTRAINT\_NAME|4|  
  
## Restrictions de schéma SQL Server 2008  
 Les tableaux suivants répertorient les restrictions pour les collections de schémas SQL Server 2008.  Ces restrictions s'appliquent à partir de la version 3.5 SP1 de .NET Framework et SQL Server 2008.  Elles ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
### ColumnSetColumns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|TABLE\_CATALOG|1|  
|Propriétaire|@Owner|TABLE\_SCHEMA|2|  
|Table|@Table|TABLE\_NAME|3|  
  
### AllColumns  
  
|Nom de restriction|Nom du paramètre|Valeur par défaut de la restriction|Numéro de restriction|  
|------------------------|----------------------|-----------------------------------------|---------------------------|  
|Catalogue|@Catalog|TABLE\_CATALOG|1|  
|Propriétaire|@Owner|TABLE\_SCHEMA|2|  
|Table|@Table|TABLE\_NAME|3|  
|Colonne|@Column|COLUMN\_NAME|4|  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)