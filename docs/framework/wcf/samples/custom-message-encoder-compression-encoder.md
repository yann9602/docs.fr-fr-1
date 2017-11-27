---
title: 'Custom Message Encoder: Compression Encoder'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
caps.latest.revision: "37"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 09566625b6159fb8ce6da6ef347e2d1ddecce1db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="75a48-102">Custom Message Encoder: Compression Encoder</span><span class="sxs-lookup"><span data-stu-id="75a48-102">Custom Message Encoder: Compression Encoder</span></span>
<span data-ttu-id="75a48-103">Cet exemple montre comment implémenter un encodeur personnalisé à l'aide de la plateforme [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75a48-103">This sample demonstrates how to implement a custom encoder using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] platform.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75a48-104">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="75a48-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="75a48-105">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="75a48-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="75a48-106">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="75a48-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75a48-107">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="75a48-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a><span data-ttu-id="75a48-108">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="75a48-108">Sample Details</span></span>  
 <span data-ttu-id="75a48-109">Cet exemple se compose d'un programme de console cliente (.exe), d'un programme de console de service auto-hébergé (.exe) et d'une bibliothèque d'encodeurs de message de compression (.dll).</span><span class="sxs-lookup"><span data-stu-id="75a48-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="75a48-110">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="75a48-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="75a48-111">Le contrat est défini par l'interface `ISampleServer`, laquelle expose la chaîne de base qui reproduit en écho les opérations (`Echo` et `BigEcho`).</span><span class="sxs-lookup"><span data-stu-id="75a48-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="75a48-112">Le client adresse des demandes synchrones à une opération donnée et le service répond en répétant de nouveau le message au client.</span><span class="sxs-lookup"><span data-stu-id="75a48-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="75a48-113">L'activité du client et du service est visible dans les fenêtres de console.</span><span class="sxs-lookup"><span data-stu-id="75a48-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="75a48-114">Cet exemple montre comment écrire un encodeur personnalisé et présente l'impact de la compression d'un message sur le câble.</span><span class="sxs-lookup"><span data-stu-id="75a48-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="75a48-115">Vous pouvez ajouter l'instrumentation à l'encodeur de message de compression afin de calculer la taille de message, le temps de traitement ou les deux.</span><span class="sxs-lookup"><span data-stu-id="75a48-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75a48-116">Dans .NET Framework 4, la décompression automatique a été activée sur un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] si le serveur envoie une réponse compressée (créée avec un algorithme tel que GZip ou Deflate).</span><span class="sxs-lookup"><span data-stu-id="75a48-116">In the .NET Framework 4, automatic decompression has been enabled on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="75a48-117">Si le service est hébergé sur le Web dans Internet Information Server (IIS), IIS peut être configuré de sorte que le service envoie une réponse compressée.</span><span class="sxs-lookup"><span data-stu-id="75a48-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="75a48-118">Cet exemple peut être utilisé si la compression et la décompression doivent s'effectuer sur le client et dans le service, ou si le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="75a48-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>  
  
 <span data-ttu-id="75a48-119">L'exemple montre comment créer et intégrer un encodeur de message personnalisé dans une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75a48-119">The sample demonstrates how to build and integrate a custom message encoder into a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="75a48-120">La bibliothèque GZipEncoder.dll est déployée avec le client et le service.</span><span class="sxs-lookup"><span data-stu-id="75a48-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="75a48-121">Cet exemple montre également l'impact de la compression des messages.</span><span class="sxs-lookup"><span data-stu-id="75a48-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="75a48-122">Le code dans GZipEncoder.dll présente les procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="75a48-122">The code in GZipEncoder.dll demonstrates the following:</span></span>  
  
-   <span data-ttu-id="75a48-123">Création d'un encodeur personnalisé et d'une fabrique d'encodeur.</span><span class="sxs-lookup"><span data-stu-id="75a48-123">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="75a48-124">Développement d'un élément de liaison pour un encodeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75a48-124">Developing a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="75a48-125">Utilisation de la configuration de liaison personnalisée permettant d'intégrer des éléments de liaison personnalisés.</span><span class="sxs-lookup"><span data-stu-id="75a48-125">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="75a48-126">Développement d'un gestionnaire de configuration personnalisé afin de permettre la configuration de fichier d'un élément de liaison personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75a48-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
 <span data-ttu-id="75a48-127">Comme indiqué précédemment, plusieurs couches sont implémentées dans un encodeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75a48-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="75a48-128">Pour mieux illustrer la relation entre chacune d'elles, la liste suivante présente un ordre simplifié des événements de démarrage du service :</span><span class="sxs-lookup"><span data-stu-id="75a48-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>  
  
