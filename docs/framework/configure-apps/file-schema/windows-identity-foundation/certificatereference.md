---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c8acf4b6d6e6e8a0fcf7d73139a1d2c5ea03f063
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
Spécifie les paramètres qui sont utilisés pour rechercher et valider un certificat X.509 dans un magasin de certificats.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<serviceCertificate >  
\<certificateReference >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|storeName|Le nom du magasin de certificats X.509. La valeur par défaut est « My ». Facultatif.|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie l’emplacement du magasin de certificats X.509. La valeur par défaut est « Ordinateur_local ». Facultatif.|  
|x509FindType|Un <xref:System.Security.Cryptography.X509Certificates.X509FindType> valeur qui spécifie le type de recherche doit être exécutée. La valeur par défaut est « FindBySubjectDistinguishedName ». Facultatif.|  
|findValue|Valeur à rechercher dans le magasin de certificats X.509. Facultatif.|  
|isChainIncluded|Spécifie si la validation doit être effectuée à l’aide de la chaîne de certificats. La valeur par défaut est « true » ; la validation est effectuée à l’aide de la chaîne de certificats. Facultatif.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Configure le certificat qui est utilisé pour chiffrer et déchiffrer les jetons.|  
  
## <a name="remarks"></a>Remarques  
 Le `<certificateReference>` élément spécifie les paramètres qui permettent de rechercher et de valider le certificat dans un magasin de certificats X.509. Lorsqu’il est spécifié en tant qu’élément enfant de le `<serviceCertficate>` élément, il spécifie les paramètres d’emplacement et la vérification du certificat X.509 qui est utilisé pour chiffrer et déchiffrer les jetons. Le `<certificateReference>` élément est représenté par la <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.
