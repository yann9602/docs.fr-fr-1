---
title: "&lt;settings&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#settings"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<settings> (élément)"
  - "settings (élément)"
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: 21
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 21
---
# &lt;settings&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Configure les options réseau de base pour l'espace de noms <xref:System.Net?displayProperty=fullName>.  
  
## Syntaxe  
  
```  
  
      <settings>  
..<httpListener> … </httpListener>  
..<httpWebRequest> … </httpWebRequest>  
..<ipv6> … </ipv6>  
..<performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
..<socket> … </socket>  
..<webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[httpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|Personnalise les paramètres utilisés par la classe <xref:System.Net.HttpListener>.|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|Personnalise les paramètres de demande Web.|  
|[ipv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|Active la prise en charge du protocole IPv6.|  
|[\<performanceCounters\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|Active les compteurs de performance réseau.|  
|[servicePointManager](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|Configure des connexions aux ressources réseau.|  
|[socket](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|Spécifie si les opérations de socket utilisent des ports de terminaison.|  
|[Élément \<webProxyScript\> \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|Configure les caractéristiques du script utilisé pour découvrir des proxies Web.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[System.Net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont le .NET Framework se connecte au réseau.|  
  
## Notes  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Voir aussi  
 <xref:System.Net?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)