---
title: "&lt;peer&gt;, élément de &lt;clientCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f26321afdbe53c4ab3750eae4a7a730bcb5ae4e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a>&lt;peer&gt;, élément de &lt;clientCredentials&gt;
Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.  
  
 \<système. ServiceModel >  
\<comportements >  
\<endpointBehaviors >  
\<comportement >  
\<clientCredentials >  
\<homologue >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<certificat >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair. .|  
|[\<peerAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|Spécifie les options d'authentification pour les clients du réseau pair à pair.|  
|[\<messageSenderAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|Spécifie les options d'authentification pour les expéditeurs de messages.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément de configuration spécifie les informations d'identification qu'un nœud homologue utilise pour s'authentifier sur les autres nœuds de la maille, ainsi que les paramètres d'authentification qu'un nœud homologue utilise pour authentifier les autres nœuds homologues. Pour plus d’informations, consultez [l’authentification de Message du canal homologue](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) et [sécurisation des Applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Mise en réseau pair à pair](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)  
 [Authentification de Message de canal homologue](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Authentification personnalisée de canal homologue](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Sécurisation des Applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
