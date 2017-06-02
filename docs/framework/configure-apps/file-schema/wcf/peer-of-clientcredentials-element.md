---
title: "&lt;peer&gt;, &#233;l&#233;ment de &lt;clientCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;peer&gt;, &#233;l&#233;ment de &lt;clientCredentials&gt;
Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.  
  
## Syntaxe  
  
```  
  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<certificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair.  .|  
|[\<peerAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|Spécifie les options d'authentification pour les clients du réseau pair à pair.|  
|[\<messageSenderAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|Spécifie les options d'authentification pour les expéditeurs de messages.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.|  
  
## Notes  
 Cet élément de configuration spécifie les informations d'identification qu'un nœud homologue utilise pour s'authentifier sur les autres nœuds de la maille, ainsi que les paramètres d'authentification qu'un nœud homologue utilise pour authentifier les autres nœuds homologues.  Pour plus d’informations, consultez [Peer Channel Message Authentication](http://msdn.microsoft.com/fr-fr/80e73386-514e-4c30-9e4a-b9ca8c173a95) et [Sécurisation des applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>   
 <xref:System.ServiceModel.Security.PeerCredential>   
 [Réseaux homologues](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/fr-fr/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/fr-fr/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [Sécurisation des applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)