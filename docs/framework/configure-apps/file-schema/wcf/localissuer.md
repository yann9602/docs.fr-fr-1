---
title: "&lt;localIssuer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;localIssuer&gt;
Spécifie l'adresse et la liaison de l'émetteur local à utiliser pour obtenir un jeton de sécurité.  
  
## Syntaxe  
  
```  
  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|address|Chaîne requise.  Spécifie l'URI de l'émetteur local.|  
|liaison|Chaîne facultative.  Une des liaisons fournies par le système.  Pour obtenir une liste, consultez [Liaisons fournies par le système](../../../../../docs/framework/wcf/system-provided-bindings.md).|  
|bindingConfiguration|Chaîne facultative.  Spécifie une configuration de liaison recherchée dans le fichier de configuration.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Spécifie les informations d'identité de l'émetteur local.|  
|[\<en\-têtes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Collection d'en\-têtes d'adresse requis pour adresser correctement l'émetteur local.  Vous pouvez utiliser le mot clé `add` pour ajouter un en\-tête à cette collection.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedToken\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.|  
  
## Notes  
 Lors de l'obtention d'un jeton émis depuis un service d'émission de jeton de sécurité \(STS\), l'application cliente doit être configurée avec l'adresse et la liaison à utiliser pour pouvoir communiquer avec le STS.  Lorsque <xref:System.ServiceModel.WSFederationHttpBinding> ne fournit pas d'URL pour le service d'émission de jeton de sécurité ou lorsque l'adresse de l'émetteur d'une liaison fédérée est http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous ou `null`, le canal [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] du client utilise les valeurs spécifiées par `address` et `binding` afin de communiquer avec le STS pour obtenir le jeton émis.  Pour plus d'informations sur la configuration d'un émetteur local, consultez [Comment : configurer un émetteur local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## Exemple  
 L'exemple suivant définit les attributs `address`, `binding` et `bindingConfiguration` d'un élément `localIssuer`.  
  
```  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>   
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Comment : configurer un émetteur local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Comment : créer un client fédéré](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)