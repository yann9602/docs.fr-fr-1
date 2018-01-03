---
title: "Création de colonnes AutoIncrement"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4c9c7e321ac5749aedf7168afaef9d6a7119de62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-autoincrement-columns"></a>Création de colonnes AutoIncrement
Pour garantir que les valeurs de colonne sont uniques, vous pouvez les définir de sorte qu'elles s'incrémentent automatiquement lors de l'ajout de lignes à la table. Pour créer un auto-incrémentée <xref:System.Data.DataColumn>, définissez le <xref:System.Data.DataColumn.AutoIncrement%2A> propriété de la colonne à **true**. Le <xref:System.Data.DataColumn> commence alors avec la valeur définie dans le <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriété et à chaque ligne ajoutée à la valeur de la **AutoIncrement** colonne augmente la valeur définie dans le <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriété de la colonne.  
  
 Pour **AutoIncrement** colonnes, nous vous recommandons la <xref:System.Data.DataColumn.ReadOnly%2A> propriété de la **DataColumn** avoir la valeur **true**.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataColumn>  
 [Définition de schéma de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