1.  <span data-ttu-id="75a48-129">Le serveur démarre.</span><span class="sxs-lookup"><span data-stu-id="75a48-129">The server starts.</span></span>  
  
2.  <span data-ttu-id="75a48-130">Les informations de configuration sont lues.</span><span class="sxs-lookup"><span data-stu-id="75a48-130">The configuration information is read.</span></span>  
  
    1.  <span data-ttu-id="75a48-131">La configuration du service enregistre le gestionnaire de configuration personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75a48-131">The service configuration registers the custom configuration handler.</span></span>  
  
    2.  <span data-ttu-id="75a48-132">L'hôte de service est créé et ouvert.</span><span class="sxs-lookup"><span data-stu-id="75a48-132">The service host is created and opened.</span></span>  
  
    3.  <span data-ttu-id="75a48-133">L'élément de configuration personnalisé crée et retourne l'élément de liaison personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75a48-133">The custom configuration element creates and returns the custom binding element.</span></span>  
  
    4.  <span data-ttu-id="75a48-134">L'élément de liaison personnalisé crée et retourne une fabrique d'encodeur de message.</span><span class="sxs-lookup"><span data-stu-id="75a48-134">The custom binding element creates and returns a message encoder factory.</span></span>  
  
3.  <span data-ttu-id="75a48-135">Un message est reçu.</span><span class="sxs-lookup"><span data-stu-id="75a48-135">A message is received.</span></span>  
  
4.  <span data-ttu-id="75a48-136">La fabrique retourne un encodeur de message permettant de lire dans le message et d'écrire la réponse.</span><span class="sxs-lookup"><span data-stu-id="75a48-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>  
  
