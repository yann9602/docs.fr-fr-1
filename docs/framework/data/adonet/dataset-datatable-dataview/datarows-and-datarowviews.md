---
title: DataRows et DataRowViews
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
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e342ce805880da848da1e17700c055aba2c74f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datarows-and-datarowviews"></a>DataRows et DataRowViews
Un objet <xref:System.Data.DataView> expose une collection énumérable d'objets <xref:System.Data.DataRowView>. Le **DataRowView** objets exposent des valeurs en tant que tableaux d’objets qui sont indexées par le nom ou la référence ordinale de la colonne dans la table sous-jacente. Vous pouvez accéder à la <xref:System.Data.DataRow> qui est exposé par le **DataRowView** à l’aide de la <xref:System.Data.DataRowView.Row%2A> propriété de la **DataRowView**.  
  
 Lorsque vous affichez des valeurs à l’aide un **DataRowView**, le <xref:System.Data.DataView.RowStateFilter%2A> propriété de la **DataView** détermine la version de ligne de sous-jacent **DataRow** est exposé. Pour plus d’informations sur les différentes versions de ligne à l’aide de l’accès à un **DataRow**, consultez [état des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 L'exemple de code suivant affiche toutes les valeurs actuelles et d'origine d'une table.  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)      
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataRowVersion>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
