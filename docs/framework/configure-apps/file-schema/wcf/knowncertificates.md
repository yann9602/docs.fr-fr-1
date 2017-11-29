---
title: '&lt;knownCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e1ce8be4dfa71685933512c1c0db36000ce93c12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltknowncertificatesgt"></a>&lt;knownCertificates&gt;
Représente une collection des certificats X.509 fournis pour authentifier des informations d’identification de sécurité publiées à partir d’un service d’émission de jetons de sécurité (STS).  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<serviceCredentials >  
\<issuedTokenAuthentication >  
\<knownCertificates >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|Ajoute un certificat X.509 à la collection.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Spécifie un jeton émis en guise d'information d'identification du service.|  
  
## <a name="remarks"></a>Remarques  
 Le scénario de jeton émis comporte trois étapes. Dans la première phase, un client tente d’accéder à un service est appelée un *service de jeton sécurisé*. Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language). Le client retourne ensuite au service avec le jeton. Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client. Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.  
  
 Le [ \<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) élément est le référentiel pour tous les certificats de service de jeton sécurisé ce type. Pour ajouter des certificats, utilisez le [ \<knownCertificates > élément](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Insérer un [ \<Ajouter >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé. Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.  
  
 Pour passer en revue les conditions requises pour un client soit authentifié par un service fédéré, ainsi que de plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer les informations d’identification sur un Service de fédération](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Pour plus d’informations sur les scénarios de fédération, consultez [fédération et les jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Pour obtenir un exemple qui montre comment remplir la collection dans la configuration, consultez [ \<Ajouter >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Comment : configurer les informations d’identification sur un Service de fédération](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
