---
title: "Utilisation d’un socket serveur asynchrone | Microsoft Docs"
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
  - "Socket (classe), sockets serveur asynchrones"
  - "requêtes de données, sockets"
  - "sockets, sockets serveur asynchrones"
  - "demande de données en provenance d’Internet, sockets"
  - "sockets serveur"
  - "réception de données, sockets"
  - "sockets serveur asynchrones"
  - "protocoles, sockets"
  - "Internet, sockets"
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# Utilisation d’un socket serveur asynchrone
Sockets asynchrones du serveur utilisent le modèle de programmation asynchrone .NET Framework pour traiter les requêtes de service réseau.  La classe d' <xref:System.Net.Sockets.Socket> suit le modèle d'affectation de noms asynchrone standard du .NET Framework ; par exemple, la méthode synchrone d' <xref:System.Net.Sockets.Socket.Accept%2A> correspond à <xref:System.Net.Sockets.Socket.BeginAccept%2A> et aux méthodes asynchrones d' <xref:System.Net.Sockets.Socket.EndAccept%2A> .  
  
 Un socket asynchrone de serveur requiert une méthode de démarrer recevant des demandes de connexion réseau, d'une méthode de rappel de gérer les demandes de connexion et de démarrer réception de données du réseau, et une méthode de rappel pour terminer recevoir les données.  Toutes ces méthodes sont décrites plus loin dans cette section.  
  
 Dans l'exemple suivant, pour démarrer la réception des demandes de connexion réseau, la méthode `StartListening` initialise **Socket** puis utilise la méthode de **BeginAccept** pour commencer à recevoir de nouvelles connexions.  La méthode de rappel pour recevoir est appelée lorsqu'une nouvelle demande de connexion est reçue du socket.  Il est chargé d'obtenir l'instance de **Socket** qui gérera la connexion et réinitialiser ce **Socket** désactiver le thread qui gérera la demande.  La méthode de rappel pour recevoir implémente le délégué d' <xref:System.AsyncCallback> ; elle retourne un type void et accepte un seul paramètre de type <xref:System.IAsyncResult>.  L'exemple suivant est le shell d'une méthode de rappel pour recevoir.  
  
```vb  
Sub acceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'acceptCallback  
```  
  
```csharp  
void acceptCallback( IAsyncResult ar) {  
    // Add the callback code here.  
}  
```  
  
 La méthode de **BeginAccept** accepte deux paramètres, un délégué d' **AsyncCallback** qui indique la méthode de rappel pour recevoir et un objet utilisé pour passer des informations d'état à la méthode de rappel.  Dans l'exemple suivant, **Socket** écoutant est passé à la méthode de rappel par le paramètre d' *état* .  Cet exemple crée un délégué d' **AsyncCallback** et commence à accepter les connexions réseau.  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.acceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(  
    new AsyncCallback(SocketListener.acceptCallback),   
    listener);  
```  
  
 L'utilisation asynchrone de sockets threads du pool de threads système pour traiter les connexions entrantes.  Un thread est chargé de recevoir des connexions, un autre thread est utilisé pour gérer chaque connexion entrante, et un autre thread est chargé de recevoir des données de la connexion.  Ils peuvent être le même thread, en fonction de le thread est assigné par le pool de threads.  Dans l'exemple suivant, la classe d' <xref:System.Threading.ManualResetEvent?displayProperty=fullName> interrompt l'exécution du thread et des signaux principaux lorsque l'opération peut continuer.  
  
 L'exemple suivant illustre une méthode asynchrone qui crée un socket TCP\/IP asynchrone de sur l'ordinateur local et commence acceptation de connexions.  Il suppose qu'il existe **ManualResetEvent** global nommé `allDone`, que la méthode est membre d'une classe nommée `SocketListener`, et qu'une méthode de rappel nommée `acceptCallback` est définie.  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine("Local address and port : {0}", localEP.ToString())  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.acceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
  
```  
  
