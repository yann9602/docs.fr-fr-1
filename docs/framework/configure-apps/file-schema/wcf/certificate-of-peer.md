---
title: "&lt;certificate&gt; de &lt;peer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;certificate&gt; de &lt;peer&gt;
Spécifie un certificat utilisé par un homologue.  
  
## Syntaxe  
  
```  
  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`findValue`|Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.  Le type contenu dans l'attribut doit répondre aux spécifications du `x509FindType` spécifié.  La valeur par défaut est une chaîne vide.|  
|`storeLocation`|Indique l'emplacement du magasin de certificats X.509 utilisé par le client pour valider le certificat de l'homologue.  Les valeurs valides sont les suivantes :<br /><br /> -   LocalMachine : magasin de certificats assigné à l'ordinateur local.<br />-   CurrentUser : magasin de certificats assigné à l'utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.|  
|`storeName`|Spécifie le nom du magasin de certificats X.509 à ouvrir.  Les valeurs valides sont les suivantes :<br /><br /> -   AddressBook : magasin de certificats pour d'autres utilisateurs.<br />-   AuthRoot : magasin de certificats pour les autorités de certification \(CA\) tierces.<br />-   CertificateAuthority : magasin de certificats pour les autorités de certification \(CA\) intermédiaires.<br />-   Disallowed : magasin de certificats pour les certificats révoqués.<br />-   My : magasin de certificats pour les certificats personnels.<br />-   Root : magasin de certificats pour les autorités de certification \(CA\) racines approuvées.<br />-   TrustedPeople : magasin de certificats pour les personnes et les ressources directement approuvées.<br />-   TrustedPublisher : magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.|  
|`X509FindType`|Définit le type de recherche X.509 à exécuter.  Les valeurs valides sont les suivantes :<br /><br /> -   FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> Le type contenu dans l'attribut `findValue` doit répondre aux spécifications du `X509FindType` spécifié.<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Spécifie les informations d'identification actuelles d'un nœud homologue.|  
  
## Notes  
 Cet élément de configuration contient une instance de `X509Certificate2` utilisée lors de l'authentification de voisins dans la maille d'homologues.  
  
 Pour plus d'informations sur la programmation pair à pair, consultez [Réseaux homologues](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>   
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>   
 <xref:System.ServiceModel.Security.PeerCredential>   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Réseaux homologues](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/fr-fr/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/fr-fr/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [Sécurisation des applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)