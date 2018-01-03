---
title: Modifications de DataTable
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
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3d06fc3a82457972db94f82964942f446bb761be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-edits"></a>Modifications de DataTable
Lorsque vous modifiez les valeurs de colonne d'un objet <xref:System.Data.DataRow>, les modifications sont immédiatement placées dans l'état actuel de la ligne. Le <xref:System.Data.DataRowState> est alors définie sur **modifié**, et les modifications sont acceptées ou rejetées à l’aide la <xref:System.Data.DataRow.AcceptChanges%2A> ou <xref:System.Data.DataRow.RejectChanges%2A> méthodes de la **DataRow**. Le **DataRow** offre également trois méthodes que vous pouvez utiliser pour suspendre l’état de la ligne pendant sa modification. Ces méthodes sont <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> et <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Lorsque vous modifiez les valeurs de colonne dans un **DataRow** directement, les **DataRow** gère les valeurs de colonne à l’aide de la **actuel**, **par défaut**, et **D’origine** versions de ligne. En plus de ces versions de ligne, la **BeginEdit**, **EndEdit**, et **CancelEdit** méthodes utilisent une version de ligne quatrième : **proposé**. Pour plus d’informations sur les versions de ligne, consultez [état des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Le **proposé** version de ligne existe pendant une opération de modification commencée en appelant **BeginEdit** et qui termine à l’aide de **EndEdit** ou **CancelEdit,**  ou en appelant **AcceptChanges** ou **RejectChanges**.  
  
 Pendant l’opération de modification, vous pouvez appliquer la logique de validation à des colonnes individuelles en évaluant le **ProposedValue** dans les **ColumnChanged** l’événement de la **DataTable**. Le **ColumnChanged** événement contient **DataColumnChangeEventArgs** qui conserve une référence à la colonne qui est en cours de modification et à la **ProposedValue**. Après avoir évalué la valeur proposée, vous pouvez la modifier ou annuler la modification. Lorsque la modification est terminée, la ligne se déplace hors de la **proposé** état.  
  
 Vous pouvez confirmer les modifications en appelant **EndEdit**, ou vous pouvez les annuler en appelant **CancelEdit**. Notez que pendant **EndEdit** confirme vos modifications, la **DataSet** n’accepte pas réellement les modifications jusqu'à ce que **AcceptChanges** est appelée. Notez également que si vous appelez **AcceptChanges** avant de terminer la modification avec **EndEdit** ou **CancelEdit**, la modification est terminée et le **proposé** les valeurs de ligne sont acceptées pour les deux le **actuel** et **d’origine** versions de ligne. De la même manière, l’appel **RejectChanges** termine la modification et rejette les **actuel** et **proposé** versions de ligne. Appel de **EndEdit** ou **CancelEdit** après avoir appelé **AcceptChanges** ou **RejectChanges** n’a aucun effet car la modification a déjà s’est terminée.  
  
 L’exemple suivant montre comment utiliser **BeginEdit** avec **EndEdit** et **CancelEdit**. Cet exemple vérifie également le **ProposedValue** dans les **ColumnChanged** événement et décide s’il faut annuler la modification.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [Manipulation des données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Gestion des événements de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
