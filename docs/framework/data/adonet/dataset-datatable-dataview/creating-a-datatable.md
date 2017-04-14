---
title: "Cr&#233;ation d&#39;un DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Cr&#233;ation d&#39;un DataTable
Un objet <xref:System.Data.DataTable>, qui représente une table de données relationnelles en mémoire, peut être créé et utilisé de façon indépendante. Il peut également être utilisé par d'autres objets .NET Framework, la plupart du temps comme membre d'un objet <xref:System.Data.DataSet>.  
  
 Vous pouvez créer un objet **DataTable** en utilisant le constructeur **DataTable** approprié.  Vous pouvez l'ajouter au **DataSet** à l'aide de la méthode **Add** afin de l'ajouter à la collection **Tables** de l'objet **DataTable**.  
  
 Vous pouvez également créer des objets **DataTable** dans un **DataSet** à l'aide de la méthode **Fill** ou **FillSchema** de l'objet **DataAdapter** ou à partir d'un schéma XML prédéfini ou déduit à l'aide de la méthode **ReadXml**, **ReadXmlSchema** ou **InferXmlSchema** du **DataSet**.  Notez qu'une fois que vous avez ajouté un **DataTable** comme membre de la collection **Tables** d'un **DataSet**, vous ne pouvez pas l'ajouter à la collection de tables d'un autre **DataSet**.  
  
 Lorsque vous créez un **DataTable**, celui\-ci ne possède pas encore de schéma \(structure\).  Pour définir le schéma de la table, vous devez créer et ajouter des objets <xref:System.Data.DataColumn> à la collection **Columns** de la table.  Vous pouvez également définir une colonne de clé primaire pour la table et créer et ajouter des objets **Constraint** à la collection **Constraints** de la table.  Après avoir défini le schéma d'un **DataTable**, vous pouvez ajouter des lignes de données à la table en ajoutant des objets **DataRow** à la collection **Rows** de la table.  
  
 Lors de la création d'un **DataTable**, il n'est pas nécessaire que vous fournissiez une valeur pour la propriété <xref:System.Data.DataTable.TableName%2A>. Vous pouvez définir cette propriété ultérieurement ou la laisser vide.  Néanmoins, lorsque vous ajoutez à un **DataSet** une table sans valeur **TableName**, un nom incrémentiel par défaut, Table*N*, est attribué à cette table. Ce nom est « Table » pour Table0.  
  
> [!NOTE]
>  Il est recommandé d'éviter d'utiliser la convention d'affectation de noms « Table*N* » lorsque vous fournissez une valeur **TableName** car le nom fourni peut entrer en conflit avec un nom de table par défaut existant du **DataSet**.  Si le nom fourni existe déjà, une exception est levée.  
  
 L'exemple suivant crée une instance d'un objet **DataTable** et lui attribue le nom « Customers ».  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 L'exemple suivant crée une instance d'un **DataTable** en l'ajoutant à la collection **Tables** d'un **DataSet**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## Voir aussi  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataTableCollection>   
 [DataTable, objets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [Remplissage d'un DataSet à partir d'un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)   
 [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)