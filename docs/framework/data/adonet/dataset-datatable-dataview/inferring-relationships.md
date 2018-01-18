---
title: "Déduction des relations"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 79f79c1dbc74b98cff10de81c2bd7bd32d7d286b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-relationships"></a>Déduction des relations
Si un élément déduit en tant que table comporte un élément enfant également déduit en tant que table, un objet <xref:System.Data.DataRelation> sera créé entre les deux tables. Une nouvelle colonne avec un nom de **ParentTableName_Id** sera ajouté à la table créée par l’élément parent et la table créée pour l’élément enfant. Le **ColumnMapping** propriété de cette colonne d’identité est fixée à **MappingType.Hidden**. La colonne est une clé primaire auto-incrémentée pour la table parente et sera utilisée pour le **DataRelation** entre les deux tables. Le type de données de la colonne d’identité ajoutée sera **System.Int32**, contrairement au type de données de toutes les autres colonnes déduites, qui est **System.String**. A <xref:System.Data.ForeignKeyConstraint> avec **DeleteRule** = **Cascade** sera également créé à l’aide de la nouvelle colonne dans les tables parent et enfant.  
  
 Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Le processus d’inférence produira deux tables : **Element1** et **ChildElement1**.  
  
 Le **Element1** table aura deux colonnes : **Element1_Id** et **ChildElement2**. Le **ColumnMapping** propriété de la **Element1_Id** colonne a la valeur **MappingType.Hidden**. Le **ColumnMapping** propriété de la **ChildElement2** colonne a la valeur **MappingType.Element**. Le **Element1_Id** colonne sera définie comme clé primaire de la **Element1** table.  
  
 Le **ChildElement1** table aura trois colonnes : **attr1**, **attr2** et **Element1_Id**. Le **ColumnMapping** propriété pour le **attr1** et **attr2** colonnes aura pour valeur **MappingType.Attribute**. Le **ColumnMapping** propriété de la **Element1_Id** colonne a la valeur **MappingType.Hidden**.  
  
 A **DataRelation** et **ForeignKeyConstraint** sera créé à l’aide de la **Element1_Id** colonnes des deux tables.  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Table :** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation :** Element1_ChildElement1  
  
 **ParentTable :** Element1  
  
 **ParentColumn :** Element1_Id  
  
 **ChildTable :** ChildElement1  
  
 **ChildColumn :** Element1_Id  
  
 **Imbriqué :** True  
  
 **ForeignKeyConstraint :** Element1_ChildElement1  
  
 **Colonne :** Element1_Id  
  
 **ParentTable :** Element1  
  
 **ChildTable :** ChildElement1  
  
 **DeleteRule :** en Cascade  
  
 **AcceptRejectRule :** None  
  
## <a name="see-also"></a>Voir aussi  
 [Inférence de la structure relationnelle d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Chargement d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Chargement des informations de schéma de DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Imbrication de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
