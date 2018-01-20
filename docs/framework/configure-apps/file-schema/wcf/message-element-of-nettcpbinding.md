---
title: "&lt;message&gt;, élément de &lt;netTcpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab40ab1cd889665829e42072803010ad49e717a9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a>&lt;message&gt;, élément de &lt;netTcpBinding&gt;
Définit le type d’exigences de sécurité au niveau du message pour un point de terminaison configuré avec la [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<bindings>  
\<netTcpBinding>  
\<binding>  
\<security>  
\<message>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message   
      algorithmSuite=System.Servicemodel.Security.SecurityAlgorithmsuite  
    clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`algorithmSuite`|Définit les algorithmes de chiffrement de message et de clé de type WRAP. Les algorithmes et les tailles de clé sont déterminés par la classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Le tableau ci-dessous répertorie les valeurs possibles. La valeur par défaut est `Basic256`.<br /><br /> Si la liaison de service spécifie une valeur `algorithmSuite` qui n'est pas égale à la valeur par défaut, et que vous générez le fichier de configuration à l'aide de Svcutil.exe, celui-ci n'est pas généré correctement et vous devez modifier manuellement le fichier de configuration pour affecter à cet attribut la valeur souhaitée.|  
|`clientCredentialType`|Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur les messages. Le tableau ci-dessous répertorie les valeurs possibles. La valeur par défaut est `UserName`. Cet attribut est de type <xref:System.ServiceModel.MessageCredentialType>.|  
  
## <a name="algorithmsuite-attribute"></a>Attribut algorithmSuite  
  
|Valeur|Description|  
|-----------|-----------------|  
|Basic128|Utilisez le chiffrement Aes128, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic192|Utilisez le chiffrement Aes192, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256|Utilisez le chiffrement Aes256, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256Rsa15|Utilisez Aes256 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic192Rsa15|Utilisez Aes192 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDes|Utilisez le chiffrement TripleDes, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic128Rsa15|Utilisez Aes128 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDesRsa15|Utilisez le chiffrement TripleDes, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic128Sha256|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic192Sha256|Utilisez Aes192 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256Sha256|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|TripleDesSha256|Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic128Sha256Rsa15|Utilisez Aes128 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic192Sha256Rsa15|Utilisez Aes192 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic256Sha256Rsa15|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDesSha256Rsa15|Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
  
## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|Permet au service d'interagir avec les clients anonymes. Au niveau du service, indique que ce dernier ne requiert pas d'informations d'identification du client. Au niveau du client, indique que ce dernier ne fournit pas d'informations d'identification du client.|  
|Windows|Permet aux échanges SOAP d'être placés dans le contexte authentifié d'informations d'identification Windows.|  
|UserName|Autorise le service à imposer que le client soit authentifié à l'aide d'une information d'identification UserName. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ne prend pas en charge l'envoi d'un mot de passe Digest ou la dérivation de clés à l'aide du mot de passe et l'utilisation de telles clés pour la sécurité de message. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] s'assure ainsi que le transport est sécurisé lors de l'utilisation d'informations d'identification UserName. Ce mode d'informations d'identification a pour résultat soit un échange interopérable, soit une négociation non interopérable basée sur l'attribut `negotiateServiceCredential`.|  
|Certificat|Autorise le service à exiger une authentification du client via un certificat. Si le mode de sécurité des messages est utilisé et que l'attribut `negotiateServiceCredential` a la valeur `false`, le client doit être configuré avec le certificat de service.|  
|IssuedToken|Spécifie un jeton personnalisé, généralement émis par un service de jeton de sécurité (STS).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Définit les fonctionnalités de sécurité pour le <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.|  
  
## <a name="remarks"></a>Notes  
 Le message utilise la sécurité au niveau du message pour l'intégrité et la confidentialité du message SOAP, ainsi que pour l'authentification mutuelle des homologues de communication. Si ce mode de sécurité est sélectionné sur une liaison, la pile de canaux est configurée avec les éléments de liaison de sécurité du message et les messages SOAP sont sécurisés conformément aux normes WS-Security*.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)
