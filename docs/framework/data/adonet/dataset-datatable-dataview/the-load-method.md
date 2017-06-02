---
title: "M&#233;thode Load | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# M&#233;thode Load
Vous pouvez utiliser la méthode <xref:System.Data.DataTable.Load%2A> pour charger un objet <xref:System.Data.DataTable> de lignes d'une source de données.  Il s'agit d'une méthode surchargée qui, sous sa forme la plus simple, accepte un simple paramètre, **DataReader**.  Sous cette forme, elle charge simplement le **DataTable** de lignes.  À titre facultatif, vous pouvez spécifier le paramètre **LoadOption** pour contrôler la manière dont les données sont ajoutées au **DataTable**.  
  
 Le paramètre **LoadOption** est particulièrement utile dans les cas où le **DataTable** contient déjà des lignes de données car il décrit la manière dont des données entrantes en provenance de la source de données seront combinées aux données figurant déjà dans la table.  Par exemple, **PreserveCurrentValues** \(paramètre par défaut\) spécifie que, dans les cas où une ligne est marquée comme **Added** dans le **DataTable**, la valeur **Original** de chaque colonne correspond au contenu de la ligne correspondante dans la source de données.  La valeur **Current** conservera les valeurs affectées lors de l'ajout de la ligne et le **RowState** de la ligne aura la valeur **Changed**.  
  
 Le tableau suivant donne une brève description des valeurs d'énumération <xref:System.Data.LoadOption>.  
  
|Valeur LoadOption|Description|  
|-----------------------|-----------------|  
|**OverwriteRow**|Si des lignes entrantes ont la même valeur **PrimaryKey** qu'une ligne figurant déjà dans le **DataTable**, les valeurs **Original** et **Current** de chaque colonne sont remplacées par les valeurs de la ligne entrante et la propriété **RowState** prend la valeur **Unchanged**.<br /><br /> Les lignes de la source de données qui n'existent pas encore dans le **DataTable** sont ajoutées avec une valeur de **RowState** **Unchanged**.<br /><br /> Cette option actualise le contenu du **DataTable** de façon à ce qu'il corresponde à celui de la source de données.|  
|**PreserveCurrentValues \(par défaut\)**|Si des lignes entrantes ont la même valeur **PrimaryKey** qu'une ligne figurant déjà dans le **DataTable**, la valeur **Original** est le contenu de la ligne entrante et la valeur **Current**  n'est pas modifiée.<br /><br /> Si le **RowState** est **Added** ou **Modified**, il prend la valeur **Modified**.<br /><br /> Si le **RowState** était **Deleted**, il conserve la valeur **Deleted**.<br /><br /> Les lignes de la source de données qui n'existent pas encore dans le **DataTable** sont ajoutées avec une valeur de **RowState** **Unchanged**.|  
|**UpdateCurrentValues**|Si des lignes entrantes ont la même valeur **PrimaryKey** qu'une ligne figurant déjà dans le **DataTable**, la valeur **Current** est copiée dans la valeur **Original** et la valeur **Current** est le contenu de la ligne entrante.<br /><br /> Si le **RowState** dans le **DataTable** était **Added**, le **RowState** conserve la valeur **Added**.  Pour les lignes marquées comme **Modified** ou **Deleted**, le **RowState** a la valeur **Modified**.<br /><br /> Les lignes de la source de données qui n'existent pas encore dans le **DataTable** sont ajoutées et la valeur de **RowState** est **Added**.|  
  
 L'exemple suivant utilise la méthode **Load** pour afficher une liste d'anniversaires des employés dans la base de données **Northwind**.  
  
 \[Visual Basic\]  
  
```  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## Voir aussi  
 [Manipulation de données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)