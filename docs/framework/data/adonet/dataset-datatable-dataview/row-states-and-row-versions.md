---
title: "États des lignes et versions des lignes"
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
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f03ddd0c8a09826068ae30e23773016faf3f56e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="5b655-102">États des lignes et versions des lignes</span><span class="sxs-lookup"><span data-stu-id="5b655-102">Row States and Row Versions</span></span>
<span data-ttu-id="5b655-103">ADO.NET gère les lignes des tables à l'aide des états et des versions de ligne.</span><span class="sxs-lookup"><span data-stu-id="5b655-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="5b655-104">Un état de ligne indique le statut d'une ligne ; les versions de ligne conservent les valeurs stockées dans une ligne pendant leur modification, notamment les valeurs actuelles, d'origine et par défaut.</span><span class="sxs-lookup"><span data-stu-id="5b655-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="5b655-105">Par exemple, une fois qu'une modification a été apportée à une colonne dans une ligne, la ligne possède un état de ligne `Modified` et deux versions de ligne : `Current`, qui contient les valeurs de ligne actuelles et `Original`, qui renferme les valeurs de ligne avant la modification de la colonne.</span><span class="sxs-lookup"><span data-stu-id="5b655-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="5b655-106">Chaque objet <xref:System.Data.DataRow> a la propriété <xref:System.Data.DataRow.RowState%2A> que vous pouvez examiner pour déterminer l'état actuel de la ligne.</span><span class="sxs-lookup"><span data-stu-id="5b655-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="5b655-107">Le tableau suivant fournit une brève description de chacune des valeurs d'énumération `RowState`.</span><span class="sxs-lookup"><span data-stu-id="5b655-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="5b655-108">Valeur RowState</span><span class="sxs-lookup"><span data-stu-id="5b655-108">RowState value</span></span>|<span data-ttu-id="5b655-109">Description</span><span class="sxs-lookup"><span data-stu-id="5b655-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="5b655-110">Aucune modification n'a été apportée depuis le dernier appel à `AcceptChanges` ou depuis la création de la ligne par `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="5b655-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="5b655-111">La ligne a été ajoutée à la table mais la `AcceptChanges` n'a pas été appelé.</span><span class="sxs-lookup"><span data-stu-id="5b655-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="5b655-112">Certains éléments de la ligne ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="5b655-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="5b655-113">La ligne a été supprimée d'une table et `AcceptChanges` n'a pas été appelé.</span><span class="sxs-lookup"><span data-stu-id="5b655-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="5b655-114">La ligne ne fait partie d'aucun `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="5b655-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="5b655-115">Le `RowState` d'une ligne nouvellement créée prend la valeur `Detached`.</span><span class="sxs-lookup"><span data-stu-id="5b655-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="5b655-116">Une fois le `DataRow` ajouté au `DataRowCollection` à l'aide de l'appel à la méthode `Add`, la propriété `RowState` prend la valeur `Added`.</span><span class="sxs-lookup"><span data-stu-id="5b655-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="5b655-117">`Detached` est également défini pour une ligne qui a été supprimée d'un `DataRowCollection` à l'aide de la méthode `Remove` ou par la méthode `Delete` suivie de la méthode `AcceptChanges`.</span><span class="sxs-lookup"><span data-stu-id="5b655-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="5b655-118">Lorsque `AcceptChanges` est appelé sur un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou sur un <xref:System.Data.DataRow>, toutes les lignes avec un état de ligne `Deleted` sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="5b655-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="5b655-119">Un état de ligne `Unchanged` est attribué aux autres lignes et les valeurs de la version de ligne `Original` sont remplacées par celles de la version de ligne `Current`.</span><span class="sxs-lookup"><span data-stu-id="5b655-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="5b655-120">Lorsque `RejectChanges` est appelé, toutes les lignes avec un état de ligne `Added` sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="5b655-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="5b655-121">Un état de ligne `Unchanged` est attribué aux autres lignes et les valeurs de la version de ligne `Current` sont remplacées par celles de la version de ligne `Original`.</span><span class="sxs-lookup"><span data-stu-id="5b655-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="5b655-122">Vous pouvez afficher les différentes versions de ligne d'une ligne en passant un paramètre <xref:System.Data.DataRowVersion> avec la référence de colonne, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5b655-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="5b655-123">Le tableau suivant fournit une brève description de chacune des valeurs d'énumération `DataRowVersion`.</span><span class="sxs-lookup"><span data-stu-id="5b655-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="5b655-124">Valeur DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="5b655-124">DataRowVersion value</span></span>|<span data-ttu-id="5b655-125">Description</span><span class="sxs-lookup"><span data-stu-id="5b655-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="5b655-126">Les valeurs actuelles de la ligne.</span><span class="sxs-lookup"><span data-stu-id="5b655-126">The current values for the row.</span></span> <span data-ttu-id="5b655-127">Cette version de ligne n'existe pas pour les lignes ayant un `RowState``Deleted`.</span><span class="sxs-lookup"><span data-stu-id="5b655-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="5b655-128">Version de ligne par défaut d'une ligne particulière.</span><span class="sxs-lookup"><span data-stu-id="5b655-128">The default row version for a particular row.</span></span> <span data-ttu-id="5b655-129">La version de ligne par défaut d'une ligne `Added`, `Modified` ou `Unchanged` est `Current`.</span><span class="sxs-lookup"><span data-stu-id="5b655-129">The default row version for an `Added`, `Modified`, or `Unchanged` row is `Current`.</span></span> <span data-ttu-id="5b655-130">La version de ligne par défaut d'une ligne `Deleted` est `Original`.</span><span class="sxs-lookup"><span data-stu-id="5b655-130">The default row version for a `Deleted` row is `Original`.</span></span> <span data-ttu-id="5b655-131">La version de ligne par défaut d'une ligne `Detached` est `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="5b655-131">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="5b655-132">Les valeurs d'origine de la ligne.</span><span class="sxs-lookup"><span data-stu-id="5b655-132">The original values for the row.</span></span> <span data-ttu-id="5b655-133">Cette version de ligne n'existe pas pour les lignes ayant un `RowState``Added`.</span><span class="sxs-lookup"><span data-stu-id="5b655-133">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="5b655-134">Les valeurs proposées de la ligne.</span><span class="sxs-lookup"><span data-stu-id="5b655-134">The proposed values for the row.</span></span> <span data-ttu-id="5b655-135">Cette version de ligne existe pendant une opération de modification sur une ligne ou pour une ligne qui ne fait pas partie d'un `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="5b655-135">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="5b655-136">Vous pouvez vérifier si un `DataRow` possède une version de ligne particulière en appelant la méthode <xref:System.Data.DataRow.HasVersion%2A> et en transmettant un `DataRowVersion` comme argument.</span><span class="sxs-lookup"><span data-stu-id="5b655-136">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="5b655-137">Par exemple, `DataRow.HasVersion(DataRowVersion.Original)` retournera la valeur `false` pour des lignes qui ont été ajoutées avant l'appel à la méthode `AcceptChanges`.</span><span class="sxs-lookup"><span data-stu-id="5b655-137">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="5b655-138">L'exemple de code suivant affiche les valeurs dans toutes les lignes supprimées d'une table.</span><span class="sxs-lookup"><span data-stu-id="5b655-138">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="5b655-139">Les lignes `Deleted` n'ont pas de version de ligne `Current`, vous devez donc passer `DataRowVersion.Original` lors de l'accès aux valeurs de colonne.</span><span class="sxs-lookup"><span data-stu-id="5b655-139">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b655-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b655-140">See Also</span></span>  
 [<span data-ttu-id="5b655-141">Manipulation de données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="5b655-141">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="5b655-142">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="5b655-142">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="5b655-143">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="5b655-143">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="5b655-144">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="5b655-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
