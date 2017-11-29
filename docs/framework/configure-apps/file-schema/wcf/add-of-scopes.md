---
title: '&lt;add&gt; de &lt;scopes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c720d99a5abee00eeb52f91586503e0a8a89027b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a>&lt;add&gt; de &lt;scopes&gt;
Ajoute un URI de portée personnalisé qui permet de filtrer les points de terminaison de service pendant la requête.  
  
\<système. ServiceModel >  
\<comportements >  
\<endpointBehaviors >  
\<comportement >  
\<endpointDiscovery >  
\<étendues >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|portée|URI qui contient les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<étendues >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
