---
title: "Informations sur les erreurs de ligne | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Informations sur les erreurs de ligne
Pour éviter d'avoir à répondre chaque fois qu'une erreur de ligne se produit pendant que vous modifiez des valeurs dans un objet <xref:System.Data.DataTable>, vous pouvez ajouter les informations d'erreur à la ligne pour une utilisation ultérieure.  L'objet <xref:System.Data.DataRow> fournit une propriété <xref:System.Data.DataRow.RowError%2A> sur chaque ligne à cette fin.  L'ajout de données à la propriété **RowError** d'un **DataRow** attribue la valeur **true** à la propriété <xref:System.Data.DataRow.HasErrors%2A> du **DataRow**.  Si le **DataRow** fait partie d'un **DataTable** et si **DataRow.HasErrors** a la valeur **true**, la propriété **DataTable.HasErrors** a également la valeur **true**.  Cela s'applique également au **DataSet** auquel appartient le **DataTable**.  Lorsque vous testez les erreurs, vous pouvez vérifier la propriété **HasErrors** pour déterminer si des informations sur les erreurs ont été ajoutées à des lignes.  Si **HasErrors** a la valeur **true**, vous pouvez utiliser la méthode <xref:System.Data.DataTable.GetErrors%2A> du **DataTable** pour ne retourner et n'examiner que les lignes ayant des erreurs, comme le montre l'exemple suivant.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## Voir aussi  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataTable>   
 [Manipulation de données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)