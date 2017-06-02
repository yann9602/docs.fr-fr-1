---
title: "&lt;soapProcessing&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;soapProcessing&gt;
Définit le comportement de point de terminaison client utilisé pour marshaler des messages entre les versions de message et les types de liaison différents.  
  
## Syntaxe  
  
```  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Élément|Description|  
|-------------|-----------------|  
|processMessages|Valeur booléenne qui spécifie si les messages doivent être marshalés entre des versions de message SOAP.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## Notes  
 Le traitement SOAP est le processus par lequel les messages sont convertis entre des versions de message.  
  
 Le service de routage [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] peut convertir des messages entre différents protocoles.  Si les versions des messages entrant et sortant sont différentes, un nouveau message est créé dans la version correcte.  Le traitement des messages d'un <xref:System.ServiceModel.Channel.MessageVersion> à un autre s'effectue en créant un nouveau message [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] contenant le corps et les en\-têtes pertinents du message [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] entrant.  Les en\-têtes spécifiques à l'adressage ou reconnus au niveau du routeur ne sont pas utilisés pendant la création du nouveau message WCF car ils sont de versions différentes \(dans le cas d'en\-têtes d'adressage\) ou ont été traités dans le cadre de la communication entre le client et le routeur.  
  
 Le placement d'un en\-tête dans le message sortant dépend de son balisage comme étant compris au moment où il traverse la couche du canal entrant.  Les en\-têtes non reconnus \(tels que les en\-têtes personnalisés\) ne sont pas supprimés et traversent donc le service de routage en étant copiés dans le message sortant.  Le corps du message est copié dans le message sortant.  Le message est ensuite envoyé via le canal de sortie ; les en\-têtes et autres données d'enveloppe spécifiques à ce protocole de communication\/transport sont alors créés et ajoutés.  
  
 Ces étapes de traitement s'exécutent lorsque le comportement de traitement SOAP est spécifié.  Ce comportement [\<soapProcessingExtension\>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) est un comportement de point de terminaison qui est appliqué à tous les points de terminaison \(sortants\) clients lorsque le service de routage démarre.  par défaut, le comportement [\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) crée et joint un nouveau comportement [\<soapProcessingExtension\>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) avec `processMessages` ayant la valeur `true` pour chaque point de terminaison client.  Si vous utilisez un protocole non reconnu par le service de routage ou souhaitez remplacer le comportement de traitement par défaut, vous pouvez désactiver le traitement SOAP pour l'intégralité du service de routage ou pour des points de terminaison particuliers. Pour désactiver le traitement SOAP pour l'ensemble du service de routage sur tous les points de terminaison, affectez à l'attribut `soapProcessing` du comportement [\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) la valeur `false`.  Pour désactiver le traitement SOAP pour un point de terminaison particulier, utilisez ce comportement et affectez à son attribut `processMessages` la valeur `false`, puis attachez ce comportement au point de terminaison au niveau duquel vous ne voulez pas exécuter le code de traitement par défaut. Lorsque le comportement [\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) installe le service de routage, il ne réapplique pas le comportement du point de terminaison puisqu'il en existe déjà un.  
  
## Voir aussi  
 <xref:System.ServiceModel.Routing.Configuration.> SoapProcessingExtensionElement?qualifyHint=False&autoUpgrade=True   
 <xref:System.ServiceModel.Routing.SoapProcessingBehavior>