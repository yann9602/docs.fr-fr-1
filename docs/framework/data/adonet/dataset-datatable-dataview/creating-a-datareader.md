---
title: "Cr&#233;ation d&#39;un DataReader | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Cr&#233;ation d&#39;un DataReader
Les classes <xref:System.Data.DataTable> et <xref:System.Data.DataSet> ont une méthode <xref:System.Data.DataTable.CreateDataReader%2A> qui retourne le contenu de la collection <xref:System.Data.DataSet.Tables%2A> de l'objet <xref:System.Data.DataTable> ou de l'objet <xref:System.Data.DataSet> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.  
  
## Exemple  
 L'application console suivante crée une instance de l'objet <xref:System.Data.DataTable>.  Cet exemple passe ensuite le <xref:System.Data.DataTable> `` rempli à une procédure qui appelle la méthode <xref:System.Data.DataTable.CreateDataReader%2A> qui itère au sein des résultats contenus dans <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 L'exemple affiche la sortie suivante dans la fenêtre de console :  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## Voir aussi  
 <xref:System.Data.DataTable.CreateDataReader%2A>   
 <xref:System.Data.DataSet.CreateDataReader%2A>   
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)