---
title: Modification des DataViews
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
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 921707b07f1e8c8a9208df7de74512325f3027d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-dataviews"></a><span data-ttu-id="0e15b-102">Modification des DataViews</span><span class="sxs-lookup"><span data-stu-id="0e15b-102">Modifying DataViews</span></span>
<span data-ttu-id="0e15b-103">Vous pouvez utiliser l'objet <xref:System.Data.DataView> pour ajouter, supprimer ou modifier des lignes de données dans la table sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="0e15b-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="0e15b-104">La possibilité d’utiliser le **DataView** pour modifier les données dans la table sous-jacente est contrôlé en définissant une des trois propriétés booléennes de la **DataView**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="0e15b-105">Ces propriétés sont <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A> et <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e15b-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="0e15b-106">Ils sont définis sur **true** par défaut.</span><span class="sxs-lookup"><span data-stu-id="0e15b-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="0e15b-107">Si **AllowNew** est **true**, vous pouvez utiliser la <xref:System.Data.DataView.AddNew%2A> méthode de la **DataView** pour créer un nouveau <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="0e15b-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="0e15b-108">Notez qu’une nouvelle ligne n’est pas en réalité ajoutées à sous-jacent <xref:System.Data.DataTable> jusqu'à ce que le <xref:System.Data.DataRowView.EndEdit%2A> méthode de la **DataRowView** est appelée.</span><span class="sxs-lookup"><span data-stu-id="0e15b-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="0e15b-109">Si le <xref:System.Data.DataRowView.CancelEdit%2A> méthode de la **DataRowView** est appelée, la nouvelle ligne est ignorée.</span><span class="sxs-lookup"><span data-stu-id="0e15b-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="0e15b-110">Notez également que vous pouvez modifier qu’un seul **DataRowView** à la fois.</span><span class="sxs-lookup"><span data-stu-id="0e15b-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="0e15b-111">Si vous appelez le **AddNew** ou **BeginEdit** méthode de la **DataRowView** alors qu’une ligne en attente existe, **EndEdit** est implicitement appelée sur le ligne en attente.</span><span class="sxs-lookup"><span data-stu-id="0e15b-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="0e15b-112">Lorsque **EndEdit** est appelée, les modifications sont appliquées à l’objet sous-jacent **DataTable** et pourront ensuite être validées ou refusées à l’aide de la **AcceptChanges** ou  **RejectChanges** méthodes de la **DataTable**, **DataSet**, ou **DataRow** objet.</span><span class="sxs-lookup"><span data-stu-id="0e15b-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="0e15b-113">Si **AllowNew** est **false**, une exception est levée si vous appelez le **AddNew** méthode de la **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="0e15b-114">Si **AllowEdit** est **true**, vous pouvez modifier le contenu d’un **DataRow** via la **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="0e15b-115">Vous pouvez confirmer les modifications apportées à la ligne sous-jacente en utilisant **DataRowView.EndEdit** ou rejeter les modifications à l’aide de **DataRowView.CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="0e15b-116">Notez que vous ne pouvez modifier qu'une seule ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="0e15b-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="0e15b-117">Si vous appelez le **AddNew** ou **BeginEdit** méthodes de la **DataRowView** alors qu’une ligne en attente existe, **EndEdit** est implicitement appelée sur la ligne en attente.</span><span class="sxs-lookup"><span data-stu-id="0e15b-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="0e15b-118">Lorsque **EndEdit** est appelée, les modifications proposées sont placées dans le **actuel** version de ligne de l’objet sous-jacent **DataRow** et pourront ensuite être validées ou refusées à l’aide de la  **AcceptChanges** ou **RejectChanges** méthodes de la **DataTable**, **DataSet**, ou **DataRow** objet.</span><span class="sxs-lookup"><span data-stu-id="0e15b-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="0e15b-119">Si **AllowEdit** est **false**, une exception est levée si vous tentez de modifier une valeur dans la **DataView**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="0e15b-120">Lorsqu’un existant **DataRowView** est en cours de modification, les événements de l’objet sous-jacent **DataTable** seront toujours déclenchés avec les modifications proposées.</span><span class="sxs-lookup"><span data-stu-id="0e15b-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="0e15b-121">Notez que si vous appelez **EndEdit** ou **CancelEdit** sur sous-jacent **DataRow**, en attente seront appliquées ou annulées indépendamment du fait que des modifications  **EndEdit** ou **CancelEdit** est appelée sur le **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="0e15b-122">Si **AllowDelete** est **true**, vous pouvez supprimer des lignes à partir de la **DataView** à l’aide de la **supprimer** méthode de la **DataView**  ou **DataRowView** objet, les lignes sont supprimées de sous-jacent **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="0e15b-123">Vous pouvez ultérieurement valider ou refuser les suppressions à l’aide de **AcceptChanges** ou **RejectChanges** respectivement.</span><span class="sxs-lookup"><span data-stu-id="0e15b-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="0e15b-124">Si **AllowDelete** est **false**, une exception est levée si vous appelez le **supprimer** méthode de la **DataView** ou  **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="0e15b-125">L’exemple de code suivant désactive à l’aide de la **DataView** pour supprimer les lignes et ajoute une nouvelle ligne à la table sous-jacente à l’aide du **DataView**.</span><span class="sxs-lookup"><span data-stu-id="0e15b-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e15b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e15b-126">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="0e15b-127">DataViews</span><span class="sxs-lookup"><span data-stu-id="0e15b-127">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="0e15b-128">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="0e15b-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
