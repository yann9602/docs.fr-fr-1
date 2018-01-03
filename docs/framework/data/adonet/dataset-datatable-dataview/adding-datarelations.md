---
title: Ajout de DataRelations
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
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9741f44b68e1cac8c464338f556979d682d9e128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-datarelations"></a>Ajout de DataRelations
Dans un objet <xref:System.Data.DataSet> contenant plusieurs objets <xref:System.Data.DataTable>, vous pouvez utiliser des objets <xref:System.Data.DataRelation> pour associer une table à une autre, pour vous déplacer dans les tables et pour retourner les lignes enfants ou parentes d'une table associée.  
  
 Les arguments requis pour créer un **DataRelation** sont un nom pour le **DataRelation** est créé et un tableau d’un ou plusieurs <xref:System.Data.DataColumn> références aux colonnes de servir de parent et enfant colonnes dans la relation. Après avoir créé un **DataRelation**, vous pouvez l’utiliser pour naviguer entre les tables et de récupérer des valeurs.  
  
 Ajout d’un **DataRelation** à un <xref:System.Data.DataSet> ajoute par défaut, un <xref:System.Data.UniqueConstraint> à la table parente et une <xref:System.Data.ForeignKeyConstraint> à la table enfant. Pour plus d’informations sur ces contraintes par défaut, consultez [contraintes DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 L’exemple de code suivant crée un **DataRelation** à l’aide de deux <xref:System.Data.DataTable> des objets dans un <xref:System.Data.DataSet>. Chaque <xref:System.Data.DataTable> contient une colonne nommée **CustID**, qui sert de lien entre les deux <xref:System.Data.DataTable> objets. L’exemple ajoute un seul **DataRelation** à la **Relations** collection de la <xref:System.Data.DataSet>. Le premier argument dans l’exemple spécifie le nom de la **DataRelation** en cours de création. Le deuxième argument définit le parent **DataColumn** et le troisième argument définit l’enfant **DataColumn**.  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 A **DataRelation** a également un **Nested** propriété qui, lorsque la valeur **true**, imbrique les lignes de la table enfant dans la ligne associée de la table parente lors de l’écriture en tant qu’éléments XML à l’aide de <xref:System.Data.DataSet.WriteXml%2A> . Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Voir aussi  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
