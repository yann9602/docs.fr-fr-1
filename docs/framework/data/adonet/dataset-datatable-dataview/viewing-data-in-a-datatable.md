---
title: "Affichage des données dans un DataTable"
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
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ab7a60b4195f3d8976a61e3909682b3748e30341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="9a8dd-102">Affichage des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="9a8dd-102">Viewing Data in a DataTable</span></span>
<span data-ttu-id="9a8dd-103">Vous pouvez accéder au contenu d’un <xref:System.Data.DataTable> à l’aide de la **lignes** et **colonnes** collections de la **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="9a8dd-104">Vous pouvez également utiliser le <xref:System.Data.DataTable.Select%2A> méthode pour retourner des sous-ensembles des données dans un **DataTable** en fonction de critères, notamment les critères de recherche, l’ordre de tri et l’état de la ligne.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="9a8dd-105">En outre, vous pouvez utiliser la <xref:System.Data.DataRowCollection.Find%2A> méthode de la **DataRowCollection** lors de la recherche pour une ligne particulière à l’aide d’une valeur de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>  
  
 <span data-ttu-id="9a8dd-106">Le **sélectionnez** méthode de la **DataTable** objet retourne un jeu de <xref:System.Data.DataRow> objets qui correspondent aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="9a8dd-107">**Sélectionnez** prend des arguments facultatifs d’une expression de filtre, l’expression de tri, et **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="9a8dd-108">L’expression de filtre identifie les lignes à retourner en fonction des **DataColumn** valeurs, telles que `LastName = 'Smith'`.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="9a8dd-109">L'expression de tri respecte les conventions SQL standard de tri des colonnes, comme `LastName ASC, FirstName ASC`.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="9a8dd-110">Pour plus d’informations sur l’écriture d’expressions, consultez la <xref:System.Data.DataColumn.Expression%2A> propriété de la **DataColumn** classe.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="9a8dd-111">Si vous effectuez un nombre d’appels à la **sélectionnez** méthode d’un **DataTable**, vous pouvez augmenter les performances en créant d’abord un <xref:System.Data.DataView> pour le **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="9a8dd-112">Création de la **DataView** indexe les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="9a8dd-113">Le **sélectionnez** méthode utilise ensuite cet index, ce qui réduit considérablement le temps de générer le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-113">The **Select** method then usees that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="9a8dd-114">Pour plus d’informations sur la création d’un **DataView** pour un **DataTable**, consultez [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span><span class="sxs-lookup"><span data-stu-id="9a8dd-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span></span>  
  
 <span data-ttu-id="9a8dd-115">Le **sélectionnez** méthode détermine quelle version des lignes à afficher ou manipuler selon un <xref:System.Data.DataViewRowState>.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="9a8dd-116">Le tableau suivant décrit la possible **DataViewRowState** valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>  
  
|<span data-ttu-id="9a8dd-117">Valeur DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="9a8dd-117">DataViewRowState value</span></span>|<span data-ttu-id="9a8dd-118">Description</span><span class="sxs-lookup"><span data-stu-id="9a8dd-118">Description</span></span>|  
|----------------------------|-----------------|  
|<span data-ttu-id="9a8dd-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="9a8dd-119">**CurrentRows**</span></span>|<span data-ttu-id="9a8dd-120">Les lignes en cours comprennent les lignes non modifiées, les lignes ajoutées et les lignes modifiées.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-120">Current rows including unchanged, added, and modified rows.</span></span>|  
|<span data-ttu-id="9a8dd-121">**Supprimé**</span><span class="sxs-lookup"><span data-stu-id="9a8dd-121">**Deleted**</span></span>|<span data-ttu-id="9a8dd-122">Ligne supprimée.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-122">A deleted row.</span></span>|  
|<span data-ttu-id="9a8dd-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="9a8dd-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="9a8dd-124">Une version actuelle, qui est une version modifiée des données d'origine.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="9a8dd-125">(Consultez **ModifiedOriginal**.)</span><span class="sxs-lookup"><span data-stu-id="9a8dd-125">(See **ModifiedOriginal**.)</span></span>|  
|<span data-ttu-id="9a8dd-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="9a8dd-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="9a8dd-127">La version d'origine de toutes les lignes modifiées.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-127">The original version of all modified rows.</span></span> <span data-ttu-id="9a8dd-128">La version actuelle est disponible à l’aide **ModifiedCurrent**.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-128">The current version is available using **ModifiedCurrent**.</span></span>|  
|<span data-ttu-id="9a8dd-129">**Ajouté**</span><span class="sxs-lookup"><span data-stu-id="9a8dd-129">**Added**</span></span>|<span data-ttu-id="9a8dd-130">Nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-130">A new row.</span></span>|  
|<span data-ttu-id="9a8dd-131">**Aucun**</span><span class="sxs-lookup"><span data-stu-id="9a8dd-131">**None**</span></span>|<span data-ttu-id="9a8dd-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-132">None.</span></span>|  
|<span data-ttu-id="9a8dd-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="9a8dd-133">**OriginalRows**</span></span>|<span data-ttu-id="9a8dd-134">Les lignes d'origine, notamment les lignes non modifiées et les lignes supprimées.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-134">Original rows, including unchanged and deleted rows.</span></span>|  
|<span data-ttu-id="9a8dd-135">**Non modifié**</span><span class="sxs-lookup"><span data-stu-id="9a8dd-135">**Unchanged**</span></span>|<span data-ttu-id="9a8dd-136">Ligne non modifiée.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-136">An unchanged row.</span></span>|  
  
 <span data-ttu-id="9a8dd-137">Dans l’exemple suivant, la **DataSet** objet est filtré afin que vous travaillez uniquement avec des lignes dont **DataViewRowState** a la valeur **CurrentRows**.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 <span data-ttu-id="9a8dd-138">Le **sélectionnez** méthode peut être utilisée pour retourner les lignes avec différentes **RowState** valeurs ou des valeurs de champ.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="9a8dd-139">L’exemple suivant retourne un **DataRow** tableau qui fait référence à toutes les lignes qui ont été supprimés, ainsient qu’un autre **DataRow** tableau qui fait référence à toutes les lignes, classés par **CustLName**, où le **CustID** colonne est supérieure à 5.</span><span class="sxs-lookup"><span data-stu-id="9a8dd-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="9a8dd-140">Pour plus d’informations sur la façon d’afficher les informations contenues dans le **Deleted** de ligne, consultez [état des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="9a8dd-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a8dd-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a8dd-141">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [<span data-ttu-id="9a8dd-142">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="9a8dd-142">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="9a8dd-143">États des lignes et versions des lignes</span><span class="sxs-lookup"><span data-stu-id="9a8dd-143">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="9a8dd-144">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="9a8dd-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
