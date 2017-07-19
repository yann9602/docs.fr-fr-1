---
title: "&lt;serviceCertificate&gt; de &lt;serviceCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;serviceCertificate&gt; de &lt;serviceCredentials&gt;
Spécifiez un certificat X.509 qui sera utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message.  
  
## Syntaxe  
  
```  
  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`findValue`|Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.  Le type contenu dans l'attribut doit satisfaire les spécifications du X509FindType spécifié.  La valeur par défaut est une chaîne vide.|  
|`storeLocation`|Spécifie l'emplacement du magasin de certificats X.509 que le client utilise pour valider le certificat du serveur.  Les valeurs valides sont les suivantes :<br /><br /> -   LocalMachine : magasin de certificats assigné à l'ordinateur local.<br />-   CurrentUser : magasin de certificats assigné à l'utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.|  
|`storeName`|Spécifie le nom du magasin de certificats X.509 à ouvrir.  Les valeurs valides sont les suivantes :<br /><br /> -   AddressBook : magasin de certificats pour d'autres utilisateurs.<br />-   AuthRoot : magasin de certificats pour les autorités de certification \(CA\) tierces.<br />-   CertificatAuthority : magasin de certificats pour les autorités de certification \(CA\) intermédiaires.<br />-   Disallowed : magasin de certificats pour les certificats révoqués.<br />-   My : magasin de certificats pour les certificats personnels.<br />-   Root : magasin de certificats pour les autorités de certification \(CA\) racines approuvées.<br />-   TrustedPeople : magasin de certificats pour les personnes et les ressources directement approuvées.<br />-   TrustedPublisher : magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.|  
|`X509FindType`|Définit le type de recherche X.509 à exécuter.  Les valeurs valides sont les suivantes :<br /><br /> -   FindByThumbprint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> Le type contenu dans l'attribut `findValue` doit satisfaire les spécifications du X509FindType spécifié.<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l'information d'identification du client.|  
  
## Notes  
 Cet élément vous permet de spécifier un certificat X.509 qui sera utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message.  Si vous utilisez un certificat qui sera périodiquement renouvelé, son empreinte numérique changera.  Dans ce cas, utilisez le nom du sujet comme `X509FindType` car le certificat peut être réémis avec le même nom du sujet.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] l'utilisation de cet élément, consultez [Comment : spécifier des valeurs d'informations d'identification du client](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>   
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>   
 [Comment : spécifier des valeurs d'informations d'identification du client](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)