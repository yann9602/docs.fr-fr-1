---
title: "&lt;diagnostics&gt; pour l&#39;activation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;diagnostics&gt; pour l&#39;activation
Configure les fonctionnalités de diagnostic de l'écouteur [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## Syntaxe  
  
```  
  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## Type  
 `Type`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`performanceCountersEnabled`|Valeur booléenne qui indique si les compteurs de performance sont activés à des fins de diagnostic.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel.activation\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>