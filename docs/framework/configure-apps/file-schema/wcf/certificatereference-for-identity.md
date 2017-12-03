---
title: '&lt;certificateReference&gt; de &lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27bcccab90c4627f2c9a1d241af3b1833ae13a18
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcertificatereferencegt-for-ltidentitygt"></a>&lt;certificateReference&gt; de &lt;identity&gt;
Spécifie les paramètres de validation du certificat X.509. Un client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sécurisé qui se connecte à un point de terminaison avec cette identité vérifie que les revendications présentées par le serveur contiennent la revendication d'identité utilisée pour construire cette identité.  
  
 \<identité >  
\<certificateReference >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificateReference   
        findValue="String"   
    isChainIncluded="Boolean"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
  
    storeLocation="LocalMachine/CurrentUser"  
  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
</certificateReference>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|findValue|Indique la valeur à rechercher dans le magasin de certificats X.509. Le type contenu dans cet attribut doit répondre aux spécifications de la valeur `X509FindType` spécifiée. La valeur par défaut est une chaîne vide.|  
|isChainIncluded|Valeur booléenne indiquant si la validation est effectuée à l'aide d'une chaîne de certificats.|  
|storeLocation|Indique l'emplacement du magasin de certificats pouvant être utilisé par le client pour valider le certificat du serveur.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> -LocalMachine : Magasin de certificats assigné à l’ordinateur local.<br />-CurrentUser : Magasin de certificats assigné à l’utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.<br /><br /> Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Spécifie le nom du magasin de certificats X.509 à ouvrir.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> -AddressBook : Magasin de certificats pour d’autres utilisateurs.<br />-AuthRoot : Magasin de certificats pour autorités de certification tierces (CAs).<br />-CertificateAuthority : Magasin de certificats des autorités de certification intermédiaires.<br />-Disallowed : Magasin de certificats pour les certificats révoqués.<br />-My : Magasin de certificats pour les certificats personnels.<br />-Root : Magasin de certificats pour des autorités de certification racine approuvée.<br />-TrustedPeople : Magasin de certificats pour les personnes de confiance directement et de ressources.<br />-TrustedPublisher : Magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.<br /><br /> Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Indique le type de recherche X.509 à exécuter. Le type contenu dans l'attribut `findValue` doit satisfaire les spécifications du X509FindType spécifié.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.<br /><br /> Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identité >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Indique les paramètres permettant l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>
