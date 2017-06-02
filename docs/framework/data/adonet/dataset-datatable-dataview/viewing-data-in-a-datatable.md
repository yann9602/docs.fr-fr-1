---
title: "Visualisation de donn&#233;es dans un DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Visualisation de donn&#233;es dans un DataTable
Vous pouvez accéder au contenu d'un objet <xref:System.Data.DataTable> à l'aide des collections **Rows** et **Columns** du **DataTable**.  Vous pouvez également utiliser la méthode <xref:System.Data.DataTable.Select%2A> pour retourner des sous\-ensembles des données d'un **DataTable** en fonction de certains critères, notamment des critères de recherche, l'ordre de tri et l'état de la ligne.  De plus, vous pouvez utiliser la méthode <xref:System.Data.DataRowCollection.Find%2A> du **DataRowCollection** lorsque vous recherchez une ligne particulière à l'aide d'une valeur de clé primaire.  
  
 La méthode **Select** de l'objet **DataTable** retourne un ensemble d'objets <xref:System.Data.DataRow> correspondant aux critères spécifiés.  **Select** prend des arguments facultatifs d'une expression de filtre, une expression de tri et **DataViewRowState**.  L'expression de filtre identifie la ligne à retourner en fonction des valeurs de **DataColumn**, telles que `LastName = 'Smith'`.  L'expression de tri respecte les conventions SQL standard de tri des colonnes, comme `LastName ASC, FirstName ASC`.  Pour des informations sur les règles d'écriture des expressions, voir la propriété <xref:System.Data.DataColumn.Expression%2A> de la classe **DataColumn**.  
  
> [!TIP]
>  Si vous devez effectuer plusieurs appels à la méthode **Select** d'un **DataTable**, vous pouvez améliorer les performances en créant préalablement un objet <xref:System.Data.DataView> pour le **DataTable**.  La création du **DataView** indexe les lignes de la table.  La méthode **Select** utilise ensuite cet index, ce qui réduit sensiblement le temps nécessaire pour générer les résultats de la requête.  Pour plus d'informations sur la création d'un **DataView** pour un **DataTable**, voir [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 La méthode **Select** détermine la version des lignes à afficher ou à manipuler, en fonction d'un objet <xref:System.Data.DataViewRowState>.  Le tableau suivant répertorie les valeurs possibles d'énumération **DataViewRowState**.  
  
|Valeur DataViewRowState|Description|  
|-----------------------------|-----------------|  
|**CurrentRows**|Les lignes en cours comprennent les lignes non modifiées, les lignes ajoutées et les lignes modifiées.|  
|**Supprimé**|Ligne supprimée.|  
|**ModifiedCurrent**|Une version actuelle, qui est une version modifiée des données d'origine.  \(Voir **ModifiedOriginal**.\)|  
|**ModifiedOriginal**|La version d'origine de toutes les lignes modifiées.  La version actuelle est disponible à l'aide de **ModifiedCurrent**.|  
|**Added**|Nouvelle ligne.|  
|**None**|Aucun|  
|**OriginalRows**|Les lignes d'origine, notamment les lignes non modifiées et les lignes supprimées.|  
|**Inchangé**|Ligne non modifiée.|  
  
 Dans l'exemple suivant, l'objet **DataSet** est filtré de sorte que vous n'utilisiez que les lignes dont le **DataViewRowState** a la valeur **CurrentRows**.  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 La méthode **Select** peut être utilisée pour retourner des lignes ayant des valeurs de champs ou des valeurs **RowState** différentes.  L'exemple suivant retourne un tableau **DataRow** qui référence toutes les lignes supprimées, ainsi qu'un autre tableau **DataRow** qui référence toutes les lignes, classées par **CustLName**, où la colonne **CustID** est supérieure à 5.  Pour plus d'informations sur l'affichage des informations de la ligne **Deleted**, consultez [États et versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## Voir aussi  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataViewRowState>   
 [Manipulation de données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [États et versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)