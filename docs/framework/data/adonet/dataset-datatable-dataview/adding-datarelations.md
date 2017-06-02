---
title: "Ajout d&#39;objets DataRelation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Ajout d&#39;objets DataRelation
Dans un objet <xref:System.Data.DataSet> contenant plusieurs objets <xref:System.Data.DataTable>, vous pouvez utiliser des objets <xref:System.Data.DataRelation> pour associer une table à une autre, pour vous déplacer dans les tables et pour retourner les lignes enfants ou parentes d'une table associée.  
  
 Les arguments requis pour créer un **DataRelation** sont un nom pour le **DataRelation** et un tableau d'une ou de plusieurs références d'objet <xref:System.Data.DataColumn> aux colonnes qui serviront de colonnes parentes et enfants dans la relation.  Une fois que vous avez créé un **DataRelation**, vous pouvez l'utiliser pour vous déplacer entre les tables et extraire des valeurs.  
  
 Le fait d'ajouter un **DataRelation** à un objet <xref:System.Data.DataSet> ajoute, par défaut, un objet <xref:System.Data.UniqueConstraint> à la table parente et un objet <xref:System.Data.ForeignKeyConstraint> à la table enfant.  Pour plus d'informations sur ces contraintes par défaut, voir [Contraintes DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 L'exemple de code suivant crée un **DataRelation** entre deux objets <xref:System.Data.DataTable> dans un objet <xref:System.Data.DataSet>.  Chaque objet <xref:System.Data.DataTable> contient une colonne nommée **CustID** qui sert de lien entre les deux objets <xref:System.Data.DataTable>.  L'exemple ajoute un seul **DataRelation** à la collection **Relations** de l'objet <xref:System.Data.DataSet>.  Le premier argument de l'exemple spécifie le nom du **DataRelation** créé.  Le deuxième définit le **DataColumn** parent et le troisième le **DataColumn** enfant.  
  
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
  
 Un **DataRelation** est également assorti d'une propriété **Nested** qui, définie sur **true**, imbrique les lignes de la table enfant dans la ligne associée de la table parente lorsque ce contenu est écrit sous la forme d'éléments XML à l'aide de <xref:System.Data.DataSet.WriteXml%2A>.  Pour plus d'informations, consultez [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## Voir aussi  
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)