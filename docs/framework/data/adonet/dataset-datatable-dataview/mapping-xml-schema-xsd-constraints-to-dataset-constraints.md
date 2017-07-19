---
title: "Mappage de contraintes de sch&#233;ma XML (XSD) &#224; des contraintes de DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Mappage de contraintes de sch&#233;ma XML (XSD) &#224; des contraintes de DataSet
Le langage XSD \(XML Schema Definition\) permet la spécification de contraintes sur les éléments et attributs qu'il définit.  Lors du mappage d'un schéma XML au schéma relationnel d'un objet <xref:System.Data.DataSet>, les contraintes du schéma XML sont mappées aux contraintes relationnelles appropriées sur les tables et les colonnes contenues dans le **DataSet**.  
  
 Cette section présente le mappage des contraintes de schéma XML suivantes :  
  
-   contrainte unique spécifiée à l'aide de l'élément **unique** ;  
  
-   contrainte de clé spécifiée à l'aide de l'élément **key** ;  
  
-   contrainte de référence à une clé spécifiée à l'aide de l'élément **keyref**.  
  
 En utilisant une contrainte sur un élément ou un attribut, vous spécifiez certaines restrictions sur les valeurs de l'élément dans toute instance du document.  Par exemple, une contrainte de clé sur un élément enfant **CustomerID** d'un élément **Customer** dans le schéma indique que les valeurs de l'élément enfant **CustomerID** doivent être uniques dans toute instance du document et que les valeurs null ne sont pas autorisées.  
  
 Des contraintes peuvent également être spécifiées entre les éléments et les attributs figurant dans un document afin d'établir une relation dans ce document.  Les contraintes key et keyref sont utilisées dans le schéma pour spécifier les contraintes au sein du document, créant ainsi une relation entre éléments et attributs du document.  
  
 Le processus de mappage convertit ces contraintes de schéma en contraintes appropriées sur les tables créées dans le **DataSet**.  
  
## Dans cette section  
 [Mapper des contraintes de schéma XML \(XSD\) uniques sur des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML qui servent à créer des contraintes uniques dans un **DataSet**.  
  
 [Mapper des contraintes de schéma XML \(XSD\) key sur des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML qui servent à créer des contraintes de clé \(contraintes uniques où les valeurs null ne sont pas autorisées\) dans un **DataSet**.  
  
 [Mapper des contraintes de schéma XML \(XSD\) keyref sur des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML qui servent à créer des contraintes keyref \(clé étrangère\) dans un **DataSet**.  
  
## Rubriques connexes  
 [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d'un **DataSet** créé à partir d'un schéma XSD.  
  
 [Génération des relations d'un DataSet à partir d'un schéma XSD \(XML Schema Definition\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Décrit les éléments de schéma XML qui servent à créer des relations entre les colonnes de table dans un **DataSet**.  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)