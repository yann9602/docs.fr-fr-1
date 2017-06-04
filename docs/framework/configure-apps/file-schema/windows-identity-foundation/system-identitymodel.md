---
title: "&lt;system.identityModel&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;system.identityModel&gt;
Fournit la configuration pour l'activation des options Windows Identity Foundation \(WIF\) dans les applications.  
  
 \<system.identityModel\>  
  
## Syntaxe  
  
```  
<system.identityModel>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Spécifie les paramètres d'identité au niveau de service.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`<configuration>`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## Notes  
 Ajouter un `<system.identityModel>` section au fichier de configuration pour configurer un service ou une application à utiliser Windows Identity Foundation \(WIF\).  Le `<system.identityModel>` élément est représenté par la <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> classe.  
  
## Exemple  
 L'exemple suivant montre comment ajouter un `<system.identityModel>` section dans un fichier de configuration.  Vous devez d'abord ajouter la déclaration d'espace de noms et de la section configuration sous la `<configSections>` élément.  Vous pouvez alors ajouter le `<system.IdentityModel>` élément à votre fichier de configuration pour spécifier une ou plusieurs configurations d'identité.  
  
```  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>