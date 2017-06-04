---
title: "&lt;issuerMetadata&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# &lt;issuerMetadata&gt;
## Syntaxe  
  
```  
  
<issuerMetadata address=String" >  
   <headers>  
      <add name="String"  
                 namespace="String" />  
   </headers>  
   <identity>  
           <certificate encodedValue="String"/>  
      <certificateReference findValue="String"   
         isChainIncluded="Boolean"  
         storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
         storeLocation="LocalMachine/CurrentUser"  
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuerMetadata>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|address|Attribut `string` requis.<br /><br /> Spécifie l'adresse du point de terminaison.  L'adresse doit être un URI absolu.  La valeur par défaut est une chaîne vide.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<en\-têtes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Collection d'en\-têtes d'adresses.|  
|[\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|Définit les paramètres de sécurité au niveau du message pour l'élément [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).|  
  
## Voir aussi  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>   
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>   
 [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)