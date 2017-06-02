---
title: "&lt;certificateValidation&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;certificateValidation&gt;
Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider des certificats.  Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|certificateValidationMode|Une valeur d' <xref:System.ServiceModel.Security.X509CertificateValidationMode> qui spécifie le mode de validation à utiliser pour le certificat X.509.  La valeur par défaut est « PeerOrChainTrust ».  Pour spécifier un validateur personnalisé, définissez cet attribut « custom » et spécifiez le validateur [\<certificateValidator\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) à l'aide de l'élément.  Facultatif.|  
|revocationMode|Une valeur d' <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> qui spécifie le mode de révocation à utiliser pour le certificat X.509.  La valeur par défaut est « en ligne ».  Facultatif.|  
|trustedStoreLocation|Une valeur d' <xref:System.Security.Cryptography.X509Certificates.StoreLocation> qui spécifie le magasin de certificats X.509.  La valeur par défaut est « LocalMachine ».  Facultatif.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<certificateValidator\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|Spécifie un type personnalisé pour la validation de certificat.  Ce type est utilisé uniquement si l'attribut d' [\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)`certificateValidationMode` de l'élément est « custom ».|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Spécifie des paramètres d'identité au niveau de le service.|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## Notes  
 Un élément d' `<certificateValidation>` peut être spécifié au niveau de le service sous l'élément d' `<identityConfiguration>` ou sur la collection de gestionnaire de jetons de sécurité de niveau à l'élément d' `<securityTokenHandlerConfiguration>` .  Les paramètres définis pour une collection de jetons substituent ceux spécifiés dans le service.  Certains gestionnaires de jetons vous permettent de spécifier des paramètres de validation de certificat dans la configuration.  Les paramètres sur des gestionnaires de jetons substituent ceux spécifiés au niveau de le service et sur la collection de gestionnaire de jetons de sécurité.  
  
## Exemple  
  
```  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```