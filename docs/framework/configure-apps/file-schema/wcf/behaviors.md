---
title: "&lt;comportements&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;comportements&gt;
Cet élément définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.  Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services.  Chaque élément de comportement est identifié par son attribut `name` unique.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<system.ServiceModel\>  
  
## Syntaxe  
  
```  
  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
   <endpointBehaviors>  
   </endpointBehaviors>  
</behaviors>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 None  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<endpointBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Cette section de configuration représente tous les comportements définis pour un point de terminaison spécifique.|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Cette section de configuration représente tous les comportements définis pour un service spécifique.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Élément racine de tous les éléments de configuration Windows Communication Foundation \(WCF\).|  
  
## Notes  
 Vous pouvez utiliser l'élément `<remove>` pour supprimer un comportement particulier de la collection.  Pour cela, fournissez le nom du comportement à supprimer dans l'attribut `name` de l'élément `<remove>`.  Vous pouvez également utiliser l'élément `<clear>` pour vous assurer qu'une collection de comportements est vide au démarrage en supprimant tout le contenu de la collection.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>   
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>   
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>   
 [Configuration et extension de l'exécution à l'aide de comportements](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)   
 [Configuration des comportements clients](../../../../../docs/framework/wcf/configuring-client-behaviors.md)   
 [Spécification du comportement du client au moment de l'exécution](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)   
 [Spécification du comportement du service au moment de l'exécution](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)