5.  <span data-ttu-id="75a48-137">La couche d'encodeur est implémentée sous forme de fabrique de classe.</span><span class="sxs-lookup"><span data-stu-id="75a48-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="75a48-138">Seule la fabrique de classe d'encodeur doit être exposée publiquement pour l'encodeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75a48-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="75a48-139">L'objet de fabrique est retourné par l'élément de liaison lorsque l'objet <xref:System.ServiceModel.ServiceHost> ou <xref:System.ServiceModel.ChannelFactory%601> est créé.</span><span class="sxs-lookup"><span data-stu-id="75a48-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="75a48-140">Les encodeurs de message peuvent fonctionner en mode de mise en mémoire tampon ou en mode de diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="75a48-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="75a48-141">Cet exemple présente ces deux modes.</span><span class="sxs-lookup"><span data-stu-id="75a48-141">This sample demonstrates both buffered mode and streaming mode.</span></span>  
  
 <span data-ttu-id="75a48-142">Chaque mode est associée à une méthode `ReadMessage` et `WriteMessage` sur la classe abstraite `MessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="75a48-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="75a48-143">La majeure partie de l'encodage a lieu dans ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="75a48-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="75a48-144">L'exemple encapsule les encodeurs de message texte et binaire existants.</span><span class="sxs-lookup"><span data-stu-id="75a48-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="75a48-145">Cela permet à l'exemple de déléguer la lecture et l'écriture de la représentation de câble des messages à l'encodeur interne, et à l'encodeur de compression de compresser ou décompresser les résultats.</span><span class="sxs-lookup"><span data-stu-id="75a48-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="75a48-146">Comme il n'existe aucun pipeline pour l'encodage de message, c'est le seul modèle permettant d'utiliser plusieurs encodeurs dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75a48-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="75a48-147">Une fois que le message a été décompressé, le message résultant est passé en haut de la pile pour être géré par la pile de canaux.</span><span class="sxs-lookup"><span data-stu-id="75a48-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="75a48-148">Pendant la compression, le message compressé résultant est écrit directement dans le flux fourni.</span><span class="sxs-lookup"><span data-stu-id="75a48-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>  
  
 <span data-ttu-id="75a48-149">Cet exemple utilise des méthodes d'assistance (`CompressBuffer` et `DecompressBuffer`) permettant d'effectuer la conversion des mémoires tampon en flux afin d'utiliser la classe `GZipStream`.</span><span class="sxs-lookup"><span data-stu-id="75a48-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>  
  
 <span data-ttu-id="75a48-150">Les classes `ReadMessage` et `WriteMessage` mises en mémoire tampon utilisent la classe `BufferManager`.</span><span class="sxs-lookup"><span data-stu-id="75a48-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="75a48-151">L'encodeur est uniquement accessible via la fabrique d'encodeur.</span><span class="sxs-lookup"><span data-stu-id="75a48-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="75a48-152">La classe abstraite `MessageEncoderFactory` fournit la propriété `Encoder` permettant d'accéder à l'encodeur actuel et la méthode `CreateSessionEncoder` permettant de créer un encodeur qui prend en charge les sessions.</span><span class="sxs-lookup"><span data-stu-id="75a48-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="75a48-153">Un encodeur de ce type peut être utilisé dans le scénario où le canal prend en charge des sessions, est ordonné et est fiable.</span><span class="sxs-lookup"><span data-stu-id="75a48-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="75a48-154">Ce scénario permet d'optimiser dans chaque session les données écrites sur le câble.</span><span class="sxs-lookup"><span data-stu-id="75a48-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="75a48-155">Si cet objectif n'est pas souhaité, la méthode de base ne doit pas être surchargée.</span><span class="sxs-lookup"><span data-stu-id="75a48-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="75a48-156">La propriété `Encoder` fournit un mécanisme permettant d'accéder à l'encodeur sans session, et l'implémentation par défaut de la méthode `CreateSessionEncoder` retourne la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="75a48-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="75a48-157">Cet exemple encapsulant un encodeur existant pour fournir la compression, l'implémentation `MessageEncoderFactory` accepte un `MessageEncoderFactory` qui représente la fabrique d'encodeur interne.</span><span class="sxs-lookup"><span data-stu-id="75a48-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>  
  
 <span data-ttu-id="75a48-158">L'encodeur et la fabrique d'encodeur étant maintenant définis, ils peuvent être utilisés avec un client et un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75a48-158">Now that the encoder and encoder factory are defined, they can be used with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and service.</span></span> <span data-ttu-id="75a48-159">Toutefois, ces encodeurs doivent être ajoutés à la pile de canaux.</span><span class="sxs-lookup"><span data-stu-id="75a48-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="75a48-160">Vous pouvez dériver des classes des classes <xref:System.ServiceModel.ServiceHost> et <xref:System.ServiceModel.ChannelFactory%601>, et substituer les méthodes `OnInitialize` pour ajouter cette fabrique d'encodeur manuellement.</span><span class="sxs-lookup"><span data-stu-id="75a48-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="75a48-161">Vous pouvez également exposer la fabrique d'encodeur via un élément de liaison personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75a48-161">You can also expose the encoder factory through a custom binding element.</span></span>  
  
 <span data-ttu-id="75a48-162">Pour créer un élément de liaison personnalisé, dérivez une classe de la classe <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="75a48-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="75a48-163">Cependant, il existe plusieurs types d'éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="75a48-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="75a48-164">Pour s'assurer que l'élément de liaison personnalisé est reconnu en tant qu'élément de liaison d'encodage de message, vous devez également implémenter <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="75a48-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="75a48-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> expose une méthode permettant de créer une nouvelle fabrique d'encodeur de message (`CreateMessageEncoderFactory`), laquelle est implémentée pour retourner une instance de la fabrique d'encodeur de message correspondante.</span><span class="sxs-lookup"><span data-stu-id="75a48-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="75a48-166">En outre, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> possède une propriété permettant d'indiquer la version d'adressage.</span><span class="sxs-lookup"><span data-stu-id="75a48-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="75a48-167">Cet exemple encapsulant les encodeurs existants, l'implémentation encapsule également les éléments de liaison d'encodeur existants et fournit un élément de liaison d'encodeur interne comme paramètre au constructeur, puis l'expose via une propriété.</span><span class="sxs-lookup"><span data-stu-id="75a48-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="75a48-168">L'exemple de code suivant présente l'implémentation de la classe `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="75a48-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>  
  
