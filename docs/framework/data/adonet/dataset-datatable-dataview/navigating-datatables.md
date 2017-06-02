---
title: "Navigation DataTables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Navigation DataTables
L'objet <xref:System.Data.DataTableReader> obtient le contenu d'un ou plusieurs objets <xref:System.Data.DataTable> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.  
  
 Un objet <xref:System.Data.DataTableReader> peut contenir plusieurs jeux de résultats s'il est créé à l'aide de la méthode <xref:System.Data.DataSet.CreateDataReader%2A>.  S'il y a plusieurs jeux de résultats, la méthode <xref:System.Data.DataTableReader.NextResult%2A> déplace le curseur sur le jeu de résultats suivant.  Il s'agit d'un processus en avant uniquement.  Il n'est pas possible de revenir à un jeu de résultats précédent.  
  
## Exemple  
 Dans l'exemple suivant, la méthode `TestConstructor` crée deux instances de <xref:System.Data.DataTable> `` .  Pour montrer ce constructeur pour la classe <xref:System.Data.DataTableReader>, l'exemple crée un nouveau **DataTableReader** basé sur un tableau contenant les deux **DataTables** et effectue une opération simple, en imprimant le contenu de quelques\-unes des premières colonnes sur la fenêtre de console.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## Voir aussi  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)