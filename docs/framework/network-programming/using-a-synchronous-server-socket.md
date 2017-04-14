---
title: "Utilisation d’un socket serveur synchrone | Microsoft Docs"
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
  - "sockets serveur synchrones"
  - "envoyer des données, sockets"
  - "demandes de données, sockets"
  - "demander des données à partir d’Internet, sockets"
  - "sockets serveur"
  - "recevoir des données, sockets"
  - "classe Socket, sockets serveur synchrones"
  - "protocoles, sockets"
  - "sockets, sockets serveur synchrones"
  - "Internet, sockets"
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Utilisation d’un socket serveur synchrone
Sockets synchrones de serveur interrompent l'exécution de l'application jusqu'à ce qu'une demande de connexion réception du socket.  Sockets synchrones de serveur ne sont pas appropriés pour les applications qui utilisent intensive réseau dans leur exécution, mais ils peuvent convenir pour les applications réseau simples.  
  
 Après <xref:System.Net.Sockets.Socket> est défini pour écouter sur le point de terminaison à l'aide de les méthodes d' <xref:System.Net.Sockets.Socket.Bind%2A> et d' <xref:System.Net.Sockets.Socket.Listen%2A> , il est prêt de recevoir des invites de connexion entrante à l'aide de la méthode d' <xref:System.Net.Sockets.Socket.Accept%2A> .  L'application est interrompue jusqu'à ce qu'une demande de connexion réception lorsque la méthode de **Accepter** est appelée.  
  
 Lorsqu'une demande de connexion est reçue, **Accepter** retourne une nouvelle instance de **Socket** associée au client se connecte.  L'exemple suivant lit les données du client, les affiche dans la console, et répercute les données au client.  **Socket** Ne spécifie aucun protocole de messagerie, les jetons « \<EOF\> » de chaîne des données du message.  Il suppose que **Socket** nommé `listener`a été initialisé et lié à un point de terminaison.  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## Voir aussi  
 [Utilisation d’un socket serveur asynchrone](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [Exemple de socket serveur synchrone](../../../docs/framework/network-programming/synchronous-server-socket-example.md)   
 [Écoute avec des sockets](../../../docs/framework/network-programming/listening-with-sockets.md)