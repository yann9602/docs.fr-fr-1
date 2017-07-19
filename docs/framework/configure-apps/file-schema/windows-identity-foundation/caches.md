---
title: "&lt;caches&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;caches&gt;
Enregistre les caches utilisés pour les jetons de session et la détection de relecture de jeton.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jeton de sécurité.|  
|[\<tokenReplayCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|Inscrit un cache de rediffusion jeton avec un service ou une collection de gestionnaires de jeton de sécurité.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Spécifie les paramètres d'identité au niveau de service.|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit les gestionnaires de jetons de configuration pour une collection de sécurité.|  
  
## Notes  
 A `<caches>` élément peut être spécifié au niveau de service sous la `<identityConfiguration>` élément ou sur le niveau de collection de Gestionnaire de jetons de sécurité sous la `<securityTokenHandlerConfiguration>` élément.  Les paramètres sur une collection de gestionnaires de jeton remplacent ceux spécifiés sur le service.  
  
 Le `<caches>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.  Les caches configurés sont représentés par la <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.  
  
## Exemple  
 Le code XML suivant illustre la configuration d'un cache de maintien de session de jetons de sécurité personnalisé \(<xref:System.IdentityModel.Tokens.SessionSecurityToken>\).  La configuration provient de la `ClaimsAwareWebFarm` exemple.  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```