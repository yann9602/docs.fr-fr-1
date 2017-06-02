---
title: "&lt;peerAuthentication&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;peerAuthentication&gt;, &#233;l&#233;ment
Spécifie les options d'authentification pour les clients du réseau pair à pair.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] la programmation d'égal à égal, consultez [Réseaux homologues](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## Syntaxe  
  
```  
  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`customCertificateValidatorType`|Chaîne facultative.  Type et assembly utilisés pour valider un type personnalisé.  Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.|  
|`certifcateValidationMode`|Énumération facultative.  Spécifie l'un de trois modes utilisés pour valider des informations d'identification.  S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.  La valeur par défaut est `ChainTrust`.|  
|`revocationMode`|Énumération facultative.  Un des modes utilisés pour vérifier des listes de certificat révoqués \(CRL\).  La valeur par défaut est `Online`.|  
|`trustedStoreLocation`|Énumération facultative.  L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.  Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.  La validation est exécutée sur le magasin **Personnes autorisées** dans l'emplacement de magasin spécifié.  La valeur par défaut est `CurrentUser`.|  
  
## customCertificateValidatorType, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Chaîne|Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.  Au minimum, un espace de noms et un nom de type sont requis.  Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.|  
  
## certificateValidationMode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.  La valeur par défaut est `ChainTrust`.<br /><br /> Pour plus d'informations, consultez [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## revocationMode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.  La valeur par défaut est `Online`.<br /><br /> Pour plus d'informations, consultez [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## trustedStoreLocation, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.  La valeur par défaut est `CurrentUser`.  Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.  Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.|  
  
## Notes  
 L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>.  Cet élément spécifie un validateur, appelé pendant l'authentification de voisins dans la maille.  Lorsqu'un nouvel homologue essaie d'établir une connexion avec un voisin, il transmet ses propres informations d'identification à l'homologue répondant.  Le validateur du répondeur est appelé pour vérifier les informations d'identification du tiers distant.  Chaque fois qu'une connexion est établie avec un homologue de la maille, les deux homologues sont authentifiés mutuellement, ce qui signifie que des validateurs sont appelés à chaque extrémité.  
  
## Exemple  
 Le code suivant affecte la valeur `PeerOrChainTrust` au mode de validation du certificat.  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
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