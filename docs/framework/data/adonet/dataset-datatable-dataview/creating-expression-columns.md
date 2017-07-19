---
title: "Cr&#233;ation de colonnes d&#39;expression | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Cr&#233;ation de colonnes d&#39;expression
Vous pouvez définir une expression pour une colonne lui permettant de contenir une valeur calculée à partir d'autres valeurs de colonne de la même ligne ou de valeurs de colonne de plusieurs lignes de la table.  Pour définir l'expression à évaluer, utilisez la propriété <xref:System.Data.DataColumn.Expression%2A> de la colonne cible. Utilisez la propriété <xref:System.Data.DataColumn.ColumnName%2A> pour faire référence à d'autres colonnes dans l'expression.  La propriété <xref:System.Data.DataColumn.DataType%2A> de la colonne d'expression doit être appropriée pour la valeur que l'expression retournera.  
  
 Le tableau suivant énumère différentes utilisations possibles des colonnes d'expression dans une table.  
  
|Type d'expression|Exemple|  
|-----------------------|-------------|  
|Comparaison|"Total \>\= 500"|  
|Calcul|"UnitPrice \* Quantity"|  
|Agrégation|Sum\(Price\)|  
  
 Vous pouvez attribuer un objet **DataColumn** existant à la propriété **Expression** ou inclure la propriété comme troisième argument passé au constructeur <xref:System.Data.DataColumn>, comme le montre l'exemple suivant.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 Les expressions peuvent faire référence à d'autres colonnes d'expression ; cependant, une référence circulaire, dans laquelle deux expressions se référencent mutuellement, générera une exception.  Pour des informations sur les règles d'écriture des expressions, voir la propriété <xref:System.Data.DataColumn.Expression%2A> de la classe **DataColumn**.  
  
## Voir aussi  
 <xref:System.Data.DataColumn>   
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 [Définition du schéma d'un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable, objets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)