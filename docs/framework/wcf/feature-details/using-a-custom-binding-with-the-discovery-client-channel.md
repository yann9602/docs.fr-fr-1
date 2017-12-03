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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c18be6868c2b0d092d1924b227b444b8b679a383
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Utilisation d’une liaison personnalisée avec le canal client de découverte
Lorsque vous utilisez une liaison personnalisée avec l'élément <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, vous devez définir un objet <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> qui crée des instances <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Création d'un DiscoveryEndpointProvider  
 Le <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> est responsable de la création de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances à la demande. Pour définir un fournisseur de points de terminaison de découverte, dérivez une classe à partir de <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, substituez la méthode <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> et retournez un nouveau point de terminaison de découverte. L'exemple suivant indique comment créer un fournisseur de points de terminaison de découverte.  
  
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
  
 Une fois que vous avez défini le fournisseur de points de terminaison de découverte, vous pouvez créer une liaison personnalisée et ajouter l'objet <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, qui référence le fournisseur de points de terminaison de découverte, comme indiqué dans l'exemple suivant.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]utilisation du canal client de découverte, consultez [à l’aide du canal Client de découverte](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). Pour obtenir un exemple de code complet, consultez [exemple Discovery Binding Element](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la découverte WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Utilisation du canal Client de découverte](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Exemple Discovery Binding Element](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
