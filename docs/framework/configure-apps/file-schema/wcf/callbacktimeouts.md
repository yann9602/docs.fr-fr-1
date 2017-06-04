---
title: "&lt;callbackTimeouts&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &lt;callbackTimeouts&gt;
Spécifie la valeur du délai d'attente lors du transfert de transactions du serveur vers un client dans un scénario de contrat de rappel duplex.  
  
## Syntaxe  
  
```  
  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## Type  
 `Type`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`transactionTimeout`|Valeur <xref:System.TimeSpan> qui spécifie l'intervalle au cours duquel les transactions doivent être automatiquement effectuées ou arrêtées.  La valeur par défaut est « 00:00:00 ».|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>