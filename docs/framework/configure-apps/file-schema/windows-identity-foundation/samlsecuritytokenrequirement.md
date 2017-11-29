---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e0d8d467c2636f5ce95cf5fed189ae00c3ca75fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsamlsecuritytokenrequirementgt"></a>&lt;samlSecurityTokenRequirement&gt;
Fournit la configuration pour le <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> (classe), la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée d’un de ces classes. Représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<add>  
\<samlSecurityTokenRequirement >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|mapToWindows|Spécifie si le Gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante. La valeur par défaut est « false ».|  
|issuerCertificateRevocationMode|Un <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valeur qui spécifie le mode de révocation à utiliser pour le certificat X.509. La valeur par défaut est « Online ».|  
|issuerCertificateValidationMode|Un <xref:System.ServiceModel.Security.X509CertificateValidationMode> valeur qui spécifie le mode de validation à utiliser pour le certificat X.509. La valeur par défaut est « PeerOrChainTrust ».|  
|issuerCertificateTrustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie le magasin de certificats X.509. La valeur par défaut est « Ordinateur_local ».|  
|issuerCertificateValidator|Un type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Si le `issuerCertificateValidationMode` attribut est « Custom », une instance de ce type est utilisée pour la validation de certificat de l’émetteur.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<nameClaimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|Définit le type de revendication qui spécifie le <xref:System.Security.Principal.IIdentity.Name%2A> propriété.|  
|[\<roleClaimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|Spécifie le type de revendication qui définit les revendications de type de rôle dans la collection de <xref:System.Security.Claims.ClaimsIdentity> objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode du Gestionnaire de jeton.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Ajoute le Gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.|  
  
## <a name="remarks"></a>Remarques  
 Le `<samlSecurityTokenRequirement>` élément est représenté par le <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> dans le modèle objet de classe et est utilisé pour configurer le `SamlSecurityTokenRequirement` propriété sur un <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou un <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.  
  
## <a name="example"></a>Exemple  
  
```xml  
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
