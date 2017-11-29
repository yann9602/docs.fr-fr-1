---
title: "Utilisation d’une liaison personnalisée avec le canal client de découverte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 716dc09d38c778c49a1e2e5fa094ef1bf004eb46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="2db27-102">Utilisation d’une liaison personnalisée avec le canal client de découverte</span><span class="sxs-lookup"><span data-stu-id="2db27-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="2db27-103">Lorsque vous utilisez une liaison personnalisée avec l'élément <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, vous devez définir un objet <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> qui crée des instances <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="2db27-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="2db27-104">Création d'un DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="2db27-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="2db27-105">Le <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> est responsable de la création de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances à la demande.</span><span class="sxs-lookup"><span data-stu-id="2db27-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="2db27-106">Pour définir un fournisseur de points de terminaison de découverte, dérivez une classe à partir de <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, substituez la méthode <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> et retournez un nouveau point de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="2db27-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="2db27-107">L'exemple suivant indique comment créer un fournisseur de points de terminaison de découverte.</span><span class="sxs-lookup"><span data-stu-id="2db27-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="2db27-108">Une fois que vous avez défini le fournisseur de points de terminaison de découverte, vous pouvez créer une liaison personnalisée et ajouter l'objet <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, qui référence le fournisseur de points de terminaison de découverte, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2db27-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
```  
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2db27-109">utilisation du canal client de découverte, consultez [à l’aide du canal Client de découverte](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="2db27-109"> using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> <span data-ttu-id="2db27-110">Pour obtenir un exemple de code complet, consultez [exemple Discovery Binding Element](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span><span class="sxs-lookup"><span data-stu-id="2db27-110">For a complete code example, see [Discovery Binding Element Sample](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db27-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2db27-111">See Also</span></span>  
 [<span data-ttu-id="2db27-112">Vue d’ensemble de la découverte WCF</span><span class="sxs-lookup"><span data-stu-id="2db27-112">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="2db27-113">Utilisation du canal Client de découverte</span><span class="sxs-lookup"><span data-stu-id="2db27-113">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [<span data-ttu-id="2db27-114">Exemple Discovery Binding Element</span><span class="sxs-lookup"><span data-stu-id="2db27-114">Discovery Binding Element Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
