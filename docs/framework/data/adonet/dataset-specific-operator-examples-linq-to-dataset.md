---
title: "Exemple d&#39;op&#233;rateurs sp&#233;cifiques aux DataSets (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Exemple d&#39;op&#233;rateurs sp&#233;cifiques aux DataSets (LINQ to DataSet)
Les exemples de cette rubrique montrent comment utiliser la méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> et la classe <xref:System.Data.DataRowComparer>.  
  
 La méthode `FillDataSet` utilisée dans ces exemples est spécifiée dans [Chargement de données dans un DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.  
  
 Les exemples de cette rubrique utilisent les instructions `using`\/`Imports` suivantes :  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Pour plus d'informations, consultez [Procédure : créer un projet LINQ to DataSet dans Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## CopyToDataTable  
  
### Exemple  
 Cet exemple montre comment charger un <xref:System.Data.DataTable> avec les résultats de la requête à l'aide de la méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
```  
  
```  
  
## DataRowComparer  
  
### Exemple  
 Cet exemple montre comment comparer deux lignes de données différentes à l'aide de <xref:System.Data.DataRowComparer>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## Voir aussi  
 [Chargement de données dans un DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)   
 [Exemples de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)