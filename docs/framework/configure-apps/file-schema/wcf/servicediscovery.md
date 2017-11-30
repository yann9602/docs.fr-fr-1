---
title: '&lt;serviceDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c371455767b912bd124c2207a1cc29b8ead71cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicediscoverygt"></a>&lt;serviceDiscovery&gt;
Spécifie la fonctionnalité de découverte des points de terminaison de service.  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<serviceDiscovery >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String" 
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String" 
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Collection de points de terminaison d’annonce. Cette section permet de spécifier les points de terminaison à utiliser pour l'envoi de messages d'annonce.|  
|[\<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Collection de points de terminaison de découverte. Cette section permet de spécifier les points de terminaison sur lesquels écouter les messages de découverte.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Remarques  
 Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration rend tous les points de terminaison de ce service détectables. Vous pouvez configurer davantage les fonctionnalités de découverte de tels points de terminaison à l’aide de la [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) ou [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) des éléments enfants. Utilisez le [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section pour configurer les annonces en spécifiant la configuration de point de terminaison à utiliser pour envoyer des annonces de service (en ligne/Hello et Bye hors connexion /). Utilisez le [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section pour spécifier manuellement le point de terminaison d’écoute pour les messages de découverte.  
  
## <a name="example"></a>Exemple  
 L'exemple de configuration suivant spécifie que CalculatorService doit être détectable et indique éventuellement le point de terminaison d'annonce à utiliser.  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
  ...  
  </service>  
</services>  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery>  
        <announcementEndpoints>  
              <endpoint name="udpEndpoint"  
                        kind="udpAnnouncementEndpoint" />  
        </announcementEndpoints>  
      </serviceDiscovery>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
