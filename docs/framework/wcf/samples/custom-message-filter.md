---
title: Custom Message Filter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bf8950ae023d60222ccd843035b5fb808de39c84
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-message-filter"></a>Custom Message Filter
Cet exemple montre comment remplacer les filtres de message permettant à [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de distribuer des messages aux points de terminaison.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Lorsque le premier message sur un canal arrive au niveau du serveur, ce dernier doit déterminer le point de terminaison (le cas échéant) associé à cet URI qui doit recevoir le message. Ce processus est contrôlé par les objets <xref:System.ServiceModel.Dispatcher.MessageFilter> joints à <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Chaque point de terminaison d'un service a un <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> unique. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> possède à la fois <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> et <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. L'association de ces deux filtres forme le filtre de messages utilisé pour ce point de terminaison.  
  
 Par défaut, le <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> d'un point de terminaison correspond aux messages envoyés à une adresse qui correspond au <xref:System.ServiceModel.EndpointAddress> du point de terminaison de service. Par défaut, le <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> pour un point de terminaison inspecte l’action du message entrant et correspond à un message avec une action qui correspond à l’une des actions des opérations du contrat de point de terminaison service (uniquement `IsInitiating` = `true`actions sont pris en compte). Par défaut, le filtre d'un point de terminaison correspond donc uniquement si l'en-tête To du message est le <xref:System.ServiceModel.EndpointAddress> du point de terminaison et que l'action du message correspond à l'une des actions de l'opération de point de terminaison.  
  
 Ces filtres peuvent être modifiés à l'aide d'un comportement. Dans l'exemple, le service crée un <xref:System.ServiceModel.Description.IEndpointBehavior> qui remplace <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> et <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> sur <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 Deux filtres d'adresse sont définis :  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 `FilteringEndpointBehavior` est rendu configurable et accepte deux variantes différentes.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 La variante 1 correspond uniquement aux adresses qui contiennent un 'e' (mais qui comportent des actions), tandis que la variante 2 correspond uniquement aux adresses sans 'e' :  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 Dans le fichier de configuration, le service enregistre le nouveau comportement :  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 Il crée ensuite des configurations `endpointBehavior` pour chaque variante :  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 Enfin, le point de terminaison du service référence l'un des `behaviorConfigurations` :  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 L'implémentation de l'application cliente est simple : elle crée deux canaux à l'URI du service (en passant cette valeur comme deuxième paramètre (`via`) à <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29>) et envoie un message unique sur chaque canal, mais utilise des adresses de point de terminaison différentes pour chacun d'entre eux. Par conséquent, les messages sortants provenant du client ont des désignations To différentes, et le serveur réagit en conséquence, tel qu'indiqué par la sortie du client :  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Le passage d'une variante à une autre dans le fichier de configuration du serveur provoque la permutation du filtre et l'activation du comportement opposé sur le client (le message à `urn:e` réussit, alors que le message à `urn:a` échoue).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Pour exécuter l’exemple dans une configuration de machine unique, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à plusieurs ordinateurs, suivez les instructions à [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) et modifiez la ligne suivante dans Client.cs.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Remplacez localhost par le nom du serveur.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a>Voir aussi
