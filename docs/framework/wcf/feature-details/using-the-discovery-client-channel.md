---
title: "Utilisation du canal client de découverte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d0aede489c6b5db029a9df37f84d0a067bbf836
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-discovery-client-channel"></a>Utilisation du canal client de découverte
Lors de l'écriture d'une application cliente WCF vous devez connaître l'adresse du point de terminaison du service que vous appelez. Dans de nombreux cas, l'adresse du point de terminaison d'un service n'est pas connue à l'avance ou bien l'adresse du service change avec le temps. Le canal client de découverte vous permet d'écrire une application cliente WCF, de décrire le service que vous souhaitez appeler, et le canal client envoie automatiquement une demande de sonde. Lorsqu'un service répond, le canal client de découverte extrait de la réponse de sonde l'adresse du point de terminaison du service et l'utilise pour appeler le service.  
  
## <a name="using-the-discovery-client-channel"></a>Utilisation du canal client de découverte  
 Pour utiliser le canal client de découverte, ajoutez une instance de <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> à la pile des canaux de votre client. Vous pouvez également utiliser l'objet <xref:System.ServiceModel.Discovery.DynamicEndpoint> et un élément <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> est automatiquement ajouté à votre liaison, s'il n'est pas déjà présent.  
  
> [!CAUTION]
>  Il est recommandé de placer <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> au niveau supérieur sur votre pile des canaux clients. Tout élément de liaison ajouté par-dessus <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> doit s'assurer que l'objet <xref:System.ServiceModel.ChannelFactory>, ou le canal qu'il crée, n'utilise pas l'adresse du point de terminaison ni l'adresse `Via` (transmise à la méthode `CreateChannel`). Elles risquent en effet de ne pas contenir d'adresse correcte.  
  
 La classe <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> contient deux propriétés publiques :  
  
1.  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, utilisée pour décrire le service que vous souhaitez appeler.  
  
2.  <!--zz <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpoint%2A>  --> `DiscoveryEndpoint`, which specifies the discovery endpoint to send discovery messages to.  
  
 La propriété <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A> vous permet de spécifier le contrat de service que vous recherchez, un URI d'étendue requis et la durée maximale de tentative d'ouverture du canal. Le type de contrat est spécifié en appelant le constructeur <<!--zz <xref:System.ServiceModel.Discovery.FindCriteria%2A>  --> `FindCriteria`>. Des URI d'étendue peuvent être ajoutés à la propriété <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A>. La propriété <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> vous permet de spécifier le nombre maximal de résultats auxquels le client essaie de se connecter. Lorsqu'une réponse de sonde est reçue, le client tente d'ouvrir le canal à l'aide de l'adresse du point de terminaison de la réponse de sonde. Si une exception se produit, le client passe à la réponse de sonde suivante, en attendant que davantage de réponses soit reçues, si nécessaire. Il continue à procéder ainsi jusqu'à ce que le canal s'ouvre avec succès ou que le nombre maximal de résultats soit atteint. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ces paramètres, consultez <<!--zz <xref:System.ServiceModel.Discovery.FindCriteria%2A>  --> `FindCriteria`>.  
  
 Le <!--zz <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpoint%2A>  --> `DiscoveryEndpoint%2A>` propriété vous permet de spécifier le point de terminaison de découverte à utiliser. Normalement, c'est un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, mais il peut s'agir de tout point de terminaison valide.  
  
 Lorsque vous créez la liaison à utiliser pour communiquer avec le service, vous devez veiller à utiliser exactement la même liaison que le service. La seule différence est que la liaison cliente a un <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> sur le haut de la pile. Si le service utilise l'une des liaisons fournies par le système, créez un <xref:System.ServiceModel.Channels.CustomBinding> et passez la liaison fournie par le système au constructeur <!--zz <xref:System.ServiceModel.CustomBinding.CustomBinding%2A> `CustomBinding` -->. Vous pouvez ensuite ajouter le <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> en appelant `Insert` sur la <!--zz <xref:System.ServiceModel.Channels.Binding.Elements%2A> --> `Elements` propriété.  
  
 Une fois que vous avez ajouté le <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> à votre liaison et que vous l'avez configuré, vous pouvez créer une instance de la classe de client WCF, l'ouvrir et appeler ses méthodes. L'exemple suivant utilise le canal client de découverte pour découvrir un service WCF qui implémente la classe `ICalculator` (utilisée dans le didacticiel de mise en route de WCF) et appelle sa méthode `Add`.  
  
```  
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the   
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a>La sécurité et le canal client de découverte  
 Lors de l'utilisation du canal client de découverte, deux points de terminaison sont spécifiés. L'un, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> habituellement, est utilisé pour les messages de découverte et l'autre est le point de terminaison d'application. Lors de l'implémentation d'un service sécurisé, il faut veiller à sécuriser les deux points de terminaison. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]la sécurité, consultez [sécurisation des Services et les Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
