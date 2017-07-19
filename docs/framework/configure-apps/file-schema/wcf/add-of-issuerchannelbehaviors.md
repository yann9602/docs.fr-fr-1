---
title: "&lt;add&gt; de &lt;issuerChannelBehaviors&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;add&gt; de &lt;issuerChannelBehaviors&gt;
Ajoute un comportement de point de terminaison à utiliser lors de la communication avec un service STS.  
  
> [!NOTE]
>  Lorsqu'un comportement de point de terminaison contient un élément [\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md), une exception est levée.  
  
## Syntaxe  
  
```  
  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|issuerAddress|URI de l'émetteur de jeton de sécurité avec lequel communiquer.|  
|behaviorConfiguration|Nom d'un comportement de point de terminaison défini dans le même fichier de configuration.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuerChannelBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Contient une collection de comportements de point de terminaison du client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] à utiliser lors d'une communication avec les services STS spécifiés.|  
  
## Notes  
 `issuerAddress` contient l'URI du service d'émission de jeton de sécurité avec lequel le client souhaite communiquer.  `behaviorConfiguration` pointe vers un comportement de point de terminaison que l'application utilise dans les canaux créés par [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] pour obtenir les jetons émis depuis les services d'émission de jeton de sécurité.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>   
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>   
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>   
 [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Comment : créer un client fédéré](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [Comment : configurer un émetteur local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [\<issuerChannelBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)