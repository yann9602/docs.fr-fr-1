---
title: '&lt;transport&gt; de &lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60880461a3d71e64be2b3b74b1a236625426c2b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a>&lt;transport&gt; de &lt;netPeerTcpBinding&gt;
Spécifie les paramètres de sécurité de niveau transport lors de l’utilisation du [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).  
  
 \<système. ServiceModel >  
\<liaisons >  
\<netPeerTcpBinding >  
\<liaison >  
\<sécurité >  
\<transport >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|credentialType|Facultatif. Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues. Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.|  
  
## <a name="credentialtype-attribute"></a>Attribut credentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|Certificat|L'authentification du transport de canal homologue requiert un certificat X509.|  
|Mot de passe|L'authentification du transport de canal homologue requiert un mot de passe correct.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|Définit les paramètres de sécurité pour le [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