```csharp  
public void StartListening() {  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0],11000);  
  
    Console.WriteLine("Local address and port : {0}",localEP.ToString());  
  
    Socket listener = new Socket( localEP.Address.AddressFamily,  
        SocketType.Stream, ProtocolType.Tcp );  
  
    try {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true) {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(  
                new AsyncCallback(SocketListener.acceptCallback),   
                listener );  
  
            allDone.WaitOne();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine( "Closing the listener...");  
}  
```  
  
 La méthode de rappel pour recevoir \(`acceptCallback` dans l'exemple précédent\) est chargé de signaler le thread d'application principal pour poursuivre le traitement, d'établir la connexion avec le client, et démarrer l'asynchrone lire des données à partir de le client.  L'exemple suivant est la première partie d'une implémentation de la méthode d' `acceptCallback` .  Cette section de la méthode signale le thread d'application principal pour poursuivre le traitement et établit la connexion au client.  Il suppose **ManualResetEvent** global nommé `allDone`.  
  
```vb  
Public Sub acceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'acceptCallback  
```  
  
```csharp  
public void acceptCallback(IAsyncResult ar) {  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 Lire les données d'un socket client requiert un objet d'état qui passe des valeurs entre les appels asynchrones.  l'exemple suivant implémente un objet d'état pour recevoir une chaîne du client distant.  Il contient les champs du socket client, une mémoire tampon de données pour recevoir des données, et <xref:System.Text.StringBuilder> pour créer des chaînes données envoyées par le client.  Définir ces champs dans l'objet état permet leurs valeurs à conserver dans plusieurs appels pour lire les données du socket client.  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 La section de la méthode d' `acceptCallback` qui commence à recevoir les données du socket client d'abord initialise une instance de la classe d' `StateObject` puis appelle la méthode d' <xref:System.Net.Sockets.Socket.BeginReceive%2A> pour commencer à lire les données du socket client de façon asynchrone.  
  
 L'exemple suivant affiche la méthode complète d' `acceptCallback` .  Il suppose qu'il existe **ManualResetEvent** global nommé `allDone,` que la classe d' `StateObject` est définie, et que la méthode d' `readCallback` est définie dans une classe nommée `SocketListener`.  
  
```vb  
Public Shared Sub acceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.readCallback, state)  
End Sub 'acceptCallback  
  
```  
  
```csharp  
public static void acceptCallback(IAsyncResult ar) {  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.readCallback), state);  
}  
```  
  
 La méthode final qui doit être implémentée pour le serveur asynchrone de socket est la méthode de rappel lue qui retourne les données envoyées par le client.  Comme la méthode de rappel pour recevoir, la méthode de rappel lue est un délégué d' **AsyncCallback** .  Cette méthode lit un ou plusieurs octets du socket client dans la mémoire tampon de données puis appelle la méthode de **BeginReceive** de nouveau jusqu'à ce que les données envoyées par le client soient terminées.  Une fois que le message entier a été lu du client, la chaîne est affichée sur la console et le socket de serveur gérant la connexion au client est fermé.  
  
 L'exemple suivant implémente la méthode d' `readCallback` .  Il suppose que la classe d' `StateObject` est définie.  
  
```vb  
Public Shared Sub readCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf readCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine("Read {0} bytes from socket." + _  
                ControlChars.Cr + " Data : {1}", content.Length, content)  
        End If  
    End If  
End Sub 'readCallback  
  
```  
  
```csharp  
public static void readCallback(IAsyncResult ar) {  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0) {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer,0,StateObject.BufferSize, 0,  
            new AsyncCallback(readCallback), state);  
    } else {  
        if (state.sb.Length > 1) {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine("Read {0} bytes from socket.\n Data : {1}",  
               content.Length, content);  
        }  
        handler.Close();  
    }  
}  
```  
  
## Voir aussi  
 [Utilisation d’un socket serveur synchrone](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)   
 [Exemple de sockets serveur asynchrones](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)   
 [Threading](../../../docs/standard/threading/index.md)   
 [Écoute avec des sockets](../../../docs/framework/network-programming/listening-with-sockets.md)