---
title: "&lt;authentication&gt;, &#233;l&#233;ment de &lt;serviceCertificate&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;authentication&gt;, &#233;l&#233;ment de &lt;serviceCertificate&gt;
Spécifie les paramètres utilisés par le proxy client pour authentifier les certificats de service obtenus à l'aide de la négociation SSL\/TLS.  
  
## Syntaxe  
  
```  
  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|customCertificateValidatorType|Chaîne.  Type et assembly utilisés pour valider un type personnalisé.|  
|certificateValidationMode|Spécifie l'un de trois modes utilisés pour valider des informations d'identification.  S'il est défini à `Custom`, un customCertificateValidator doit également être fourni.  La valeur par défaut est `ChainTrust`.|  
|revocationMode|Un des modes utilisés pour vérifier des listes de certificat révoqués \(CRL\).  La valeur par défaut est `Online`.|  
|trustedStoreLocation|L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.  Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.  La validation est exécutée sur le magasin **Personnes autorisées** dans l'emplacement de magasin spécifié.  La valeur par défaut est `CurrentUser`.|  
  
## customCertificateValidator, attribut  
  
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
|Énumération|Une des valeurs suivantes : NoCheck, Online, Offline.<br /><br /> Pour plus d'informations, consultez [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## trustedStoreLocation, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : LocalMachine ou CurrentUser.  La valeur par défaut est CurrentUser.  Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans LocalMachine.  Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans CurrentUser.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Spécifie un certificat à utiliser lors de l'authentification d'un service au client.|  
  
## Notes  
 L'attribut `certificateValidationMode` de cet élément de configuration spécifie le niveau de confiance utilisé pour authentifier les certificats.  Par défaut, le niveau a la valeur `ChainTrust`, qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne.  C'est le mode le plus sécurisé.  Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto\-émis \(approbation homologue\) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.  Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto\-émis auprès d'une autorité approuvée.  Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.  Vous pouvez également affecter la valeur `Custom` ou `None`.  Pour utiliser la valeur `Custom`, vous devez également affecter à l'attribut `customCertificateValidator` l'assembly et le type utilisés pour valider le certificat.  Pour créer un validateur personnalisé, vous devez hériter de la classe X509CertificateValidator abstraite.  Pour plus d'informations, consultez [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 L'attribut `revocationMode` spécifie le mode de vérification des certificats à révoquer.  La valeur par défaut est `online`, qui indique que les certificats sont automatiquement vérifiés pour révocation.  Pour plus d'informations, consultez [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## Exemple  
 Dans l'exemple suivant, deux tâches sont effectuées :  Premièrement, un certificat de service est spécifié, que le client utilise au cours de communications avec les points de terminaison dont le nom de domaine est www.contoso.com sur le protocole HTTP.  Deuxièmement, le mode de révocation et l'emplacement de magasin utilisés pendant l'authentification sont définis.  
  
```  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>   
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)   
 [\<authentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)