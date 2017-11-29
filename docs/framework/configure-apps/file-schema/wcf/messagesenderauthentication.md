---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 428dbdc65a4f66e5632e4ded7d7ded0d10b7c9d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagesenderauthenticationgt"></a>&lt;messageSenderAuthentication&gt;
Spécifie les paramètres d'authentification pour le certificat homologue utilisé par l'expéditeur d'un message.  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<serviceCredentials >  
\<homologue >  
\<messageSenderAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`certificateValidationMode`|Énumération facultative. Spécifie l'un des cinq modes utilisés pour valider les informations d'identification. Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>. S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.|  
|`customCertificateValidatorType`|Chaîne facultative. Spécifie un type et un assembly utilisés pour valider un type personnalisé. Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`. Cet attribut est de type <xref:System.IdentityModel.Selectors.X509CertificateValidator>. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] fournit un validateur de certificat homologue par défaut qui vérifie le certificat homologue par rapport au magasin de personnes de confiance. Il vérifie également que le certificat remonte jusqu'à une racine valide. Vous pouvez implémenter un validateur personnalisé pour spécifier un comportement différent et utiliser cet attribut pour pointer vers ce validateur.|  
|`revocationMode`|Énumération facultative. Spécifie le mode de révocation de certificat. Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Le système vérifie que le certificat homologue n'a pas été révoqué en le recherchant dans la liste des certificats révoqués. Cette vérification peut être effectuée en ligne ou par rapport à une liste de révocations mise en cache. La vérification de la révocation peut être désactivée en affectant la valeur NoCheck à cet attribut.|  
|`trustedStoreLocation`|Énumération facultative. Spécifie l'emplacement de magasin approuvé où le certificat homologue est validé par le système de sécurité [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<homologue >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Spécifie les informations d'identification actuelles d'un nœud homologue.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément doit être configuré si l'authentification des messages est sélectionnée. Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [ \<certificat >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément. Le validateur peut accepter ou rejeter les informations d'identification.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Mise en réseau pair à pair](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Authentification de Message de canal homologue](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Authentification personnalisée de canal homologue](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Sécurisation des Applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
