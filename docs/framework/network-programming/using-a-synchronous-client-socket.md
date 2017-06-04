---
title: "Utilisation d’un socket client synchrone | Microsoft Docs"
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
  - "sockets clients synchrones"
  - "Socket (classe), sockets clients synchrones"
  - "réception de données, sockets"
  - "sockets, sockets clients synchrones"
  - "protocoles, sockets"
  - "Internet, sockets"
  - "sockets clients"
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# Utilisation d’un socket client synchrone
Un socket client synchrone interrompt l'application pendant l'exécution de réseau se termine.  Sockets synchrones ne sont pas appropriés pour les applications qui utilisent intensive réseau pour leur exécution, mais ils peuvent permettre l'accès simple aux services réseau pour d'autres applications.  
  
 Pour envoyer des données, passez un tableau d'octets en une des méthodes de envoyer\- données de la classe d' <xref:System.Net.Sockets.Socket> \(<xref:System.Net.Sockets.Socket.Send%2A> et <xref:System.Net.Sockets.Socket.SendTo%2A>\).  L'exemple suivant encode une chaîne dans une mémoire tampon de tableau d'octets à l'aide de la propriété d' <xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName> puis transmet la mémoire tampon à l'appareil réseau à l'aide de la méthode de **Envoyer** .  La méthode de **Envoyer** retourne le nombre d'octets envoyés à l'appareil réseau.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 La méthode de **Envoyer** supprime les octets de la mémoire tampon et les met en file d'attente avec l'interface réseau à envoyer au périphérique réseau.  L'interface réseau ne peut pas envoyer des données immédiatement, mais elle envoie par la suite, tant que la connexion est fermée normalement avec la méthode d' <xref:System.Net.Sockets.Socket.Shutdown%2A> .  
  
 Pour recevoir les données d'un périphérique réseau, passez une mémoire tampon avec une des méthodes de recevoir\- données de la classe de **Socket** \(<xref:System.Net.Sockets.Socket.Receive%2A> et <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>\).  Sockets synchrones interrompront l'application jusqu'à ce que les octets sont acceptés réseau ou jusqu'à ce que le socket est fermé.  L'exemple suivant accepte des données du réseau puis l'affiche dans la console.  Cet exemple suppose que les données provenant du réseau sont ASCII\- texte encodé.  La méthode de **Recevoir** retourne le nombre d'octets envoyés du réseau.  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 Lorsque le socket n'est plus nécessaire, vous devez le libérer en appelant la méthode d' <xref:System.Net.Sockets.Socket.Shutdown%2A> puis en appelant la méthode de **Fermer** .  L'exemple suivant récupère **Socket**.  L'énumération d' <xref:System.Net.Sockets.SocketShutdown> définit des constantes qui indiquent si le socket doit être fermé pour envoyer, pour accepter, ou pour les deux.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## Voir aussi  
 [Utilisation d’un socket client asynchrone](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [Écoute avec des sockets](../../../docs/framework/network-programming/listening-with-sockets.md)   
 [Exemple de socket client synchrone](../../../docs/framework/network-programming/synchronous-client-socket-example.md)