---
title: "Modification des objets DataView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Modification des objets DataView
Vous pouvez utiliser l'objet <xref:System.Data.DataView> pour ajouter, supprimer ou modifier des lignes de données dans la table sous\-jacente.  La possibilité d'utiliser le **DataView** pour modifier des données dans la table sous\-jacente est contrôlée par la définition d'une de ses trois propriétés de type booléen.  Ces propriétés sont <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A> et <xref:System.Data.DataView.AllowDelete%2A>.  Par défaut, elles ont la valeur **true**.  
  
 Si **AllowNew** a la valeur **true**, vous pouvez utiliser la méthode <xref:System.Data.DataView.AddNew%2A> du **DataView** pour créer un nouvel objet <xref:System.Data.DataRowView>.  Notez qu'une nouvelle ligne n'est effectivement ajoutée à l'objet <xref:System.Data.DataTable> sous\-jacent qu'après l'appel de la méthode <xref:System.Data.DataRowView.EndEdit%2A> du **DataRowView**.  Si la méthode <xref:System.Data.DataRowView.CancelEdit%2A> du **DataRowView** est appelée, la nouvelle ligne est ignorée.  Notez également que vous ne pouvez modifier qu'un **DataRowView** à la fois.  Si vous appelez la méthode **AddNew** ou **BeginEdit** du **DataRowView** alors qu'une ligne en attente existe, la méthode **EndEdit** est implicitement appelée sur cette ligne.  Lorsque la méthode **EndEdit** est appelée, les modifications sont apportées au **DataTable** sous\-jacent et pourront ensuite être validées ou refusées à l'aide des méthodes **AcceptChanges** ou **RejectChanges** de l'objet **DataTable**, **DataSet** ou **DataRow**.  Si **AllowNew** a la valeur **false**, une exception est levée si vous appelez la méthode **AddNew** du **DataRowView**.  
  
 Si **AllowEdit** a la valeur **true**, vous pouvez modifier le contenu d'un **DataRow** via le **DataRowView**.  Vous pouvez confirmer les modifications à apporter à la ligne sous\-jacente en utilisant **DataRowView.EndEdit** ou refuser ces modifications à l'aide de **DataRowView.CancelEdit**.  Notez que vous ne pouvez modifier qu'une seule ligne à la fois.  Si vous appelez la méthode **AddNew** ou **BeginEdit** du **DataRowView** alors qu'une ligne en attente existe, la méthode **EndEdit** est implicitement appelée sur cette ligne.  Lorsque la méthode **EndEdit** est appelée, les modifications proposées sont placées dans la version de ligne **Current** du **DataRow** sous\-jacent et pourront ensuite être validées ou refusées à l'aide de la méthode **AcceptChanges** ou **RejectChanges** de l'objet **DataTable**, **DataSet** ou **DataRow**.  Si **AllowEdit** a la valeur **false**, une exception est levée si vous tentez de modifier une valeur du **DataView**.  
  
 Lorsqu'un **DataRowView** existant est en cours de modification, les événements du **DataTable** sous\-jacent seront toujours déclenchés avec les modifications proposées.  Notez que si vous appelez **EndEdit** ou **CancelEdit** sur le **DataRow** sous\-jacent, les changements en attente seront appliqués ou annulés, que la méthode **EndEdit** ou **CancelEdit** soit ou non appelée sur le **DataRowView**.  
  
 Si **AllowDelete** a la valeur **true**, vous pouvez supprimer des lignes du **DataView** à l'aide de la méthode **Delete** de l'objet **DataView** ou **DataRowView**, et les lignes sont supprimées du **DataTable** sous\-jacent.  Vous pouvez par la suite valider ou refuser les suppressions à l'aide de **AcceptChanges** ou de **RejectChanges** respectivement.  Si **AllowDelete** a la valeur **false**, une exception est levée si vous appelez la méthode **Delete** du **DataView** ou du **DataRowView**.  
  
 L'exemple de code suivant désactive la possibilité de supprimer des lignes à l'aide du **DataView** et ajoute une nouvelle ligne à la table sous\-jacente à l'aide du **DataView**.  
  
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
  
## Voir aussi  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 <xref:System.Data.DataRowView>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)