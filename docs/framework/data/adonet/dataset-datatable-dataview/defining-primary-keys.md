---
title: "D&#233;finition des cl&#233;s primaires | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# D&#233;finition des cl&#233;s primaires
Une table de base de données a généralement une colonne ou un groupe de colonnes identifiant de façon unique chaque ligne de la table.  Cette colonne ou ce groupe de colonnes d'identification s'appelle la clé primaire.  
  
 Lorsque vous identifiez un seul objet <xref:System.Data.DataColumn> comme la propriété <xref:System.Data.DataTable.PrimaryKey%2A> d'un objet <xref:System.Data.DataTable>, la table attribue automatiquement la valeur **false** à la propriété <xref:System.Data.DataColumn.AllowDBNull%2A> de la colonne et la valeur **true** à la propriété <xref:System.Data.DataColumn.Unique%2A>.  Pour les clés primaires à plusieurs colonnes, la valeur **false** n'est automatiquement attribuée qu'à la propriété **AllowDBNull**.  
  
 La propriété **PrimaryKey** d'un objet <xref:System.Data.DataTable> reçoit comme valeur un tableau d'un ou plusieurs objets **DataColumn**, comme le montrent les exemples suivants.  Le premier exemple définit une colonne unique comme clé primaire.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 L'exemple suivant définit deux colonnes comme clé primaire.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## Voir aussi  
 <xref:System.Data.DataTable>   
 [Définition du schéma d'un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable, objets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)