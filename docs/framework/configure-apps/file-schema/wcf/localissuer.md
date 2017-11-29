---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b11f5cbf2d70b4fff607ac42c2c98af7fb9542b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlocalissuergt"></a>&lt;localIssuer&gt;
Spécifie l’adresse et la liaison de l’émetteur local à utiliser pour obtenir un jeton de sécurité.  
  
 \<système. ServiceModel >  
\<comportements >  
section d’endpointBehaviors  
\<comportement >  
\<clientCredentials >  
\<jeton issuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|address|Chaîne requise. Spécifie l'URI de l'émetteur local.|  
|liaison|Chaîne facultative. Une des liaisons fournies par le système. Pour obtenir la liste, consultez [les liaisons fournies](../../../../../docs/framework/wcf/system-provided-bindings.md).|  
|bindingConfiguration|Chaîne facultative. Spécifie une configuration de liaison recherchée dans le fichier de configuration.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identité >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Spécifie les informations d'identité de l'émetteur local.|  
|[\<en-têtes >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Collection d’en-têtes d’adresse requis pour adresser correctement l’émetteur local. Vous pouvez utiliser le mot clé `add` pour ajouter un en-tête à cette collection.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<jeton issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.|  
  
## <a name="remarks"></a>Remarques  
 Lors de l’obtention d’un jeton émis depuis un service d’émission de jeton de sécurité (STS), l’application cliente doit être configurée avec l’adresse et la liaison à utiliser pour pouvoir communiquer avec le STS. Lorsque <xref:System.ServiceModel.WSFederationHttpBinding> ne fournit pas d'URL pour le service d'émission de jeton de sécurité ou lorsque l'adresse de l'émetteur d'une liaison fédérée est http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous ou `null`, le canal [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] du client utilise les valeurs spécifiées par `address` et `binding` afin de communiquer avec le STS pour obtenir le jeton émis. Pour plus d’informations sur la configuration d’un émetteur local, consultez [Comment : configurer un émetteur Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant définit les attributs `address`, `binding` et `bindingConfiguration` d'un élément `localIssuer`.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Comment : configurer un émetteur Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [L’authentification et identité de Service](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)  
 [Comment : créer un Client fédéré](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
