---
title: "Utilisation d’un socket serveur asynchrone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5c696e04b940923d53eb79c055330a91734e1a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="8fed3-102">Utilisation d’un socket serveur asynchrone</span><span class="sxs-lookup"><span data-stu-id="8fed3-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="8fed3-103">Les sockets serveur asynchrones utilisent le modèle de programmation asynchrone de .NET Framework pour traiter les demandes de service réseau.</span><span class="sxs-lookup"><span data-stu-id="8fed3-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="8fed3-104">La classe <xref:System.Net.Sockets.Socket> respecte la convention de nommage standard de .NET Framework pour les méthodes asynchrones. Par exemple, la méthode synchrone <xref:System.Net.Sockets.Socket.Accept%2A> correspond aux méthodes asynchrones <xref:System.Net.Sockets.Socket.BeginAccept%2A> et <xref:System.Net.Sockets.Socket.EndAccept%2A>.</span><span class="sxs-lookup"><span data-stu-id="8fed3-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="8fed3-105">Un socket serveur asynchrone nécessite une méthode pour commencer à accepter les demandes de connexion du réseau, une méthode de rappel pour gérer les demandes de connexion et commencer à recevoir des données du réseau, et une méthode de rappel pour terminer la réception des données.</span><span class="sxs-lookup"><span data-stu-id="8fed3-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="8fed3-106">Toutes ces méthodes sont décrites plus loin dans cette section.</span><span class="sxs-lookup"><span data-stu-id="8fed3-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="8fed3-107">Dans l’exemple suivant, pour commencer à accepter les demandes de connexion du réseau, la méthode `StartListening` initialise le **Socket**, puis elle utilise la méthode **BeginAccept** pour commencer à accepter les nouvelles connexions.</span><span class="sxs-lookup"><span data-stu-id="8fed3-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="8fed3-108">La méthode de rappel d’acceptation est appelée quand une nouvelle demande de connexion est reçue sur le socket.</span><span class="sxs-lookup"><span data-stu-id="8fed3-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="8fed3-109">Elle est chargée d’obtenir l’instance **Socket** qui va gérer la connexion et de passer ce **Socket** au thread qui va traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="8fed3-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="8fed3-110">La méthode de rappel d’acceptation implémente le délégué <xref:System.AsyncCallback>. Elle retourne une valeur void et accepte un seul paramètre de type <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="8fed3-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="8fed3-111">L’exemple suivant illustre une méthode de rappel d’acceptation.</span><span class="sxs-lookup"><span data-stu-id="8fed3-111">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="8fed3-112">La méthode **BeginAccept** accepte deux paramètres, un délégué **AsyncCallback** qui pointe vers la méthode de rappel d’acceptation et un objet qui sert à passer les informations d’état à la méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="8fed3-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="8fed3-113">Dans l’exemple suivant, l’écoute **Socket** est passée à la méthode de rappel via le paramètre d’*état*.</span><span class="sxs-lookup"><span data-stu-id="8fed3-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="8fed3-114">Cet exemple crée un délégué **AsyncCallback** et démarre l’acceptation des connexions à partir du réseau.</span><span class="sxs-lookup"><span data-stu-id="8fed3-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
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
  
 <span data-ttu-id="8fed3-115">Les sockets asynchrones utilisent des threads du pool de threads système pour traiter les connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="8fed3-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="8fed3-116">Un thread est chargé d’accepter les connexions, un autre thread de la gestion de chaque connexion entrante et un autre thread de la réception des données provenant de la connexion.</span><span class="sxs-lookup"><span data-stu-id="8fed3-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="8fed3-117">Il peut s’agir du même thread, en fonction du thread qui a été assigné par le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="8fed3-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="8fed3-118">Dans l’exemple suivant, la classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> interrompt l’exécution du thread principal et signale à ce thread la reprise possible de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8fed3-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="8fed3-119">L’exemple suivant montre une méthode asynchrone qui crée un socket TCP/IP asynchrone sur l’ordinateur local et commence à accepter des connexions.</span><span class="sxs-lookup"><span data-stu-id="8fed3-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="8fed3-120">Il suppose qu’il existe un **ManualResetEvent** global nommé `allDone`, que la méthode est membre d’une classe nommée `SocketListener` et qu’une méthode de rappel nommée `acceptCallback` est définie.</span><span class="sxs-lookup"><span data-stu-id="8fed3-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `acceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="8fed3-121">La méthode de rappel d’acceptation (`acceptCallback` dans l’exemple précédent) est chargée de signaler au thread d’application principal la reprise possible de l’exécution, d’établir la connexion avec le client et de démarrer la lecture asynchrone des données du client.</span><span class="sxs-lookup"><span data-stu-id="8fed3-121">The accept callback method (`acceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="8fed3-122">L’exemple suivant montre la première partie d’une implémentation de la méthode `acceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-122">The following example is the first part of an implementation of the `acceptCallback` method.</span></span> <span data-ttu-id="8fed3-123">Cette section de la méthode indique au thread d’application principal qu’il peut reprendre l’exécution et établir la connexion au client.</span><span class="sxs-lookup"><span data-stu-id="8fed3-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="8fed3-124">L’exemple suppose l’utilisation d’un **ManualResetEvent** global nommé `allDone`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="8fed3-125">La lecture des données reçues d’un socket client nécessite l’utilisation d’un objet d’état qui passe les valeurs entre les appels asynchrones.</span><span class="sxs-lookup"><span data-stu-id="8fed3-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="8fed3-126">L’exemple suivant implémente un objet d’état pour la réception d’une chaîne à partir du client distant.</span><span class="sxs-lookup"><span data-stu-id="8fed3-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="8fed3-127">Il contient des champs pour le socket client, une mémoire tampon pour recevoir les données et un <xref:System.Text.StringBuilder> pour la création de la chaîne de données envoyée par le client.</span><span class="sxs-lookup"><span data-stu-id="8fed3-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="8fed3-128">Le fait que ces champs soient placés dans l’objet d’état permet à leurs valeurs d’être conservées entre les appels pour lire les données reçues du socket client.</span><span class="sxs-lookup"><span data-stu-id="8fed3-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="8fed3-129">La section de la méthode `acceptCallback` qui démarre la réception des données à partir du socket client initialise d’abord une instance de la classe `StateObject`, puis appelle la méthode <xref:System.Net.Sockets.Socket.BeginReceive%2A> pour démarrer la lecture asynchrone des données reçues du socket client.</span><span class="sxs-lookup"><span data-stu-id="8fed3-129">The section of the `acceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="8fed3-130">L’exemple suivant montre la méthode `acceptCallback` complète.</span><span class="sxs-lookup"><span data-stu-id="8fed3-130">The following example shows the complete `acceptCallback` method.</span></span> <span data-ttu-id="8fed3-131">Il suppose qu’il existe un **ManualResetEvent** global nommé `allDone,`, que la classe `StateObject` est définie et que la méthode `readCallback` est définie dans une classe nommée `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `readCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="8fed3-132">La dernière méthode à implémenter pour le socket serveur asynchrone est la méthode de rappel de lecture qui retourne les données envoyées par le client.</span><span class="sxs-lookup"><span data-stu-id="8fed3-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="8fed3-133">Comme la méthode de rappel d’acceptation, la méthode de rappel de lecture est un délégué **AsyncCallback**.</span><span class="sxs-lookup"><span data-stu-id="8fed3-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="8fed3-134">Cette méthode lit un ou plusieurs octets de données provenant du socket client, les stocke dans la mémoire tampon de données, puis appelle de nouveau la méthode **BeginReceive** jusqu’à la fin de la réception des données envoyées par le client.</span><span class="sxs-lookup"><span data-stu-id="8fed3-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="8fed3-135">Une fois que l’intégralité du message du client a été lue, la chaîne est affichée sur la console et le socket serveur qui gère la connexion au client est fermé.</span><span class="sxs-lookup"><span data-stu-id="8fed3-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="8fed3-136">L’exemple suivant implémente la méthode `readCallback`.</span><span class="sxs-lookup"><span data-stu-id="8fed3-136">The following sample implements the `readCallback` method.</span></span> <span data-ttu-id="8fed3-137">Il suppose que la classe `StateObject` est définie.</span><span class="sxs-lookup"><span data-stu-id="8fed3-137">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8fed3-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fed3-138">See Also</span></span>  
 [<span data-ttu-id="8fed3-139">À l’aide d’un Socket serveur synchrone</span><span class="sxs-lookup"><span data-stu-id="8fed3-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="8fed3-140">Exemple de socket serveur asynchrone</span><span class="sxs-lookup"><span data-stu-id="8fed3-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [<span data-ttu-id="8fed3-141">Thread</span><span class="sxs-lookup"><span data-stu-id="8fed3-141">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="8fed3-142">Écoute avec des sockets</span><span class="sxs-lookup"><span data-stu-id="8fed3-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
