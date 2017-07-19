---
title: "Inf&#233;rence des relations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Inf&#233;rence des relations
Si un élément déduit en tant que table comporte un élément enfant également déduit en tant que table, un objet <xref:System.Data.DataRelation> sera créé entre les deux tables.  Une nouvelle colonne, nommée **ParentTableName\_Id** sera ajoutée aux deux tables ; celle qui a été créée pour l'élément parent et celle qui l'a été pour l'élément enfant.  La propriété **ColumnMapping** de cette colonne d'identité aura pour valeur **MappingType.Hidden**.  La colonne constituera une clé primaire auto\-incrémentée pour la table parente et sera utilisée pour le **DataRelation** entre les deux tables.  Le type de données de la colonne d'identité ajoutée sera **System.Int32**, à la différence du type de données de toutes les autres colonnes déduites, qui est **System.String**.  Un objet <xref:System.Data.ForeignKeyConstraint> avec **DeleteRule** \= **Cascade** sera également créé à l'aide de la nouvelle colonne dans les tables parente et enfant.  
  
 Examinons, par exemple, le code XML suivant :  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produira deux tables : **Element1** et **ChildElement1**.  
  
 La table **Element1** aura deux colonnes : **Element1\_Id** et **ChildElement2**.  La propriété **ColumnMapping** de la colonne **Element1\_Id** aura pour valeur **MappingType.Hidden**.  La propriété **ColumnMapping** de la colonne **ChildElement2** aura pour valeur **MappingType.Element**.  La colonne **Element1\_Id** sera définie comme clé primaire de la table **Element1**.  
  
 La table **ChildElement1** aura trois colonnes : **attr1**, **attr2** et **Element1\_Id**.  La propriété **ColumnMapping** des colonnes **attr1** et **attr2** aura pour valeur **MappingType.Attribute**.  La propriété **ColumnMapping** de la colonne **Element1\_Id** aura pour valeur **MappingType.Hidden**.  
  
 Un **DataRelation** et un **ForeignKeyConstraint** seront créés à l'aide des colonnes **Element1\_Id** des deux tables.  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|Element1\_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Table :** ChildElement1  
  
|attr1|attr2|Element1\_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation :** Element1\_ChildElement1  
  
 **ParentTable :** Element1  
  
 **ParentColumn :** Element1\_Id  
  
 **ChildTable :** ChildElement1  
  
 **ChildColumn :** Element1\_Id  
  
 **Imbriqué :** True  
  
 **ForeignKeyConstraint :** Element1\_ChildElement1  
  
 **Column :** Element1\_Id  
  
 **ParentTable :** Element1  
  
 **ChildTable :** ChildElement1  
  
 **DeleteRule :** Cascade  
  
 **AcceptRejectRule :** Aucun  
  
## Voir aussi  
 [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [Imbrication de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)   
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)