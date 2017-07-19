---
title: "&lt;servicePrincipalName&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;servicePrincipalName&gt;
Spécifie l'identité d'un service par son nom de principal du service \(SPN\).  
  
 Pour plus d'informations sur la définition du nom SPN, consultez [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## Syntaxe  
  
```  
  
<servicePrincipalName value = "String" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|par défaut|Nom SPN par lequel un client identifie de manière unique l'instance d'un service.  Si vous installez plusieurs instances d'un service sur les ordinateurs d'une forêt, chaque instance doit posséder son propre SPN.  Une instance de service donnée peut posséder plusieurs noms SPN si les clients peuvent utiliser plusieurs noms pour l'authentification.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## Notes  
 Un client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sécurisé qui se connecte à un point de terminaison avec cette identité utilise le SPN pour effectuer l'authentification SSPI avec le point de terminaison.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 <xref:System.ServiceModel.SpnEndpointIdentity>   
 [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)