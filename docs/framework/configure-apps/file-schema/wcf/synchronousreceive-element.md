---
title: "&lt;synchronousReceive&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;synchronousReceive&gt;, &#233;l&#233;ment
Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service.  Il n'a aucun attribut ou élément enfant.  
  
## Syntaxe  
  
```  
  
<synchronousReceive />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## Notes  
 Utilisez ce comportement pour indiquer à l'écouteur de canal d'utiliser une réception synchrone au lieu de celle par défaut \(asynchrone\).  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] émet un nouveau thread pour pomper chaque canal accepté.  Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>   
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>