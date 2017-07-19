---
title: "DataTableReaders | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTableReaders
L'objet <xref:System.Data.DataTableReader> présente le contenu d'un objet <xref:System.Data.DataTable> ou d'un objet <xref:System.Data.DataSet> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.  
  
 Lorsque vous créez un **DataTableReader** à partir d'un **DataTable**, l'objet **DataTableReader** obtenu contient un jeu de résultats contenant les mêmes données que le **DataTable** à partir duquel il a été créé, à l'exception des lignes marquées comme supprimées.  La colonne se présente dans le même ordre que le **DataTable** original.  
  
 Un **DataTableReader** peut contenir plusieurs jeux de résultats s'il a été créé par un appel à la méthode <xref:System.Data.DataSet.CreateDataReader%2A>.  Les résultats sont présentés dans le même ordre que les **DataTables** dans la collection <xref:System.Data.DataSet.Tables%2A> de l'objet **DataSet**.  
  
## Dans cette section  
 [Création d'un DataReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 Explique comment créer un objet **DataTableReader**.  
  
 [Navigation DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 Décrit l'utilisation de la méthode **Read** pour se déplacer dans le contenu d'un **DataTableReader**.  
  
## Voir aussi  
 [Extraction et modification de données dans ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)