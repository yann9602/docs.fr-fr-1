---
title: "&lt;identityConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# &lt;identityConfiguration&gt;
Spécifie les paramètres d'identité au niveau de service.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Le nom de la section de configuration de l'identité.  Vous pouvez utiliser ce nom pour référencer une section de configuration spécifiques.  Si aucun `name` attribut est spécifié, la section définit la configuration par défaut.  La configuration par défaut est toujours utilisée pour les scénarios de fédération passive.  Pour plus d'informations, consultez l'élément [\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md).|  
|saveBootstrapContext|Spécifie si les jetons d'amorçage doivent être incluses dans le jeton de session.  La valeur peut également être définie sur une collection de gestionnaires de jeton en définissant la `saveBootstrapContext` d'attribut sur le [\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) élément.  Une valeur définie sur la collection de gestionnaires token remplace la valeur définie sur le service.|  
|maximumClockSkew|A <xref:System.TimeSpan> qui spécifie le décalage d'horloge maximale autorisée.  Contrôle l'inclinaison d'horloge maximale autorisée lors des opérations sensibles au temps, telles que la validation du délai d'expiration d'une session.  La valeur par défaut est de 5 minutes, "00 : 05: 00 ».  Pour plus d'informations sur la façon de spécifier <xref:System.TimeSpan> valeurs, voir [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues).  Le décalage horaire maximale peut également être définie sur une collection de gestionnaires de jeton en définissant la `maximumClockSkew` d'attribut sur le [\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) élément.  Une valeur définie sur la collection de gestionnaires token remplace la valeur définie sur le service.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<caches\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Enregistre les caches utilisés pour les jetons de session et la détection de relecture de jeton.  Peuvent être spécifiées au niveau du service ou sur une collection de gestionnaires de jeton de sécurité.  Facultatif.|  
|[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Contrôle les paramètres qui utilisent des gestionnaires de jetons pour valider les certificats.  Peuvent être spécifiées au niveau du service ou sur une collection de gestionnaires de jeton de sécurité.  Facultatif.|  
|[\<claimsAuthenticationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Inscrit un gestionnaire d'authentification de sinistres pour les revendications entrantes.  Facultatif.|  
|[\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Inscrit un gestionnaire d'autorisations de sinistres pour les demandes entrantes.  Facultatif.|  
|[\<claimTypeRequired\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Spécifie le jeu de déclarations obligatoires pour les jetons de sécurité entrants.  Facultatif.|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jeton de sécurité.  Zéro ou plusieurs collections de gestionnaires de jeton de sécurité peuvent être spécifiées.  Facultatif.|  
|[\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Permet la détection de relecture de jeton et spécifie le délai d'expiration pour les jetons.  Peuvent être spécifiées au niveau du service ou sur une collection de gestionnaires de jeton de sécurité.  Facultatif.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.identityModel\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Fournit la configuration pour l'activation des options Windows Identity Foundation \(WIF\) dans les applications.|  
  
## Notes  
 Identités multiples configurations peuvent être définies, chacun avec un nom unique.  Le comportement est comme suit :  
  
1.  Si aucun `<identityConfiguration>` élément est spécifié.  Une configuration d'identité par défaut est créée lors de l'exécution et remplie avec les valeurs par défaut.  
  
2.  Si un seul `<identityConfiguration>` élément est spécifié.  Il s'agit de la configuration d'identité par défaut.  Il n'a pas d'importance qu'elle soit nommée ou sans nom.  
  
3.  Si plusieurs `<identityConfiguration>` éléments sont spécifiés.  L'élément sans nom spécifie la configuration d'identité par défaut.  Il est recommandé que lorsque vous spécifiez plusieurs `<identityConfiguration>` des éléments, l'un d'eux doit être sans nom.  
  
> [!WARNING]
>  Si vous spécifiez plusieurs `<identityConfiguration>` des éléments, l'un d'eux doit être sans nom.  L'élément sans nom sera la configuration d'identité par défaut.  
  
 Certains des paramètres spécifiés dans la `<identityConfiguration>` élément peut être substituée par les paramètres sur une collection de gestionnaires de jeton de sécurité ou par les paramètres sur les gestionnaires de jeton de sécurité individuels.  
  
> [!IMPORTANT]
>  Lorsque vous utilisez le <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou le <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe pour fournir un contrôle d'accès basé sur les revendications dans votre code, la configuration de l'identité qui est référencée par le `<federationConfiguration>` élément configure le Gestionnaire de demandes d'autorisations et la stratégie qui est utilisé pour prendre des décisions d'autorisation.  Ceci est vrai même dans les scénarios qui ne sont pas les scénarios Web passifs, par exemple les applications Windows Communication Foundation \(WCF\) ou une application qui n'est pas basé sur le Web.  Si l'application n'est pas une application Web passive, la [\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) élément \(et ses éléments de stratégie enfant, le cas échéant\) de la configuration de l'identité référencées sont les seuls paramètres appliqués.  Tous les autres paramètres sont ignorés.  Pour plus d'informations, consultez l'élément [\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md).  
  
 Le `<identityConfiguration>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> classe.  Une section de configuration de l'identité est représentée par la <xref:System.IdentityModel.Configuration.IdentityConfiguration> classe.  
  
> [!IMPORTANT]
>  Spécifier les éléments suivants en tant qu'éléments enfants de le `<identityConfiguration>` élément a été désapprouvé, bien que le comportement est toujours pris en charge pour la compatibilité ascendante.  Ces éléments doivent, au lieu de cela, être spécifiés sous la [\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) élément.  
>   
>  -   [\<audienceUris\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\< issuerNameRegistry \>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## Exemple  
 L'exemple suivant crée une configuration de l'identité nommée « alternateConfiguration ».  La configuration de l'identité spécifie les paramètres par défaut.  
  
```  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>   
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>