---
title: "AcceptChanges et RejectChanges | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# AcceptChanges et RejectChanges
Après avoir vérifié l'exactitude des modifications apportées aux données d'un objet <xref:System.Data.DataTable>, vous pouvez les accepter à l'aide de la méthode <xref:System.Data.DataRow.AcceptChanges%2A> des objets <xref:System.Data.DataRow>, <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>, qui définira les valeurs de ligne **Current** comme valeurs **Original** et attribuera la valeur **Unchanged** à la propriété **RowState**.  L'acceptation ou le rejet des modifications supprime toutes les informations **RowError** et attribue la valeur **false** à la propriété **HasErrors**.  L'acceptation ou le rejet des modifications peut également affecter la mise à jour des données dans la source de données.  Pour plus d'informations, consultez [Mise à jour de sources de données avec des DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 S'il existe des contraintes de clé étrangère dans le **DataTable**, les modifications acceptées ou rejetées à l'aide de **AcceptChanges** et **RejectChanges** sont propagées aux lignes enfants du **DataRow** en fonction de **ForeignKeyConstraint.AcceptRejectRule**.  Pour plus d'informations, consultez [Contraintes DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 L'exemple suivant vérifie les lignes ayant des erreurs, résout, le cas échéant, les erreurs et rejette les lignes dans lesquelles les erreurs ne peuvent pas être résolues.  Notez que, pour les erreurs résolues, la valeur **RowError** est réinitialisée sur une chaîne vide, provoquant l'attribution de la valeur **false** à la propriété **HasErrors**.  Lorsque toutes les lignes ayant des erreurs ont été résolues ou rejetées, **AcceptChanges** est appelée pour accepter toutes les modifications pour l'ensemble du **DataTable**.  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## Voir aussi  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 [Manipulation de données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)