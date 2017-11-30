---
title: '&lt;standardEndpoints&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd4de65da3dcce6360fef6e404b0951dbbd26336
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltstandardendpointsgt"></a>&lt;standardEndpoints&gt;
Cette section de configuration vous permet de définir une collection de points de terminaison standard, qui sont des points de terminaison préconfigurés et réutilisables. Un point de terminaison standard possède un ou plusieurs attributs d'adresse, de liaison et de contrat ayant une valeur fixe. Par exemple, dans le point de terminaison de découverte, le contrat est fixe. Vous pouvez également utiliser des points de terminaison standard pour étendre le point de terminaison de service avec de nouvelles propriétés, ce qui revient à définir des liaisons personnalisées.  
  
 \<système. ServiceModel >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Définit un point de terminaison standard avec un contrat d'annonce fixe. Un service peut éventuellement annoncer sa disponibilité en envoyant un message d'annonce en ligne ou hors connexion selon qu'il est respectivement ouvert ou fermé. A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service spécifie les points de terminaison d’annonce dans le [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) élément et utilise le AnnouncementClient pour effectuer les annonces. Un client souhaite écouter l’annonce à partir de l’autre service est en réalité agissant comme un [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service ; par conséquent, vous devez configurer les points de terminaison d’annonce pour le client dans le [ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.|  
|[\<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Définit un point de terminaison standard avec un contrat de découverte fixe. Lorsqu'il est ajouté à la configuration du service, il spécifie où écouter les messages de découverte. Lorsqu'il est ajouté à la configuration client, il spécifie où envoyer les requêtes de découverte.|  
|[\<dynamicEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|Cet élément de configuration définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.|  
|[\<mexEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|Définit un point de terminaison standard avec un contrat IMetadataExchange fixe. Puisque tous les points de terminaison d'échange de métadonnées ont comme contrat IMetadataExchange, vous pouvez utiliser ce point standard au lieu d'en définir un à votre intention.|  
|[\<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|Définit un point de terminaison standard qui permet aux services d’envoyer des messages d’annonce via une liaison UDP. Il a un contrat fixe et prend en charge deux versions de découverte. De plus, il possède une liaison UDP fixe et une valeur d'adresse par défaut indiquée dans les spécifications WS-Discovery (WS-Discovery Avril 2005 ou WS-Discovery version 1.1). Vous pouvez spécifier l'adresse de multidiffusion à utiliser pour l'envoi et la réception de messages d'annonce.|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Définit un point de terminaison standard, préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP. Ce point de terminaison a un contrat fixe et prend en charge deux versions de protocole WS-Discovery. De plus, il a une liaison UDP fixe et une valeur d’adresse par défaut indiquée dans les spécifications WS-Discovery (WS-Discovery Avril 2005 ou WS-Discovery V1.1).|  
|[\<webHttpEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|Définit un point de terminaison standard avec une liste fixe [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) automatiquement une liaison qui ajoute le [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportement. Utilisez ce point de terminaison lors de l'écriture d'un service REST.|  
|[\<webScriptEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|Définit un point de terminaison standard avec une liste fixe [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) automatiquement une liaison qui ajoute le [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportement. Utilisez ce point de terminaison lorsque vous écrivez un service appelé à partir d'une application ASP.NET AJAX.|  
|[\<workflowControlEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|Définit un point de terminaison standard permettant de contrôler l'exécution d'instances de flux de travail (créer, exécuter, interrompre, arrêter, etc.).|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<système. ServiceModel >|Élément racine de tous les éléments de configuration WCF.|  
  
## <a name="see-also"></a>Voir aussi  
 [Points de terminaison standard](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
