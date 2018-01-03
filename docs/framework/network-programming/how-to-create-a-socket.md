---
title: "Comment : créer un socket"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 24ec39798f5f31cf20cc5c84714efaae6ccbed52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-socket"></a>Comment : créer un socket
Avant de pouvoir utiliser un socket pour communiquer avec des appareils distants, le socket doit être initialisé avec des informations de protocole et d’adresse réseau. Le constructeur de la classe <xref:System.Net.Sockets.Socket> a des paramètres qui spécifient la famille d’adresses, le type de socket et le type de protocole que le socket utilise pour établir des connexions.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un socket qui peut être utilisé pour communiquer sur un réseau TCP/IP comme Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Pour utiliser le protocole UDP plutôt que TCP, remplacez le type de protocole, comme dans l’exemple suivant :  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 L’énumération <xref:System.Net.Sockets.AddressFamily> spécifie les familles d’adresses standard utilisées par la classe **Socket** pour résoudre les adresses réseau (par exemple, le membre **AddressFamily.InterNetwork** spécifie la famille d’adresses IP version 4).  
  
 L’énumération <xref:System.Net.Sockets.SocketType> spécifie le type de socket (par exemple, le membre **SocketType.Stream** indique un socket standard pour envoyer et recevoir des données avec le contrôle de flux).  
  
 L’énumération <xref:System.Net.Sockets.ProtocolType> spécifie le protocole réseau à utiliser lors de communications sur le **socket** (par exemple, **ProtocolType.Tcp** indique que le socket utilise TCP ; **ProtocolType.Udp** indique que le socket utilise UDP).  
  
 Une fois qu’un **socket** est créé, il peut initier une connexion à un point de terminaison distant ou recevoir des connexions d’appareils distants.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de sockets clients](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Écoute avec des sockets](../../../docs/framework/network-programming/listening-with-sockets.md)
