---
title: "Inf&#233;rence des tables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Inf&#233;rence des tables
Lors de l'inférence du schéma d'un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET identifie d'abord les éléments XML qui représentent des tables.  Les structures XML suivantes donneront une table pour le schéma du **DataSet** :  
  
-   éléments avec attributs ;  
  
-   éléments avec éléments enfants ;  
  
-   éléments qui se répètent.  
  
## Éléments avec attributs  
 Les éléments contenant des attributs spécifiés donnent des tables déduites.  Examinons, par exemple, le code XML suivant :  
  
```  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit une table nommée « Element1 ».  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|attr1|Element1\_Text|  
|-----------|--------------------|  
|value1||  
|value2|Text1|  
  
## Éléments avec éléments enfants  
 Les éléments possédant des éléments enfants donnent des tables déduites.  Examinons, par exemple, le code XML suivant :  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit une table nommée « Element1 ».  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 L'élément document, ou racine, donne une table déduite s'il comporte des attributs ou des éléments enfants qui sont inférés en tant que colonnes.  Si l'élément document ne comporte pas d'attributs ni d'éléments enfants qui seraient déduits en tant que colonnes, il est déduit en tant que **DataSet**.  Examinons, par exemple, le code XML suivant :  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit une table nommée « DocumentElement ».  
  
 **DataSet :** NewDataSet  
  
 **Table :** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 Examinons également le code XML suivant :  
  
```  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit un **DataSet** nommé « DocumentElement » contenant une table nommée « Element1 ».  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## Éléments qui se répètent  
 Les éléments qui se répètent donnent une seule table déduite.  Examinons, par exemple, le code XML suivant :  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit une table nommée « Element1 ».  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|Element1\_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## Voir aussi  
 [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)