```  
public sealed class GZipMessageEncodingBindingElement   
                        : MessageEncodingBindingElement //BindingElement  
                        , IPolicyExportExtension  
{  
  
    //We use an inner binding element to store information   
    //required for the inner encoder.  
    MessageEncodingBindingElement innerBindingElement;  
  
        //By default, use the default text encoder as the inner encoder.  
        public GZipMessageEncodingBindingElement()  
            : this(new TextMessageEncodingBindingElement()) { }  
  
    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)  
    {  
        this.innerBindingElement = messageEncoderBindingElement;  
    }  
  
    public MessageEncodingBindingElement InnerMessageEncodingBindingElement  
    {  
        get { return innerBindingElement; }  
        set { innerBindingElement = value; }  
    }  
  
    //Main entry point into the encoder binding element.   
    // Called by WCF to get the factory that creates the  
    //message encoder.  
    public override MessageEncoderFactory CreateMessageEncoderFactory()  
    {  
        return new   
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get { return innerBindingElement.MessageVersion; }  
        set { innerBindingElement.MessageVersion = value; }  
    }  
  
    public override BindingElement Clone()  
    {  
        return new   
        GZipMessageEncodingBindingElement(this.innerBindingElement);  
    }  
  
    public override T GetProperty<T>(BindingContext context)  
    {  
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))  
        {  
            return innerBindingElement.GetProperty<T>(context);  
        }  
        else   
        {  
            return base.GetProperty<T>(context);  
        }  
    }  
  
    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelFactory<TChannel>();  
    }  
  
    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelListener<TChannel>();  
    }  
  
    public override bool CanBuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.CanBuildInnerChannelListener<TChannel>();  
    }  
  
    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)  
    {  
        if (policyContext == null)  
        {  
            throw new ArgumentNullException("policyContext");  
        }  
       XmlDocument document = new XmlDocument();  
       policyContext.GetBindingAssertions().Add(document.CreateElement(  
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,  
            GZipMessageEncodingPolicyConstants.GZipEncodingName,  
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));  
    }  
}  
```  
  
 <span data-ttu-id="75a48-169">Notez que la classe `GZipMessageEncodingBindingElement` implémente l'interface `IPolicyExportExtension`, afin que cet élément de liaison puisse être exporté en tant que stratégie dans les métadonnées, tel qu'indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="75a48-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">  
    <wsp:ExactlyOne>  
      <wsp:All>  
        <gzip:text xmlns:gzip=  
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />   
       <wsaw:UsingAddressing />   
     </wsp:All>  
   </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="75a48-170">La classe `GZipMessageEncodingBindingElementImporter` implémente l'interface `IPolicyImportExtension` et importe la stratégie pour `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="75a48-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="75a48-171">L'outil Svcutil.exe permet d'importer des stratégies dans le fichier de configuration et de gérer `GZipMessageEncodingBindingElement` ; les éléments suivants doivent être ajoutés à Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="75a48-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="gzipMessageEncoding"   
          type=  
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </bindingElementExtensions>  
    </extensions>  
    <client>  
      <metadata>  
        <policyImporters>  
          <remove type=  
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
          <extension type=  
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="75a48-172">Maintenant qu'un élément de liaison correspondant existe pour l'encodeur de compression, il peut être raccordé par programme au service ou au client en construisant un nouvel objet de liaison personnalisé et en lui ajoutant l'élément de liaison personnalisé, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="75a48-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 <span data-ttu-id="75a48-173">Même si cela peut s'avérer suffisant pour la majorité de scénarios utilisateur, la prise en charge d'une configuration de fichier est critique si un service doit être hébergé sur le Web.</span><span class="sxs-lookup"><span data-stu-id="75a48-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="75a48-174">Pour prendre en charge le scénario hébergé sur le Web, vous devez développer un gestionnaire de configuration personnalisé afin de permettre la configuration d'un élément de liaison personnalisé dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="75a48-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>  
  
 <span data-ttu-id="75a48-175">Vous pouvez créer un gestionnaire de configuration pour l'élément de liaison en plus du système de configuration fourni par [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75a48-175">You can build a configuration handler for the binding element on top of the configuration system provided by the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="75a48-176">Ce gestionnaire de configuration doit dériver de la classe <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="75a48-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="75a48-177">La propriété `BindingElementType` permet d'indiquer au système de configuration le type d'élément de liaison à créer pour cette section.</span><span class="sxs-lookup"><span data-stu-id="75a48-177">The `BindingElementType` property is used to inform the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="75a48-178">Tous les aspects de `BindingElement` qui peuvent être définis doivent être exposés en tant que propriétés dans la classe dérivée <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="75a48-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="75a48-179"><xref:System.Configuration.ConfigurationPropertyAttribute> permet de mapper les attributs d'élément de configuration aux propriétés et d'affecter des valeurs par défaut si les attributs ne sont pas définis.</span><span class="sxs-lookup"><span data-stu-id="75a48-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> is used to assist in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="75a48-180">Après avoir chargé et appliqué les valeurs de la configuration aux propriétés, la méthode <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> est appelée et convertit les propriétés en instance concrète d'un élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="75a48-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="75a48-181">La méthode <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> permet de convertir les propriétés sur la classe dérivée <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> en valeurs à définir sur l'élément de liaison récemment créé.</span><span class="sxs-lookup"><span data-stu-id="75a48-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newlycreated binding element.</span></span>  
  
 <span data-ttu-id="75a48-182">L'exemple de code suivant présente l'implémentation de `GZipMessageEncodingElement`.</span><span class="sxs-lookup"><span data-stu-id="75a48-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>  
  
