---
title: "&lt;peerAuthentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;peerAuthentication&gt;
Spécifie des paramètres d'authentification pour un certificat d'homologue utilisé par un nœud homologue.  
  
## Syntaxe  
  
```  
  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`certificateValidationMode`|Énumération facultative.  Spécifie l'un de trois modes utilisés pour valider des informations d'identification.  Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.  S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.|  
|`customCertificateValidatorType`|Chaîne facultative.  Spécifie un type et un assembly utilisés pour valider un type personnalisé.  Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.  Cet attribut est de type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] fournit un validateur de certificat homologue par défaut qui vérifie le certificat homologue par rapport au magasin de personnes de confiance.  Il vérifie également que le certificat remonte jusqu'à une racine valide.  Vous pouvez implémenter un validateur personnalisé pour spécifier un comportement différent et utiliser cet attribut pour pointer vers ce validateur.|  
|`revocationMode`|Énumération facultative.  Spécifie le mode de révocation de certificat.  Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.  Le système vérifie que le certificat homologue n'a pas été révoqué en le recherchant dans la liste des certificats révoqués.  Cette vérification peut être effectuée en ligne ou par rapport à une liste de révocations mise en cache.  La vérification de la révocation peut être désactivée en affectant la valeur NoCheck à cet attribut.|  
|`trustedStoreLocation`|Énumération facultative.  Spécifie l'emplacement de magasin approuvé où le certificat homologue est validé par le système de sécurité [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Spécifie les informations d'identification actuelles d'un nœud homologue.|  
  
## Notes  
 L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>.  Cet élément spécifie un validateur, appelé pendant l'authentification de voisins dans la maille.  Lorsqu'un nouvel homologue essaie d'établir une connexion avec un voisin, il transmet ses propres informations d'identification à l'homologue répondant.  Le validateur du répondeur est appelé pour vérifier les informations d'identification du tiers distant.  Chaque fois qu'une connexion est établie avec un homologue de la maille, les deux homologues sont authentifiés mutuellement, ce qui signifie que des validateurs sont appelés à chaque extrémité.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>   
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Réseaux homologues](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/fr-fr/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/fr-fr/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [Sécurisation des applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)