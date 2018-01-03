---
title: '&lt;transport&gt; de &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fc0a7a402ab12d034db2e5a3e87a58168fa9cc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a>&lt;transport&gt; de &lt;netMsmqBinding&gt;
Définit les paramètres de sécurité de transport.  
  
 \<système. ServiceModel >  
\<liaisons >  
\<netMsmqBinding >  
\<liaison >  
\<sécurité >  
\<transport >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|msmqAuthenticationMode|Spécifie comment le message doit être authentifié par le transport MSMQ. Les valeurs valides sont les suivantes :<br /><br /> -None : Aucune authentification.<br />-WindowsDomain : Le mécanisme d’authentification utilise Active Directory pour récupérer le certificat X.509 pour l’identificateur de sécurité associé au message. Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation en écriture dans la file d'attente.<br />-Certificate : Le canal extrait le certificat du magasin de certificats.<br /><br /> La valeur par défaut est `WindowsDomain`.<br /><br /> Si cet attribut a la valeur `None`, l'attribut `msmqProtectionLevel` doit également être défini à `None`. Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages. Les valeurs valides sont les suivantes :<br /><br /> -RC4Stream<br />-AES<br />-La valeur par défaut est `RC4Stream`. Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|Spécifie la façon dont les messages sont sécurisés au niveau du transport MSMQ. Le chiffrement garantit l'intégrité des messages, tandis que la signature et le chiffrement garantissent à la fois l'intégrité et le non-rejet des messages. Autrement dit, le message a été effectivement envoyé par l'expéditeur et l'expéditeur est celui qu'il prétend. Les valeurs valides sont les suivantes :<br /><br /> -None : Aucune protection.<br />-Sign : Les Messages sont signés.<br />-EncryptAndSign : Les Messages sont chiffrés et signés.<br />-La valeur par défaut est `Sign`.|  
|msmqSecureHashAlgorithm|Spécifie l'algorithme de hachage à utiliser pour calculer le résumé de message. Les valeurs valides sont les suivantes :<br /><br /> -MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> La valeur par défaut est `SHA1`. Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Définit les paramètres de sécurité de transport pour les transports de mise en file d'attente.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Files d’attente dans WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
