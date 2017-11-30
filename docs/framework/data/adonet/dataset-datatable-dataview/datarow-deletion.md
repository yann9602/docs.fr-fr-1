---
title: Suppression de DataRow
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
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f9eb89d711cbf66f3b6816e597c14359be1f3639
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datarow-deletion"></a><span data-ttu-id="1fb8f-102">Suppression de DataRow</span><span class="sxs-lookup"><span data-stu-id="1fb8f-102">DataRow Deletion</span></span>
<span data-ttu-id="1fb8f-103">Il existe deux méthodes, vous pouvez utiliser pour supprimer un <xref:System.Data.DataRow> à partir de l’objet un <xref:System.Data.DataTable> objet : le **supprimer** méthode de la <xref:System.Data.DataRowCollection> objet et le <xref:System.Data.DataRow.Delete%2A> méthode de la **DataRow**objet.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="1fb8f-104">Alors que le <xref:System.Data.DataRowCollection.Remove%2A> méthode supprime un **DataRow** à partir de la **DataRowCollection**, le <xref:System.Data.DataRow.Delete%2A> méthode marque seulement la ligne pour la suppression.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="1fb8f-105">La suppression réelle se produit lorsque l’application appelle la **AcceptChanges** (méthode).</span><span class="sxs-lookup"><span data-stu-id="1fb8f-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="1fb8f-106">En utilisant <xref:System.Data.DataRow.Delete%2A>, vous pouvez vérifier par programme les lignes marquées pour suppression avant de les supprimer.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="1fb8f-107">Lorsqu'une ligne est marquée pour suppression, sa propriété <xref:System.Data.DataRow.RowState%2A> prend la valeur <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="1fb8f-108">Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne doivent être appelées dans une boucle foreach lors de l'itération au sein d'un objet <xref:System.Data.DataRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="1fb8f-109">Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne modifient l'état de la collection.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="1fb8f-110">Lorsque vous utilisez un <xref:System.Data.DataSet> ou **DataTable** conjointement avec un **DataAdapter** et une source de données relationnelle, utilisez la **supprimer** méthode de la  **DataRow** pour supprimer la ligne.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="1fb8f-111">Le **supprimer** méthode marque la ligne comme **Deleted** dans les **DataSet** ou **DataTable** mais ne la supprime ne pas.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="1fb8f-112">Au lieu de cela, lorsque la **DataAdapter** rencontre une ligne marquée comme **Deleted**, il exécute sa **DeleteCommand** méthode pour supprimer la ligne à la source de données.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="1fb8f-113">La ligne peut ensuite être définitivement supprimée à l’aide de la **AcceptChanges** (méthode).</span><span class="sxs-lookup"><span data-stu-id="1fb8f-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="1fb8f-114">Si vous utilisez **supprimer** pour supprimer la ligne, la ligne est entièrement supprimée de la table, mais la **DataAdapter** ne supprimera pas la ligne à la source de données.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="1fb8f-115">Le **supprimer** méthode de la **DataRowCollection** prend un **DataRow** en tant qu’argument et le supprime de la collection, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="1fb8f-116">En revanche, l’exemple suivant montre comment appeler le **supprimer** méthode sur un **DataRow** pour modifier son **RowState** à **Deleted** .</span><span class="sxs-lookup"><span data-stu-id="1fb8f-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="1fb8f-117">Si une ligne est marquée pour suppression et que vous appelez le **AcceptChanges** méthode de la **DataTable** de l’objet, la ligne est supprimée de la **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="1fb8f-118">En revanche, si vous appelez **RejectChanges**, le **RowState** de la ligne revient à qu’il avait avant d’être marqué comme **Deleted**.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fb8f-119">Si le **RowState** d’un **DataRow** est **Added**, ce qui signifie qu’il vient d’être ajouté à la table, et il est ensuite marqué comme **Deleted**, il est supprimé de la table.</span><span class="sxs-lookup"><span data-stu-id="1fb8f-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb8f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fb8f-120">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="1fb8f-121">Manipulation de données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="1fb8f-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="1fb8f-122">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="1fb8f-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
