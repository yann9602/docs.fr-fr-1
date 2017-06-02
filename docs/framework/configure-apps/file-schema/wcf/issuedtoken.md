---
title: "&lt;issuedToken&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;issuedToken&gt;
Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.  
  
## Syntaxe  
  
```  
  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`cacheIssuedTokens`|Attribut booléen facultatif indiquant si les jetons sont mis en cache.  La valeur par défaut est `true`.|  
|`defaultKeyEntropyMode`|Attribut de chaîne facultatif qui spécifie les valeurs aléatoires \(entropies\) utilisées pour les opérations de protocole de transfert.  Les valeurs comprennent `ClientEntropy`, `ServerEntropy` et `CombinedEntropy`. La valeur par défaut est `CombinedEntropy`.  Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Attribut entier facultatif indiquant le pourcentage d'un délai valide \(fourni par l'émetteur du jeton\) pouvant s'écouler avant le renouvellement d'un jeton.  Les valeurs sont comprises entre 0 et 100.  La valeur par défaut est 60, c'est\-à\-dire que 60 % du délai s'écoule avant la tentative de renouvellement.|  
|`issuerChannelBehaviors`|Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur.|  
|`localIssuerChannelBehaviors`|Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur local.|  
|`maxIssuedTokenCachingTime`|Attribut Timespan facultatif indiquant la durée de mise en cache des jetons émis lorsque l'émetteur de jeton \(un STS\) ne spécifie aucune durée.  La valeur par défaut est « 10675199.02:48:05.4775807 ».|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<localIssuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Spécifie l'adresse de l'émetteur local du jeton et la liaison utilisée pour communiquer avec le point de terminaison.|  
|[\<issuerChannelBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Spécifie les comportements de point de terminaison à utiliser lors d'une communication avec un émetteur local.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.|  
  
## Notes  
 Un jeton émis est un type d'informations d'identification personnalisé utilisé, par exemple, lors d'une authentification à l'aide d'un service STS dans un scénario fédéré.  Par défaut, le jeton est un jeton SAML.  Pour plus d'informations, consultez [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  et [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Cette section contient les éléments permettant de configurer un émetteur local de jetons ou les comportements utilisés avec un service d'émission de jeton de sécurité.  Pour obtenir des instructions sur la configuration d'un client pour qu'il utilise un émetteur local, consultez [Comment : configurer un émetteur local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>   
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Comment : créer un client fédéré](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [Comment : configurer un émetteur local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)