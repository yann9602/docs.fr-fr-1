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
ms.workload: dotnet
ms.openlocfilehash: ac8209432cd975539983226cfba51f229d696bd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="39a00-102">DataRows et DataRowViews</span><span class="sxs-lookup"><span data-stu-id="39a00-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="39a00-103">Un objet <xref:System.Data.DataView> expose une collection énumérable d'objets <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="39a00-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="39a00-104">Le **DataRowView** objets exposent des valeurs en tant que tableaux d’objets qui sont indexées par le nom ou la référence ordinale de la colonne dans la table sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="39a00-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="39a00-105">Vous pouvez accéder à la <xref:System.Data.DataRow> qui est exposé par le **DataRowView** à l’aide de la <xref:System.Data.DataRowView.Row%2A> propriété de la **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="39a00-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="39a00-106">Lorsque vous affichez des valeurs à l’aide un **DataRowView**, le <xref:System.Data.DataView.RowStateFilter%2A> propriété de la **DataView** détermine la version de ligne de sous-jacent **DataRow** est exposé.</span><span class="sxs-lookup"><span data-stu-id="39a00-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="39a00-107">Pour plus d’informations sur les différentes versions de ligne à l’aide de l’accès à un **DataRow**, consultez [état des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="39a00-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="39a00-108">L'exemple de code suivant affiche toutes les valeurs actuelles et d'origine d'une table.</span><span class="sxs-lookup"><span data-stu-id="39a00-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39a00-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39a00-109">See Also</span></span>  
 <xref:System.Data.DataRowVersion>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="39a00-110">DataViews</span><span class="sxs-lookup"><span data-stu-id="39a00-110">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="39a00-111">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="39a00-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
