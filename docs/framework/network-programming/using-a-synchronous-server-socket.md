---
title: "Utilisation d’un socket serveur synchrone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c4ecba2d6c5026a3b2f7d65540fcf40dd71ba3d7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="using-a-synchronous-server-socket"></a>Utilisation d’un socket serveur synchrone
Les sockets serveur synchrones interrompent l’exécution de l’application jusqu’à la réception d’une demande de connexion sur le socket. Les sockets serveur synchrones ne sont pas appropriés pour les applications dont l’exécution nécessite une utilisation intensive du réseau, mais ils peuvent être utiles pour les applications réseau simples.  
  
 Après qu’un <xref:System.Net.Sockets.Socket> a été défini pour écouter un point de terminaison à l’aide des méthodes <xref:System.Net.Sockets.Socket.Bind%2A> et <xref:System.Net.Sockets.Socket.Listen%2A>, il est prêt à accepter les demandes de connexion entrantes à l’aide de la méthode <xref:System.Net.Sockets.Socket.Accept%2A>. L’exécution de l’application est interrompue jusqu’à la réception d’une demande de connexion après l’appel de la méthode **Accept**.  
  
 Après la réception d’une demande de connexion, **Accept** retourne une nouvelle instance **Socket** qui est associée au client qui se connecte. L’exemple suivant lit les données reçues du client, les affiche sur la console et les renvoie au client. Le **Socket** ne spécifie pas de protocole de messagerie. La chaîne « \<EOF> » marque donc la fin des données du message. L’exemple suppose qu’un **Socket** nommé `listener` a été initialisé et associé à un point de terminaison.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’un socket serveur asynchrone](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [Exemple de socket serveur asynchrone](../../../docs/framework/network-programming/synchronous-server-socket-example.md)   
 [Écoute avec des sockets](../../../docs/framework/network-programming/listening-with-sockets.md)

