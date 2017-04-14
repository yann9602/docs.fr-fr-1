---
title: "&lt;param&#232;tre&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;param&#232;tre&gt;
Indique le paramètre générique lorsqu'un type déclaré est générique.  
  
## Syntaxe  
  
```  
  
<parameter index="integer"  
                      type=String" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|index|Lorsque le type déclaré est générique, spécifie le paramètre générique qui renverra le type connu.|  
|type|Chaîne décrivant le type connu utilisé pour la sérialisation et la désérialisation.|  
  
## Indexer l'Attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|"0"|Premier paramètre du type générique.  Par exemple, <xref:System.Collections.Generic.List%601> dispose d'un seul paramètre.  S'il est utilisé comme type déclaré, l'index a la valeur « 0 ».|  
|"1"|Second paramètre d'un type générique.  Par exemple, <xref:System.Collections.Generic.Dictionary%602> dispose de deux paramètres.  Si le type connu est renvoyé par le second paramètre, affectez à l'attribut d'index la valeur « 1 ».|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<knownType\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Spécifie un type connu pouvant être renvoyé par un champ ou une propriété du type déclaré.|  
  
## Notes  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] les types connus, consultez [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Pour obtenir un exemple d'utilisation de cet élément, consultez [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md).  
  
 Cet élément de configuration ne peut pas contenir les deux attributs simultanément.  Si c'est le cas, un <xref:System.Configuration.ConfigurationErrorsException> survient.  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)