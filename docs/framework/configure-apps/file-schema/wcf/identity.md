---
title: '&lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e583acee6309b6f8145cf8567cff12cea1c237e7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltidentitygt"></a>&lt;identity&gt;
L'élément d'identité autorise un développeur client à spécifier au moment de la conception l'identité attendue du service. Dans le processus de négociation entre le client et le service, l'infrastructure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] garantit que l'identité du service attendu correspond aux valeurs de cet élément et peut donc être authentifiée. Pour plus d’informations, consultez [l’identité du Service et l’authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|certificate|Spécifie les paramètres d'un certificat X.509. Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateElement>. Il contient un `encodedValue` d'attribut qui est une chaîne indiquant la valeur encodée par ce certificat.|  
|certificateReference|Spécifie les paramètres de validation du certificat X.509. Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un service. Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.|  
|rsa|Indique la valeur du champ RSA d'un certificat X.509 utilisée pour authentifier un service au niveau d'un client. Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.|  
|servicePrincipalName|Indique le nom SPN correspondant au nom principal utilisé par un client pour identifier de manière unique l'instance d'un service. Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel. Cet élément est de type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Spécifie une identité UPN correspondant au type de nom de connexion d'un utilisateur sur un réseau. Le nom d'utilisateur principal se compose du nom d'objet utilisateur utilisé dans Active Directory, suivi par le symbole @, puis, généralement, du domaine DNS parent. Par exemple, dans l’arborescence de domaine Fabrikam.com peut avoir le nom d’utilisateur principal [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel. Cet élément est de type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<custom>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Indique le programme de résolution d'homologue personnalisé pour un netPeerTcpBinding.|  
|[\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)|Configure différents types de points de terminaison.|  
|[\<issuer>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Spécifie le service STS pour le service fédéré.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Spécifie le point de terminaison de métadonnées pour le service STS d'un service fédéré.|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Définit des paramètres correspondant à un jeton émis dans une liaison personnalisée.|  
|[\<localIssuer>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Spécifie un service STS local.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Points de terminaison : adresses, liaisons et contrats](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