```  
public class GZipMessageEncodingElement : BindingElementExtensionElement  
{  
    public GZipMessageEncodingElement()  
    {  
    }  
  
//Called by the WCF to discover the type of binding element this   
//config section enables  
    public override Type BindingElementType  
    {  
        get { return typeof(GZipMessageEncodingBindingElement); }  
    }  
  
    //The only property we need to configure for our binding element is   
    //the type of inner encoder to use. Here, we support text and  
    //binary.  
    [ConfigurationProperty("innerMessageEncoding",   
                         DefaultValue = "textMessageEncoding")]  
    public string InnerMessageEncoding  
    {  
        get { return (string)base["innerMessageEncoding"]; }  
        set { base["innerMessageEncoding"] = value; }  
    }  
  
    //Called by the WCF to apply the configuration settings (the   
    //property above) to the binding element  
    public override void ApplyConfiguration(BindingElement bindingElement)  
    {  
        GZipMessageEncodingBindingElement binding =   
                (GZipMessageEncodingBindingElement)bindingElement;  
        PropertyInformationCollection propertyInfo =   
                    this.ElementInformation.Properties;  
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=   
                                     PropertyValueOrigin.Default)  
        {  
            switch (this.InnerMessageEncoding)  
            {  
                case "textMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                      new TextMessageEncodingBindingElement();  
                    break;  
                case "binaryMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                         new BinaryMessageEncodingBindingElement();  
                    break;  
            }  
        }  
    }  
  
    //Called by the WCF to create the binding element  
    protected override BindingElement CreateBindingElement()  
    {  
        GZipMessageEncodingBindingElement bindingElement =   
                new GZipMessageEncodingBindingElement();  
        this.ApplyConfiguration(bindingElement);  
        return bindingElement;  
    }  
}   
```  
  
 <span data-ttu-id="75a48-183">Ce gestionnaire de configuration mappe à la représentation suivante dans le fichier App.config ou Web.config du service ou du client.</span><span class="sxs-lookup"><span data-stu-id="75a48-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 <span data-ttu-id="75a48-184">Pour utiliser ce gestionnaire de configuration, elle doit être inscrite dans le [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément, comme indiqué dans l’exemple de configuration suivantes.</span><span class="sxs-lookup"><span data-stu-id="75a48-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
       <add   
           name="gzipMessageEncoding"   
           type=  
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,  
           GZipEncoder, Version=1.0.0.0, Culture=neutral,   
           PublicKeyToken=null" />  
      </bindingElementExtensions>  
</extensions>  
```  
  
 <span data-ttu-id="75a48-185">Lorsque vous exécutez le serveur, les demandes et réponses d'opération s'affichent dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="75a48-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="75a48-186">Appuyez sur ENTER dans la fenêtre pour arrêter le serveur.</span><span class="sxs-lookup"><span data-stu-id="75a48-186">Press ENTER in the window to shut down the server.</span></span>  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 <span data-ttu-id="75a48-187">Lorsque vous exécutez le client, les demandes et réponses d'opération s'affichent dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="75a48-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="75a48-188">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="75a48-188">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="75a48-189">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="75a48-189">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="75a48-190">Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="75a48-190">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="75a48-191">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75a48-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="75a48-192">Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75a48-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="75a48-193">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75a48-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75a48-194">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="75a48-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="75a48-195">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="75a48-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="75a48-196">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="75a48-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75a48-197">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="75a48-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a><span data-ttu-id="75a48-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75a48-198">See Also</span></span>
