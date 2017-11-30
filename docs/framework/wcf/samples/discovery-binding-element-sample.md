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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 821f629a7f39869975af19c793fe26188a40d7d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-binding-element-sample"></a>Exemple Discovery Binding Element
Cet exemple montre comment utiliser l’élément de liaison du client de découverte pour découvrir un service. Cette fonctionnalité permet aux développeurs d'ajouter un canal client de découverte à leur pile de canaux clients existante, ce qui rend le modèle de programmation très intuitif. Lorsque le canal associé est ouvert, l'adresse du service est résolue à l'aide de la découverte. Cet exemple est composé des projets suivants :  
  
-   **CalculatorService**: un détectable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.  
  
-   **CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application cliente qui utilise le canal client de découverte pour rechercher et appeler le CalculatorService.  
  
-   **DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application cliente qui utilise un point de terminaison dynamique pour rechercher et appeler le CalculatorService.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 Ce projet contient un service de calculatrice simple qui implémente le contrat `ICalculatorService`.  
  
 Le fichier App.config suivant est utilisé pour ajouter un comportement `<serviceDiscovery>` dans les comportements de service, ainsi que le point de terminaison de découverte.  
  
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
  
 Le service et ses points de terminaison deviennent ainsi détectables. Le CalculatorService est un service auto-hébergé qui ajoute un point de terminaison utilisant la liaison NetTcpBinding. Il ajoute également un `EndpointDiscoveryBehavior` au point de terminaison et spécifie une portée, comme le montre le code suivant.  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 Ce projet contient une implémentation cliente qui envoie des messages au CalculatorService. Ce programme utilise la méthode `CreateCustomBindingWithDiscoveryElement()` pour créer une liaison personnalisée qui utilise le canal client de découverte.  
  
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
  
 Une fois le <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> instancié, le développeur spécifie les critères à utiliser lors de la recherche d'un service. Dans ce cas, le critère de recherche de découverte est le type `ICalculatorService`. En outre, le développeur spécifie un <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> qui retourne un <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> indiquant où rechercher les services. Le <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> retourne une nouvelle instance de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][à l’aide d’une liaison personnalisée avec le canal Client de découverte](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).  
  
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
  
 Dans ce cas, le client utilise le mécanisme de multidiffusion UDP défini par le protocole Discovery pour rechercher des services sur le sous-réseau local. Le reste de la méthode crée une liaison personnalisée et insère l'élément de liaison de découverte en haut de la pile.  
  
> [!NOTE]
>  Le <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> doit être placé en haut de la pile de liaisons. Tout <xref:System.ServiceModel.Channels.BindingElement> en plus de <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> doit veiller à ce que la fabrique de canaux ou le canal qu'il crée n'utilise pas les propriétés `EndpointAddress` ou `Via`, car l'adresse réelle est recherchée uniquement au niveau du canal client de découverte.  
  
 Ensuite, le `CalculatorClient` peut être instancié en passant cette liaison personnalisée, ainsi qu'une adresse de point de terminaison.  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 Lors de l'utilisation du canal client de découverte, l'adresse du point de terminaison constante spécifiée précédemment est passée. À présent, au moment, de l'exécution, le canal client de découverte recherche le service spécifié par les critères de recherche et s'y connecte. Pour que le service et le client établissent une connexion, ils doivent également avoir la même pile de liaisons sous-jacente.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Générez la solution.  
  
3.  Exécutez l'application de service et chacune des applications clientes.  
  
4.  Observez que le client a trouvé le service sans connaître son adresse.  
  
## <a name="see-also"></a>Voir aussi
