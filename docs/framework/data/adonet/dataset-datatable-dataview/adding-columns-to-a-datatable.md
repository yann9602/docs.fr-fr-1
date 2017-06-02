---
title: "Ajout de colonnes &#224; un DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Ajout de colonnes &#224; un DataTable
Un objet <xref:System.Data.DataTable> contient une collection d'objets <xref:System.Data.DataColumn> référencés par la propriété **Columns** de la table.  Cette collection de colonnes, ainsi que toute contrainte, définit le schéma, ou structure, de la table.  
  
 Vous pouvez créer des objets **DataColumn** dans une table en utilisant le constructeur **DataColumn** ou en appelant la méthode **Add** de la propriété **Columns** de la table, qui est un objet <xref:System.Data.DataColumnCollection>.  La méthode **Add** accepte des arguments facultatifs **ColumnName**, **DataType** et **Expression** et crée un nouveau **DataColumn** en tant que membre de la collection.  Elle accepte également un objet **DataColumn** existant, l'ajoute à la collection et retourne une référence au **DataColumn** ajouté, si nécessaire.  Étant donné que les objets **DataTable** ne sont spécifiques à aucune source de données, les types .NET Framework sont utilisés lors de la spécification du type de données d'un **DataColumn**.  
  
 L'exemple suivant ajoute quatre colonnes à un **DataTable**.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 Dans cet exemple, remarquez que les propriétés de la colonne **CustID** sont définies de façon à ne pas accepter de valeurs **DBNull** et à limiter les valeurs à des valeurs uniques.  Cependant, si vous définissez la colonne **CustID** comme colonne de clé primaire de la table, la propriété **AllowDBNull** prendra automatiquement la valeur **false** et la propriété **Unique** la valeur **true**.  Pour plus d'informations, consultez [Définition des clés primaires](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Si aucun nom n'est fourni pour une colonne, un nom incrémentiel par défaut de Column*N* \(à partir de « Column1 »\) est attribué à cette colonne lors de son ajout au **DataColumnCollection**.  Il est recommandé d'éviter d'utiliser la convention de dénomination « Column*N* » lorsque vous fournissez un nom de colonne car le nom fourni peut entrer en conflit avec un nom de colonne par défaut existant du **DataColumnCollection**.  Si le nom fourni existe déjà, une exception est levée.  
  
 Si vous utilisez <xref:System.Xml.XLinq.XElement> en tant que <xref:System.Data.DataColumn.DataType%2A> d'un <xref:System.Data.DataColumn> dans <xref:System.Data.DataTable>, la sérialisation XML ne fonctionnera pas lors de la lecture dans les données.  Par exemple, si vous écrivez un <xref:System.Xml.XmlDocument> à l'aide de la méthode `DataTable.WriteXml`, lors de la sérialisation vers XML, un nœud parent supplémentaire est ajouté dans le <xref:System.Xml.XLinq.XElement>.  Pour contourner ce problème, utilisez le type <xref:System.Data.SqlTypes.SqlXml> à la place de <xref:System.Xml.XLinq.XElement>.  `ReadXml` et `WriteXml` fonctionnent correctement avec <xref:System.Data.SqlTypes.SqlXml>.  
  
## Voir aussi  
 <xref:System.Data.DataColumn>   
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataTable>   
 [Définition du schéma d'un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable, objets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)