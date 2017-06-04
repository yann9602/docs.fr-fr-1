---
title: "Utilisation de sockets clients | Microsoft Docs"
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
  - "requêtes de données, sockets"
  - "demande de données en provenance d’Internet, sockets"
  - "réception de données, sockets"
  - "Socket (classe), sockets clients"
  - "protocoles, sockets"
  - "Internet, sockets"
  - "sockets, sockets clients"
  - "sockets clients"
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Utilisation de sockets clients
Avant de pouvoir initialiser une conversation via <xref:System.Net.Sockets.Socket>, vous devez créer un canal de données entre votre application et le périphérique distant.  Bien que d'autres familles et protocoles d'adresse réseau existent, les de cet exemple montre comment créer une connexion TCP\/IP à un service distant.  
  
 TCP\/IP utilise une adresse réseau et un numéro de port de service pour identifier un service.  l'adresse réseau identifie un appareil spécifique sur le réseau ; le numéro de port identifie le service spécifique à l'appareil pour se connecter à.  La combinaison de port d'adresse réseau et de service est appelée un point de terminaison, qui est représenté dans le.NET Framework par la classe d' <xref:System.Net.EndPoint> .  Un descendant de **point de terminaison** est défini pour chaque famille d'adresses prise en charge ; pour la famille d'adresse IP, la classe est <xref:System.Net.IPEndPoint>.  
  
 La classe d' <xref:System.Net.Dns> fournit des services de noms de domaines aux applications qui utilisent des services Internet de TCP\/IP.  La méthode d' <xref:System.Net.Dns.Resolve%2A> interroge un serveur DNS pour mapper un nom de champ convivial \(tel que « host.contoso.com »\) à une adresse Internet numérique \(par exemple 192.168.1.1\).  **Resolve** retourne [IPHostEnty](frlrfsystemnetiphostentryclasstopic) qui contient une liste d'adresses et de alias pour le nom demandé.  Dans la plupart des cas, vous pouvez utiliser la première adresse retournée dans le tableau d' <xref:System.Net.IPHostEntry.AddressList%2A> .  Le code suivant obtient <xref:System.Net.IPAddress> contenant l'adresse IP du serveur host.contoso.com.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Assigned Numbers Authority \(Iana\) définit les numéros de port pour les services communs \(pour plus d'informations, consultez www.iana.org\/assignments\/port\-numbers\).  D'autres services peuvent avoir enregistré les numéros de port dans la plage 1.024 à 65.535.  Le code suivant combine l'adresse IP pour host.contoso.com avec un numéro de port pour créer un point de terminaison distant pour une connexion.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Après avoir déterminé l'adresse du périphérique distant et avoir choisi un port à utiliser pour la connexion, l'application peut tenter d'établir une connexion avec le périphérique distant.  L'exemple suivant utilise **IPEndPoint** existant pour se connecter à un périphérique distant et intercepte toutes les exceptions levées.  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## Voir aussi  
 [Utilisation d’un socket client synchrone](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)   
 [Utilisation d’un socket client asynchrone](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [Comment : créer un socket](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [Sockets](../../../docs/framework/network-programming/sockets.md)