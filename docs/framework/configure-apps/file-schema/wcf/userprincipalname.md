---
title: "&lt;userPrincipalName&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;userPrincipalName&gt;
Indique le nom d'utilisateur principal \(UPN\) d'un service à authentifier par le client.  
  
 Pour plus d'informations sur la définition du nom UPN, consultez [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## Syntaxe  
  
```  
  
<userPrincipalName value = "String" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|par défaut|Nom de compte d'utilisateur \(parfois connu sous le nom de connexion d'utilisateur\) et nom de domaine identifiant le domaine dans lequel se trouve le compte d'utilisateur.  Il s'agit de la méthode de connexion standard à un domaine Windows.  Le format est : personne@exemple.com \(comme pour une adresse de messagerie\).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## Notes  
 Un client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sécurisé qui se connecte à un point de terminaison avec cette identité utilise l'UPN pour effectuer l'authentification SSPI avec le point de terminaison.  
  
## Exemple  
 Le code de configuration suivant indique le nom UPN du service devant être authentifié par le client.  
  
```  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 <xref:System.ServiceModel.UpnEndpointIdentity>   
 [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)