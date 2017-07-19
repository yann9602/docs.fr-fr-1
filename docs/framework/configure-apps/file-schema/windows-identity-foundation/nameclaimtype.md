---
title: "&lt;nameClaimType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;nameClaimType&gt;
Définit le type de revendication qui spécifie la propriété d' <xref:System.Security.Principal.IIdentity.Name%2A> .  Le type de revendication est utilisé pour rechercher <xref:System.Security.Claims.Claim> dans la collection d'objets <xref:System.Security.Claims.ClaimsIdentity> retournés par la méthode d' <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> de ce gestionnaire de jetons.  La valeur de la revendication correspondante est alors définie par le nom d' <xref:System.Security.Principal.IIdentity> généré de ce gestionnaire de jetons.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|value|Chaîne qui spécifie l'URI qui représente le type de revendication du prétendre à utiliser pour la propriété d' <xref:System.Security.Principal.IIdentity.Name%2A> .  Obligatoire.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Fournit la définition de la classe d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , la classe d' <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , ou une classe dérivée de l'un ou l'autre de ces classes.|  
  
## Notes  
 L'élément définit d' `<nameClaimType>` la propriété d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> lorsqu'un objet d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> est initialisé de la configuration.  
  
## Exemple  
  
```  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>