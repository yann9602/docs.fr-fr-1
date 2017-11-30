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
ms.openlocfilehash: 0a8478e9b21c6c2abdc02677305e468109e7b9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="modifying-dataviews"></a>Modification des DataViews
Vous pouvez utiliser l'objet <xref:System.Data.DataView> pour ajouter, supprimer ou modifier des lignes de données dans la table sous-jacente. La possibilité d’utiliser le **DataView** pour modifier les données dans la table sous-jacente est contrôlé en définissant une des trois propriétés booléennes de la **DataView**. Ces propriétés sont <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A> et <xref:System.Data.DataView.AllowDelete%2A>. Ils sont définis sur **true** par défaut.  
  
 Si **AllowNew** est **true**, vous pouvez utiliser la <xref:System.Data.DataView.AddNew%2A> méthode de la **DataView** pour créer un nouveau <xref:System.Data.DataRowView>. Notez qu’une nouvelle ligne n’est pas en réalité ajoutées à sous-jacent <xref:System.Data.DataTable> jusqu'à ce que le <xref:System.Data.DataRowView.EndEdit%2A> méthode de la **DataRowView** est appelée. Si le <xref:System.Data.DataRowView.CancelEdit%2A> méthode de la **DataRowView** est appelée, la nouvelle ligne est ignorée. Notez également que vous pouvez modifier qu’un seul **DataRowView** à la fois. Si vous appelez le **AddNew** ou **BeginEdit** méthode de la **DataRowView** alors qu’une ligne en attente existe, **EndEdit** est implicitement appelée sur le ligne en attente. Lorsque **EndEdit** est appelée, les modifications sont appliquées à l’objet sous-jacent **DataTable** et pourront ensuite être validées ou refusées à l’aide de la **AcceptChanges** ou  **RejectChanges** méthodes de la **DataTable**, **DataSet**, ou **DataRow** objet. Si **AllowNew** est **false**, une exception est levée si vous appelez le **AddNew** méthode de la **DataRowView**.  
  
 Si **AllowEdit** est **true**, vous pouvez modifier le contenu d’un **DataRow** via la **DataRowView**. Vous pouvez confirmer les modifications apportées à la ligne sous-jacente en utilisant **DataRowView.EndEdit** ou rejeter les modifications à l’aide de **DataRowView.CancelEdit**. Notez que vous ne pouvez modifier qu'une seule ligne à la fois. Si vous appelez le **AddNew** ou **BeginEdit** méthodes de la **DataRowView** alors qu’une ligne en attente existe, **EndEdit** est implicitement appelée sur la ligne en attente. Lorsque **EndEdit** est appelée, les modifications proposées sont placées dans le **actuel** version de ligne de l’objet sous-jacent **DataRow** et pourront ensuite être validées ou refusées à l’aide de la  **AcceptChanges** ou **RejectChanges** méthodes de la **DataTable**, **DataSet**, ou **DataRow** objet. Si **AllowEdit** est **false**, une exception est levée si vous tentez de modifier une valeur dans la **DataView**.  
  
 Lorsqu’un existant **DataRowView** est en cours de modification, les événements de l’objet sous-jacent **DataTable** seront toujours déclenchés avec les modifications proposées. Notez que si vous appelez **EndEdit** ou **CancelEdit** sur sous-jacent **DataRow**, en attente seront appliquées ou annulées indépendamment du fait que des modifications  **EndEdit** ou **CancelEdit** est appelée sur le **DataRowView**.  
  
 Si **AllowDelete** est **true**, vous pouvez supprimer des lignes à partir de la **DataView** à l’aide de la **supprimer** méthode de la **DataView**  ou **DataRowView** objet, les lignes sont supprimées de sous-jacent **DataTable**. Vous pouvez ultérieurement valider ou refuser les suppressions à l’aide de **AcceptChanges** ou **RejectChanges** respectivement. Si **AllowDelete** est **false**, une exception est levée si vous appelez le **supprimer** méthode de la **DataView** ou  **DataRowView**.  
  
 L’exemple de code suivant désactive à l’aide de la **DataView** pour supprimer les lignes et ajoute une nouvelle ligne à la table sous-jacente à l’aide du **DataView**.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
