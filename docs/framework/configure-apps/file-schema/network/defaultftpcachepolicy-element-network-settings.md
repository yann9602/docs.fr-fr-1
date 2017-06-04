---
title: "&lt;defaultFtpCachePolicy&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<defaultFtpCachePolicy> (élément)"
  - "defaultFtpCachePolicy (élément)"
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;defaultFtpCachePolicy&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.  
  
## Syntaxe  
  
```  
< defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`policyLevel`|Spécifie la stratégie de mise en cache FTP.  La valeur par défaut est `Default`.|  
  
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
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
  
## Notes  
  
## Exemple  
 L'exemple de code suivant indique comment spécifier une stratégie de mise en cache FTP de `NoCacheNoStore`.  
  
```  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        Level="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.Cache>   
 <xref:System.Net.WebRequest>   
 <xref:System.Net.Cache.RequestCacheLevel>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)