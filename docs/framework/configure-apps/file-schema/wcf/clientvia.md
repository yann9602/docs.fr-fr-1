---
title: "&lt;clientVia&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;clientVia&gt;
Spécifie l'URI pour lequel le canal de transport doit être créé.  Pour plus d'informations, consultez <xref:System.ServiceModel.Description.ClientViaBehavior>.  
  
## Syntaxe  
  
```  
  
<clientVia viaUri="String"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`viaUri`|Chaîne qui spécifie un URI indiquant l'itinéraire d'un message.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ClientViaElement>   
 <xref:System.ServiceModel.Description.ClientViaBehavior>