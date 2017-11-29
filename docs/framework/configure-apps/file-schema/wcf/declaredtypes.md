---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 138bc800625a8334d692bd46a3ceb7dfe2ea4ae1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdeclaredtypesgt"></a>&lt;declaredTypes&gt;
Contient les types connus utilisés par le <xref:System.Runtime.Serialization.DataContractSerializer> lors de la désérialisation.  
  
 Pour plus d’informations sur les contrats de données et les types connus, consultez [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Ajoute des types qui requièrent des types connus.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Remarques  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]types connus, consultez [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre les types déclarés et connus types ajoutés à un `DataContractSerializer` élément. L'exemple montre l'ajout de trois types. Le premier est un type personnalisé nommé « Orders » qui utilise un type connu nommé « Item ». Le deuxième est un <xref:System.Collections.Generic.List%601> qui utilise `Item` comme un type connu. Le troisième et dernier est un <xref:System.Collections.Generic.Dictionary%602>. Le type de classe <xref:System.Collections.Generic.Dictionary%602> est un type générique contenant deux paramètres de type. Le premier représente la clé et le second représente la valeur. L'exemple suivant ajoute un <xref:System.Collections.Generic.List%601> du deuxième type (la valeur) à la liste de types connus. Vous devez utiliser l'attribut `index` pour spécifier le paramètre de type à utiliser dans le type connu. Dans ce cas, le type de valeur est indiqué par l’ensemble d’attributs d’index ayant la valeur "1" (la collection est de base zéro).  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
