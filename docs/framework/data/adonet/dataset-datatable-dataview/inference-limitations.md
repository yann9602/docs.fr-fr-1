---
title: "Limitations applicables &#224; l&#39;inf&#233;rence | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Limitations applicables &#224; l&#39;inf&#233;rence
Le processus d'inférence d'un schéma de l'objet <xref:System.Data.DataSet> à partir de XML peut aboutir à des schémas différents en fonction des éléments XML figurant dans chaque document.  Examinons, par exemple, les documents XML suivants.  
  
 Document1 :  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2 :  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 Pour « Document1 », le processus d'inférence produit un **DataSet** nommé « DocumentElement » et une table nommée « Element1 » car « Element1 » est un élément récurrent.  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|Element1\_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 Toutefois, pour « Document2 », le processus d'inférence produit un **DataSet** nommé « NewDataSet » et une table nommée « DocumentElement ». « Element1 » est déduit en tant que colonne car il n'a ni attribut, ni élément enfant.  
  
 **DataSet :** NewDataSet  
  
 **Table :** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 Ces deux documents XML peuvent avoir été conçus de manière à produire le même schéma, mais le processus d'inférence donne des résultats très différents en fonction des éléments contenus dans chaque document.  
  
 Pour éviter les différences qui peuvent se produire lors de la génération d'un schéma à partir d'un document XML, il est recommandé de spécifier explicitement un schéma à l'aide du langage XSD \(XML Schema Definition\) ou de XDR \(XML\-Data Reduced\) lors du chargement d'un **DataSet** à partir de XML.  Pour plus d'informations sur la spécification explicite du schéma d'un **DataSet** à l'aide d'un schéma XML, voir [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## Voir aussi  
 [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)