---
title: Exemple Discovery Binding Element
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b658cc481d3ca5e87b5b9e2aab6b7561be2c65b1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="20ca6-102">Exemple Discovery Binding Element</span><span class="sxs-lookup"><span data-stu-id="20ca6-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="20ca6-103">Cet exemple montre comment utiliser l’élément de liaison du client de découverte pour découvrir un service.</span><span class="sxs-lookup"><span data-stu-id="20ca6-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="20ca6-104">Cette fonctionnalité permet aux développeurs d'ajouter un canal client de découverte à leur pile de canaux clients existante, ce qui rend le modèle de programmation très intuitif.</span><span class="sxs-lookup"><span data-stu-id="20ca6-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="20ca6-105">Lorsque le canal associé est ouvert, l'adresse du service est résolue à l'aide de la découverte.</span><span class="sxs-lookup"><span data-stu-id="20ca6-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="20ca6-106">Cet exemple est composé des projets suivants :</span><span class="sxs-lookup"><span data-stu-id="20ca6-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="20ca6-107">**CalculatorService**: un détectable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span><span class="sxs-lookup"><span data-stu-id="20ca6-107">**CalculatorService**: A discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
-   <span data-ttu-id="20ca6-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application cliente qui utilise le canal client de découverte pour rechercher et appeler le CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="20ca6-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="20ca6-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application cliente qui utilise un point de terminaison dynamique pour rechercher et appeler le CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="20ca6-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20ca6-110">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="20ca6-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20ca6-111">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="20ca6-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="20ca6-112">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="20ca6-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20ca6-113">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="20ca6-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="20ca6-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="20ca6-114">CalculatorService</span></span>  
 <span data-ttu-id="20ca6-115">Ce projet contient un service de calculatrice simple qui implémente le contrat `ICalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="20ca6-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="20ca6-116">Le fichier App.config suivant est utilisé pour ajouter un comportement `<serviceDiscovery>` dans les comportements de service, ainsi que le point de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="20ca6-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="20ca6-117">Le service et ses points de terminaison deviennent ainsi détectables.</span><span class="sxs-lookup"><span data-stu-id="20ca6-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="20ca6-118">Le CalculatorService est un service auto-hébergé qui ajoute un point de terminaison utilisant la liaison NetTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="20ca6-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="20ca6-119">Il ajoute également un `EndpointDiscoveryBehavior` au point de terminaison et spécifie une portée, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="20ca6-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="20ca6-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="20ca6-120">CalculatorClient</span></span>  
 <span data-ttu-id="20ca6-121">Ce projet contient une implémentation cliente qui envoie des messages au CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="20ca6-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="20ca6-122">Ce programme utilise la méthode `CreateCustomBindingWithDiscoveryElement()` pour créer une liaison personnalisée qui utilise le canal client de découverte.</span><span class="sxs-lookup"><span data-stu-id="20ca6-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 <span data-ttu-id="20ca6-123">Une fois le <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> instancié, le développeur spécifie les critères à utiliser lors de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="20ca6-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="20ca6-124">Dans ce cas, le critère de recherche de découverte est le type `ICalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="20ca6-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="20ca6-125">En outre, le développeur spécifie un <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> qui retourne un <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> indiquant où rechercher les services.</span><span class="sxs-lookup"><span data-stu-id="20ca6-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="20ca6-126">Le <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> retourne une nouvelle instance de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="20ca6-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="20ca6-127">[à l’aide d’une liaison personnalisée avec le canal Client de découverte](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="20ca6-127"> [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 <span data-ttu-id="20ca6-128">Dans ce cas, le client utilise le mécanisme de multidiffusion UDP défini par le protocole Discovery pour rechercher des services sur le sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="20ca6-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="20ca6-129">Le reste de la méthode crée une liaison personnalisée et insère l'élément de liaison de découverte en haut de la pile.</span><span class="sxs-lookup"><span data-stu-id="20ca6-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20ca6-130">Le <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> doit être placé en haut de la pile de liaisons.</span><span class="sxs-lookup"><span data-stu-id="20ca6-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="20ca6-131">Tout <xref:System.ServiceModel.Channels.BindingElement> en plus de <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> doit veiller à ce que la fabrique de canaux ou le canal qu'il crée n'utilise pas les propriétés `EndpointAddress` ou `Via`, car l'adresse réelle est recherchée uniquement au niveau du canal client de découverte.</span><span class="sxs-lookup"><span data-stu-id="20ca6-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="20ca6-132">Ensuite, le `CalculatorClient` peut être instancié en passant cette liaison personnalisée, ainsi qu'une adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="20ca6-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="20ca6-133">Lors de l'utilisation du canal client de découverte, l'adresse du point de terminaison constante spécifiée précédemment est passée.</span><span class="sxs-lookup"><span data-stu-id="20ca6-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="20ca6-134">À présent, au moment, de l'exécution, le canal client de découverte recherche le service spécifié par les critères de recherche et s'y connecte.</span><span class="sxs-lookup"><span data-stu-id="20ca6-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="20ca6-135">Pour que le service et le client établissent une connexion, ils doivent également avoir la même pile de liaisons sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="20ca6-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="20ca6-136">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="20ca6-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="20ca6-137">Ouvrez la solution dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20ca6-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="20ca6-138">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="20ca6-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="20ca6-139">Exécutez l'application de service et chacune des applications clientes.</span><span class="sxs-lookup"><span data-stu-id="20ca6-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="20ca6-140">Observez que le client a trouvé le service sans connaître son adresse.</span><span class="sxs-lookup"><span data-stu-id="20ca6-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ca6-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20ca6-141">See Also</span></span>
