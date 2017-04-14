---
title: "Sockets | Microsoft Docs"
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
  - "envoyer des données, sockets"
  - "requêtes de données, sockets"
  - "Windows Sockets"
  - "sockets, à propos des sockets"
  - "Socket (classe), à propos de la classe Socket"
  - "sockets"
  - "demander des données à partir d’Internet, sockets"
  - "réseau, sockets"
  - "recevoir des données, sockets"
  - "protocoles, sockets"
  - "Internet, sockets"
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# Sockets
L'espace de noms d' <xref:System.Net.Sockets> contient une implémentation managée de l'interface Windows Sockets.  Toutes les autres classes d'accès réseau dans l'espace de noms d' <xref:System.Net> reposent sur cette implémentation des sockets.  
  
 La classe.NET Framework <xref:System.Net.Sockets.Socket> est une version de code managé des services de socket fournis par l'API Winsock32.  Dans la plupart des cas, les méthodes de la classe de **Socket** marshalent simplement des données dans leurs équivalents Win32 natives et gérer toutes les vérifications de sécurité nécessaires.  
  
 La classe de **Socket** prend en charge deux modes de base, synchrone et asynchrone.  En mode synchrone, les appels aux fonctions qui effectuent des opérations de réseau \(telles qu' <xref:System.Net.Sockets.Socket.Send%2A> et <xref:System.Net.Sockets.Socket.Receive%2A>\) attendent jusqu'à ce que l'opération se termine avant de retourner le contrôle au programme appelant.  En mode asynchrone, ces appels retournent immédiatement.  
  
## Voir aussi  
 [Comment : créer un socket](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)   
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)