---
title: "&#201;coute avec des sockets | Microsoft Docs"
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
  - "envoi de données, sockets"
  - "sockets, écoute avec des sockets"
  - "demandes de données, sockets"
  - "demande de données en provenance d’Internet, sockets"
  - "réception de données, sockets"
  - "protocoles, sockets"
  - "écoute avec des sockets"
  - "Internet, sockets"
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &#201;coute avec des sockets
Sockets d'écouteur ou serveur ouvrez un port sur le réseau puis attendent un client pour se connecter à ce port.  Bien que d'autres familles et protocoles d'adresse réseau existent, les de cet exemple montre comment créer le service distant pour un réseau TCP\/IP.  
  
 L'adresse unique d'un service de TCP\/IP est définie en combinant l'adresse IP de l'hôte avec le numéro de port du service pour créer un point de terminaison pour le service.  La classe d' <xref:System.Net.Dns> fournit des méthodes qui retournent des informations sur les adresses réseau sont prises en charge par le périphérique de réseau local.  Lorsque le périphérique de réseau local a plusieurs adresse réseau, ou si plusieurs appareils en charge réseau de techniques locales, la classe de **DNS** retourne des informations sur les adresses réseau, et l'application doit choisir l'adresse appropriée pour le service.  Internet Assigned Numbers Authority \(Iana\) définit les numéros de port pour les services communs \(pour plus d'informations, consultez www.iana.org\/assignments\/port\-numbers\).  D'autres services peuvent avoir enregistré les numéros de port dans la plage 1.024 à 65.535.  
  
 L'exemple suivant crée <xref:System.Net.IPEndPoint> pour un serveur en combinant la première adresse IP retournée par **DNS** de l'ordinateur \- hôte avec un numéro de port sélectionnez les numéros de port stockés s'étendre.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 Après le point de terminaison local est déterminé, <xref:System.Net.Sockets.Socket> doit être associé à ce point de terminaison à l'aide de la méthode et le jeu d' <xref:System.Net.Sockets.Socket.Bind%2A> pour écouter sur le point de terminaison à l'aide de la méthode d' <xref:System.Net.Sockets.Socket.Listen%2A> .  **Lier** lève une exception si la combinaison d'adresse spécifique et de port est déjà en cours de utilisation.  L'exemple suivant montre comment associer **Socket** avec **IPEndPoint**.  
  
```vb  
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 La méthode de **Écouter** prend un paramètre unique qui spécifie le nombre de connexions en attente à **Socket** sont autorisées avant qu'une erreur occupée de serveur soit retournée au client se connecte.  Dans ce cas, jusqu'à 100 clients sont définis dans la file d'attente de connexion avant qu'une réponse occupée de serveur soit retournée au client nombre 101.  
  
## Voir aussi  
 [Utilisation d’un socket serveur synchrone](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)   
 [Utilisation d’un socket serveur asynchrone](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [Utilisation de sockets clients](../../../docs/framework/network-programming/using-client-sockets.md)   
 [Comment : créer un socket](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [Sockets](../../../docs/framework/network-programming/sockets.md)