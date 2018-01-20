---
title: '&lt;message&gt; de &lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60f0b1d767cba44d1eedc4fdd37ee6b038952ef8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagegt-of-ltwsdualhttpbindinggt"></a>&lt;message&gt; de &lt;wsDualHttpBinding&gt;
Définit la sécurité au niveau du message pour le [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 \<system.ServiceModel>  
\<bindings>  
\<wsDualHttpBinding>  
\<binding>  
\<security>  
\<message>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message   
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
     negotiateServiceCredential="Boolean"  
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"/>  
</message>  
```  
  
## <a name="type"></a>Type  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|algorithmSuite|Facultatif. Définit les algorithmes de chiffrement de message et de clé de type WRAP. Les algorithmes et les tailles de clé sont déterminés par la classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Une liste des valeurs possibles se trouve ci-après. La valeur par défaut est `Basic256`.|  
|clientCredentialType|Facultatif. Spécifie le type d'information d'identification à utiliser lorsque l'exécution de l'authentification du client à l'aide du mode de sécurité est `Message`. Une liste des valeurs possibles se trouve ci-après. La valeur par défaut est `Windows`.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|Facultatif. Valeur booléenne qui spécifie si les informations d'identification du service sont configurées sur le client hors bande ou transférées du service au client via un processus de négociation. Ce type de négociation précède l'échange habituel de messages.<br /><br /> Si le `clientCredentialType` attribut correspond à aucun nom d’utilisateur ou de certificat, cet attribut `false` implique que le certificat de service est disponible au niveau du client hors bande et que le client spécifier le certificat de service (à l’aide de la [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) dans le [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) comportement de service. Ce mode est interopérable avec les piles SOAP qui implémentent WS-Trust et WS-SecureConversation.<br /><br /> Si l'attribut `ClientCredentialType` a la valeur `Windows`, l'affectation de la valeur `false` à cet attribut spécifie l'authentification basée sur Kerberos. Cela signifie que le client et le service doivent faire partie du même domaine Kerberos. Ce mode est interopérable avec les piles SOAP qui implémentent le profil de jeton Kerberos (comme défini dans OASIS WSS TC) ainsi que WS-Trust et WS-SecureConversation. Lorsque cet attribut a la valeur `true`, il entraîne une négociation .NET SOAP qui tunnelle l'échange SPNego par des messages SOAP.<br /><br /> La valeur par défaut est `true`.|  
  
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
|None|Permet au service d'interagir avec les clients anonymes. Du côté du service, cela indique que le service ne requiert pas d'informations d'identification du client. Au niveau du client, indique que ce dernier ne fournit pas d'informations d'identification du client.|  
|Windows|Permet aux échanges SOAP d'être placés dans le contexte authentifié d'informations d'identification Windows. Si l'attribut `negotiateServiceCredential` a la valeur `true`, cela exécute une négociation SSPI ou Kerberos (norme interopérable).|  
|UserName|Autorise le service à imposer que le client soit authentifié à l'aide d'une information d'identification UserName. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ne prend pas en charge l'envoi d'un mot de passe Digest ou la dérivation de clés à l'aide du mot de passe et l'utilisation de telles clés pour la sécurité de message. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] s'assure ainsi que le transport est sécurisé lors de l'utilisation d'informations d'identification UserName. Ce mode d'informations d'identification a pour résultat soit un échange interopérable, soit une négociation non interopérable basée sur l'attribut `negotiateServiceCredential`.|  
|Certificat|Autorise le service à exiger une authentification du client via un certificat. Si le mode de sécurité du message est utilisé et que l'attribut `negotiateServiceCredential` est définit à `false`, le client doit être configuré avec le certificat de service.|  
|IssuedToken|Spécifie un jeton personnalisé, habituellement publié par un service d'émission de jeton de sécurité.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Définit les fonctionnalités de sécurité le [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)
