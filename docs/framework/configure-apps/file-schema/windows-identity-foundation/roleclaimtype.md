---
title: "&lt;roleClaimType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;roleClaimType&gt;
Spécifie le type de revendication qui définit le rôle de type revendications dans la collection d'objets <xref:System.Security.Claims.ClaimsIdentity> retournés par la méthode d' <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> du gestionnaire de jetons.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
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
|value|Chaîne qui spécifie l'URI qui représente le type de revendication du prétendre à utiliser pour le rôle de type de revendication.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Fournit la définition de la classe d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , la classe d' <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , ou une classe dérivée de l'un ou l'autre de ces classes.|  
  
## Notes  
 L'élément définit d' `<roleClaimType>` la propriété d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> lorsqu'un objet d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> est initialisé de la configuration.  
  
## Exemple  
  
```  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>