---
title: "&lt;securityTokenHandlerConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;securityTokenHandlerConfiguration&gt;
Fournit la configuration de la collection de gestionnaires de jetons.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|saveBootstrapContext|Spécifie si les jetons d'amorçage doivent être incluses dans le jeton de session.  La valeur peut également être définie sur une collection de gestionnaires de jeton en définissant la `saveBootstrapContext` d'attribut sur le [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément.  Une valeur définie sur la collection de gestionnaires token remplace la valeur définie sur le service.|  
|maximumClockSkew|A <xref:System.TimeSpan> qui spécifie le décalage d'horloge maximale autorisée.  Contrôle l'inclinaison d'horloge maximale autorisée lors des opérations sensibles au temps, telles que la validation du délai d'expiration d'une session.  La valeur par défaut est de 5 minutes, "00 : 05: 00 ».  Pour plus d'informations sur la façon de spécifier <xref:System.TimeSpan> valeurs, voir [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues).  Le décalage horaire maximale peut également être définie au niveau du service en définissant le `maximumClockSkew` d'attribut sur le [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément.  Une valeur définie sur la collection de gestionnaires token remplace la valeur définie sur le service.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<audienceUris\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Spécifie le jeu d'URI qui sont des identificateurs acceptables de cette partie utilisatrice.  Facultatif.|  
|[\<caches\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Enregistre les caches utilisés pour les jetons de session et la détection de relecture de jeton.  Peuvent être spécifiées au niveau du service ou sur une collection de gestionnaires de jeton de sécurité.  Facultatif.|  
|[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Contrôle les paramètres qui utilisent des gestionnaires de jetons pour valider les certificats.  Peuvent être spécifiées au niveau du service ou sur une collection de gestionnaires de jeton de sécurité.  Ces paramètres sont annulés si un gestionnaire spécifique est configuré avec son propre validateur.  Facultatif.|  
|[\< issuerNameRegistry \>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Configure le Registre de nom de l'émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jeton.  Facultatif.|  
|[\<issuerTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Inscrit le résolveur de jeton émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jeton.  Le résolveur de jeton de l'émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.  Facultatif.|  
|[\<serviceTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Inscrit le résolveur de jeton de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jeton.  Le résolveur de jeton de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.  Facultatif.|  
|[\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Permet la détection de relecture de jeton et spécifie le délai d'expiration pour les jetons.  Peuvent être spécifiées au niveau du service ou sur une collection de gestionnaires de jeton de sécurité.  Facultatif.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jeton de sécurité qui sont enregistrés avec le point de terminaison.|  
  
## Notes  
 Cette section fournit des valeurs de propriété pour un <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objet.  Les paramètres configurés dans cette section remplacent ceux configurés sur le service.  Certains de ces paramètres peuvent, à son tour, être substituée par les paramètres sont spécifiés lorsqu'un gestionnaire est ajouté à la collection de gestionnaires de jeton de sécurité.  
  
## Exemple  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```