---
title: "Liaison de sécurité de message"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f0c8b125d3fc313dca4140b871ccea8165329fda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-binding"></a>Liaison de sécurité de message
Cette section contient des exemples qui illustrent la liaison de sécurité des messages dans les services Windows [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Sécurité de message anonyme](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 Cet exemple illustre comment implémenter une application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui utilise la sécurité au niveau du message sans authentifier le client mais nécessite l'authentification du serveur à l'aide du certificat X.509 afférent.  
  
 [Certificat de sécurité de message](../../../../docs/framework/wcf/samples/message-security-certificate.md)  
 Cet exemple montre comment implémenter une application qui utilise WS-Security avec l'authentification de certificat X.509 v3 pour le client et requiert l'authentification de serveur à l'aide du certificat X.509 v3 du serveur.  
  
 [Nom d’utilisateur de sécurité de message](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 Cet exemple montre comment implémenter une application qui utilise WS-Security et l'authentification de nom d'utilisateur pour le client et qui nécessite l'authentification du serveur à l'aide de son certificat X.509v3.  
  
 [Sécurité de message Windows](../../../../docs/framework/wcf/samples/message-security-windows.md)  
 Cet exemple illustre comment configurer une liaison <xref:System.ServiceModel.WSHttpBinding> pour permettre l'utilisation de la sécurité de niveau message avec authentification Windows.
