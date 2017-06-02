---
title: "&lt;tokenReplayDetection&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;tokenReplayDetection&gt;
Active la détection du jeton par reconstitution et spécifie le moment d'expiration pour les jetons.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Type  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|activé|Valeur qui spécifie si un jeton relire la détection est activée ; « true » pour activer la détection du jeton par reconstitution.|  
|expirationPeriod|<xref:System.TimeSpan> qui spécifie la quantité maximale de temps avant qu'un élément soit considéré comme expiré et supprimé du cache.  Pour plus d'informations sur la spécification des valeurs d' <xref:System.TimeSpan> , consultez [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Spécifie des paramètres d'identité au niveau de le service.|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## Notes  
 Un élément d' `<tokenReplayDetection>` peut être spécifié au niveau de le service sous l'élément d' `<identityConfiguration>` ou sur la collection de gestionnaire de jetons de sécurité de niveau à l'élément d' `<securityTokenHandlerConfiguration>` .  Les paramètres définis pour une collection de jetons substituent ceux spécifiés dans le service.  
  
 Le type du cache du jeton par reconstitution est spécifié par [\<tokenReplayCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) l'élément.