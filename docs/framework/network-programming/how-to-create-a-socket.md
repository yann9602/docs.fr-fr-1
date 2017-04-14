---
title: "Comment&#160;: cr&#233;er un socket | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "protocoles d’application, sockets"
  - "Réseau"
  - "envoyer des données, sockets"
  - "demandes de données, sockets"
  - "demander des données à partir d’Internet, sockets"
  - "classe Socket, créer des sockets"
  - "Ressources réseau"
  - "recevoir des données, sockets"
  - "protocoles, sockets"
  - "Internet, sockets"
  - "sockets, créer"
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# Comment&#160;: cr&#233;er un socket
Avant de pouvoir utiliser un socket pour communiquer avec les appareils distants, le socket doit être initialisé avec les informations de fournisseur et d'adresse réseau.  Le constructeur pour la classe d' <xref:System.Net.Sockets.Socket> a les paramètres qui spécifient la famille d'adresses, le type de socket, et le type de fournisseur que le socket utilise pour rendre des connexions.  
  
## Exemple  
 L'exemple suivant crée un socket qui peut être utilisé pour communiquer sur un réseau de TCP\/IP\-based, tel qu'Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
  
```  
  
 Pour utiliser UDP plutôt que TCP, remplacez le type de fournisseur, comme dans l'exemple suivant :  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
  
```  
  
 L'énumération d' <xref:System.Net.Sockets.AddressFamily> spécifie les familles d'adresses standard utilisées par la classe de **Socket** pour résoudre les adresses réseau \(par exemple, le membre d' **AddressFamily.InterNetwork** spécifie la famille d'adresses de la version 4 IP\).  
  
 l'énumération d' <xref:System.Net.Sockets.SocketType> spécifie le type de socket \(par exemple, le membre de **SocketType.Stream** indique un socket standard pour envoyer et recevoir des données avec le contrôle de flux\).  
  
 L'énumération d' <xref:System.Net.Sockets.ProtocolType> spécifie le protocole réseau à utiliser lorsque qui communiquent sur **Socket** \(par exemple, **ProtocolType.Tcp** indique que le socket utilise TCP ; **ProtocolType.Udp** indique que le socket utilise UDP\).  
  
 Une fois que **Socket** créé, il peut initialiser une connexion à un point de terminaison distant ou recevoir des connexions des appareils distants.  
  
## Voir aussi  
 [Utilisation de sockets clients](../../../docs/framework/network-programming/using-client-sockets.md)   
 [Écoute avec des sockets](../../../docs/framework/network-programming/listening-with-sockets.md)