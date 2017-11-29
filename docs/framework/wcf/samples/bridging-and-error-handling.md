---
title: "Débogage et gestion des erreurs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eec60855dc8ce3c611fa0fe3c8668973b43099b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="bridging-and-error-handling"></a>Débogage et gestion des erreurs
Cet exemple illustre l'utilisation du service de routage [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour établir un pontage de communication entre un client et un service qui utilisent des liaisons différentes. Il montre également comment utiliser un service de sauvegarde pour les scénarios de basculement. Le service de routage est un composant [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui facilite l'inclusion d'un routeur basé sur le contenu dans votre application. Cet exemple adapte l'exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator standard pour communiquer à l'aide du service de routage.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Dans cet exemple, le client Calculator est configuré pour envoyer des messages à un point de terminaison exposé par le routeur. Le service de routage (Routing Service) est configuré de façon à accepter tous les messages qui lui sont envoyés et les transférer à un point de terminaison qui correspond au service Calculator. Les points suivants décrivent la configuration du service Calculator principal, du service Calculator de sauvegarde et du client Calculator, ainsi que la façon dont la communication entre le client et le service s'effectue à l'aide du service de routage :  
  
-   Le client Calculator est configuré pour utiliser BasicHttpBinding, alors que le service Calculator est configuré pour utiliser NetTcpBinding. Au besoin, le service de routage convertit automatiquement les messages avant de les envoyer au service Calculator et convertit également les réponses afin que le client Calculator puisse y accéder.  
  
-   Le service de routage connaît l'existence de deux services Calculator : le service Calculator principal et le service Calculator de sauvegarde. Le service de routage essaie d'abord de communiquer avec le point de terminaison du service Calculator principal. Si cette tentative échoue en raison d'une défaillance du point de terminaison, le service de routage essaie de communiquer avec le point de terminaison du service Calculator de sauvegarde.  
  
 Les messages envoyés à partir du client sont donc reçus par le routeur et reroutés au véritable service Calculator. Si le point de terminaison du service Calculator subit une défaillance, le service de routage route le message vers le point de terminaison du service Calculator de sauvegarde. Les messages du service Calculator de sauvegarde sont renvoyés au routeur du service, qui à son tour les retransmet au client Calculator.  
  
> [!NOTE]
>  Plusieurs points de terminaison peuvent être définis dans une même liste de sauvegarde. Dans ce cas, si le point de terminaison du service de sauvegarde subit une défaillance, le service de routage essaie de se connecter au point de terminaison de sauvegarde suivant dans la liste, jusqu'à ce qu'une connexion puisse être établie.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez RouterBridgingAndErrorHandling.sln.  
  
2.  Appuyez sur F5 ou sur CTRL+MAJ+B dans Visual Studio.  
  
    1.  Si vous souhaitez lancer automatiquement les projets nécessaires lorsque vous appuyez sur F5, cliquez sur la solution, sélectionnez **propriétés**et dans le **projet de démarrage** nœud sous **depropriétéscommunes**, sélectionnez **plusieurs projets de démarrage**et tous les projets **Démarrer**.  
  
    2.  Si vous générez le projet avec CTRL+MAJ+B, vous devez démarrer les applications suivantes :  
  
        1.  Client Calculator (./CalculatorClient/bin/client.exe)  
  
        2.  Service Calculator (./CalculatorService/bin/service.exe)  
  
        3.  Service Routing (./RoutingService/bin/RoutingService.exe)  
  
3.  Dans le client Calculator, appuyez sur ENTRÉE pour démarrer le client.  
  
     Vous devez voir la sortie suivante :  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Configurable au moyen d'un code ou d'un fichier App.config  
 L'exemple est fourni en étant configuré de façon à utiliser un fichier App.config pour définir le comportement du routeur. Vous pouvez également renommer le fichier App.config afin qu'il ne soit pas reconnu et supprimer les marques de commentaire de l'appel de méthode à `ConfigureRouterViaCode()`. Quelle que soit la méthode employée, le comportement de routeur obtenu est le même.  
  
### <a name="scenario"></a>Scénario  
 Cet exemple illustre le routeur du service agissant en tant que pont de protocole et gestionnaire d'erreurs. Dans ce scénario, aucun routage basé sur le contenu n'intervient ; le service de routage fait office de nœud de proxy transparent configuré pour passer les messages directement à un ensemble préconfiguré de points de terminaison de destination. Le service de routage assure aussi la gestion transparente des erreurs qui se produisent lorsqu'il tente d'effectuer des envois vers les points de terminaison avec lesquels il est configuré pour communiquer. En jouant le rôle de pont de protocole, le service de routage permet à l'utilisateur de définir un protocole pour la communication externe et un autre pour la communication interne.  
  
### <a name="real-world-scenario"></a>Scénario réel  
 Contoso souhaite fournir un point de terminaison de service pouvant interagir avec le monde extérieur, tout en optimisant les performances en interne. Il expose donc ses services au monde via un point de terminaison utilisant BasicHttpBinding, et recourt en interne au service de routage pour établir un pont entre cette connexion et le point de terminaison NetTcpBinding qu'utilisent ses services. En outre, Contoso souhaite que son offre de services présente une tolérance aux pannes temporaires dans chacun de ses services de production. À cette fin, il virtualise plusieurs points de terminaison derrière le service de routeur en s'appuyant sur les fonctionnalités de gestion des erreurs pour basculer automatiquement vers les points de terminaison de sauvegarde en cas de nécessité.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
