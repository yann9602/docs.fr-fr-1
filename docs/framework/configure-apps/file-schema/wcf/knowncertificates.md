---
title: "&lt;knownCertificates&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# &lt;knownCertificates&gt;
Représente une collection des certificats X.509 fournis pour authentifier des informations d'identification de sécurité publiées à partir d'un service d'émission de jetons de sécurité \(STS\).  
  
## Syntaxe  
  
```  
  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|Ajoute un certificat X.509 à la collection.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Spécifie un jeton émis en guise d'information d'identification du service.|  
  
## Notes  
 Le scénario de jeton émis comporte trois étapes.  Dans la première, un client qui essaie d'accéder à un service est désigné sous le terme de *service d'émission de jeton sécurisé*.  Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML \(Security Assertions Markup Language\).  Le client retourne ensuite au service avec le jeton.  Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.  Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.  
  
 L'élément [\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) est le référentiel pour les certificats de service d'émission de jeton sécurisé de ce type.  Pour ajouter des certificats, utilisez [\<knownCertificates\> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).  Insérez [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pour chaque certificat, tel qu'indiqué dans l'exemple suivant.  
  
```  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.  Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.  
  
 Pour examiner les conditions requises pour l'authentification d'un client par un service fédéré, ainsi que pour plus d'informations sur l'utilisation de cet élément de configuration, consultez [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  Pour plus d'informations sur les scénarios fédérés, consultez [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Pour obtenir un exemple qui indique comment remplir la collection dans la configuration, consultez [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).  
  
## Voir aussi  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>   
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>   
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>   
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>   
 [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)   
 [\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)