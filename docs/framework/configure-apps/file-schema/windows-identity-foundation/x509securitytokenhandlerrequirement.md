---
title: "&lt;x509SecurityTokenHandlerRequirement&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# &lt;x509SecurityTokenHandlerRequirement&gt;
Fournit la configuration facultative pour la classe d' <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> ou les classes dérivées.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
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
|certificateValidationMode|Une valeur d' <xref:System.ServiceModel.Security.X509CertificateValidationMode> qui spécifie le mode de validation à utiliser pour le certificat X.509.  La valeur par défaut est « PeerOrChainTrust ».|  
|mapToWindows|Spécifie si le gestionnaire de jetons doit mapper le jeton validante à un compte Windows à l'aide d'une revendication entrante d'UPN.  La valeur par défaut est « false ».|  
|revocationMode|Une valeur d' <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> qui spécifie le mode de révocation à utiliser pour le certificat X.509.  La valeur par défaut est « en ligne ».|  
|trustedStoreLocation|Une valeur d' <xref:System.Security.Cryptography.X509Certificates.StoreLocation> qui spécifie le magasin de certificats X.509.  La valeur par défaut est « LocalMachine ».|  
|certificateValidator|Un type personnalisé qui dérive d' <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  Si l'attribut d' `certificateValidationMode` est « custom », une instance de ce type est utilisée pour la validation de certificat d'expéditeur.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Ajoute le gestionnaire de jetons de sécurité spécifié à la collection du gestionnaire de jetons.|  
  
## Exemple  
  
```  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```