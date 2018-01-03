---
title: "Limitations des inférences"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3053d4e83233027f28357d8c45087df71c21ca18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="inference-limitations"></a>Limitations des inférences
Le processus d'inférence d'un schéma de l'objet <xref:System.Data.DataSet> à partir de XML peut aboutir à des schémas différents en fonction des éléments XML figurant dans chaque document. Examinons, par exemple, les documents XML suivants.  
  
 Document1 :  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2 :  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 Pour « Document1 », le processus d’inférence produit un **DataSet** nommé « DocumentElement » et une table nommée « Element1 » car « Element1 » est un élément répétitif.  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 Toutefois, pour « Document2 », le processus d’inférence produit un **DataSet** nommé « NewDataSet » et une table nommée « DocumentElement ». « Element1 » est déduit en tant que colonne car il n'a ni attribut, ni élément enfant.  
  
 **DataSet :** NewDataSet  
  
 **Table :** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 Ces deux documents XML peuvent avoir été conçus de manière à produire le même schéma, mais le processus d'inférence donne des résultats très différents en fonction des éléments contenus dans chaque document.  
  
 Pour éviter les différences qui peuvent se produire lors de la génération de schéma à partir d’un document XML, nous vous recommandons de spécifier explicitement un schéma à l’aide du langage de définition de schéma XML (XSD) ou (XML-Data Reduced) lors du chargement d’un **DataSet** à partir de XML. Pour plus d’informations sur la spécification explicite un **DataSet** schéma avec le schéma XML, consultez [dérivant Structure relationnelle des DataSet à partir de XSD (XML Schema)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Inférence de la structure relationnelle d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Chargement d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Chargement des informations de schéma de DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
