---
title: "Création de colonnes d'expressions"
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
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 03c049ea3fb4b0f75418de4f9e8318512c198f41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-expression-columns"></a>Création de colonnes d'expressions
Vous pouvez définir une expression pour une colonne lui permettant de contenir une valeur calculée à partir d'autres valeurs de colonne de la même ligne ou de valeurs de colonne de plusieurs lignes de la table. Pour définir l'expression à évaluer, utilisez la propriété <xref:System.Data.DataColumn.Expression%2A> de la colonne cible. Utilisez la propriété <xref:System.Data.DataColumn.ColumnName%2A> pour faire référence à d'autres colonnes dans l'expression. La propriété <xref:System.Data.DataColumn.DataType%2A> de la colonne d'expression doit être appropriée pour la valeur que l'expression retournera.  
  
 Le tableau suivant énumère différentes utilisations possibles des colonnes d'expression dans une table.  
  
|Type d'expression|Exemple|  
|---------------------|-------------|  
|Comparaison|"Total >= 500"|  
|Calcul|"UnitPrice * Quantity"|  
|Agrégation|Sum(Price)|  
  
 Vous pouvez définir le **Expression** propriété sur un **DataColumn** objet, ou vous pouvez inclure la propriété comme troisième argument passé à la <xref:System.Data.DataColumn> constructeur, comme indiqué dans l’exemple suivant.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 Les expressions peuvent faire référence à d'autres colonnes d'expression ; cependant, une référence circulaire, dans laquelle deux expressions se référencent mutuellement, générera une exception. Pour plus d’informations sur l’écriture d’expressions, consultez la <xref:System.Data.DataColumn.Expression%2A> propriété de la **DataColumn** classe.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Définition de schéma de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
