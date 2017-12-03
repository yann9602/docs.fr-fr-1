---
title: "Sécurisation des applications de canal homologue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 377c2425ff1647c43687aa0a5d9584930cb6b1c2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="securing-peer-channel-applications"></a>Sécurisation des applications de canal homologue
Comme d'autres liaisons sous le [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` a la sécurité activée par défaut et offre les sécurités de transport et de message. Cette rubrique traite de ces deux types de sécurité. Le type de sécurité est spécifié par la balise de mode de sécurité dans la spécification de liaison (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Sécurité basée sur le transport  
 Le canal homologue prend en charge deux types d'informations d'identification pour l'authentification en vue de sécuriser le transport. Les deux impliquent la définition de la propriété `ClientCredentialSettings.Peer` sur la `ChannelFactory` associée :  
  
-   Mot de passe. Les clients utilisent leur connaissance d'un mot de passe secret pour authentifier les connexions. Lorsque ce type d'informations d'identification est utilisé, `ClientCredentialSettings.Peer.MeshPassword` doit contenir un mot de passe valide et éventuellement une instance `X509Certificate2`.  
  
-   certificat ;  L'authentification d'application spécifique est utilisée. Lorsque ce type d'informations d'identification est utilisé, vous devez utiliser une implémentation concrète de <xref:System.IdentityModel.Selectors.X509CertificateValidator> dans `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>Sécurité basée sur le message  
 Avec la sécurité basée sur le message, une application peut signer les messages sortants afin que tous les destinataires puissent vérifier que le message a été envoyé par un correspondant approuvé et qu'il n'a pas été falsifié. Actuellement, le canal homologue prend en charge uniquement la signature des messages d'informations d'identification X.509.  
  
## <a name="best-practices"></a>Meilleures pratiques  
  
-   Cette section présente les meilleures pratiques pour sécuriser les applications de canal homologue.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Activer la sécurité avec les applications de canal homologue  
 En raison de la nature distribuée des protocoles de canal homologue, il est difficile d'appliquer l'appartenance de maille et la confidentialité dans une maille non protégée. Il convient également de penser à sécuriser la communication entre les clients et le service de résolution. Sous le protocole PNRP (Peer Name Resolution Protocol), utilisez des noms sécurisés afin d'éviter l'usurpation et autres attaques courantes. Sécurisez un service de résolution personnalisé en activant la sécurité sur les clients de connexion utilisés pour contacter le service de résolution, avec à la fois la sécurité de message et la sécurité de transport.  
  
### <a name="use-the-strongest-possible-security-model"></a>Utiliser le modèle de sécurité le plus fort possible  
 Par exemple, si chaque membre de la maille doit être identifié individuellement, utilisez un modèle d'authentification basé les certificats. Si cela est impossible, utilisez l'authentification basée sur mot de passe et suivez les recommandations actuelles afin d'assurer leur sécurité. Cela implique le partage des mots de passe uniquement avec des correspondants de confiance, la transmission des mots de passe à l'aide d'un support sécurisé, la modification fréquente des mots de passe et la garantie que les mots de passe sont forts (longueur d'au moins huit caractères, au moins une lettre de chaque casse, un chiffre et un caractère spécial).  
  
### <a name="never-accept-self-signed-certificates"></a>Ne jamais accepter de certificats auto-signés  
 N'acceptez jamais d'informations d'identification de certificat basées sur des noms de sujet. Notez que n'importe qui peut créer un certificat et choisir un nom que vous validez. Pour éviter la possibilité d'usurpation, validez les certificats sur la base des informations d'identification d'autorité émettrice (un émetteur approuvé ou une autorité de certification racine).  
  
### <a name="use-message-authentication"></a>Utiliser l'authentification de message  
 Utilisez l'authentification de message pour vérifier qu'un message provient d'une source fiable et que personne ne l'a falsifié durant la transmission. Sans authentification de message, il est facile pour un client malveillant d'usurper ou de falsifier des messages dans la maille.  
  
## <a name="peer-channel-code-examples"></a>Exemples de code de canal homologue  
 [Scénarios de canal homologue](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de canal homologue](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Création d’une Application de canal homologue](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
