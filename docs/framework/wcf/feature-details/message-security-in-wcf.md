---
title: "Sécurité des messages dans WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 21cbeff554be6da77ce28e87b7f82ffdd58f542d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="message-security-in-wcf"></a>Sécurité des messages dans WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] possède deux principaux modes de sécurité (`Transport` et `Message`) et un troisième mode (`TransportWithMessageCredential`) qui associe les deux premiers. Cette rubrique présente la sécurité des messages et les raisons de l'employer.  
  
## <a name="what-is-message-security"></a>Qu'est ce que la sécurité des messages ?  
 La sécurité des messages utilise la spécification WS-Security pour sécuriser les messages. La spécification Ws-Security décrit les améliorations apportées à la messagerie SOAP afin de garantir la confidentialité, l'intégrité et l'authentification au niveau du message SOAP (plutôt qu'au niveau du transport).  
  
 En bref, la sécurité des messages diffère de la sécurité du transport en encapsulant les informations d'identification de sécurité et les revendications avec chaque message accompagné de toute protection des messages (signature ou chiffrement). L'application directe de la sécurité au message en modifiant son contenu permet au message sécurisé d'être autonome en ce qui concerne les aspects de la sécurité. Cela permet quelques scénarios qui ne sont pas possibles lorsque la sécurité du transport est utilisée.  
  
## <a name="reasons-to-use-message-security"></a>Raisons d'utiliser la sécurité des messages  
 Dans la sécurité au niveau du message, toutes les informations de sécurité sont encapsulées dans le message. La sécurisation du message avec une sécurité au niveau du message au lieu d'une sécurité au niveau du transport présente les avantages suivants :  
  
-   Sécurité de bout en bout. La sécurité du transport, telle que le protocole SSL (Secure Sockets Layer), ne sécurise les messages que lorsqu'il s'agit d'une communication point à point. Si le message est routé vers un ou plusieurs intermédiaires SOAP (par exemple, un routeur) avant d'atteindre le dernier destinataire, il n'est lui-même pas protégé une fois qu'un intermédiaire l'a lu depuis le câble. En outre, les informations d'authentification du client sont uniquement disponibles pour le premier intermédiaire et doivent être retransmises au dernier destinataire de manière hors bande, si nécessaire. Cela s'applique même si l'itinéraire entier utilise la sécurité SSL entre des sauts individuels. Étant donné que la sécurité des messages fonctionne directement avec le message et sécurise le XML qu'il contient, la sécurité reste avec le message indépendamment du nombre d'intermédiaires impliqué avec le message avant qu'il n'atteigne le dernier destinataire. Il s'agit donc d'un vrai scénario de sécurité de bout en bout.  
  
-   Flexibilité augmentée. Vous pouvez signer ou chiffrer des parties du message, au lieu du message entier. Cela signifie que les intermédiaires peuvent consulter les parties du message qui leur sont destinées. Si l'expéditeur a besoin de rendre une partie des informations du message visible aux intermédiaires mais qu'il souhaite empêcher sa falsification, il peut juste la signer et la laisser déchiffrée. Puisque la signature fait partie du message, le dernier destinataire peut vérifier que les informations du message ont été reçues intactes. Un autre scénario peut impliquer un service d'intermédiaire SOAP qui route un message en fonction de la valeur d'en-tête Action. Par défaut, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne chiffre pas la valeur Action mais la signe si la sécurité des messages est utilisée. Par conséquent, ces informations sont disponibles à tous les intermédiaires, mais personne ne peut les modifier.  
  
-   Prise en charge de plusieurs transports. Vous pouvez envoyer des messages sécurisés sur de nombreux transports différents, tels que les canaux nommés et le protocole TCP, sans devoir compter sur le protocole pour la sécurité. Avec la sécurité au niveau du transport, toutes les informations de sécurité sont étendues à une connexion de transport particulière unique et elles ne sont pas disponibles à partir du contenu du message lui-même. La sécurité des messages sécurise le message indépendamment du transport utilisé pour transmettre le message et le contexte de sécurité est directement incorporé à l'intérieur du message.  
  
-   Prise en charge d'un large jeu d'informations d'identification et de revendications. La sécurité des messages se base sur la spécification WS-Security, qui fournit un cadre extensible capable de transmettre tout type de revendication à l'intérieur du message SOAP. Contrairement à la sécurité du transport, le jeu de mécanismes d'authentification, ou les revendications, que vous pouvez utiliser ne sont pas limités par les fonctions de transport. La sécurité des messages [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclut plusieurs types d'authentifications et de transmissions de revendications et peut être étendue pour prendre en charge des types supplémentaires selon vos besoins. Pour ces raisons, par exemple, un scénario d'informations d'identification fédérées n'est pas possible sans la sécurité des messages. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les scénarios de fédération WCF prend en charge, consultez [fédération et les jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="how-message-and-transport-security-compare"></a>Comparaison de la sécurité des messages et du transport  
  
### <a name="pros-and-cons-of-transport-level-security"></a>Avantages et inconvénients de la sécurité au niveau du transport  
 La sécurité du transport présente les avantages suivants :  
  
-   Ne requiert pas que les parties qui communiquent comprennent des concepts de sécurité au niveau du XML. Par exemple, cet avantage peut améliorer l'interopérabilité lorsque HTTPS est utilisé pour sécuriser la communication.  
  
-   Performance globale améliorée.  
  
-   Les accélérateurs de matériel sont disponibles.  
  
-   La diffusion en continu est possible.  
  
 La sécurité du transport présente les inconvénients suivants :  
  
-   Saut à saut uniquement.  
  
-   Jeu d'informations d'identification limité et non extensible.  
  
-   Dépendance vis-à-vis du transport.  
  
### <a name="disadvantages-of-message-level-security"></a>Inconvénients de la sécurité au niveau du message  
 La sécurité des messages présente les inconvénients suivants :  
  
-   Performances  
  
-   Impossible d'utiliser la diffusion en continu de messages.  
  
-   Requiert l'implémentation de mécanismes de sécurité au niveau du XML et la prise en charge de la spécification WS-Security. L'interopérabilité peut en être affectée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des Services et Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Sécurité de transport](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Comment : utilise la sécurité de Transport et les informations d’identification de Message](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft Patterns and Practices, chapitre 3 : sécurité de couche de Transport de mise en œuvre et de Message](http://go.microsoft.com/fwlink/?LinkId=88897)
