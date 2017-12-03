---
title: "Vue d'ensemble de la création de points de terminaison"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 309d19ee75f506ab781703ebe1068d6d90d9c47c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="213f2-102">Vue d'ensemble de la création de points de terminaison</span><span class="sxs-lookup"><span data-stu-id="213f2-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="213f2-103">Toutes les communications avec un [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service s’effectue via le *points de terminaison* du service.</span><span class="sxs-lookup"><span data-stu-id="213f2-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="213f2-104">Les points de terminaison fournissent aux clients l'accès aux fonctionnalités offertes par un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="213f2-104">Endpoints provide the clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span> <span data-ttu-id="213f2-105">Cette section décrit la structure d'un point de terminaison et explique comment définir un point de terminaison dans la configuration et dans le code.</span><span class="sxs-lookup"><span data-stu-id="213f2-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="213f2-106">Structure d'un point de terminaison</span><span class="sxs-lookup"><span data-stu-id="213f2-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="213f2-107">Chaque point de terminaison contient une adresse qui indique où rechercher le point de terminaison, une liaison qui spécifie le mode de communication d’un client avec le point de terminaison, et un contrat qui identifie les méthodes disponibles.</span><span class="sxs-lookup"><span data-stu-id="213f2-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
-   <span data-ttu-id="213f2-108">**Adresse**.</span><span class="sxs-lookup"><span data-stu-id="213f2-108">**Address**.</span></span> <span data-ttu-id="213f2-109">L'adresse identifie le point de terminaison de manière unique et indique aux consommateurs potentiels l'emplacement du service.</span><span class="sxs-lookup"><span data-stu-id="213f2-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="213f2-110">Elle est représentée dans le modèle objet [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] par l'adresse <xref:System.ServiceModel.EndpointAddress> qui contient un URI (Uniform Resource Identifier) et les propriétés d'adresse qui incluent une identité, certains éléments WSDL (Web Services Description Language) et une collection d'en-têtes facultatifs.</span><span class="sxs-lookup"><span data-stu-id="213f2-110">It is represented in the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="213f2-111">Les en-têtes facultatifs fournissent des données d'adressage détaillées supplémentaires pour identifier ou interagir avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="213f2-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="213f2-112">[Spécification d’une adresse de point de terminaison](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="213f2-112"> [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="213f2-113">**Liaison**.</span><span class="sxs-lookup"><span data-stu-id="213f2-113">**Binding**.</span></span> <span data-ttu-id="213f2-114">La liaison spécifie le mode de communication avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="213f2-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="213f2-115">La liaison spécifie comment le point de terminaison communique avec le monde, y compris quel protocole de transport utiliser (par exemple, TCP ou HTTP), quel encodage utiliser pour les messages (par exemple, texte ou binaire), et quelles exigences de sécurité sont nécessaires (par exemple, SSL [Secure Sockets Layer] ou la sécurité des messages SOAP).</span><span class="sxs-lookup"><span data-stu-id="213f2-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="213f2-116">[à l’aide de liaisons pour configurer les Clients et Services](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="213f2-116"> [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
-   <span data-ttu-id="213f2-117">**Contrat de service**.</span><span class="sxs-lookup"><span data-stu-id="213f2-117">**Service contract**.</span></span> <span data-ttu-id="213f2-118">Le contrat de service définit les fonctionnalités que le point de terminaison expose au client.</span><span class="sxs-lookup"><span data-stu-id="213f2-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="213f2-119">Un contrat spécifie les opérations qu'un client peut appeler, la forme du message et le type de paramètres d'entrée ou de données requis pour appeler l'opération, ainsi que le type du traitement ou le message de réponse auquel le client peut s'attendre.</span><span class="sxs-lookup"><span data-stu-id="213f2-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="213f2-120">Trois types de contrats de base correspondent aux modèles d'échange de messages (MEPs, message exchange patterns) de base : datagramme (unidirectionnel), demande/réponse et duplex (bidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="213f2-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="213f2-121">Le contrat de service peut aussi employer des contrats de données et de message pour requérir des types de données spécifiques et des formats de message lors de son accès.</span><span class="sxs-lookup"><span data-stu-id="213f2-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="213f2-122">comment définir un contrat de service, consultez [concevoir des contrats de Service](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="213f2-122"> how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="213f2-123">Notez qu'un client peut aussi devoir implémenter un contrat défini par le service, appelé un contrat de rappel, pour recevoir des messages du service dans un MEP duplex.</span><span class="sxs-lookup"><span data-stu-id="213f2-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="213f2-124">[Services duplex](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="213f2-124"> [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="213f2-125">Le point de terminaison pour un service peut être spécifié de manière impérative en utilisant le code ou de façon déclarative par la configuration.</span><span class="sxs-lookup"><span data-stu-id="213f2-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="213f2-126">Si aucun point de terminaison n'est spécifié, le runtime fournit les points de terminaison par défaut en ajoutant un point de terminaison par défaut pour chaque adresse de base pour chaque contrat de service implémenté par le service.</span><span class="sxs-lookup"><span data-stu-id="213f2-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="213f2-127">La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.</span><span class="sxs-lookup"><span data-stu-id="213f2-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="213f2-128">En général, il est plus pratique de définir des points de terminaison de service à l'aide de la configuration plutôt que du code.</span><span class="sxs-lookup"><span data-stu-id="213f2-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="213f2-129">Le fait de conserver les informations de liaison et d'adressage hors du code leur permet de changer sans devoir recompiler ou de redéployer l'application.</span><span class="sxs-lookup"><span data-stu-id="213f2-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="213f2-130">Lorsque vous ajoutez un point de terminaison de service qui effectue un emprunt d'identité, vous devez utiliser une des méthodes <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> ou la méthode <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> pour charger correctement le contrat dans un nouvel objet <xref:System.ServiceModel.Description.ServiceDescription>.</span><span class="sxs-lookup"><span data-stu-id="213f2-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="213f2-131">Définition de points de terminaison dans le code</span><span class="sxs-lookup"><span data-stu-id="213f2-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="213f2-132">L'exemple suivant illustre comment spécifier un point de terminaison dans le code avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="213f2-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
-   <span data-ttu-id="213f2-133">Définissez un contrat pour un `IEcho` type de service qui accepte le nom et renvoie la réponse d’une personne « Hello \<nom > ! ».</span><span class="sxs-lookup"><span data-stu-id="213f2-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
-   <span data-ttu-id="213f2-134">Implémentez un service `Echo` du type défini par le contrat `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="213f2-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
-   <span data-ttu-id="213f2-135">Spécifiez une adresse de point de terminaison http://localhost:8000/Echo pour le service.</span><span class="sxs-lookup"><span data-stu-id="213f2-135">Specify an endpoint address of http://localhost:8000/Echo for the service.</span></span>  
  
-   <span data-ttu-id="213f2-136">Configurez le service `Echo` à l'aide d'une liaison <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="213f2-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  <span data-ttu-id="213f2-137">L'hôte de service est créé avec une adresse de base, puis le reste de l'adresse, relatif à l'adresse de base, est spécifié dans le cadre d'un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="213f2-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="213f2-138">Ce partitionnement de l'adresse permet de définir plus simplement plusieurs points de terminaison pour les services à un hôte.</span><span class="sxs-lookup"><span data-stu-id="213f2-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="213f2-139">Les propriétés de <xref:System.ServiceModel.Description.ServiceDescription> dans l'application de service ne doivent pas être modifiées à l'issue de la méthode <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sur <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="213f2-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="213f2-140">Certains membres, tels que la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> et les méthodes `AddServiceEndpoint` sur <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.ServiceHost>, lèvent une exception s'ils sont modifiés au-delà de ce point.</span><span class="sxs-lookup"><span data-stu-id="213f2-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="213f2-141">D'autres membres peuvent être modifiés, mais le résultat n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="213f2-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="213f2-142">De la même façon, sur le client les valeurs <xref:System.ServiceModel.Description.ServiceEndpoint> ne doivent pas être modifiées après l'appel à <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sur <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="213f2-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="213f2-143">La propriété <xref:System.ServiceModel.ChannelFactory.Credentials%2A> lève une exception si elle est modifiée au-delà de ce point.</span><span class="sxs-lookup"><span data-stu-id="213f2-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="213f2-144">Les autres valeurs de description du client peuvent être modifiées sans erreur, mais le résultat n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="213f2-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="213f2-145">Aussi bien pour le service que le client, il est recommandé de modifier la description avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="213f2-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="213f2-146">Définition de points de terminaison dans la configuration</span><span class="sxs-lookup"><span data-stu-id="213f2-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="213f2-147">Lorsque vous créez une application, vous souhaitez souvent remettre des décisions à l'administrateur chargé de son déploiement.</span><span class="sxs-lookup"><span data-stu-id="213f2-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="213f2-148">Par exemple, il est souvent impossible de déterminer à l'avance à quoi correspond une adresse de service (URI).</span><span class="sxs-lookup"><span data-stu-id="213f2-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="213f2-149">Au lieu de d'encoder de manière irréversible une adresse, il est préférable de permettre à un administrateur de le faire après avoir créé un service.</span><span class="sxs-lookup"><span data-stu-id="213f2-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="213f2-150">Cette souplesse est obtenue par le biais de la configuration.</span><span class="sxs-lookup"><span data-stu-id="213f2-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="213f2-151">Pour plus d’informations, consultez [configuration des Services](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="213f2-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="213f2-152">Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) avec la `/config:` *nom de fichier*`[,`*nom de fichier* `]` basculer vers Créez rapidement des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="213f2-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="213f2-153">Utilisation des points de terminaison par défaut</span><span class="sxs-lookup"><span data-stu-id="213f2-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="213f2-154">Si aucun point de terminaison n'est spécifié dans le code ou dans la configuration, le runtime fournit les points de terminaison par défaut en ajoutant un point de terminaison par défaut pour chaque adresse de base pour chaque contrat de service implémenté par le service.</span><span class="sxs-lookup"><span data-stu-id="213f2-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="213f2-155">L'adresse de base peut être spécifiée dans le code ou dans la configuration, et les points de terminaison par défaut sont ajoutés lors de l'appel de <xref:System.ServiceModel.ICommunicationObject.Open> sur le <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="213f2-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="213f2-156">Cet exemple est le même que celui de la section précédente, mais, étant donné qu'aucun point de terminaison n'est spécifié, les points de terminaison par défaut sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="213f2-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 <span data-ttu-id="213f2-157">Si des points de terminaison sont fournis explicitement, les points de terminaison par défaut peuvent toujours être ajoutés en appelant <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> sur le <xref:System.ServiceModel.ServiceHost> avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="213f2-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="213f2-158">par défaut des points de terminaison, consultez [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="213f2-158"> default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="213f2-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="213f2-159">See Also</span></span>  
 [<span data-ttu-id="213f2-160">Implémentation de contrats de service</span><span class="sxs-lookup"><span data-stu-id="213f2-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
