---
title: "&lt;dispatcherSynchronization&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;dispatcherSynchronization&gt;
Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.  
  
## Syntaxe  
  
```  
  
<dispatcherSynchronizationBehavior   
   asynchronousSendEnabled=”Boolean”  
   maxPendingReceives="Integer" />  
```  
  
## Type  
 `Type`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|asynchronousSendEnabled|Valeur booléenne qui indique si un comportement d'envoi asynchrone est activé.|  
|`maxPendingReceives`|Entier qui spécifie le nombre de réceptions simultanées qui peuvent être émises sur le canal.<br /><br /> Cette valeur doit être configurée uniquement après avoir correctement configuré le comportement de limitation de service.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.DispatcherSynchronizationBehaviorElement>   
 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>