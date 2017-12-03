---
title: 'Transport: WSE 3.0 TCP Interoperability'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50bd1492c4e2e8941a77f344c04414a763390e89
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="44cf8-102">Transport: WSE 3.0 TCP Interoperability</span><span class="sxs-lookup"><span data-stu-id="44cf8-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="44cf8-103">Cet exemple indique comment implémenter une session duplex TCP en tant que transport [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] personnalisé.</span><span class="sxs-lookup"><span data-stu-id="44cf8-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport.</span></span> <span data-ttu-id="44cf8-104">Il décrit également comment utiliser l'extensibilité de la couche du canal pour assurer l'interface sur le câble avec les systèmes déployés existants.</span><span class="sxs-lookup"><span data-stu-id="44cf8-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="44cf8-105">Les étapes suivantes indiquent comment générer ce transport [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] personnalisé :</span><span class="sxs-lookup"><span data-stu-id="44cf8-105">The following steps show how to build this custom [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport:</span></span>  
  
1.  <span data-ttu-id="44cf8-106">À partir d'un socket TCP, créez les implémentations serveur et client de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> qui utilisent le tramage DIME pour définir les limites de message.</span><span class="sxs-lookup"><span data-stu-id="44cf8-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2.  <span data-ttu-id="44cf8-107">Créez une fabrique de canaux qui se connecte à un service TCP WSE et envoie des messages tramés sur le client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="44cf8-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3.  <span data-ttu-id="44cf8-108">Créez un écouteur de canal pour accepter les connexions TCP entrantes et produire les canaux correspondants.</span><span class="sxs-lookup"><span data-stu-id="44cf8-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4.  <span data-ttu-id="44cf8-109">Assurez-vous que les exceptions spécifiques au réseau sont normalisées selon la classe dérivée appropriée de <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="44cf8-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5.  <span data-ttu-id="44cf8-110">Ajoutez un élément de liaison qui ajoute le transport personnalisé à une pile de canaux.</span><span class="sxs-lookup"><span data-stu-id="44cf8-110">Add a binding element that adds the custom transport to a channel stack.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="44cf8-111">[Ajout d’un élément de liaison].</span><span class="sxs-lookup"><span data-stu-id="44cf8-111"> [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="44cf8-112">Création de IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="44cf8-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="44cf8-113">La première étape de l'écriture du transport WSE 3.0 TCP Interoperability consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> sur <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="44cf8-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="44cf8-114">`WseTcpDuplexSessionChannel` dérive de <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="44cf8-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="44cf8-115">La logique d'envoi d'un message comporte deux parties principales : (1) encodage du message en octets, et (2) tramage et envoi des octets sur le câble.</span><span class="sxs-lookup"><span data-stu-id="44cf8-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="44cf8-116">En outre, un verrou est utilisé afin que les appels Send() conservent la garantie de l’ordre IDuplexSessionChannel et afin que les appels du socket sous-jacent soient correctement synchronisés.</span><span class="sxs-lookup"><span data-stu-id="44cf8-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="44cf8-117">`WseTcpDuplexSessionChannel` utilise <xref:System.ServiceModel.Channels.MessageEncoder> pour traduire <xref:System.ServiceModel.Channels.Message> vers et à partir de byte[].</span><span class="sxs-lookup"><span data-stu-id="44cf8-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="44cf8-118">Dans la mesure où il s'agit d'un transport, `WseTcpDuplexSessionChannel` est également chargé d'appliquer l'adresse distante avec laquelle le canal a été configuré.</span><span class="sxs-lookup"><span data-stu-id="44cf8-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="44cf8-119">`EncodeMessage` encapsule la logique de cette conversion.</span><span class="sxs-lookup"><span data-stu-id="44cf8-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="44cf8-120">Une fois que <xref:System.ServiceModel.Channels.Message> est encodé en octets, il doit être transmis sur le câble.</span><span class="sxs-lookup"><span data-stu-id="44cf8-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="44cf8-121">Pour cela, un système permettant de définir des limites de message est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="44cf8-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="44cf8-122">WSE 3.0 utilise une version de [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) comme protocole de tramage.</span><span class="sxs-lookup"><span data-stu-id="44cf8-122">WSE 3.0 uses a version of [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="44cf8-123">`WriteData` encapsule la logique de tramage afin d'encapsuler byte[] dans un ensemble d'enregistrements DIME.</span><span class="sxs-lookup"><span data-stu-id="44cf8-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="44cf8-124">La logique de réception des messages est très similaire.</span><span class="sxs-lookup"><span data-stu-id="44cf8-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="44cf8-125">La principale difficulté consiste à gérer le fait qu'une lecture de socket peut retourner un nombre d'octets inférieur à celui demandé.</span><span class="sxs-lookup"><span data-stu-id="44cf8-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="44cf8-126">Pour recevoir un message, `WseTcpDuplexSessionChannel` lit des octets du câble, décode le tramage DIME, puis utilise <xref:System.ServiceModel.Channels.MessageEncoder> pour transformer byte[] en <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="44cf8-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="44cf8-127">Le `WseTcpDuplexSessionChannel` de base suppose qu'il reçoit un socket connecté.</span><span class="sxs-lookup"><span data-stu-id="44cf8-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="44cf8-128">La classe de base gère l'arrêt du socket.</span><span class="sxs-lookup"><span data-stu-id="44cf8-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="44cf8-129">Trois valeurs correspondent à la fermeture du socket :</span><span class="sxs-lookup"><span data-stu-id="44cf8-129">There are three places that interface with socket closure:</span></span>  
  
