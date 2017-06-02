---
title: "&lt;tokenReplayCache&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;tokenReplayCache&gt;
Inscrit un cache de rediffusion jeton avec un service ou une collection de gestionnaires de jeton de sécurité.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Un type qui dérive de la <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.  Pour plus d'informations sur la façon de spécifier un personnalisé `type`, voir [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<caches\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Enregistre les caches utilisés par un service ou une collection de gestionnaires de jeton de sécurité.|  
  
## Notes  
 Le cache de relecture du jeton est utilisé pour détecter les jetons relus.  La détection de relecture jeton est activée par le [\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) élément, qui indique également l'heure d'expiration maximal de jetons.  
  
## Exemple  
 Le code XML suivant montre la configuration d'un cache personnalisé pour détecter les jetons relus.  
  
```  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>   
 [\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)