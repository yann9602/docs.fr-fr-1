---
title: Reconfiguration dynamique
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbf286891211da0e35274ff59f3bee69ebf3c9bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dynamic-reconfiguration"></a>Reconfiguration dynamique
Cet exemple illustre le service de routage [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Le service de routage est un composant [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui facilite l'inclusion d'un routeur basé sur le contenu dans votre application. Cet exemple adapte l'exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator standard pour communiquer à l'aide du service de routage. Il montre comment le service de routage peut être reconfiguré dynamiquement pendant l'exécution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Pour reconfigurer dynamiquement le service de routage (Routing Service) pendant l'exécution, cet exemple déclenche toutes les cinq secondes un minuteur qui crée un objet <xref:System.ServiceModel.Routing.RoutingConfiguration> et l'applique. Cette configuration fait référence au point de terminaison soit Regular Calculator, soit Rounding Calculator. Les messages retournés à l'application Calculator Client proviennent de l'un ou l'autre de ces services, selon le service de routage configuré pour assurer le routage à ce moment-là.  
  
 Il est fait appel à la capacité de reconfiguration dynamique du service de routage via un comportement personnalisé. Ce comportement personnalisé joint une extension de service contenant un simple minuteur de thread qui se déclenche toutes les cinq secondes, ce qui aboutit à un rappel à la méthode `UpdateRules`. Ce rappel crée et applique la nouvelle configuration de routage. Dans un déploiement réel, ce rappel interviendrait probablement suite à un autre type d'événement, comme une notification d'événements SQL ou une annonce WS-Discovery.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez DynamicReconfiguration.sln.  
  
2.  Pour ouvrir **l’Explorateur de solutions**, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.  
  
3.  Appuyez sur **F5** ou **CTRL + MAJ + B** dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Si vous souhaitez lancer automatiquement les projets nécessaires lorsque vous appuyez sur **F5**, avec le bouton droit de la solution et sélectionnez **propriétés**. Sélectionnez le **projet de démarrage** nœud sous **propriétés communes** dans le volet gauche. Sélectionnez le **plusieurs projets de démarrage** case d’option et tous les projets d’avoir défini la **Démarrer** action.  
  
    2.  Si vous générez le projet avec **CTRL + MAJ + B**, vous devez démarrer les applications suivantes :  
  
        1.  Client Calculator (./CalculatorClient/bin/client.exe)  
  
        2.  Service Calculator (./CalculatorService/bin/service.exe)  
  
        3.  Service Rounding Calculator (./RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (./RoutingService/bin/RoutingService.exe)  
  
4.  Dans la fenêtre de console du client Calculator, appuyez sur ENTRÉE pour démarrer le client et appeler les opérations du service Calculator.  
  
     Le service de routage route dynamiquement des messages en alternant entre Rounding Calculator et Regular Calculator, étant donné que la configuration du routage change de configuration de façon dynamique toutes les cinq secondes. Les sorties fournies dans la fenêtre de console du client diffèrent donc en fonction du point de terminaison auquel le service de routage envoie les messages.  
  
5.  Appuyez sur ENTRÉE à plusieurs reprises pendant plus de cinq secondes et observez la modification dans les résultats du service.  
  
    1.  Voici la sortie retournée si le service de routage est configuré pour router les messages vers le service Rounding Calculator.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Voici la sortie retournée si le service de routage est configuré pour router les messages vers le service Regular Calculator.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  Le service Calculator et le service Rounding Calculator génèrent également un journal des opérations appelé dans leur fenêtre de console.  
  
7.  Dans la fenêtre de console client, tapez « quitter » et appuyez sur ENTRÉE pour quitter.  
  
8.  Appuyez sur ENTRÉE dans les fenêtres de console des services pour les arrêter.  
  
## <a name="scenario"></a>Scénario  
 Cet exemple illustre l'utilisation du routeur en tant que routeur basé sur le contenu qui autorise l'exposition via un même point de terminaison de plusieurs types ou implémentations de services.  
  
### <a name="real-world-scenario"></a>Scénario réel  
 Contoso souhaite virtualiser tous ses services afin de n'exposer publiquement qu'un seul point de terminaison via lequel donner accès à différents types de services. Dans ce cas, la société utilise les fonctions de routage basé sur le contenu du service de routage afin de déterminer l'endroit où doivent être envoyées les demandes entrantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
