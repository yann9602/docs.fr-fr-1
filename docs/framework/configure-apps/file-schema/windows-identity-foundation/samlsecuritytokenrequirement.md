---
title: "&lt;samlSecurityTokenRequirement&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;samlSecurityTokenRequirement&gt;
Fournit la définition de la classe d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , la classe d' <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , ou une classe dérivée de l'un ou l'autre de ces classes.  Représenté par la classe d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
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
|mapToWindows|Spécifie si le gestionnaire de jetons doit mapper le jeton validante à un compte Windows à l'aide d'une revendication entrante d'UPN.  La valeur par défaut est « false ».|  
|issuerCertificateRevocationMode|Une valeur d' <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> qui spécifie le mode de révocation à utiliser pour le certificat X.509.  La valeur par défaut est « en ligne ».|  
|issuerCertificateValidationMode|Une valeur d' <xref:System.ServiceModel.Security.X509CertificateValidationMode> qui spécifie le mode de validation à utiliser pour le certificat X.509.  La valeur par défaut est « PeerOrChainTrust ».|  
|issuerCertificateTrustedStoreLocation|Une valeur d' <xref:System.Security.Cryptography.X509Certificates.StoreLocation> qui spécifie le magasin de certificats X.509.  La valeur par défaut est « LocalMachine ».|  
|issuerCertificateValidator|Un type personnalisé qui dérive d' <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  Si l'attribut d' `issuerCertificateValidationMode` est « custom », une instance de ce type est utilisée pour la validation de certificat d'expéditeur.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<nameClaimType\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|Définit le type de revendication qui spécifie la propriété d' <xref:System.Security.Principal.IIdentity.Name%2A> .|  
|[\<roleClaimType\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|Spécifie le type de revendication qui définit le rôle de type revendications dans la collection d'objets <xref:System.Security.Claims.ClaimsIdentity> retournés par la méthode d' <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> du gestionnaire de jetons.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Ajoute le gestionnaire de jetons de sécurité spécifié à la collection du gestionnaire de jetons.|  
  
## Notes  
 l'élément d' `<samlSecurityTokenRequirement>` est représenté par la classe d' <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> dans le modèle objet et est utilisé pour configurer la propriété d' `SamlSecurityTokenRequirement` sur <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.  
  
## Exemple  
  
```  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```