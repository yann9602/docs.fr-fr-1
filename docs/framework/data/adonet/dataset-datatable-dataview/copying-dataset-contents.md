---
title: Copie de contenu de DataSet
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
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bdeb462955816a53372719bf374f7d4b55aa7f18
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="copying-dataset-contents"></a>Copie de contenu de DataSet
Vous pouvez créer une copie d’un <xref:System.Data.DataSet> afin que vous pouvez utiliser des données sans affecter les données d’origine ou travailler avec un sous-ensemble des données à partir d’un **DataSet**. Lorsque vous copiez un **DataSet**, vous pouvez :  
  
-   Créer une copie exacte de la **DataSet**, y compris le schéma, les données, les informations d’état de ligne et les versions de ligne.  
  
-   Créer un **DataSet** qui contient le schéma d’un objet **DataSet**, mais uniquement les lignes qui ont été modifiées. Vous pouvez retourner toutes les lignes qui ont été modifiées, ou spécifier un spécifique **DataRowState**. Pour plus d’informations sur l’état des lignes, consultez [état des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Copier le schéma ou la structure relationnelle, de la **DataSet** uniquement, sans copie toutes les lignes. Les lignes peuvent être importées dans un objet <xref:System.Data.DataTable> existant à l'aide de la méthode <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Pour créer une copie exacte de la **DataSet** qui inclut le schéma et les données, utilisez la <xref:System.Data.DataSet.Copy%2A> méthode de la **DataSet**. L’exemple de code suivant montre comment créer une copie exacte de la **DataSet**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Pour créer une copie d’un **DataSet** qui inclut le schéma et seulement les données représentant **Added**, **modifié**, ou **Deleted** lignes, utilisez le <xref:System.Data.DataSet.GetChanges%2A> méthode de la **DataSet**. Vous pouvez également utiliser **GetChanges** pour retourner uniquement les lignes avec un état de ligne spécifié en passant une **DataRowState** valeur lors de l’appel **GetChanges**. L’exemple de code suivant montre comment passer un **DataRowState** lors de l’appel **GetChanges**.  
  
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
  
 Pour créer une copie d’un **DataSet** qui inclut uniquement le schéma, utilisez la <xref:System.Data.DataSet.Clone%2A> méthode de la **DataSet**. Vous pouvez également ajouter des lignes existantes à cloné **DataSet** à l’aide de la **ImportRow** méthode de la **DataTable**. **ImportRow** ajoute des données, état de ligne et les informations de version de ligne à la table spécifiée. Les valeurs de colonne ne seront ajoutées que si le nom de colonne est identique et le type de données compatible.  
  
 L’exemple de code suivant crée un clone d’un **DataSet** , puis ajoute les lignes à partir de la version d’origine **DataSet** à la **clients** de table dans le **jeu de données**  clone pour les clients où le **CountryRegion** colonne a la valeur « Germany ».  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
