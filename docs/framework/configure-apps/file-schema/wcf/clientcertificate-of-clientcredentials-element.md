---
title: "&lt;clientCertificate&gt;, &#233;l&#233;ment de &lt;clientCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;clientCertificate&gt;, &#233;l&#233;ment de &lt;clientCredentials&gt;
Définit un certificat X.509 utilisé pour authentifier un client à un service.  
  
## Syntaxe  
  
```  
  
<clientCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`findValue`|Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.  Le type contenu dans cet attribut doit répondre aux spécifications de l'attribut `X509FindType` spécifié.  La valeur par défaut est une chaîne vide.|  
|`storeLocation`|Indique l'emplacement du certificat X.509 utilisé par le client pour s'authentifier auprès du service.  Les valeurs valides sont les suivantes :<br /><br /> -   LocalMachine : magasin de certificats assigné à l'ordinateur local.<br />-   CurrentUser : magasin de certificats assigné à l'utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.  Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|`storeName`|Spécifie le nom du magasin de certificats X.509 dans lequel effectuer la recherche.  Les valeurs valides sont les suivantes :<br /><br /> -   AddressBook : magasin de certificats pour d'autres utilisateurs.<br />-   AuthRoot : magasin de certificats pour les autorités de certification \(CA\) tierces.<br />-   CertificateAuthority : magasin de certificats pour les autorités de certification \(CA\) intermédiaires.<br />-   Disallowed : magasin de certificats pour les certificats révoqués.<br />-   My : magasin de certificats pour les certificats personnels.<br />-   Root : magasin de certificats pour les autorités de certification \(CA\) racines approuvées.<br />-   TrustedPeople : magasin de certificats pour les personnes et les ressources directement approuvées.<br />-   TrustedPublisher : magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.  Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Définit le type de recherche X.509 à exécuter.  Le type contenu dans l'attribut `findValue` doit répondre aux spécifications de cet attribut.  Les valeurs valides sont les suivantes :<br /><br /> -   FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.  Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.|  
  
## Notes  
 Cet élément de configuration spécifie le certificat utilisé pour authentifier le client avec cet élément.  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Comment : spécifier des valeurs d'informations d'identification du client](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>   
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Comment : spécifier des valeurs d'informations d'identification du client](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)