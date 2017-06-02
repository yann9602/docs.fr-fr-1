---
title: "&lt;declaredTypes&gt; | Microsoft Docs"
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
  - "<declaredTypes> (élément)"
  - "DataContractSerializer"
  - "dataContractSerializer (élément)"
  - "declaredTypes (élément)"
  - "KnownTypes"
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;declaredTypes&gt;
Contient les types connus utilisés par le <xref:System.Runtime.Serialization.DataContractSerializer> lors de la désérialisation.  
  
 Pour plus d'informations sur les contrats de données et les types connus, consultez [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## Syntaxe  
  
```  
  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
                <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Ajoute des types qui requièrent des types connus.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## Notes  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] les types connus, consultez [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## Exemple  
 Le code XML suivant illustre l'ajout de types déclarés et connus à un élément `DataContractSerializer` .  L'exemple montre l'ajout de trois types.  Le premier est un type personnalisé nommé « Orders » qui utilise un type connu nommé « Item ».  Le deuxième est un <xref:System.Collections.Generic.List%601> qui utilise `Item` comme un type connu.  Le troisième et dernier est un <xref:System.Collections.Generic.Dictionary%602>.  Le type de classe <xref:System.Collections.Generic.Dictionary%602> est un type générique contenant deux paramètres de type.  Le premier représente la clé et le second représente la valeur.  L'exemple suivant ajoute un <xref:System.Collections.Generic.List%601> du deuxième type \(la valeur\) à la liste de types connus.  Vous devez utiliser l'attribut `index` pour spécifier le paramètre de type à utiliser dans le type connu.  Dans ce cas, le type de valeur est indiqué par l'ensemble d'attributs d'index ayant la valeur "1" \(la collection est de base zéro\).  
  
```  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [Types connus de contrats de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)