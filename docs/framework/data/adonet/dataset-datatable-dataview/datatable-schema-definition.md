---
title: "D&#233;finition du sch&#233;ma d&#39;un DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# D&#233;finition du sch&#233;ma d&#39;un DataTable
Le schéma, ou structure, d'une table est représenté par des colonnes et des contraintes.  Vous définissez le schéma d'un objet <xref:System.Data.DataTable> à l'aide d'objets <xref:System.Data.DataColumn> ainsi que d'objets <xref:System.Data.ForeignKeyConstraint> et <xref:System.Data.UniqueConstraint>.  Les colonnes d'une table peuvent mapper aux colonnes d'une source de données. Elles contiennent des valeurs calculées à partir d'expressions, incrémentent automatiquement leurs valeurs ou contiennent des valeurs de clé primaire.  
  
 Les références par nom aux colonnes, relations et contraintes d'une table respectent la casse.  Une table peut donc contenir plusieurs colonnes, relations ou contraintes dont les noms ne diffèrent que par la casse.  Vous pouvez, par exemple, avoir **Col1** et **col1**.  Dans ce cas, une référence par nom à l'une des colonnes doit correspondre exactement à la casse du nom de colonne. Sinon, une exception est levée.  Par exemple, si la table **myTable** contient les colonnes **Col1** et **col1**, vous devez référencer **Col1** par nom comme **myTable.Columns\["Col1"\]** et **col1** comme **myTable.Columns\["col1"\]**.  Si vous tentez de référencer l'une des colonnes comme **myTable.Columns\["COL1"\]**, une exception sera levée.  
  
 La règle de respect de la casse ne s'applique pas s'il n'existe qu'une seule colonne, relation ou contrainte ayant un nom particulier.  En d'autres termes, si aucun autre objet de colonne, relation ou contrainte de la table ne correspond au nom de cet objet de colonne, relation ou contrainte, vous pouvez référencer l'objet par son nom sans respecter la casse, sans qu'une exception ne soit levée.  Par exemple, si la table n'a que **Col1**, vous pouvez référencer cette colonne comme **my.Columns\["COL1"\]**.  
  
> [!NOTE]
>  La propriété <xref:System.Data.DataTable.CaseSensitive%2A> du **DataTable** n'affecte pas ce comportement.  La propriété **CaseSensitive** s'applique aux données de la table et affecte les contraintes de tri, de recherche, de filtrage, d'application, etc., mais pas les références aux colonnes, relations et contraintes.  
  
## Dans cette section  
 [Ajout de colonnes à un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 Décrit comment définir les colonnes d'une table à l'aide d'objets **DataColumn**.  
  
 [Création de colonnes d'expression](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Explique comment utiliser la propriété **Expression** d'une colonne pour calculer des valeurs en fonction des valeurs d'autres colonnes de la ligne.  
  
 [Création de colonnes AutoIncrement](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 Décrit comment définir une colonne afin qu'elle incrémente automatiquement des valeurs numériques de façon à garantir le caractère unique des valeurs de colonne d'une ligne.  
  
 [Définition des clés primaires](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 Décrit comment spécifier la clé primaire d'une table à partir d'un ou plusieurs objets **DataColumn**.  
  
 [Contraintes DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 Décrit comment définir des contraintes uniques et de clé étrangère pour les colonnes d'une table.  
  
## Voir aussi  
 [DataTable, objets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)