---
title: "&lt;certificateReference&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;certificateReference&gt;
Spécifie les paramètres qui sont utilisés pour trouver et valider un certificat X.509 dans un magasin de certificats.  
  
## Syntaxe  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName=”AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher”  
        storeLocation=”CurrentUser||LocalMachine”  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|storeName|Le nom du magasin de certificats X.509.  La valeur par défaut est « My ».  Facultatif.|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie l'emplacement du magasin de certificats X.509.  La valeur par défaut est « LocalMachine ».  Facultatif.|  
|x509FindType|Un <xref:System.Security.Cryptography.X509Certificates.X509FindType> valeur qui spécifie le type de recherche qui doit être exécutée.  La valeur par défaut est « FindBySubjectDistinguishedName ».  Facultatif.|  
|findValue|Valeur à rechercher dans le magasin de certificats X.509.  Facultatif.|  
|isChainIncluded|Spécifie si la validation doit être effectuée à l'aide de la chaîne de certificats.  La valeur par défaut est « true » ; validation est effectuée à l'aide de la chaîne de certificats.  Facultatif.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Configure le certificat qui est utilisé pour crypter et décrypter les jetons.|  
  
## Notes  
 Le `<certificateReference>` élément spécifie les paramètres qui sont utilisés pour trouver et valider un certificat X.509 dans un magasin de certificats.  Quand il est spécifié en tant qu'élément enfant de le `<serviceCertficate>` élément, il spécifie les paramètres d'emplacement et la vérification du certificat X.509 utilisé pour crypter et décrypter les jetons.  Le `<certificateReference>` élément est représenté par la <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.