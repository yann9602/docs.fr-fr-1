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
ms.openlocfilehash: d33bd8900c48222142a46ed2c5bd64412d2eaab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-edits"></a><span data-ttu-id="70b50-102">Modifications de DataTable</span><span class="sxs-lookup"><span data-stu-id="70b50-102">DataTable Edits</span></span>
<span data-ttu-id="70b50-103">Lorsque vous modifiez les valeurs de colonne d'un objet <xref:System.Data.DataRow>, les modifications sont immédiatement placées dans l'état actuel de la ligne.</span><span class="sxs-lookup"><span data-stu-id="70b50-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="70b50-104">Le <xref:System.Data.DataRowState> est alors définie sur **modifié**, et les modifications sont acceptées ou rejetées à l’aide la <xref:System.Data.DataRow.AcceptChanges%2A> ou <xref:System.Data.DataRow.RejectChanges%2A> méthodes de la **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="70b50-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="70b50-105">Le **DataRow** offre également trois méthodes que vous pouvez utiliser pour suspendre l’état de la ligne pendant sa modification.</span><span class="sxs-lookup"><span data-stu-id="70b50-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="70b50-106">Ces méthodes sont <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> et <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="70b50-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="70b50-107">Lorsque vous modifiez les valeurs de colonne dans un **DataRow** directement, les **DataRow** gère les valeurs de colonne à l’aide de la **actuel**, **par défaut**, et **D’origine** versions de ligne.</span><span class="sxs-lookup"><span data-stu-id="70b50-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="70b50-108">En plus de ces versions de ligne, la **BeginEdit**, **EndEdit**, et **CancelEdit** méthodes utilisent une version de ligne quatrième : **proposé**.</span><span class="sxs-lookup"><span data-stu-id="70b50-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="70b50-109">Pour plus d’informations sur les versions de ligne, consultez [état des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="70b50-109">For more information about row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="70b50-110">Le **proposé** version de ligne existe pendant une opération de modification commencée en appelant **BeginEdit** et qui termine à l’aide de **EndEdit** ou **CancelEdit,**  ou en appelant **AcceptChanges** ou **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="70b50-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="70b50-111">Pendant l’opération de modification, vous pouvez appliquer la logique de validation à des colonnes individuelles en évaluant le **ProposedValue** dans les **ColumnChanged** l’événement de la **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="70b50-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="70b50-112">Le **ColumnChanged** événement contient **DataColumnChangeEventArgs** qui conserve une référence à la colonne qui est en cours de modification et à la **ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="70b50-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="70b50-113">Après avoir évalué la valeur proposée, vous pouvez la modifier ou annuler la modification.</span><span class="sxs-lookup"><span data-stu-id="70b50-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="70b50-114">Lorsque la modification est terminée, la ligne se déplace hors de la **proposé** état.</span><span class="sxs-lookup"><span data-stu-id="70b50-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="70b50-115">Vous pouvez confirmer les modifications en appelant **EndEdit**, ou vous pouvez les annuler en appelant **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="70b50-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="70b50-116">Notez que pendant **EndEdit** confirme vos modifications, la **DataSet** n’accepte pas réellement les modifications jusqu'à ce que **AcceptChanges** est appelée.</span><span class="sxs-lookup"><span data-stu-id="70b50-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="70b50-117">Notez également que si vous appelez **AcceptChanges** avant de terminer la modification avec **EndEdit** ou **CancelEdit**, la modification est terminée et le **proposé** les valeurs de ligne sont acceptées pour les deux le **actuel** et **d’origine** versions de ligne.</span><span class="sxs-lookup"><span data-stu-id="70b50-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="70b50-118">De la même manière, l’appel **RejectChanges** termine la modification et rejette les **actuel** et **proposé** versions de ligne.</span><span class="sxs-lookup"><span data-stu-id="70b50-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="70b50-119">Appel de **EndEdit** ou **CancelEdit** après avoir appelé **AcceptChanges** ou **RejectChanges** n’a aucun effet car la modification a déjà s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="70b50-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="70b50-120">L’exemple suivant montre comment utiliser **BeginEdit** avec **EndEdit** et **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="70b50-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="70b50-121">Cet exemple vérifie également le **ProposedValue** dans les **ColumnChanged** événement et décide s’il faut annuler la modification.</span><span class="sxs-lookup"><span data-stu-id="70b50-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70b50-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70b50-122">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [<span data-ttu-id="70b50-123">Manipulation de données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="70b50-123">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="70b50-124">La gestion des événements de DataTable</span><span class="sxs-lookup"><span data-stu-id="70b50-124">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="70b50-125">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="70b50-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
