---
title: Services duplex
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
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08fcb852977272d593229abea426abc8bf9b7e48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="duplex-services"></a>Services duplex
Un contrat de service duplex est un modèle d’échange de messages dans lequel les deux points de terminaison peuvent envoyer indépendamment des messages à l’autre. Un service duplex peut, par conséquent, renvoyer des messages au point de terminaison client, en fournissant un comportement de type événement. La communication duplex se produit lorsqu'un client se connecte à un service et lui fournit un canal sur lequel il peut lui renvoyer des messages. Notez que le comportement de type événement des services duplex ne fonctionne que dans une session.  
  
 Pour créer un contrat duplex, créez une paire d'interfaces. La première est l'interface de contrat de service qui décrit les opérations qu'un client peut appeler. Ce contrat de service doit spécifier un *contrat de rappel* dans le <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriété. Le contrat de rappel est l'interface qui définit les opérations que le service peut appeler sur le point de terminaison client. Un contrat duplex ne requiert pas de session, bien que les liaisons duplex fournies par le système en utilisent.  
  
 Voici un exemple de contrat duplex :  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 La classe `CalculatorService` implémente l'interface `ICalculatorDuplex` principale. Le service utilise le mode d'instance <xref:System.ServiceModel.InstanceContextMode.PerSession> pour conserver le résultat de chaque session. Une propriété privée appelée `Callback` accède au canal de rappel au client. Le service utilise le rappel pour renvoyer des messages au client via l'interface de rappel, comme le montre l'exemple de code suivant.  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 Le client doit fournir une classe qui implémente l'interface de rappel du contrat duplex pour permettre la réception des messages envoyés par le service. L'exemple de code suivant présente une classe `CallbackHandler` qui implémente l'interface `ICalculatorDuplexCallback`.  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 Le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] généré pour un contrat duplex requiert une classe <xref:System.ServiceModel.InstanceContext> à fournir au moment de la construction. Cette classe <xref:System.ServiceModel.InstanceContext> est utilisée comme site pour un objet qui implémente l'interface de rappel et gère les messages renvoyés à partir du service. Une classe <xref:System.ServiceModel.InstanceContext> est construite avec une instance de la classe `CallbackHandler`. Cet objet gère les messages envoyés par le service au client sur l'interface de rappel.  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 La configuration pour le service doit être installée pour fournir une liaison prenant à la fois en charge la communication de session et la communication duplex. L'élément `wsDualHttpBinding` prend en charge la communication de session et permet la communication duplex en fournissant des connexions HTTP doubles, à raison d'une pour chaque direction.  
  
 Sur le client, vous devez configurer une adresse que le serveur peut utiliser afin de s'y connecter, tel qu'indiqué dans l'exemple de configuration suivant.  
  
  
  
> [!NOTE]
>  Les clients non duplex qui ne parviennent pas à s'authentifier à l'aide d'une conversation sécurisée lèvent en général une exception <xref:System.ServiceModel.Security.MessageSecurityException>. Toutefois, si un client duplex qui utilise une conversation sécurisée ne parvient pas à s'authentifier, il reçoit à la place une exception <xref:System.TimeoutException>.  
  
 Si vous créez un client/service à l'aide de l'élément `WSHttpBinding` et que vous n'incluez pas le point de terminaison de rappel client, vous recevrez l'erreur suivante.  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 L'exemple de code suivant indique comment spécifier l'adresse de point de terminaison client dans le code.  
  
```  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
  
 L'exemple de code suivant indique comment spécifier l'adresse de point de terminaison client dans la configuration.  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  Le model duplex ne détecte pas automatiquement si un service ou un client ferme son canal. Par conséquent, si un client se ferme de façon inattendue, par défaut le service n'est pas notifié ; il en est de même pour un client qui se ferme de façon inattendue. Les clients et les services peuvent implémenter leur propre protocole pour se notifier mutuellement s'ils le souhaitent.  
  
## <a name="see-also"></a>Voir aussi  
 [Duplex](../../../../docs/framework/wcf/samples/duplex.md)  
 [Spécification du comportement du client au moment de l’exécution](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [Guide pratique pour créer et utiliser une fabrique de canaux pour créer et gérer des canaux](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
