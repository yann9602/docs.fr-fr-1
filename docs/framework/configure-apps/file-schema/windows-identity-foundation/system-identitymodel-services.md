---
title: "&lt;system.identityModel.services&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# &lt;system.identityModel.services&gt;
Section de configuration pour l'authentification à l'aide du protocole WS\-Federation.  
  
 \<system.identityModel.services\>  
  
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
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> les modules HTTP \(SAM\).|  
  
### Éléments parents  
 Aucun  
  
## Notes  
 Ajouter un `<system.identityModel.services>` section au fichier de configuration de votre application pour fournir des paramètres pour le SAM et WSFAM.  
  
> [!IMPORTANT]
>  Lors de l'utilisation le <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou le <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe pour fournir un contrôle d'accès basé sur les revendications dans votre code, le Gestionnaire d'autorisations de revendications \(<xref:System.Security.Claims.ClaimsAuthorizationManager>\) et stratégie qui est utilisé pour prendre des décisions d'autorisation sont configurés via un `<identityConfiguration>` élément qui est implicitement ou explicitement référencée à partir un `<federationConfiguration>` élément dans cette section.  Pour plus d'informations, consultez la  **Remarques** sous la [\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) élément.  
  
 Le `<system.identityModel.services>` section est représentée par la <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe.  La collection d'enfants `<federationConfiguration>` éléments configurés dans la section est représentée par la <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> classe.  
  
## Exemple  
 Le code XML suivant montre comment ajouter un `<system.identityModel.services>` section dans un fichier de configuration.  Vous devez d'abord ajouter les déclarations de section à la fois pour le `<system.identityModel.services>` section et la `<system.identityModel>` sections.  \(Lorsque vous ajoutez un `<system.identityModel.services>` section, vous devez également ajouter une déclaration pour la `<system.identityModel>` section pour vous assurer que la valeur par défaut `<identityConfiguration>` section peut être créée par le runtime si nécessaire.\) Après les déclarations de section ont été ajoutées, vous pouvez configurer les paramètres d'authentification fédérée sous la `<system.identityModel.services>` élément.  
  
```  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```