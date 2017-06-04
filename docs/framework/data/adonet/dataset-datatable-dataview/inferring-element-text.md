---
title: "Inf&#233;rence du texte des &#233;l&#233;ments | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Inf&#233;rence du texte des &#233;l&#233;ments
Si un élément contient du texte et n'a pas d'élément enfant à déduire en tant que tables \(comme des éléments assortis d'attributs ou qui se répètent\), une nouvelle colonne nommée **TableName\_Text** sera ajoutée à la table inférée pour l'élément.  Le texte contenu dans l'élément sera ajouté à une ligne de la table et stocké dans la nouvelle colonne.  La propriété **ColumnMapping** de la nouvelle colonne aura pour valeur **MappingType.SimpleContent**.  
  
 Examinons, par exemple, le code XML suivant.  
  
```  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produira une table nommée **Element1**, avec deux colonnes, **attr1** et **Element1\_Text**.  La propriété **ColumnMapping** de la colonne **attr1** aura pour valeur **MappingType.Element**.  La propriété **ColumnMapping** de la colonne **Element1\_Text** aura pour valeur **MappingType.SimpleContent**.  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|attr1|Element1\_Text|  
|-----------|--------------------|  
|value1|Text1|  
  
 Si un élément contient du texte, mais possède également des éléments enfants contenant du texte, une colonne ne sera pas ajoutée à la table pour stocker le texte contenu dans l'élément.  Ce texte sera ignoré, alors que le texte des éléments enfants sera inclus dans une ligne de la table.  Examinons, par exemple, le code XML suivant.  
  
```  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Le processus d'inférence produira une table nommée **Element1**, avec une colonne nommée **ChildElement1**.  Le texte de l'élément **ChildElement1** sera inclus dans une ligne de la table.  L'autre texte sera ignoré.  La propriété **ColumnMapping** de la colonne **ChildElement1** aura pour valeur **MappingType.Element**.  
  
 **DataSet :** DocumentElement  
  
 **Table :** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## Voir aussi  
 [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)