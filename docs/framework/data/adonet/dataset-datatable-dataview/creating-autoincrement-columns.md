---
title: "Cr&#233;ation de colonnes AutoIncrement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Cr&#233;ation de colonnes AutoIncrement
Pour garantir que les valeurs de colonne sont uniques, vous pouvez les définir de sorte qu'elles s'incrémentent automatiquement lors de l'ajout de lignes à la table.  Pour créer un objet <xref:System.Data.DataColumn> à incrémentation automatique, attribuez la valeur **true** à la propriété <xref:System.Data.DataColumn.AutoIncrement%2A> de la colonne.  L'objet <xref:System.Data.DataColumn> commence alors avec la valeur définie dans la propriété <xref:System.Data.DataColumn.AutoIncrementSeed%2A>. À chaque ligne ajoutée, la valeur de la colonne **AutoIncrement** augmente de la valeur définie dans la propriété <xref:System.Data.DataColumn.AutoIncrementStep%2A> de la colonne.  
  
 Pour les colonnes **AutoIncrement**, il est recommandé d'attribuer la valeur **true** à la propriété <xref:System.Data.DataColumn.ReadOnly%2A> du **DataColumn**.  
  
 L'exemple suivant montre comment créer une colonne commençant par la valeur 200, avec une incrémentation par pas de 3.  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## Voir aussi  
 <xref:System.Data.DataColumn>   
 [Définition du schéma d'un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable, objets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)