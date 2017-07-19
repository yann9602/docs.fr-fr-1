---
title: "&lt;federationConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# &lt;federationConfiguration&gt;
Configure la <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) lorsque vous utilisez fédérés d'authentification via le protocole WS\-Federation.  Configure la <xref:System.Security.Claims.ClaimsAuthorizationManager> lors de l'utilisation du <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou le <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe pour fournir un contrôle d'accès basé sur les revendications.  
  
## Syntaxe  
  
```  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Le nom de cet élément de configuration de fédération.  Cet attribut fournit principalement un point d'extensibilité pour les protocoles à venir.  Facultatif.|  
|identityConfigurationName|Le nom de la section de configuration d'identité comme spécifié dans une [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément à utiliser.  Si cet attribut n'est pas spécifié, la section de configuration de l'identité par défaut est utilisée.  Facultatif.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Configure le Gestionnaire de cookie utilisé par le SAM.  Facultatif.|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Configure le certificat qui est utilisé pour crypter et décrypter les jetons.  Facultatif.|  
|[\<wsFederation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|Configure le Module d'authentification de WS\-Federation \(WSFAM\).  Facultatif.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.identityModel.services\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Section de configuration pour l'authentification à l'aide du protocole WS\-Federation.|  
  
## Notes  
 Le \<federationConfiguration\> élément fournit différents paramètres dans deux scénarios différents :  
  
-   Lors de l'utilisation de WS\-Federation dans une application Web passive, l'élément contient des paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\).  Il fait référence également à la configuration de l'identité à utiliser pour configurer les gestionnaires de jeton de sécurité et des certificats et des composants tels que le Gestionnaire d'autorisations de créances et du Gestionnaire d'authentification de revendications.  
  
-   Lorsque vous utilisez le <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou le <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> de classe pour fournir un contrôle d'accès basé sur les revendications dans votre code, l'élément fait référence à la configuration de l'identité qui configure le Gestionnaire de demandes d'autorisations et la stratégie qui est utilisé pour prendre des décisions d'autorisation.  Ceci est vrai même dans les scénarios qui ne sont pas les scénarios Web passifs ; par exemple, les applications Windows Communication Foundation \(WCF\) ou une application qui n'est pas basé sur le Web.  Si l'application n'est pas une application Web passive, la [\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) élément \(et ses éléments de stratégie enfant, le cas échéant\) de la configuration de l'identité référencée par la `<federationConfiguration>` élément sont les seuls paramètres appliqués.  Tous les autres sont ignorés.  
  
 Indépendamment du scénario, le runtime charge la configuration par défaut de la fédération.  Le comportement est défini comme suit :  
  
1.  S'il y a aucun `<federationConfiguration>` élément présent, le runtime crée une configuration de la fédération et le remplit avec les valeurs par défaut.  Cette configuration par défaut de la fédération fera référence à la configuration d'identité par défaut.  
  
2.  Si un seul `<federationConfiguration>` élément est présent, c'est la configuration de la fédération par défaut indépendamment de si elle est nommée ou sans nom.  Si sa `identityConfiguration` attribut est spécifié, la configuration de l'identité nommée est référencée ; dans le cas contraire, la configuration d'identité par défaut est référencée.  
  
3.  Si un sans nom `<federationConfiguration>` élément est présent, c'est la configuration par défaut de la fédération.  Si sa `identityConfiguration` attribut est spécifié, la configuration de l'identité nommée est référencée ; dans le cas contraire, la configuration d'identité par défaut est référencée.  
  
4.  Si plusieurs nommé `<federationConfiguration>` éléments sont présents et non sans nom `<federationConfiguration>` élément est présent, une exception est levée.  
  
 En règle générale, un seul `<federationConfiguration>` section est définie.  Cette section est la configuration par défaut de la fédération.  Vous pouvez spécifier plusieurs, nommé de manière unique `<federationConfiguration>` éléments ; Toutefois, dans ce cas, si vous souhaitez charger une configuration autre que celui sans nom de la fédération, vous devez fournir un gestionnaire pour le.  <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>événements et définir les <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=fullName> propriété dans le Gestionnaire d'un <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objet initialisé avec les valeurs appropriées de `<federationConfiguration>` élément dans le fichier de configuration.  
  
 Le `<federationConfiguration>` élément est représenté par la <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> classe.  L'objet de configuration est représenté par la <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> classe.  Un seul <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance est définie sur le <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName> propriété et fournit la configuration fédérée pour l'application.  
  
## Exemple  
 Le XML suivant un `<federationConfiguration>` élément qui spécifie les paramètres pour la WSFAM et spécifie que le Gestionnaire de cookie par défaut \(une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe\) être utilisé par le SAM.  
  
> [!WARNING]
>  Dans cet exemple, WSFAM ni le Gestionnaire de cookies sont requis pour utiliser le protocole HTTPS.  C'est parce que le `requireHttps` d'attribut sur le `<wsFederation>` élément et le `requireSsl` d'attribut sur le `<cookieHandlerElement>` sont `false`.  Ces paramètres ne sont pas recommandés pour la plupart des environnements de production car ils pourraient présenter un risque de sécurité.  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"   
      issuer="http://localhost:15839/wsFederationSTS/Issue"   
      realm="http://localhost:50969/" reply="http://localhost:50969/"   
      requireHttps="false"   
      signOutReply="http://localhost:50969/SignedOutPage.html"   
      signOutQueryString="Param1=value2&Param2=value2"   
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>   
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>   
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>   
 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)