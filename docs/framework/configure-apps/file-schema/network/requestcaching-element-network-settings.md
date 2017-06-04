---
title: "&lt;requestCaching&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<requestCaching> (élément)"
  - "requestCaching (élément)"
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;requestCaching&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Contrôle le mécanisme de mise en cache pour les demandes réseau.  
  
## Syntaxe  
  
```  
  
      <requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss""  
  <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
  <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`isPrivateCache`|Spécifie si le cache fournit l'isolation des informations des différents utilisateurs.  La valeur par défaut est `true`.  Cette valeur doit être `false` pour les applications de couche intermédiaire.|  
|`disableAllCaching`|Spécifie que la mise en cache est désactivée pour toutes les réponses Web et que la substitution par programme n'est pas possible.|  
|`defaultPolicyLevel`|Une des valeurs de l'énumération <xref:System.Net.Cache.RequestCacheLevel>.  La valeur par défaut est `BypassCache`.|  
|`unspecifiedMaximumAge`|Spécifie l'heure par défaut après laquelle le contenu est marqué comme périmé.|  
  
## Attribut policyLevel  
  
|Valeur|Description|  
|------------|-----------------|  
|`Default`|Retourne la ressource mise en cache si elle est nouvelle, si la longueur du contenu est exacte et s'il existe des attributs d'expiration, de modification et de longueur de contenu.|  
|`BypassCache`|Retourne la ressource du serveur.|  
|`CacheOnly`|Retourne la ressource mise en cache si la longueur de contenu est présente et correspond à la taille de l'entrée.|  
|`CacheIfAvailable`|Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l'entrée ; sinon, la ressource est téléchargée à partir du serveur et est retournée à l'appelant.|  
|`Revalidate`|Retourne la ressource mise en cache si l'horodatage de la ressource mise en cache est le même que l'horodatage de la ressource sur le serveur ; sinon, la ressource est téléchargée à partir du serveur, stockée dans le cache et retournée à l'appelant.|  
|`Reload`|Télécharge la ressource à partir du serveur, la stocke dans le cache et la retourne à l'appelant.|  
|`NoCacheNoStore`|S'il existe une ressource mise en cache, elle est supprimée.  La ressource est téléchargée à partir du serveur et retournée à l'appelant.|  
|`Revalidate`|Satisfait une demande en utilisant la copie mise en cache de la ressource si l'horodatage est le même que celui de la ressource sur le serveur ; sinon, la ressource est téléchargée à partir du serveur, présentée à l'appelant et stockée dans le cache.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|Élément facultatif.<br /><br /> Indique si la mise en cache HTTP est active et décrit la stratégie de mise en cache par défaut.|  
|[\<defaultFtpCachePolicy\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|Élément facultatif.<br /><br /> Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont le .NET Framework se connecte au réseau.|  
  
## Exemple  
 L'exemple de code suivant montre comment désactiver la mise en cache.  
  
```  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.Cache?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)