-   <span data-ttu-id="44cf8-130">OnAbort : fermeture du socket de façon incorrecte (fermeture stricte).</span><span class="sxs-lookup"><span data-stu-id="44cf8-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
-   <span data-ttu-id="44cf8-131">On[Begin]Close : fermeture du socket de façon correcte (fermeture souple).</span><span class="sxs-lookup"><span data-stu-id="44cf8-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
-   <span data-ttu-id="44cf8-132">session.CloseOutputSession : arrêt du flux de données sortant (fermeture partielle).</span><span class="sxs-lookup"><span data-stu-id="44cf8-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="44cf8-133">Fabrique de canaux</span><span class="sxs-lookup"><span data-stu-id="44cf8-133">Channel Factory</span></span>  
 <span data-ttu-id="44cf8-134">L'étape suivante de l'écriture du transport TCP consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelFactory> pour les canaux clients.</span><span class="sxs-lookup"><span data-stu-id="44cf8-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
-   <span data-ttu-id="44cf8-135">`WseTcpChannelFactory`dérive de <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="44cf8-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="44cf8-136">Il s'agit d'une fabrique qui substitue `OnCreateChannel` pour produire des canaux clients.</span><span class="sxs-lookup"><span data-stu-id="44cf8-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   <span data-ttu-id="44cf8-137">`ClientWseTcpDuplexSessionChannel`Ajoute une logique à la base de `WseTcpDuplexSessionChannel` pour se connecter à un serveur TCP à `channel.Open` heure.</span><span class="sxs-lookup"><span data-stu-id="44cf8-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="44cf8-138">Le nom d'hôte est d'abord résolu en une adresse IP, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="44cf8-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   <span data-ttu-id="44cf8-139">Ensuite, le nom d'hôte est connecté à la première adresse IP disponible dans une boucle, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="44cf8-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   <span data-ttu-id="44cf8-140">Dans le cadre du contrat de canal, les exceptions spécifiques du domaine sont incluses dans un wrapper, comme `SocketException` dans <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="44cf8-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="44cf8-141">Écouteur de canal</span><span class="sxs-lookup"><span data-stu-id="44cf8-141">Channel Listener</span></span>  
 <span data-ttu-id="44cf8-142">L'étape suivante de l'écriture du transport TCP consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelListener> permettant d'accepter les canaux serveur.</span><span class="sxs-lookup"><span data-stu-id="44cf8-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
