---
title: "TCP/UDP | Microsoft Docs"
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
  - "protocoles, TCP/UDP"
  - "ressources réseau, TCP/UDP"
  - "envoyer des données, TCP/UDP"
  - "TCP/UDP"
  - "classe TcpClient, à propos de la classe TcpClient"
  - "protocoles d’application, TCP/UDP"
  - "recevoir des données, TCP/UDP"
  - "classe TcpListener, à propos de la classe TcpListener"
  - "classe Socket, à propos de la classe Socket"
  - "UDP"
  - "demandes de données, TCP/UDP"
  - "demander des données à partir d’Internet, TCP/UDP"
  - "Internet, TCP/UDP"
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# TCP/UDP
Les applications peuvent utiliser des services de protocole TCP \(TCP\) et de protocole UDP \(UDP\) avec <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, les classes et d' <xref:System.Net.Sockets.UdpClient> .  Ces classes de fournisseur reposent sur la classe d' <xref:System.Net.Sockets.Socket?displayProperty=fullName> et prennent charge des détails de transférer des données.  
  
 Les classes de fournisseur utilisent les méthodes synchrones de classe de **Socket** pour fournir l'accès simple et direct aux services réseau sans la charge des informations d'état de mise à jour ou de connaître les détails d'installer les sockets spécifiques au protocole.  Pour utiliser des méthodes asynchrones de **Socket** , vous pouvez utiliser les méthodes asynchrones fournies par la classe d' <xref:System.Net.Sockets.NetworkStream> .  Pour accéder aux fonctionnalités de **Socket** classe non exposées par les classes de fournisseur, vous devez utiliser la classe de **Socket** .  
  
 **TcpClient** et **TcpListener** représentent le réseau à l'aide de la classe de **NetworkStream** .  Vous utilisez la méthode d' <xref:System.Net.Sockets.TcpClient.GetStream%2A> pour retourner le flux de réseau, puis appelez les méthodes d' <xref:System.Net.Sockets.NetworkStream.Read%2A> et d' <xref:System.Net.Sockets.NetworkStream.Write%2A> du flux.  **NetworkStream** ne possède pas de socket sous\-jacentes des classes de fournisseur, le fermer n'affecte pas le socket.  
  
 La classe d' **UdpClient** utilise un tableau d'octets pour stocker le datagramme d'UDP.  Vous utilisez la méthode d' <xref:System.Net.Sockets.UdpClient.Send%2A> pour envoyer des données au réseau et la méthode d' <xref:System.Net.Sockets.UdpClient.Receive%2A> pour recevoir un datagramme entrant.  
  
## Voir aussi  
 [Utilisation des services TCP](../../../docs/framework/network-programming/using-tcp-services.md)   
 [Utilisation des services UDP](../../../docs/framework/network-programming/using-udp-services.md)   
 [Utilisation de flux sur le réseau](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [Utilisation d’un socket serveur asynchrone](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [Utilisation d’un socket client asynchrone](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)