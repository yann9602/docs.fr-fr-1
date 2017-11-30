---
title: "Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9ac8e64c02d96450d41233cfbe65e1db839df9e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet
Le langage XSD (XML Schema Definition) permet la spécification de contraintes sur les éléments et attributs qu'il définit. Lors du mappage d’un schéma XML au schéma relationnel d’un <xref:System.Data.DataSet>, contraintes de schéma XML sont mappées aux contraintes relationnelles appropriées sur les tables et colonnes dans le **DataSet**.  
  
 Cette section présente le mappage des contraintes de schéma XML suivantes :  
  
-   Contrainte unique spécifiée à l’aide de la **unique** élément.  
  
-   La contrainte de clé spécifiée à l’aide de la **clé** élément.  
  
-   La contrainte keyref spécifiée à l’aide de la **keyref** élément.  
  
 En utilisant une contrainte sur un élément ou un attribut, vous spécifiez certaines restrictions sur les valeurs de l'élément dans toute instance du document. Par exemple, une contrainte de clé sur un **CustomerID** élément enfant d’un **client** élément dans le schéma indique que les valeurs de la **CustomerID** élément enfant doit être unique dans toute instance du document, et que les valeurs null ne sont pas autorisés.  
  
 Des contraintes peuvent également être spécifiées entre les éléments et les attributs figurant dans un document afin d'établir une relation dans ce document. Les contraintes key et keyref sont utilisées dans le schéma pour spécifier les contraintes au sein du document, créant ainsi une relation entre éléments et attributs du document.  
  
 Le processus de mappage convertit ces contraintes de schéma en contraintes appropriées sur les tables créées dans le **DataSet**.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mapper des contraintes uniques de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes uniques dans un **DataSet**.  
  
 [Clé de mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé (contraintes uniques où les valeurs null ne sont pas autorisées) dans un **DataSet**.  
  
 [Mapper keyref de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes (clé étrangère) dans keyref un **DataSet**.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Structure relationnelle des DataSet qui dérivent de schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d’un **DataSet** qui est créé à partir du schéma XSD.  
  
 [Génération des Relations d’un DataSet à partir de schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Décrit les éléments de schéma XML utilisés pour créer des relations entre les colonnes de table dans un **DataSet**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
