---
title: "&lt;sessionSecurityTokenCache&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;sessionSecurityTokenCache&gt;
Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jeton de sécurité.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Un type qui dérive de la <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.  Pour plus d'informations sur la façon de spécifier un personnalisé `type`, voir [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<caches\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Enregistre les caches utilisés par un service ou une collection de gestionnaires de jeton de sécurité.|  
  
## Exemple  
 Le code XML suivant illustre la configuration d'un cache de maintien de session de jetons de sécurité personnalisé \(<xref:System.IdentityModel.Tokens.SessionSecurityToken>\).  La configuration provient de la `ClaimsAwareWebFarm` exemple.  Pour plus d'informations sur cet exemple, consultez [Exemple d’index de code WIF](../../../../../docs/framework/security/wif-code-sample-index.md).  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>