-   <span data-ttu-id="44cf8-143">`WseTcpChannelListener`dérive de <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > et remplacements [Begin] Open et On [Begin] Close pour contrôlent la durée de vie de son socket d’écoute.</span><span class="sxs-lookup"><span data-stu-id="44cf8-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="44cf8-144">Dans OnOpen, un socket est créé pour écouter sur IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="44cf8-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="44cf8-145">Des implémentations plus avancées peuvent créer un deuxième socket pour écouter également sur IPv6.</span><span class="sxs-lookup"><span data-stu-id="44cf8-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="44cf8-146">Elles permettent également de spécifier l'adresse IP dans le nom d'hôte.</span><span class="sxs-lookup"><span data-stu-id="44cf8-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="44cf8-147">Lorsqu'un nouveau socket est accepté, un canal serveur est initialisé avec celui-ci.</span><span class="sxs-lookup"><span data-stu-id="44cf8-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="44cf8-148">Toutes les entrées et sorties étant déjà implémentées dans la classe de base, ce canal est donc chargé d'initialiser le socket.</span><span class="sxs-lookup"><span data-stu-id="44cf8-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="44cf8-149">Ajout d'un élément de liaison</span><span class="sxs-lookup"><span data-stu-id="44cf8-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="44cf8-150">Maintenant que les fabriques de canaux sont générées, elles doivent être exposées à l'exécution de ServiceModel via une liaison.</span><span class="sxs-lookup"><span data-stu-id="44cf8-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="44cf8-151">Une liaison est une collection d'éléments de liaison qui représente la pile de communication associée à une adresse de service.</span><span class="sxs-lookup"><span data-stu-id="44cf8-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="44cf8-152">Chaque élément de la pile est représenté par un élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="44cf8-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="44cf8-153">Dans notre exemple, l'élément de liaison est `WseTcpTransportBindingElement`, lequel dérive de <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="44cf8-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="44cf8-154">Il prend en charge <xref:System.ServiceModel.Channels.IDuplexSessionChannel> et substitue les méthodes suivantes pour générer les fabriques associées à notre liaison.</span><span class="sxs-lookup"><span data-stu-id="44cf8-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="44cf8-155">Notre exemple contient également des membres permettant de cloner l'élément `BindingElement` et de retourner notre schéma (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="44cf8-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="44cf8-156">Console de test TCP WSE</span><span class="sxs-lookup"><span data-stu-id="44cf8-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="44cf8-157">Le code de test permettant d'utiliser cet exemple de transport est disponible dans TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="44cf8-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="44cf8-158">Les instructions suivantes indiquent comment installer l'exemple WSE `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="44cf8-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="44cf8-159">Le code de test crée une liaison personnalisée qui utilise MTOM comme encodage et `WseTcpTransport` comme transport.</span><span class="sxs-lookup"><span data-stu-id="44cf8-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="44cf8-160">Il installe également AddressingVersion afin d'assurer la conformité avec WSE 3.0, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="44cf8-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="44cf8-161">Il se compose de deux tests : le premier installe un client typé à l'aide du code généré à partir de WSDL WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="44cf8-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="44cf8-162">Le deuxième utilise [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à la fois comme client et serveur en envoyant directement des messages sur les API de canal.</span><span class="sxs-lookup"><span data-stu-id="44cf8-162">The second test uses [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="44cf8-163">L'exécution de l'exemple est censée donner le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="44cf8-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="44cf8-164">Client :</span><span class="sxs-lookup"><span data-stu-id="44cf8-164">Client:</span></span>  
  
```  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 <span data-ttu-id="44cf8-165">Serveur :</span><span class="sxs-lookup"><span data-stu-id="44cf8-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="44cf8-166">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="44cf8-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="44cf8-167">Pour que vous puissiez exécuter cet exemple, WSE 3.0 doit être installé et vous devez disposer de l'exemple `TcpSyncStockService` WSE.</span><span class="sxs-lookup"><span data-stu-id="44cf8-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="44cf8-168">Vous pouvez télécharger [WSE 3.0 à partir de MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="44cf8-168">You can download [WSE 3.0 from MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44cf8-169">Étant donné que WSE 3.0 n'est pas pris en charge sur [!INCLUDE[lserver](../../../../includes/lserver-md.md)], vous ne pouvez pas installer ou exécuter l'exemple `TcpSyncStockService` sur ce système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="44cf8-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1.  <span data-ttu-id="44cf8-170">Après avoir installé l'exemple `TcpSyncStockService`, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="44cf8-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1.  <span data-ttu-id="44cf8-171">Ouvrez `TcpSyncStockService` dans Visual Studio (notez que l'exemple TcpSyncStockService est installé avec WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="44cf8-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="44cf8-172">Il ne fait pas partie du code de cet exemple).</span><span class="sxs-lookup"><span data-stu-id="44cf8-172">It is not part of this sample's code).</span></span>  
  
    2.  <span data-ttu-id="44cf8-173">Définissez StockService comme projet de démarrage.</span><span class="sxs-lookup"><span data-stu-id="44cf8-173">Set the StockService project as the start up project.</span></span>  
  
    3.  <span data-ttu-id="44cf8-174">Ouvrez StockService.cs dans le projet StockService et commentez l'attribut [Policy] sur la classe `StockService`.</span><span class="sxs-lookup"><span data-stu-id="44cf8-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="44cf8-175">Cette opération désactive la sécurité de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="44cf8-175">This disables security from the sample.</span></span> <span data-ttu-id="44cf8-176">Bien que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] puisse interagir avec des points de terminaison sécurisés WSE 3.0, la sécurité est désactivée afin que cet exemple reste axé sur le transport TCP personnalisé.</span><span class="sxs-lookup"><span data-stu-id="44cf8-176">While [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4.  <span data-ttu-id="44cf8-177">Appuyez sur F5 pour démarrer `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="44cf8-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="44cf8-178">Le service démarre dans une nouvelle fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="44cf8-178">The service starts in a new console window.</span></span>  
  
    5.  <span data-ttu-id="44cf8-179">Ouvrez cet exemple de transport TCP dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44cf8-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6.  <span data-ttu-id="44cf8-180">Dans TestCode.cs, mettez la variable « hostname » à jour afin qu'elle corresponde au nom de l'ordinateur qui exécute `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="44cf8-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7.  <span data-ttu-id="44cf8-181">Appuyez sur F5 pour démarrer l'exemple de transport TCP.</span><span class="sxs-lookup"><span data-stu-id="44cf8-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8.  <span data-ttu-id="44cf8-182">Le client test du transport TCP démarre dans une nouvelle console.</span><span class="sxs-lookup"><span data-stu-id="44cf8-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="44cf8-183">Le client demande les cotations boursières au service, puis affiche les résultats dans sa fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="44cf8-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44cf8-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44cf8-184">See Also</span></span>
