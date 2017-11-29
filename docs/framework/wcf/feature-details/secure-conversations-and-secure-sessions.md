---
title: "Conversations sécurisées et sessions sécurisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 6647ef8124279e9fc0b3049beb5c87f887125dfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="secure-conversations-and-secure-sessions"></a>Conversations sécurisées et sessions sécurisées
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a la capacité d'établir des sessions sécurisées entre deux points de terminaison qui s'authentifient l'un l'autre et conviennent d'un chiffrement et d'un processus de signature numérique. Par exemple, le point de terminaison de service peut demander qu'un point de terminaison de client envoie un jeton de sécurité basé sur un certificat X.509 pour l'authentification. Une fois que le client est authentifié, le point de terminaison de service renvoie un jeton de contexte de sécurité (SCT) au client, utilisé ensuite pour sécuriser tous les messages suivants dans la session. L'établissement de cette session sécurisée permet d'améliorer l'ensemble des messages échangés entre les deux points de terminaison, parce que le SCT a une clé symétrique. Les clés asymétriques, sur lesquelles les certificats X.509 sont basés, requièrent beaucoup plus de puissance de calcul que les clés symétriques pour générer une signature numérique ou chiffrer un jeu de données.  
  
 La stratégie de démarrage (défini dans la section 6.2.7 de la [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standard) contient les assertions de sécurité de message utilisées pour sécuriser le canal et d’authentifier le client avant l’échange RST/SCT et RSTR/SCT. Certaines liaisons standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ont une propriété `Security.Message.EstablishSecurityContext` qui contrôle si la conversation sécurisée est utilisée. Lorsque vous utilisez des liaisons personnalisées le programme d’amorçage est indiqué par imbrication éléments de liaison de sécurité, que ce soit via [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) dans le fichier de configuration, ou en appelant <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> dans le code.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]sessions, consultez [à l’aide de Sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sessions, instanciation et accès concurrentiel](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Comment : créer un Service qui requiert des Sessions](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
