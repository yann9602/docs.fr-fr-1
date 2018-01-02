---
title: "Création d'un DataView"
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 53cbfc5097c28c0677a164f817cfe14927814d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataview"></a>Création d'un DataView
Il existe deux façons de créer un objet <xref:System.Data.DataView>. Vous pouvez utiliser la **DataView** constructeur, ou vous pouvez créer une référence à la <xref:System.Data.DataTable.DefaultView%2A> propriété de la <xref:System.Data.DataTable>. Le **DataView** constructeur ne peut être vide ou il peut également accepter soit un **DataTable** comme un argument unique, ou un **DataTable** , ainsi que les critères de filtre, des critères de tri et une ligne filtre d’état. Pour plus d’informations sur les arguments supplémentaires pour une utilisation avec le **DataView**, consultez [de tri et de filtrage des données](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Étant donné que l’index pour un **DataView** est intégrée à la fois lors le **DataView** est créé et lorsqu’un du **tri**, **RowFilter**, ou  **RowStateFilter** propriétés sont modifiées, vous obtiendrez de meilleures performances en fournissez un ordre de tri initial ou des critères de filtre en tant qu’arguments de constructeur lorsque vous créez le **DataView**. Création d’un **DataView** sans spécification de critères de tri ou de filtre, puis en définissant le **tri**, **RowFilter**, ou **RowStateFilter** propriétés provoque ultérieurement l’index doit être créé au moins deux fois : une fois lors de la **DataView** est créé, et à nouveau lorsque toutes les propriétés de tri ou de filtre sont modifiés.  
  
 Notez que si vous créez un **DataView** à l’aide du constructeur qui n’accepte pas d’argument, vous ne serez pas être en mesure d’utiliser le **DataView** jusqu'à ce que vous avez défini le **Table** propriété .  
  
 L’exemple de code suivant montre comment créer un **DataView** à l’aide de la **DataView** constructeur. A **RowFilter**, **tri** colonne, et **DataViewRowState** sont fournis avec le **DataTable**.  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 L’exemple de code suivant montre comment obtenir une référence à la valeur par défaut **DataView** d’un **DataTable** à l’aide de la **DefaultView** propriété de la table.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Tri et filtre de données](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
