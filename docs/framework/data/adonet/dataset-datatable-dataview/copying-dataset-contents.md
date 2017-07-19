---
title: "Copie du contenu d&#39;un DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Copie du contenu d&#39;un DataSet
Vous pouvez créer une copie d'un objet <xref:System.Data.DataSet> pour pouvoir travailler sur ses données sans affecter les données d'origine ou travailler sur un sous\-ensemble des données d'un **DataSet**.  Lorsque vous copiez un **DataSet**, vous pouvez effectuer l'une des actions suivantes :  
  
-   Créer une copie exacte du **DataSet**, y compris les informations de schéma, les données, l'état des lignes et leur version.  
  
-   Créer un **DataSet** qui contient le schéma d'un **DataSet** existant, mais uniquement les lignes qui ont été modifiées.  Vous pouvez retourner toutes les lignes qui ont été modifiées ou seulement celles ayant un **DataRowState** spécifique.  Pour plus d'informations sur les états des lignes, voir [États et versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Copier uniquement le schéma, ou la structure relationnelle, du **DataSet**, en ne copiant aucune ligne.  Les lignes peuvent être importées dans un objet <xref:System.Data.DataTable> existant à l'aide de la méthode <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Pour créer une copie exacte du **DataSet** qui inclut à la fois le schéma et les données, utilisez la méthode <xref:System.Data.DataSet.Copy%2A> du **DataSet**.  L'exemple de code suivant montre comment créer une copie exacte du **DataSet**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Pour créer une copie d'un **DataSet** qui inclut le schéma et seulement les données représentant les lignes **Added**, **Modified** ou **Deleted**, utilisez la méthode <xref:System.Data.DataSet.GetChanges%2A> du **DataSet**.  Vous pouvez également utiliser **GetChanges** pour ne retourner que les lignes assorties d'un état de ligne spécifié en passant une valeur **DataRowState** lors de l'appel de **GetChanges**.  L'exemple de code suivant montre comment passer un **DataRowState** lors de l'appel de **GetChanges**.  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 Pour créer une copie d'un **DataSet** qui inclut uniquement le schéma, utilisez la méthode <xref:System.Data.DataSet.Clone%2A> du **DataSet**.  Vous pouvez aussi ajouter des lignes existantes au **DataSet** cloné à l'aide de la méthode **ImportRow** du **DataTable**.  **ImportRow** ajoute à la table spécifiée des données ainsi que des informations d'état et de version de ligne.  Les valeurs de colonne ne seront ajoutées que si le nom de colonne est identique et le type de données compatible.  
  
 L'exemple de code suivant crée un clone d'un **DataSet**, puis ajoute à la table **Customers** du clone du **DataSet** les lignes du **DataSet** d'origine relatives aux clients pour lesquels la colonne **CountryRegion** a la valeur « Germany ».  
  
```vb  
  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## Voir aussi  
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)