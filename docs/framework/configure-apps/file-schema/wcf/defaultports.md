---
title: '&lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e127935977795181411dfa6b03d8b09fe88e0f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltdefaultportsgt"></a>&lt;defaultPorts&gt;
Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.  
  
\<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<useRequestHeadersForMetadataAddress >  
\<defaultPorts >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Ajouter > de \<defaultPorts >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|Point de terminaison de communication par défaut écouté par l'application cliente.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress >](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Liste de ports par défaut.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
