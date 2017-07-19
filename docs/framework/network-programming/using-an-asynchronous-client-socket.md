---
title: "Utilisation d’un socket client asynchrone | Microsoft Docs"
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
  - "sockets clients asynchrones"
  - "Socket (classe), sockets clients asynchrones"
  - "demande de données sur Internet, sockets"
  - "sockets, sockets clients asynchrones"
  - "réception de données, sockets"
  - "protocoles, sockets"
  - "Internet, sockets"
  - "sockets clients"
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# Utilisation d’un socket client asynchrone
Un socket client asynchrone ne interrompt pas l'application en attendant des opérations de réseau soit terminée.  À la place, il utilise le modèle de programmation asynchrone standard du .NET Framework pour traiter la connexion réseau sur un thread pendant que l'application continue à s'exécuter sur le thread d'origine.  Sockets asynchrones sont appropriés pour les applications qui utilisent intensive réseau ou qui ne peuvent pas attendre des opérations de réseau se termine avant de continuer.  
  
 La classe d' <xref:System.Net.Sockets.Socket> suit le modèle d'affectation de noms .NET Framework pour les méthodes asynchrones ; par exemple, la méthode synchrone d' <xref:System.Net.Sockets.Socket.Receive%2A> correspond à <xref:System.Net.Sockets.Socket.BeginReceive%2A> et aux méthodes asynchrones d' <xref:System.Net.Sockets.Socket.EndReceive%2A> .  
  
 Les opérations asynchrones nécessitent une méthode de rappel pour retourner le résultat de l'exécution.  Si votre application n'a pas besoin de connaître le résultat, aucune méthode de rappel n'est requise.  L'exemple de code illustre l'utilisation de cette section en utilisant une méthode pour se connecter à un appareil réseau et une méthode de rappel pour terminer la connexion, une méthode aux données d'émission de début et une méthode de rappel pour terminer l'envoyer, et une méthode pour commencer à accepter des données et une méthode de rappel pour terminer la réception de données.  
  
 Threads asynchrones d'utilisation de sockets du pool de threads système pour traiter les connexions réseau.  Un thread est chargé d'initialiser l'envoi ou de la réception de données ; autres threads complète la connexion à l'appareil réseau et envoie et reçoit les données.  Dans les exemples suivants, les instances de la classe d' <xref:System.Threading.ManualResetEvent?displayProperty=fullName> sont utilisées pour interrompre l'exécution du thread principal et pour signaler lorsque l'opération peut continuer.  
  
 Dans l'exemple suivant, pour connecter un socket asynchrone à un appareil réseau, la méthode d' `Connect`initialise **Socket** puis appelle la méthode de [BeginConnect](frlrfsystemnetsocketssocketclassconnecttopic) , en passant un point de terminaison distant qui représente le périphérique réseau, la méthode de rappel connect, et un objet d'état \( **Socket**client\), qui est utilisé pour passer des informations d'état entre les appels asynchrones.  Il implémente la méthode d' `Connect` pour connecter **Socket** spécifié au point de terminaison spécifié.  Il suppose **ManualResetEvent** global nommé `connectDone`.  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,   
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 La méthode de rappel `ConnectCallback` connect implémente le délégué d' <xref:System.AsyncCallback> .  Il se connecte au périphérique distant lorsque le périphérique distant est disponible puis signale le thread d'application que la connexion est terminée en définissant **ManualResetEvent**`connectDone`.  Le code suivant implémente la méthode d' `ConnectCallback` .  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 La méthode `Send` d'exemple encode les données de chaîne spécifiées dans le format ASCII et les envoie de façon asynchrone à l'appareil réseau socket représenté par le spécifié.  L'exemple suivant implémente la méthode d' `Send` .  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 La méthode de rappel `SendCallback` d'envoyer implémente le délégué d' <xref:System.AsyncCallback> .  Elle envoie les données lorsque le périphérique réseau est prêt à recevoir.  L'exemple suivant illustre l'implémentation de la méthode d' `SendCallback` .  Il suppose **ManualResetEvent** global nommé `sendDone`.  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Lire les données d'un socket client requiert un objet d'état qui passe des valeurs entre les appels asynchrones.  La classe suivante est un objet état d'exemple pour recevoir les données d'un socket client.  Elle contient un champ du socket client, une mémoire tampon pour les données reçues, et <xref:System.Text.StringBuilder> pour contenir les données entrantes chaînes.  Définir ces champs dans l'objet état permet leurs valeurs à conserver dans plusieurs appels pour lire les données du socket client.  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing   
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte   
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 La méthode d' `Receive` d'exemple est installé l'objet d'état puis appelle la méthode de **BeginReceive** pour lire les données du socket client de façon asynchrone.  L'exemple suivant implémente la méthode d' `Receive` .  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 La méthode de rappel `ReceiveCallback` de recevoir implémente le délégué d' **AsyncCallback** .  Elle reçoit les données du périphérique réseau et génère une chaîne de message.  Il lit un ou plusieurs octets de données du réseau dans la mémoire tampon de données puis appelle la méthode de **BeginReceive** de nouveau jusqu'à ce que les données envoyées par le client soient terminées.  Une fois que toutes les données sont lues du client, `ReceiveCallback` signale le thread d'application que les données sont terminées en définissant **ManualResetEvent** `sendDone`.  
  
 L'exemple de code suivant implémente la méthode d' `ReceiveCallback`.  Il suppose une chaîne globale nommée `response` qui juge la chaîne reçue et **ManualResetEvent** global nommés `receiveDone`.  Le serveur doit arrêter le socket client correctement pour terminer la session de réseau.  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket   
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket   
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## Voir aussi  
 [Utilisation d’un socket client synchrone](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)   
 [Écoute avec des sockets](../../../docs/framework/network-programming/listening-with-sockets.md)   
 [Exemple de socket client asynchrone](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)