---
title: "&lt;behavior&gt; de &lt;serviceBehaviors&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;behavior&gt; de &lt;serviceBehaviors&gt;
L'élément `behavior` contient une collection de paramètres concernant le comportement d'un service.  Chaque comportement est indexé en fonction de son `name`.  Les services peuvent être liés à chaque comportement via ce nom à l'aide de l'attribut `behaviorConfiguration` de l'élément [\<Point de terminaison \(endpoint\)\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md).  Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
>  Les éléments de comportement spécifiques aux activités Windows Workflow, tels que l'élément [\<sendMessageChannelCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md), sont décrits dans la page [\<behavior\> de \<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md).  
  
## Syntaxe  
  
```  
  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
       <behavior name="String" />  
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Chaîne unique qui contient le nom de configuration du comportement.  Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|Contient les données de configuration pour DataContractSerializer.|  
|[\<persistenceProvider\>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|Indique le type d'implémentation de fournisseur de persistance à utiliser, ainsi que le délai d'expiration à utiliser pour les opérations de persistance.|  
|[\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Fournit un accès au service de routage au moment de l'exécution afin d'autoriser une modification dynamique de la configuration de routage.|  
|[\<serviceAuthenticationManager\>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un expéditeur.|  
|[\<serviceAuthorization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|Spécifie les paramètres qui autorisent l'accès aux opérations de service.|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.|  
|[\<serviceDebug\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|Spécifie les fonctionnalités de débogage et d'informations d'aide pour un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].|  
|[\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|Spécifie la fonctionnalité de découverte des points de terminaison de service.|  
|[\<serviceMetadata\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|Spécifie la publication de métadonnées de service et des informations associées.|  
|[\<serviceSecurityAudit\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|Spécifie des paramètres qui activent l'audit d'événements de sécurité pendant des opérations de service.|  
|[\<serviceThrottling\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|Spécifie le mécanisme de limitation d'un service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
|[\<serviceTimeouts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|Spécifie le délai d'attente pour un service.|  
|[\<workflowRuntime\>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|Spécifie les paramètres d'une instance de WorkflowRuntime pour héberger des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] basés sur le flux de travail.|  
|[\<useRequestHeadersForMetadataAddress\>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Active la récupération des informations d'adresse des métadonnées à partir des en\-têtes de message de demande.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Collection d'éléments de comportement de service.|