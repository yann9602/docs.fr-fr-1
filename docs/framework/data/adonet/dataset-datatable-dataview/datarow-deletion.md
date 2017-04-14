---
title: "Suppresion d&#39;un objet DataRow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Suppresion d&#39;un objet DataRow
Il existe deux méthodes pour supprimer un objet <xref:System.Data.DataRow> d'un objet <xref:System.Data.DataTable> : la méthode **Remove** de l'objet <xref:System.Data.DataRowCollection>, et la méthode <xref:System.Data.DataRow.Delete%2A> de l'objet **DataRow**.  La méthode <xref:System.Data.DataRowCollection.Remove%2A> supprime un **DataRow** du **DataRowCollection**. La méthode <xref:System.Data.DataRow.Delete%2A> marque seulement la ligne pour suppression.  La suppression réelle ne se produit que lorsque l'application appelle la méthode **AcceptChanges**.  En utilisant <xref:System.Data.DataRow.Delete%2A>, vous pouvez vérifier par programme les lignes marquées pour suppression avant de les supprimer.  Lorsqu'une ligne est marquée pour suppression, sa propriété <xref:System.Data.DataRow.RowState%2A> prend la valeur <xref:System.Data.DataRow.Delete%2A>.  
  
 Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne doivent être appelées dans une boucle foreach lors de l'itération au sein d'un objet <xref:System.Data.DataRowCollection>.  Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne modifient l'état de la collection.  
  
 Lors de l'utilisation d'un objet <xref:System.Data.DataSet> ou d'un **DataTable** avec un **DataAdapter** et une source de données relationnelle, utilisez la méthode **Delete** de **DataRow** pour supprimer la ligne.  La méthode **Delete** marque la ligne comme **Deleted** dans le **DataSet** ou le **DataTable** mais ne la supprime pas.  Lorsque le **DataAdapter** rencontre une ligne marquée comme **Deleted**, il exécute sa méthode **DeleteCommand** pour supprimer la ligne au niveau de la source de données.  La ligne peut ensuite être supprimée de manière permanente à l'aide de la méthode **AcceptChanges**.  Si vous utilisez **Remove** pour supprimer la ligne, celle\-ci sera entièrement supprimée de la table mais **DataAdapter** ne supprimera pas la ligne au niveau de la source de données.  
  
 La méthode **Remove** du **DataRowCollection** prend un **DataRow** comme argument et le supprime de la collection, comme le montre l'exemple suivant.  
  
```vb  
workTable.Rows.Remove(workRow)  
  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Par opposition, l'exemple suivant montre comment appeler la méthode **Delete** sur un **DataRow** pour modifier son **RowState** en **Deleted**.  
  
```vb  
workRow.Delete  
  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Si une ligne est marquée pour suppression et si vous appelez la méthode **AcceptChanges** de l'objet **DataTable**, la ligne est supprimée du **DataTable**.  Par contre, si vous appelez **RejectChanges**, le **RowState** de la ligne revient à la valeur qu'il avait avant d'être marqué comme **Deleted**.  
  
> [!NOTE]
>  Si le **RowState** d'un **DataRow** a la valeur **Added** \(indiquant qu'il vient juste d'être ajouté à la table\) et s'il est ensuite marqué comme **Deleted**, il est supprimé de la table.  
  
## Voir aussi  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataRowCollection>   
 <xref:System.Data.DataTable>   
 [Manipulation de données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)