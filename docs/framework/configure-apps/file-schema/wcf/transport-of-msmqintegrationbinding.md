---
title: '&lt;transport&gt; de &lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27b2ade7c9033ca82d3249ef18f1004e30c30025
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a>&lt;transport&gt; de &lt;msmqIntegrationBinding&gt;
Définit les paramètres de sécurité pour le transport d'intégration Message Queuing.  
  
 \<système. ServiceModel >  
\<liaisons >  
msmqIntegrationBinding  
\<liaison >  
\<sécurité >  
\<transport >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Spécifie comment le message doit être authentifié par le transport MSMQ. S'il a la valeur `None`, la valeur de l'attribut `msmqProtectionLevel` doit également être `None`.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> -None : Aucune authentification.<br />-WindowsDomain : Le mécanisme d’authentification utilise Active Directory pour obtenir le certificat X.509 du SID associé au message. Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation d'écrire dans la file d'attente.<br />-Certificate : Le canal Obtient le certificat du magasin de certificats.<br /><br /> La valeur par défaut est WindowsDomain. Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages. Les valeurs valides sont les suivantes :<br /><br /> -RC4Stream<br />-AES<br /><br /> La valeur par défaut est RC4Stream. Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Spécifie le mode de sécurisation du message au niveau du transport MSMQ. Le chiffrement garantit l'intégrité des messages tandis que EncryptAndSign garantit à la fois l'intégrité des messages et leur non-rejet ; autrement dit, le message vient en effet de l'expéditeur et c'est celui-ci qui se déclare lui-même.<br /><br /> -Les valeurs valides sont les suivantes :<br />-None : Aucune protection.<br />-Sign : Les Messages sont signés.<br />-EncryptAndSign : Les Messages sont chiffrés et signés.<br /><br /> La valeur par défaut est Sign. Cet attribut est de type ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|-Spécifie l’algorithme à utiliser pour calculer le digest dans le cadre des signatures. Les valeurs valides sont les suivantes :<br />-MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> La valeur par défaut est SHA1. Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Définit les paramètres de sécurité pour une liaison MSMQ.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément encapsule les paramètres de sécurité pour le transport d'intégration MSMQ. Les paramètres sont les mêmes à la fois pour le transport d'intégration Message Queuing et le transport de mise en file d'attente. Cet élément vous permet de définir le mode d'authentification, l'algorithme de chiffrement, l'algorithme de hachage sécurisé et le niveau de protection.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
