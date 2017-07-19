---
title: "Cr&#233;ation d&#39;un DataView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Cr&#233;ation d&#39;un DataView
Il existe deux façons de créer un objet <xref:System.Data.DataView>.  Vous pouvez utiliser le constructeur de **DataView** ou créer une référence à la propriété <xref:System.Data.DataTable.DefaultView%2A> de l'objet <xref:System.Data.DataTable>.  Le constructeur de **DataView** peut être vide, mais il peut également accepter soit un **DataTable** comme argument unique, soit un **DataTable** avec des critères de filtre, des critères de tri et un filtre d'état de ligne.  Pour plus d'informations sur les autres arguments que vous pouvez utiliser avec le **DataView**, voir [Tri et filtrage de données](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Étant donné que l'index d'un **DataView** est généré à la création du **DataView**, mais aussi lorsque l'une des propriétés **Sort**, **RowFilter** ou **RowStateFilter** est modifiée, vous obtiendrez de meilleures performances si vous fournissez un ordre de tri ou des critères de filtre initiaux comme arguments pour le constructeur lorsque vous créez le **DataView**.  La création d'un **DataView** sans spécifier de critère de tri ou de filtre et la définition ultérieure des propriétés **Sort**, **RowFilter** ou **RowStateFilter** entraînent la construction de l'index deux fois au moins : une fois lors de la création du **DataView**, puis à nouveau lorsqu'une des propriétés de tri ou de filtrage est modifiée.  
  
 Notez que si vous créez un **DataView** à l'aide du constructeur sans argument, vous ne serez en mesure d'utiliser le **DataView** qu'après avoir défini la propriété **Table**.  
  
 L'exemple de code suivant montre comment créer un **DataView** à l'aide du constructeur de **DataView**.  Un **RowFilter**, une colonne **Sort** et un **DataViewRowState** sont fournis avec le **DataTable**.  
  
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
  
 L'exemple de code suivant montre comment obtenir une référence au **DataView** par défaut d'un **DataTable** à l'aide de la propriété **DefaultView** de la table.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## Voir aussi  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [Tri et filtrage de données](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)   
 [DataTable, objets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)