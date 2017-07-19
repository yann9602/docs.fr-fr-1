---
title: "&lt;knownType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;knownType&gt;
Indique un type devant être utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.  L'élément indique un « type connu » renvoyé par un champ ou une propriété d'un « type déclaré ». Pour plus d'informations, consultez [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## Syntaxe  
  
```  
  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## Type  
 `string`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Indique le type \(espace de noms compris\), le nom de l'assembly, la version, la culture et le jeton de clé publique.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<paramètre\>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|Indique un index de paramètre lorsque le type déclaré est générique.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Ajoute un type déclaré à la collection de types déclarés.|  
  
## Notes  
 Pour plus d'informations sur les types connus, consultez [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Pour obtenir un exemple d'utilisation de cet élément, consultez [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md).  
  
## Exemple  
  
```  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)