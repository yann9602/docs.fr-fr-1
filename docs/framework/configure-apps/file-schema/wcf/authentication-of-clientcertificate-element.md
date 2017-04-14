---
title: "&lt;authentication&gt;, &#233;l&#233;ment de &lt;clientCertificate&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# &lt;authentication&gt;, &#233;l&#233;ment de &lt;clientCertificate&gt;
Spécifie les comportements d'authentification des certificats clients utilisés par un service.  
  
## Syntaxe  
  
```  
  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|customCertificateValidatorType|Chaîne facultative.  Type et assembly utilisés pour valider un type personnalisé.  Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.|  
|certificateValidationMode|Énumération facultative.  Spécifie l'un des modes utilisés pour valider les informations d'identification.  Cet attribut est de type [System.Servicemodel.Security.X509CertificateValidationMode](assetId:///System.Servicemodel.Security.X509CertificateValidationMode?qualifyHint=False&amp;autoUpgrade=True).  S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.  La valeur par défaut est `ChainTrust`.|  
|includeWindowsGroups|Valeur booléenne facultative.  Spécifie si des groupes Windows sont inclus dans le contexte de sécurité.  L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait que cela provoque une expansion de groupe complète.  Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.|  
|mapClientCertificateToWindowsAcccount|Propriété booléenne.  Spécifie si le client peut être mappé à une identité Windows à l'aide du certificat.  Active Directory doit être activé pour cela.|  
|revocationMode|Énumération facultative.  Un des modes utilisés pour vérifier des listes de certificats révoqués \(RCL\).  La valeur par défaut est `Online`.  Cette valeur est ignorée lors de l'utilisation de la sécurité de transport HTTP.|  
|trustedStoreLocation|Énumération facultative.  L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.  Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.  La validation est exécutée sur le magasin **Personnes autorisées** dans l'emplacement de magasin spécifié.  La valeur par défaut est `CurrentUser`.|  
  
## customCertificateValidatorType, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Chaîne|Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.|  
  
## certificateValidationMode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.<br /><br /> Pour plus d'informations, consultez [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## revocationMode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : NoCheck, Online, Offline.  Pour plus d'informations, consultez [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## trustedStoreLocation, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.  La valeur par défaut est `CurrentUser`.  Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.  Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|Définit un certificat X.509 utilisé pour authentifier un client à un service.|  
  
## Notes  
 L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>.  Il vous permet de personnaliser la manière dont les clients sont authentifiés.  Vous pouvez affecter `certificateValidationMode`, `None`, `ChainTrust`, `PeerOrChainTrust` ou `PeerTrust` à l'attribut `Custom`.  Par défaut, le niveau a la valeur `ChainTrust`, laquelle spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une *autorité racine* au sommet de la chaîne.  C'est le mode le plus sécurisé.  Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto\-émis \(approbation homologue\) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.  Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto\-émis auprès d'une autorité approuvée.  Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.  
  
 Vous pouvez également utiliser `Custom`.  Lorsque vous utilisez `Custom`, vous devez également affecter l'assembly et le type utilisés pour valider le certificat à l'attribut `customCertificateValidatorType`.  Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.  Pour plus d'informations, consultez [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## Exemple  
 Le code suivant spécifie un certificat X.509 et un type de validation personnalisé dans l'élément `<authentication>`.  
  
```  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>   
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>   
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>   
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)