---
title: "Proc&#233;dure&#160;: personnaliser des classes d&#39;entit&#233; &#224; l&#39;aide de l&#39;&#233;diteur de code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: personnaliser des classes d&#39;entit&#233; &#224; l&#39;aide de l&#39;&#233;diteur de code
Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent créer ou personnaliser leurs classes d'entité à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].  
  
 Vous pouvez également utiliser l'éditeur de code [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] pour écrire votre propre code de mappage ou personnaliser du code qui a déjà été généré.  Pour plus d'informations, consultez [Mappage basé sur les attributs](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
 Les rubriques de cette section décrivent comment personnaliser votre modèle objet.  
  
 [Procédure : spécifier des noms de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
 [Procédure : représenter des tables en tant que classes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
 [Procédure : représenter des colonnes en tant que membres de classe](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
 [Procédure : représenter des clés primaires](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
 [Procédure : mapper des relations de base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 Fournit des exemples d'utilisation de l'attribut <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
 [Procédure : représenter des colonnes en tant que colonnes générées par une base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.  
  
 [Procédure : représenter des colonnes en tant que colonnes timestamp ou version](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 [Procédure : spécifier des types de données de base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
 [Procédure : représenter des colonnes calculées](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
 [Procédure : spécifier des champs de stockage privés](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.  
  
 [Procédure : représenter des colonnes en tant que colonnes autorisant les valeurs Null](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
 [Procédure : mapper des hiérarchies d'héritage](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 Décrit les mappages requis pour spécifier une hiérarchie d'héritage.  
  
 [Procédure : spécifier la vérification de conflits d'accès concurrentiel](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
## Voir aussi  
 [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)