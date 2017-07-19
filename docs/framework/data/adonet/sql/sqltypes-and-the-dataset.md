---
title: "SqlTypes et le DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# SqlTypes et le DataSet
ADO.NET 2.0 a introduit une prise en charge de type avancée du `DataSet` via l'espace de noms <xref:System.Data.SqlTypes>.  Les types dans <xref:System.Data.SqlTypes> sont conçus pour fournir des types de données avec les mêmes sémantiques et précision que les types de données dans une base de données SQL Server.  Chaque type de données dans <xref:System.Data.SqlType> a un type de données équivalent dans SQL Server, avec la même représentation de données sous\-jacentes.  
  
 L'utilisation de <xref:System.Data.SqlTypes> directement dans un <xref:System.Data.DataSet> offre plusieurs avantages lors de l'utilisation de types de données SQL Server.  <xref:System.Data.SqlTypes> prend en charge la même sémantique que les types de données SQL Server natifs.  La spécification de l'un des <xref:System.Data.SqlTypes> dans la définition d'un <xref:System.Data.DataColumn> élimine la perte de précision qui peut résulter de la conversion des types de données décimales ou numériques en l'un des types de données Common Language Runtime \(CLR\).  
  
## Exemple  
 L'exemple suivant crée un objet <xref:System.Data.DataTable>, définissant de façon explicite les types de données <xref:System.Data.DataColumn> en utilisant des <xref:System.Data.SqlTypes> au lieu de types CLR.  Le code remplit l'objet <xref:System.Data.DataTable> à l'aide de données provenant de la table Sales.SalesOrderDetail de la base de données AdventureWorks dans SQL Server.  La sortie affichée dans la fenêtre de console présente le type de données de chaque colonne et les valeurs extraites de SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## Voir aussi  
 [Mappages de types de données SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)   
 [Configuration des paramètres et des types de données des paramètres](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)