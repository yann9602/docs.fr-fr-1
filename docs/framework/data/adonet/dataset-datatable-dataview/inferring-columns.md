---
title: "Inf&#233;rence des colonnes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Inf&#233;rence des colonnes
Après avoir déterminé les éléments à déduire en tant que tables pour un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET déduit les colonnes pour ces tables.  ADO.NET 2.0 a introduit un nouveau moteur d'inférence de schéma qui déduit un type de données fortement typées pour chaque élément **simpleType**.  Dans les versions précédentes, le type de données d'un élément **simpleType** déduit était toujours **xsd:string**.  
  
## Migration et compatibilité ascendante  
 La méthode **ReadXml** prend un argument de type **InferSchema**.  Cet argument vous permet de spécifier un comportement d'inférence compatible avec les versions précédentes.  Les valeurs disponibles pour l'énumération **InferSchema** sont indiquées dans le tableau suivant.  
  
 <xref:System.Data.XmlReadMode>  
 Assure la compatibilité ascendante en déduisant toujours un type simple comme l'objet <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode>  
 Déduit un type de données fortement typées.  Lève une exception s'il est utilisé avec un objet <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode>  
 Ignore tout schéma inline et lit les données dans le schéma <xref:System.Data.DataSet> existant.  
  
## Attributs  
 Comme défini dans [Inférence des tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), un élément assorti d'attributs sera déduit en tant que table.  Les attributs de cet élément seront ensuite déduits en tant que colonnes de cette table.  La propriété **ColumnMapping** des colonnes aura pour valeur **MappingType.Attribute**. De cette façon, les noms des colonnes seront écrits en tant qu'attributs, ce qui sera utile si le schéma doit être réécrit en XML.  Les valeurs des attributs sont stockées dans une ligne de la table.  Examinons, par exemple, le code XML suivant :  
  
```  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Le processus d'inférence produira une table nommée **Element1**, avec deux colonnes, **attr1** et **attr2**.  La propriété **ColumnMapping** des deux colonnes aura pour valeur **MappingType.Attribute**.  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## Éléments dépourvus d'attributs ou d'éléments enfants  
 Si un élément ne comporte ni éléments enfants, ni attributs, il sera déduit en tant que colonne.  La propriété **ColumnMapping** de la colonne aura pour valeur **MappingType.Element**.  Le texte des éléments enfants est stocké dans une ligne de la table.  Examinons, par exemple, le code XML suivant :  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produira une table nommée **Element1**, avec deux colonnes, **ChildElement1** et **ChildElement2**.  La propriété **ColumnMapping** des deux colonnes aura pour valeur **MappingType.Element**.  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## Voir aussi  
 [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)