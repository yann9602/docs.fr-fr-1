---
title: "Interrogation de DataSets (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Interrogation de DataSets (LINQ to DataSet)
Une fois qu'un objet <xref:System.Data.DataSet> a été rempli avec des données, vous pouvez commencer de l'interroger.  La formulation de requêtes avec [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] est semblable à l'utilisation de [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] sur d'autres sources de données [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].  N'oubliez pas cependant que, lorsque vous utilisez des requêtes [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sur un objet <xref:System.Data.DataSet>, vous interrogez une énumération d'objets <xref:System.Data.DataRow>, plutôt qu'une énumération d'un type personnalisé.  Cela signifie que vous pouvez utiliser n'importe quel membre de la classe <xref:System.Data.DataRow> dans vos requêtes [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].  Vous pouvez ainsi créer des requêtes riches et complexes.  
  
 Comme avec d'autres implémentations de [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], vous pouvez créer des requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] de deux formes différentes : syntaxe d'expression de requête et syntaxe de requête fondée sur une méthode.  Pour plus d'informations sur ces deux formes, consultez [Getting Started with LINQ](http://msdn.microsoft.com/fr-fr/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Vous pouvez utiliser une syntaxe d'expression de requête ou une syntaxe de requête fondée sur une méthode sur des tables uniques d'un <xref:System.Data.DataSet>, sur plusieurs tables sur un <xref:System.Data.DataSet>, ou sur les tables d'un <xref:System.Data.DataSet> typé.  
  
## Dans cette section  
 [Requêtes d'analyse unique](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Explique comment exécuter des requêtes d'analyse unique.  
  
 [Requêtes d'analyse croisée](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Explique comment exécuter des requêtes d'analyse croisée.  
  
 [Interrogation de DataSets typés](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Explique comment interroger des objets <xref:System.Data.DataSet> typés.  
  
## Voir aussi  
 [Exemples de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)   
 [Chargement de données dans un DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)