---
title: "&lt;standardEndpoints&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;standardEndpoints&gt;
Cette section de configuration vous permet de définir une collection de points de terminaison standard, qui sont des points de terminaison préconfigurés et réutilisables.  Un point de terminaison standard possède un ou plusieurs attributs d'adresse, de liaison et de contrat ayant une valeur fixe.  Par exemple, dans le point de terminaison de découverte, le contrat est fixe.  Vous pouvez également utiliser des points de terminaison standard pour étendre le point de terminaison de service avec de nouvelles propriétés, ce qui revient à définir des liaisons personnalisées.  
  
 \<system.ServiceModel\>  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
  
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<announcementEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Définit un point de terminaison standard avec un contrat d'annonce fixe.  Un service peut éventuellement annoncer sa disponibilité en envoyant un message d'annonce en ligne ou hors connexion selon qu'il est respectivement ouvert ou fermé.  Un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] spécifie les points de terminaison d'annonce dans l'élément [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) et utilise AnnouncementClient pour effectuer les annonces.  Un client qui souhaite écouter l'annonce provenant d'un autre service joue en fait le rôle de service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ; vous devez donc configurer les points de terminaison d'annonce pour ce client dans la section [\<services\>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md).|  
|[\<discoveryEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Définit un point de terminaison standard avec un contrat de découverte fixe.  Lorsqu'il est ajouté à la configuration du service, il spécifie où écouter les messages de découverte.  Lorsqu'il est ajouté à la configuration client, il spécifie où envoyer les requêtes de découverte.|  
|[\<dynamicEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|Cet élément de configuration définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.|  
|[\<mexEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|Définit un point de terminaison standard avec un contrat IMetadataExchange fixe.  Puisque tous les points de terminaison d'échange de métadonnées ont comme contrat IMetadataExchange, vous pouvez utiliser ce point standard au lieu d'en définir un à votre intention.|  
|[\<udpAnnoucementEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|Définit un point de terminaison standard qui permet aux services d'envoyer des messages d'annonce via une liaison UDP.  Il a un contrat fixe et prend en charge deux versions de découverte.  De plus, il possède une liaison UDP fixe et une valeur d'adresse par défaut indiquée dans les spécifications WS\-Discovery \(WS\-Discovery Avril 2005 ou WS\-Discovery version 1.1\).  Vous pouvez spécifier l'adresse de multidiffusion à utiliser pour l'envoi et la réception de messages d'annonce.|  
|[\<UdpDiscoveryEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Définit un point de terminaison standard, préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP.  Ce point de terminaison a un contrat fixe et prend en charge deux versions de protocole WS\-Discovery.  De plus, il a une liaison UDP fixe et une valeur d'adresse par défaut indiquée dans les spécifications WS\-Discovery \(WS\-Discovery Avril 2005 ou WS\-Discovery V1.1\).|  
|[\<webHttpEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|Définit un point de terminaison standard avec une liaison [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) fixe qui ajoute automatiquement le comportement [\<webHttp\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md).  Utilisez ce point de terminaison lors de l'écriture d'un service REST.|  
|[\<webScriptEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|Définit un point de terminaison standard avec une liaison [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) fixe qui ajoute automatiquement le comportement [\<enableWebScript\>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md).  Utilisez ce point de terminaison lorsque vous écrivez un service appelé à partir d'une application ASP.NET AJAX.|  
|[\<workflowControlEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|Définit un point de terminaison standard permettant de contrôler l'exécution d'instances de flux de travail \(créer, exécuter, interrompre, arrêter, etc.\).|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<system.ServiceModel\>|Élément racine de tous les éléments de configuration WCF.|  
  
## Voir aussi  
 [Points de terminaison standard](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)