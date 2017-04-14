---
title: "Modifications d&#39;un DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Modifications d&#39;un DataTable
Lorsque vous modifiez les valeurs de colonne d'un objet <xref:System.Data.DataRow>, les modifications sont immédiatement placées dans l'état actuel de la ligne.  L'objet <xref:System.Data.DataRowState> prend ensuite la valeur **Modified**, et les modifications sont acceptées ou rejetées à l'aide de la méthode <xref:System.Data.DataRow.AcceptChanges%2A> ou <xref:System.Data.DataRow.RejectChanges%2A> du **DataRow**.  Le **DataRow** vous offre également trois méthodes pour suspendre l'état de la ligne pendant sa modification.  Ces méthodes sont <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> et <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Lorsque vous modifiez directement les valeurs de colonne dans un **DataRow**, celui\-ci les gère à l'aide des versions de ligne **Current**, **Default** et **Original**.  En plus de ces trois versions de ligne, les méthodes **BeginEdit**, **EndEdit** et **CancelEdit** en utilisent une quatrième : **Proposed**.  Pour plus d'informations sur les versions de lignes, voir [États et versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 La version de ligne **Proposed** existe au cours d'une opération de modification commencée en appelant **BeginEdit** et terminée en utilisant **EndEdit** ou **CancelEdit** ou en appelant **AcceptChanges** ou **RejectChanges**.  
  
 Pendant l'opération de modification, vous pouvez appliquer la logique de validation à des colonnes individuelles en évaluant le **ProposedValue** dans l'événement **ColumnChanged** du **DataTable**.  L'événement **ColumnChanged** contient **DataColumnChangeEventArgs** qui conserve une référence à la colonne en cours de modification et à **ProposedValue**.  Après avoir évalué la valeur proposée, vous pouvez la modifier ou annuler la modification.  Après la modification, la ligne quitte l'état **Proposed**.  
  
 Vous pouvez confirmer les modifications en appelant **EndEdit** ou les annuler en appelant **CancelEdit**.  Notez que même si **EndEdit** confirme vos modifications, le **DataSet** ne les accepte que lorsque la méthode **AcceptChanges** est appelée.  Notez également que si vous appelez **AcceptChanges** avant de terminer la modification à l'aide de **EndEdit** ou **CancelEdit**, la modification se termine et les valeurs de ligne **Proposed** sont acceptées dans les versions de ligne **Current** et **Original**.  De même, l'appel à **RejectChanges** termine la modification et rejette les versions de ligne **Current** et **Proposed**.  L'appel à **EndEdit** ou **CancelEdit**, après l'appel à **AcceptChanges** ou **RejectChanges**, n'a aucun effet car la modification est déjà terminée.  
  
 L'exemple suivant montre comment utiliser **BeginEdit** avec **EndEdit** et **CancelEdit**.  Cet exemple vérifie également le **ProposedValue** dans l'événement **ColumnChanged** et décide si la modification doit être annulée.  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""       
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=   
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";       
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);    
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataRowVersion>   
 [Manipulation de données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [Gestion des événements DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)