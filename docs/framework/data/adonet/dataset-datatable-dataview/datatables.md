---
title: "DataTable, objets | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable, objets
Un objet <xref:System.Data.DataSet> est constitué d'une collection de tables, de relations et de contraintes.  Dans ADO.NET, les objets <xref:System.Data.DataTable> sont utilisés pour représenter les tables dans un **DataSet**.  Un **DataTable** représente une table de données relationnelles en mémoire ; ces données sont des données locales de l'application .NET dans laquelle réside la table, mais celle\-ci peut être remplie à partir d'une source de données telle que Microsoft SQL Server en utilisant un **DataAdapter**. Pour plus d'informations, voir [Remplissage d'un DataSet à partir d'un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).  
  
 La classe **DataTable** est membre de l'espace de noms **System.Data** de la bibliothèque de classes .NET Framework.  Vous pouvez créer et utiliser un **DataTable** de façon indépendante ou en tant que membre d'un **DataSet**. Les objets **DataTable** peuvent également être utilisés avec d'autres objets .NET Framework, notamment l'objet <xref:System.Data.DataView>.  Vous accédez à la collection de tables d'un **DataSet** via la propriété **Tables** de l'objet **DataSet**.  
  
 Le schéma, ou structure, d'une table est représenté par des colonnes et des contraintes.  Vous définissez le schéma d'un **DataTable** à l'aide d'objets <xref:System.Data.DataColumn> ainsi que d'objets <xref:System.Data.ForeignKeyConstraint> et <xref:System.Data.UniqueConstraint>.  Les colonnes d'une table peuvent mapper aux colonnes d'une source de données. Elles contiennent des valeurs calculées à partir d'expressions, incrémentent automatiquement leurs valeurs ou contiennent des valeurs de clé primaire.  
  
 Outre un schéma, un **DataTable** doit également avoir des lignes pour contenir et trier les données.  La classe <xref:System.Data.DataRow> représente les données en cours contenues dans une table.  Vous utilisez le **DataRow** ainsi que ses propriétés et méthodes pour extraire, évaluer et manipuler les données d'une table.  Lorsque vous accédez aux données d'une ligne et que vous les modifiez, l'objet **DataRow** conserve leur état d'origine et leur état actuel.  
  
 Vous pouvez créer des relations parent\-enfant entre des tables à l'aide d'une ou plusieurs colonnes connexes de ces tables.  Vous créez une relation entre des objets **DataTable** à l'aide d'un objet <xref:System.Data.DataRelation>.  Les objets **DataRelation** peuvent ensuite être utilisés pour retourner les lignes connexes enfants ou parentes d'une ligne particulière.  Pour plus d'informations, consultez [Ajout d'objets DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## Dans cette section  
 [Création d'un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Explique comment créer un **DataTable** et l'ajouter à un **DataSet**.  
  
 [Définition du schéma d'un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Fournit des informations sur la création et l'utilisation de contraintes et d'objets **DataColumn**.  
  
 [Manipulation de données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Explique comment ajouter, modifier et supprimer des données dans une table.  Explique comment utiliser des événements **DataTable** pour examiner les modifications des données dans la table.  
  
 [Gestion des événements DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Fournit des informations sur les événements disponibles pouvant être utilisés avec un **DataTable**, notamment les événements liés aux modifications de valeurs de colonne et à l'ajout ou à la suppression de lignes.  
  
## Rubriques connexes  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Décrit l'architecture et les composants d'ADO.NET ainsi que la façon de les utiliser pour accéder à des sources de données existantes et pour gérer des données d'application.  
  
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Fournit des informations sur le **DataSet** ADO.NET, notamment sur la façon de créer des relations entre les tables.  
  
 [Classe de contrainte](frlrfSystemDataConstraintClassTopic)  
 Fournit des informations de référence sur l'objet **Constraint**.  
  
 [Classe DataColumn](frlrfSystemDataDataColumnClassTopic)  
 Fournit des informations de référence sur l'objet **DataColumn**.  
  
 [Classe DataSet](frlrfSystemDataDataSetClassTopic)  
 Fournit des informations de référence sur l'objet **DataSet**.  
  
 [Classe DataTable](frlrfSystemDataDataTableClassTopic)  
 Fournit des informations de référence sur l'objet **DataTable**.  
  
 [Vue d'ensemble de la bibliothèque de classes](../../../../../docs/standard/class-library-overview.md)  
 Donne une vue d'ensemble de la bibliothèque de classes .NET Framework, notamment l'espace de noms **System** ainsi que son espace de noms de deuxième niveau **System.Data**.  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)