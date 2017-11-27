---
title: Autorisations web et socket
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 102d7d92384d77b5fbb56cd8c3eb859ec64bcca0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="web-and-socket-permissions"></a>Autorisations web et socket
La sécurité Internet pour les applications utilisant l’espace de noms <xref:System.Net> est apportée par les classes <xref:System.Net.WebPermission> et <xref:System.Net.SocketPermission>. La classe **WebPermission** détermine si une application est autorisée à demander des données à partir d’un URI ou d’utiliser un URI sur Internet. La classe **SocketPermission** détermine si une application est autorisée à utiliser un <xref:System.Net.Sockets.Socket> pour accepter des données sur un port local ou pour communiquer avec des appareils distants utilisant un protocole de transport à une autre adresse, en fonction de l’hôte, du numéro de port et du protocole de transport du socket.  
  
 La classe d’autorisation à utiliser dépend du type de votre application. Les applications qui utilisent <xref:System.Net.WebRequest> et ses descendants doivent utiliser la classe **WebPermission** pour gérer les autorisations. Les applications qui utilisent un accès de niveau socket doivent utiliser la classe **SocketPermission** pour gérer les autorisations.  
  
 **WebPermission** et **SocketPermission** définissent deux autorisations : Accept et Connect. Accept autorise l’application à répondre à une connexion entrante à partir d’une autre partie. Connect l’autorise à démarrer une connexion à une autre partie.  
  
 Pour les instances **SocketPermission**, Accept signifie qu’une application peut accepter des connexions entrantes sur une adresse de transport locale et Connect signifie qu’une application peut se connecter à une adresse de transport distante (ou locale).  
  
 Pour les instances **WebPermission**, Accept signifie qu’une application peut exporter l’URI contrôlé par **WebPermission** sur Internet et Connect signifie qu’une application peut accéder à cet URI (distant ou local).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité](../../../docs/standard/security/index.md)  
 [Sécurité dans la programmation réseau](../../../docs/framework/network-programming/security-in-network-programming.md)
