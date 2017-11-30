---
title: '&lt;add&gt; de &lt;issuerChannelBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7dca60a5bf1b3dd81502f9fd48d2881c3a9b71dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a>&lt;add&gt; de &lt;issuerChannelBehaviors&gt;
Ajoute un comportement de point de terminaison à utiliser lors de la communication avec un service STS.  
  
> [!NOTE]
>  Si un comportement de point de terminaison contient un [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) élément, une exception sera levée.  
  
 \<système. ServiceModel >  
\<comportements >  
section d’endpointBehaviors  
\<comportement >  
\<clientCredentials >  
\<jeton issuedToken >  
\<issuerChannelBehaviors > élément  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|issuerAddress|URI de l'émetteur de jeton de sécurité avec lequel communiquer.|  
|behaviorConfiguration|Nom d'un comportement de point de terminaison défini dans le même fichier de configuration.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Contient une collection de comportements de point de terminaison du client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] à utiliser lors d'une communication avec les services STS spécifiés.|  
  
## <a name="remarks"></a>Remarques  
 `issuerAddress` contient l'URI du service d'émission de jeton de sécurité avec lequel le client souhaite communiquer. `behaviorConfiguration` pointe vers un comportement de point de terminaison que l'application utilise dans les canaux créés par [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] pour obtenir les jetons émis depuis les services d'émission de jeton de sécurité.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [L’authentification et identité de Service](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)  
 [Comment : créer un Client fédéré](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Comment : configurer un émetteur Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
