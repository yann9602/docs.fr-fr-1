---
title: "&lt;élément persistableType&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c77bdf8ef02edf682ded95ab16b4d56dbf60b4ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpersistabletypegt"></a>&lt;élément persistableType&gt;
Spécifie tous les types persistants.  
  
 \<système. ServiceModel >  
\<comContracts >  
\<comContract >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|id|Attribut requis qui contient une chaîne spécifiant un identificateur unique pour un type persistant.|  
|name|Attribut facultatif qui contient une chaîne spécifiant le nom du type persistant.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|Collection d'éléments `persistableType`.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Intégration à des Applications COM +](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Comment : configurer les paramètres de Service COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
