---
title: "Inf&#233;rence de la structure relationnelle d&#39;un DataSet &#224; partir de XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Inf&#233;rence de la structure relationnelle d&#39;un DataSet &#224; partir de XML
La structure relationnelle, ou schéma, d'un objet <xref:System.Data.DataSet> est constituée de tables, de colonnes, de contraintes et de relations.  Lors du chargement d'un objet <xref:System.Data.DataSet> à partir de XML, le schéma peut être prédéfini ou créé, explicitement ou par inférence, à partir du XML en cours de chargement.  Pour plus d'informations sur le chargement du schéma et du contenu d'un objet <xref:System.Data.DataSet> à partir de XML, voir [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) et [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
 Si le schéma d'un objet <xref:System.Data.DataSet> est créé à partir de XML, la méthode conseillée consiste à spécifier explicitement le schéma en utilisant le langage XSD \(XML Schema Definition\) \(comme décrit dans [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)\) ou XDR \(XML\-Data Reduced\).  Si aucun schéma XML ou XDR n'est disponible dans le XML, le schéma de l'objet <xref:System.Data.DataSet> peut être déduit de la structure des éléments et attributs XML.  
  
 Cette section décrit les règles d'inférence du schéma de l'objet <xref:System.Data.DataSet> en montrant les éléments et attributs XML et leur structure, ainsi que le schéma de l'objet <xref:System.Data.DataSet> obtenu par inférence.  
  
 Tous les attributs présents dans un document XML ne doivent pas être inclus dans le processus d'inférence.  Les attributs qualifiés par espaces de noms peuvent inclure des métadonnées revêtant une importance pour le document XML mais pas pour le schéma de l'objet <xref:System.Data.DataSet>.  En utilisant la méthode <xref:System.Data.DataSet.InferXmlSchema%2A>, vous pouvez définir des espaces de noms spécifiques qui devront être ignorés au cours du processus d'inférence.  Pour plus d'informations, consultez [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
## Dans cette section  
 [Résumé du processus d'inférence du schéma d'un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 Propose un résumé succinct des règles qui permettent de déduire le schéma d'un objet <xref:System.Data.DataSet> à partir de XML.  
  
 [Inférence des tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 Décrit les éléments XML qui sont déduits en tant que tables dans un objet <xref:System.Data.DataSet>.  
  
 [Inférence des colonnes](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 Décrit les éléments et attributs XML qui sont déduits en tant que colonnes de table.  
  
 [Inférence des relations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 Décrit les objets <xref:System.Data.DataRelation> et <xref:System.Data.ForeignKeyConstraint> créés pour les tables imbriquées déduites.  
  
 [Inférence du texte des éléments](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 Décrit les colonnes créées pour le texte figurant dans les éléments XML et explique les cas où ce texte est ignoré.  
  
 [Limitations applicables à l'inférence](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 Présente les limitations liées à l'inférence des schémas.  
  
## Rubriques connexes  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Explique comment l'objet <xref:System.Data.DataSet> interagit avec des données XML.  
  
 [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d'un objet <xref:System.Data.DataSet> créée à partir d'un schéma en langage XSD \(XML Schema Definition\).  
  
 [Vue d'ensemble d'ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Décrit l'architecture et les composants d'ADO.NET ainsi que la façon de les utiliser pour accéder à des sources de données existantes et pour gérer des données d'application.  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)