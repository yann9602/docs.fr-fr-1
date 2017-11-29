---
title: "Comment : inspecter ou modifier des messages sur le client"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 164e19891e576b6d310839a1221ad8ed0d315444
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="1831f-102">Comment : inspecter ou modifier des messages sur le client</span><span class="sxs-lookup"><span data-stu-id="1831f-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="1831f-103">Vous pouvez inspecter ou modifier les messages entrants ou sortants sur un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en implémentant un <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> et en l'insérant dans l'exécution du client.</span><span class="sxs-lookup"><span data-stu-id="1831f-103">You can inspect or modify the incoming or outgoing messages across a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="1831f-104">Pour plus d’informations, consultez [Clients d’extension](../../../../docs/framework/wcf/extending/extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="1831f-104">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md).</span></span> <span data-ttu-id="1831f-105">La fonctionnalité équivalente sur le service est <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1831f-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1831f-106">Pour obtenir un exemple de code complet, consultez la [inspecteurs de Message](../../../../docs/framework/wcf/samples/message-inspectors.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="1831f-106">For a complete code example see the [Message Inspectors](../../../../docs/framework/wcf/samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="1831f-107">Pour inspecter ou modifier des messages</span><span class="sxs-lookup"><span data-stu-id="1831f-107">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="1831f-108">Implémentez l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1831f-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="1831f-109">Implémentez <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> en fonction de la portée à laquelle vous souhaitez insérer facilement l'inspecteur de message client.</span><span class="sxs-lookup"><span data-stu-id="1831f-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="1831f-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>vous permet de modifier le comportement au niveau du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1831f-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="1831f-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>permet de modifier le comportement au niveau du contrat.</span><span class="sxs-lookup"><span data-stu-id="1831f-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3.  <span data-ttu-id="1831f-112">Insérez le comportement avant d'appeler la méthode <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1831f-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1831f-113">Pour plus d’informations, consultez [configuration et l’extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="1831f-113">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1831f-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="1831f-114">Example</span></span>  
 <span data-ttu-id="1831f-115">Les exemples de code suivants affichent, dans l'ordre :</span><span class="sxs-lookup"><span data-stu-id="1831f-115">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="1831f-116">Une implémentation d'inspecteur client.</span><span class="sxs-lookup"><span data-stu-id="1831f-116">A client inspector implementation.</span></span>  
  
-   <span data-ttu-id="1831f-117">Un comportement de point de terminaison qui insère l'inspecteur.</span><span class="sxs-lookup"><span data-stu-id="1831f-117">An endpoint behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="1831f-118">Classe <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> dérivée qui vous permet d'ajouter le comportement dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1831f-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
-   <span data-ttu-id="1831f-119">Un fichier de configuration qui ajoute le comportement de point de terminaison pour insérer l'inspecteur de message client dans le runtime client.</span><span class="sxs-lookup"><span data-stu-id="1831f-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client   
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they   
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element   
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"   
                      binding="wsHttpBinding"  
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1831f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1831f-120">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="1831f-121">Configuration et extension de l’exécution des comportements</span><span class="sxs-lookup"><span data-stu-id="1831f-121">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
