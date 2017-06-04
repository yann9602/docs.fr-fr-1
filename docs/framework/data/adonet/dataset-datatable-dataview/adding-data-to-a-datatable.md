---
title: "Ajout de donn&#233;es &#224; un objet DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Ajout de donn&#233;es &#224; un objet DataTable
Après avoir créé un objet <xref:System.Data.DataTable> et défini sa structure à l'aide de colonnes et de contraintes, vous pouvez ajouter de nouvelles lignes de données à la table.  Pour ajouter une nouvelle ligne, déclarez une nouvelle variable comme type <xref:System.Data.DataRow>.  Un nouvel objet **DataRow** est retourné lorsque vous appelez la méthode <xref:System.Data.DataTable.NewRow%2A>.  Le **DataTable** créé ensuite l'objet **DataRow** en fonction de la structure de la table, telle que définie par l'objet <xref:System.Data.DataColumnCollection>.  
  
 L'exemple suivant montre comment créer une ligne en appelant la méthode **NewRow**.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Vous pouvez ensuite manipuler la ligne ajoutée en utilisant un index ou le nom de colonne, comme le montre l'exemple suivant.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Une fois que les données ont été insérées dans la nouvelle ligne, la méthode **Add** est utilisée pour ajouter la ligne à l'objet <xref:System.Data.DataRowCollection>, comme dans le code suivant.  
  
```vb  
workTable.Rows.Add(workRow)  
  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Vous pouvez également appeler la méthode **Add** pour ajouter une nouvelle ligne en passant un tableau de valeurs, de type <xref:System.Object>, comme le montre l'exemple suivant.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Le passage d'un tableau de valeurs, de type **Object**, à la méthode **Add** crée une ligne dans la table et attribue à ses valeurs de colonnes les valeurs du tableau d'objet.  Notez que les valeurs du tableau correspondent de façon séquentielle aux colonnes, en fonction de leur ordre d'apparition dans la table.  
  
 L'exemple suivant ajoute 10 lignes à la nouvelle table **Customers**.  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## Voir aussi  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataRowCollection>   
 <xref:System.Data.DataTable>   
 [Manipulation de données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)