---
title: "&lt;add&gt;, &#233;l&#233;ment de &lt;declaredTypes&gt; | Microsoft Docs"
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
  - "Contrats de données"
  - "DataContractAttribute"
  - "DataContractSerializer"
  - "dataContractSerializer (élément)"
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;add&gt;, &#233;l&#233;ment de &lt;declaredTypes&gt;
Ajoute un type utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.  Chaque type déclaré inclut les types connus qui seront renvoyés comme champ ou propriété du type déclaré.  
  
## Syntaxe  
  
```  
  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Attribut de chaîne requis.<br /><br /> Indique le nom du type \(espace de noms compris\), celui de l'assembly, le numéro de version, la culture et le jeton de clé publique.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<knownType\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Spécifie le type connu correspondant au type déclaré en cours d'ajout.  Si le type déclaré est un type générique, vous devez également ajouter un élément de paramètre à l'élément `<knownType>` pour spécifier le paramètre générique utilisé pour renvoyer le type connu.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<declaredTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|Contient les types qui requièrent des types connus pendant la désérialisation effectuée par le <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## Notes  
 Pour plus d'informations sur les types connus, consultez [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Pour obtenir un exemple d'utilisation de cet élément, consultez [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md).  
  
> [!NOTE]
>  Si vous ajoutez le type <xref:System.Object> comme `<declaredType>`, une <xref:System.Configuration.ConfigurationErrorsException> est levée.  Ceci est dû au fait que le type <xref:System.Object> ne peut pas être utilisé comme type déclaré dans la configuration.  
  
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
 [\<add\> of \<declaredTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)