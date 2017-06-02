---
title: "&lt;issuedTokenAuthentication&gt; de &lt;serviceCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;issuedTokenAuthentication&gt; de &lt;serviceCredentials&gt;
Indique un jeton personnalisé émis en tant qu'informations d'identification du service.  
  
## Syntaxe  
  
```  
  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`allowedAudienceUris`|Obtient le jeu d'URI cibles pour lesquels le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  Pour plus d'informations sur l'utilisation de cet attribut, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Valeur booléenne indiquant si les émetteurs de certificats RSA non fiables sont autorisés.<br /><br /> Les certificats sont signés par des autorités de certification \(CA\) pour en assurer l'authenticité.  Un émetteur non fiable est une autorité de certification qui n'est pas spécifiée comme étant approuvée pour signer des certificats.|  
|`audienceUriMode`|Obtient une valeur indiquant si le <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> du jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> doit être validé.  Cette valeur est de type <xref:System.IdentityModel.Selectors.AudienceUriMode>.  Pour plus d'informations sur l'utilisation de cet attribut, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Définit le mode de validation du certificat.  L'une des valeurs valides du <xref:System.ServiceModel.Security.X509CertificateValidationMode>.  S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.  La valeur par défaut est `ChainTrust`.|  
|`customCertificateValidatorType`|Chaîne facultative.  Type et assembly utilisés pour valider un type personnalisé.  Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.|  
|`revocationMode`|Définit le mode de révocation qui spécifie si un contrôle de révocation a lieu et s'il est effectué en ligne ou hors connexion.  Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Attribut de chaîne facultatif indiquant le type de SamlSerializer utilisé pour les informations d'identification du service.  La valeur par défaut est une chaîne vide.|  
|`trustedStoreLocation`|Énumération facultative.  L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`knownCertificates`|Indique une collection d'éléments <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> qui spécifient des émetteurs approuvés au niveau des informations d'identification du service.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Spécifie les informations d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.|  
  
## Notes  
 Le scénario de jeton émis comporte trois étapes.  Dans la première, un client qui essaie d'accéder à un service est désigné sous le terme de *service d'émission de jeton sécurisé*.  Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML \(Security Assertions Markup Language\).  Le client retourne ensuite au service avec le jeton.  Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.  Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.  
  
 Cet élément est le référentiel pour les certificats de service d'émission de jeton sécurisé de ce type.  Pour ajouter des certificats, utilisez [\<knownCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).  Insérez [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pour chaque certificat, tel qu'indiqué dans l'exemple suivant.  
  
```  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.  Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.  
  
 Pour plus d'informations sur l'utilisation de cet élément de configuration, consultez [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## Voir aussi  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>   
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>   
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)