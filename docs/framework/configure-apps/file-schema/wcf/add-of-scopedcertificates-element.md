---
title: "&lt;add&gt;, &#233;l&#233;ment de &lt;scopedCertificates&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &lt;add&gt;, &#233;l&#233;ment de &lt;scopedCertificates&gt;
Ajoute un certificat X.509 à la collection de certificats étendus.  
  
## Syntaxe  
  
```  
  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|targetUri|Chaîne.  Spécifie l'URI du service a associé au certificat.|  
|findValue|Chaîne.  La valeur à rechercher.|  
|x509FindType|Énumération.  L'un des champs de certificat à rechercher.|  
|storeLocation|Énumération.  L'un des deux emplacements du magasin dans lequel effectuer la recherche.|  
|storeName|Énumération.  L'un des magasins de systèmes à rechercher.|  
  
## findValue, attribute  
  
|Valeur|Description|  
|------------|-----------------|  
|Chaîne|La valeur dépend du champ \(spécifié par l'attribut X509FindType\) qui est recherché.  Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.|  
  
## x509FindType, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Les valeurs comprennent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## storeLocation, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|CurrentUser ou LocalMachine.|  
  
## storeName, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Les valeurs comprennent : AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople et TrustedPublisher.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<scopedCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|Représente une collection de certificats X.509 fournie par les services spécifiques \(étendus\) à des fins d'authentification.|  
  
## Notes  
 Cet élément permet au client de configurer un certificat de service à utiliser en fonction de l'URL du service avec lequel il communique.  Ceci s'avère particulièrement utile dans les scénarios de jeton émis dans lesquels un client peut communiquer avec plusieurs services \(autant le service final que les services de jeton de sécurité intermédiaire\).  Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, ce certificat est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.  
  
 Le certificat par défaut est utilisé si une liaison requiert un certificat pour le service et qu'aucun certificat spécifique de l'URL du service n'est trouvé dans ScopedCertificates.  
  
 Pour plus d'informations, consultez la section "Certificats à étendue" dans [Comment : créer un client fédéré](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
## Exemple  
 L'exemple suivant illustre l'ajout d'un certificat X.509 à la collection.  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <serviceCertificate>  
     <scopedCertificates>  
      <add targetUri="http://www.contoso.com"   
       findValue="www.Contoso.com"   
       storeLocation="LocalMachine"  
       storeName="Root"   
       x509FindType="FindByIssuerName" />  
     </scopedCertificates>  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>   
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>   
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>   
 [Comment : créer un client fédéré](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)