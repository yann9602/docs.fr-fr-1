---
title: '&lt;system.identityModel.services&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a5f0b6b207fbd51504149fd5c245f41ef89f17f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemidentitymodelservicesgt"></a>&lt;system.identityModel.services&gt;
Section de configuration pour l’authentification à l’aide du protocole WS-Federation.  
  
 \<system.identityModel.services >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> modules HTTP de (SAM).|  
  
### <a name="parent-elements"></a>Éléments parents  
 Aucune  
  
## <a name="remarks"></a>Remarques  
 Ajouter un `<system.identityModel.services>` section au fichier de configuration de votre application pour fournir les paramètres pour le SAM et WSFAM.  
  
> [!IMPORTANT]
>  Lors de l’utilisation la <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou le <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe pour fournir un contrôle d’accès basé sur les revendications dans votre code, le Gestionnaire d’autorisations de revendications (<xref:System.Security.Claims.ClaimsAuthorizationManager>) et de la stratégie qui permet de prendre des décisions d’autorisation sont configurés via une `<identityConfiguration>` élément implicitement ou explicitement référencé à partir d’un `<federationConfiguration>` élément dans cette section. Pour plus d’informations, consultez la **remarques** sous le [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) élément.  
  
 Le `<system.identityModel.services>` section est représentée par la <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe. La collection d’enfants `<federationConfiguration>` configurés dans la section des éléments est représenté par la <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> classe.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre comment ajouter un `<system.identityModel.services>` section dans un fichier de configuration. Vous devez d’abord ajouter les déclarations de section à la fois pour le `<system.identityModel.services>` section et `<system.identityModel>` sections. (Lorsque vous ajoutez un `<system.identityModel.services>` section, vous devez également ajouter une déclaration pour le `<system.identityModel>` section pour vous assurer que la valeur par défaut `<identityConfiguration>` section peut être créée par le runtime si nécessaire.) Après ont ajouté les déclarations de section, vous pouvez configurer les paramètres de l’authentification fédérée sous le `<system.identityModel.services>` élément.  
  
```xml  
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
