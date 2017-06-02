---
title: "&lt;dataContractSerializer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<dataContractSerializer> (élément)"
  - "DataContractSerializer"
  - "dataContractSerializer (élément)"
  - "KnownTypes"
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# &lt;dataContractSerializer&gt;
Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.  Cet élément se produit dans deux hiérarchies différentes :  l'une est répertoriée dans la section Hiérarchie de schéma suivante et l'autre dans la section Notes.  
  
## Syntaxe  
  
```  
  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Élément|Description|  
|-------------|-----------------|  
|ignoreExtensionDataObject|Valeur booléenne indiquant si les données fournies par le point de terminaison doivent être ignorées ou non lors d'une sérialisation ou d'une désérialisation.  Cet attribut peut uniquement être défini sur le `<dataContractSerializer>` situé sous l'élément `<behavior>`.|  
|maxItemsInObjectGraph|Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.  Cet attribut a la valeur 65 536.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|Collection de paramètres correspondant au comportement d'un service.|  
|[\<system.runtime.serialization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## Notes  
 Comme indiqué dans l'introduction de cette rubrique, il s'agit de la deuxième hiérarchie dans laquelle l'élément \<X509Extension\> se produit.  
  
 [\<system.runtime.serialization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 Pour plus d'informations sur les types connus, consultez <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>   
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>   
 [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [Transfert de données et sérialisation](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)