---
title: "Méthode Load"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e6c6ce0b722d901e38b728a710e3c49848fb918a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="the-load-method"></a>Méthode Load
Vous pouvez utiliser la méthode <xref:System.Data.DataTable.Load%2A> pour charger un objet <xref:System.Data.DataTable> de lignes d'une source de données. Il s’agit d’une méthode surchargée qui, dans sa forme la plus simple, accepte un seul paramètre, un **DataReader**. Dans cet écran, elle charge simplement le **DataTable** avec des lignes. Si vous le souhaitez, vous pouvez spécifier le **LoadOption** paramètre pour contrôler la façon dont les données sont ajoutées à la **DataTable**.  
  
 Le **LoadOption** paramètre est particulièrement utile dans les cas où la **DataTable** déjà contient des lignes de données, car il décrit les données entrantes à partir de la source de données seront combinées avec les données dans la table. Par exemple, **PreserveCurrentValues** (la valeur par défaut) Spécifie que dans les cas où une ligne est marquée en tant que **Added** dans les **DataTable**, le **Original** valeur ou chaque colonne est définie pour le contenu de la ligne correspondante à partir de la source de données. Le **actuel** valeur conservent les valeurs affectées lors de la ligne a été ajoutée et le **RowState** de la ligne a la valeur **a été modifié**.  
  
 Le tableau suivant donne une brève description des valeurs d'énumération <xref:System.Data.LoadOption>.  
  
|Valeur LoadOption|Description|  
|----------------------|-----------------|  
|**OverwriteRow**|Si des lignes entrantes ont la même **PrimaryKey** valeur comme une ligne figurant déjà dans le **DataTable**, le **d’origine** et **actuel** les valeurs de chaque colonne sont remplacées par les valeurs de la ligne entrante et la **RowState** est définie sur **Unchanged**.<br /><br /> Lignes de la source de données qui n’existent pas déjà dans le **DataTable** sont ajoutés avec un **RowState** valeur **Unchanged**.<br /><br /> Cette option actualise le contenu de la **DataTable** afin qu’elle corresponde à celle de la source de données.|  
|**PreserveCurrentValues (par défaut)**|Si des lignes entrantes ont la même **PrimaryKey** valeur comme une ligne figurant déjà dans le **DataTable**, le **d’origine** valeur est définie sur le contenu de la ligne entrante et la **Actuel** valeur n’est pas modifiée.<br /><br /> Si le **RowState** est **Added** ou **modifié**, elle est définie sur **modifié**.<br /><br /> Si le **RowState** a été **Deleted**, il reste **Deleted**.<br /><br /> Lignes de la source de données qui n’existent pas déjà dans le **DataTable** sont ajoutés et le **RowState** a la valeur **Unchanged**.|  
|**UpdateCurrentValues**|Si des lignes entrantes ont la même **PrimaryKey** valeur en tant que ligne figurant déjà dans le **DataTable**, le **actuel** valeur est copiée dans le **Original**valeur et le **actuel** valeur est alors définie sur le contenu de la ligne entrante.<br /><br /> Si le **RowState** dans les **DataTable** a été **Added**, le **RowState** reste **Added**. Pour les lignes marquées comme **modifié** ou **Deleted**, le **RowState** est **modifié**.<br /><br /> Lignes de la source de données qui n’existent pas déjà dans le **DataTable** sont ajoutés et le **RowState** a la valeur **Added**.|  
  
 L’exemple suivant utilise le **charge** méthode pour afficher une liste d’anniversaires des employés dans la **Northwind** base de données.  
  
```vb  
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
  
## <a name="see-also"></a>Voir aussi  
 [Manipulation des données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
