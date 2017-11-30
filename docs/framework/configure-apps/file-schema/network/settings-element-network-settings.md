---
title: "&lt;paramètres&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 07f356c0425b071ac320e702a9ba7cd6b9537341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsettingsgt-element-network-settings"></a>&lt;paramètres&gt; élément (paramètres réseau)
Configure les options réseau de base pour l’espace de noms <xref:System.Net?displayProperty=nameWithType>.  
  
 \<configuration>  
\<System.NET >  
\<Paramètres >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[httpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|Personnalise les paramètres utilisés par la <xref:System.Net.HttpListener> classe.|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|Personnalise les paramètres de la demande Web.|  
|[IPv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|Protocole Internet version 6 (IPv6) permet de prendre en charge.|  
|[\<performanceCounter >, élément (paramètres réseau)](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|Active les compteurs de performance réseau.|  
|[servicePointManager](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|Configure les connexions aux ressources réseau.|  
|[Socket](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|Spécifie si les opérations de socket utilisent des ports de terminaison.|  
|[\<webProxyScript >, élément (paramètres réseau)](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|Configure les caractéristiques du script utilisé pour découvrir les serveurs proxy Web.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net?displayProperty=nameWithType>  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
