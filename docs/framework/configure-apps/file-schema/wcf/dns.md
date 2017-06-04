---
title: "&lt;dns&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;dns&gt;
Spécifie l'identité attendue du serveur.  Cette identité est valide pour le mode d'authentification du certificat X509 si le certificat du serveur contient un DNS avec la même valeur.  Elle est également valide pour le mode d'authentification Windows si le SPN a la même valeur.  
  
 Pour plus d'informations sur la définition de la valeur de cet élément, consultez [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## Syntaxe  
  
```  
  
<dns value = "String" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|par défaut|Système DNS du certificat.  Le système DNS est un protocole standard utilisé pour localiser des ordinateurs sur un réseau IP.  Les utilisateurs peuvent se souvenir de noms complets, tels que [http:\/\/go.microsoft.com\/fwlink\/?prd\=10929](http://go.microsoft.com/fwlink/?prd=10929) ou [http:\/\/go.microsoft.com\/fwlink\/?LinkID\=96165](http://go.microsoft.com/fwlink/?LinkID=96165), qui sont plus simples que des adresses composées de chiffres \(207.46.131.137, par exemple\).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## Exemple  
 Le code de configuration suivant spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un serveur.  
  
```  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 <xref:System.ServiceModel.DnsEndpointIdentity>   
 [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)