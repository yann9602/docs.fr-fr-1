---
title: Hello World avec le service de routage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a03f3eeab6ce30c011a6f67c64cc3997130c895
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="hello-world-with-the-routing-service"></a>Hello World avec le service de routage
Cet exemple illustre le service de routage [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Le service de routage est un composant [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui facilite l'inclusion d'un routeur basé sur le contenu dans votre application. Cet exemple adapte l'exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator standard pour communiquer à l'aide du service de routage. Dans cet exemple, le client Calculator est configuré pour envoyer des messages à un point de terminaison exposé par le routeur. Le service de routage (Routing Service) est configuré de façon à accepter tous les messages qui lui sont envoyés et les transférer à un point de terminaison qui correspond au service Calculator. Les messages envoyés à partir du client sont donc reçus par le routeur et reroutés au véritable service Calculator. Les messages du service Calculator sont renvoyés au routeur, qui à son tour les retransmet au client Calculator.  
  
### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez HelloRoutingService.sln.  
  
2.  Appuyez sur F5 ou CTRL+MAJ+B.  
  
    > [!NOTE]
    >  Si vous appuyez sur F5, le client Calculator démarre automatiquement. Si vous appuyez sur CTRL+MAJ+B (génération), vous devez démarrer vous-même les applications suivantes.  
    >   
    >  1.  Client Calculator (./CalculatorClient/bin/client.exe)  
    > 2.  Service Calculator (./CalculatorService/bin/service.exe)  
    > 3.  Routing service (./RoutingService/bin/RoutingService.exe)  
  
3.  Appuyez sur ENTRÉE pour démarrer le client.  
  
     Vous devez voir la sortie suivante :  
  
     Add(100,15.99) = 115.99  
  
     Subtract(145,76.54) = 68.46  
  
     Multiply(9,81.25) = 731.25  
  
     Divide(22,7) = 3.14285714285714  
  
## <a name="configurable-via-code-or-appconfig"></a>Configurable au moyen d'un code ou d'un fichier App.config  
 L'exemple est fourni en étant configuré de façon à utiliser un fichier App.config pour définir le comportement du routeur. Vous pouvez également renommer le fichier App.config afin qu'il ne soit pas reconnu et supprimer les marques de commentaire de l'appel de méthode à ConfigureRouterViaCode(). Quelle que soit la méthode employée, le comportement de routeur obtenu est le même.  
  
### <a name="scenario"></a>Scénario  
 Cet exemple illustre l'utilisation du routeur en tant que pompe de messages de base. Le service de routage fait office de nœud de proxy transparent configuré pour passer les messages directement à un ensemble préconfiguré de points de terminaison de destination.  
  
### <a name="real-world-scenario"></a>Scénario réel  
 Contoso souhaite augmenter la flexibilité en matière d'affectation de noms, d'adressage, de configuration et de sécurité de ses services. Pour ce faire, la société place une pompe de messages de base devant ses services, qui fera office de point de terminaison face au public. Cela lui permet de renforcer la sécurité devant ses véritables services et de simplifier l'implémentation de solutions à montée en puissance parallèle ou du contrôle des versions du service à une date ultérieure.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
