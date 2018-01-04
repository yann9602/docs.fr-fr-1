---
title: "Filtres avancés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 357b57bb39ca31b48d21cb83209a72d0b3d12a62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-filters"></a>Filtres avancés
Cet exemple illustre un service de routage [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Le service de routage est un composant [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui facilite l'inclusion d'un routeur basé sur le contenu dans votre application. Cet exemple adapte l'exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator standard pour communiquer à l'aide du service de routage. Il montre comment définir une logique de routage basé sur le contenu via l'utilisation de filtres de messages et de tables de filtres de messages.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Le tableau suivant présente les filtres de messages qui sont ajoutés à la table de filtres de messages du service de routage.  
  
|Filtre|Règle|Priorité|  
|------------|----------|--------------|  
|If (has header) [contient un en-tête]|Arrondi|2|  
|If (showed up on Ep2) [apparu sur Ep2]|Normale|1|  
|If (showed up with Address2) [apparu avec Address2]|Arrondi|1|  
|If (RoundRobin1)|Normale|0|  
|If (RoundRobin2)|Arrondi|0|  
  
 Les filtres de messages et tables de filtres de messages peuvent être créés et configurés au moyen d'un code ou dans le fichier de configuration de l'application. Pour cet exemple, vous trouverez les filtres de messages et tables de filtres de messages définis au moyen d'un code dans le fichier RoutingService\routing.cs ou définis dans le fichier de configuration de l'application dans le fichier RoutingService\App.config. Les paragraphes suivants expliquent comment les filtres de messages et tables de filtres de messages sont créés pour cet exemple au moyen d'un code.  
  
 En premier lieu, un <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> recherche l'en-tête personnalisé. Notez que <xref:System.ServiceModel.WSHttpBinding> aboutit à une version d'enveloppe utilisant SOAP 1.2, de sorte que l'instruction XPath est définie pour utiliser l'espace de noms SOAP 1.2. Le gestionnaire d'espaces de noms par défaut pour les filtres <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> définit déjà un préfixe pour l'espace de noms SOAP 1.2, /s12, qui peut être utilisé. Toutefois, le gestionnaire d'espaces de noms par défaut ne possède pas l'espace de noms personnalisé que le client utilise pour définir la valeur d'en-tête réelle, aussi le préfixe doit-il être défini. Tout message qui apparaît avec cet en-tête constitue une correspondance pour ce filtre.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 Le deuxième filtre est un <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, qui accepte comme correspondance tout message ayant été reçu sur le `calculatorEndpoint`. Le nom du point de terminaison est défini au moment de la création d'un objet de point de terminaison de service.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 Le troisième filtre est un <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. Il accepte comme correspondance tout message apparu sur un point de terminaison avec une adresse qui correspond au préfixe (ou première partie) d'adresse fourni. Dans cet exemple, le préfixe d'adresse défini est "http://localhost/routingservice/router/rounding/". Cela signifie que ce filtre établit une correspondance avec tous les messages entrants adressés à "http://localhost/routingservice/router/rounding/*". Dans ce cas, il s'agit des messages qui apparaissent sur le point de terminaison Rounding Calculator, dont l'adresse est "http://localhost/routingservice/router/rounding/calculator".  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Les deux derniers filtres de messages sont <xref:System.ServiceModel.Dispatcher.MessageFilter> personnalisés. Dans cet exemple, un filtre de messages « RoundRobin » est utilisé. Ce filtre de messages est créé dans le fichier RoutingService\RoundRobinMessageFilter.cs fourni. Ces filtres, lorsqu'ils sont définis sur le même groupe, signalent alternativement qu'ils acceptent et n'acceptent pas le message comme une correspondance, de sorte qu'un seul d'entre eux à la fois répond `true`.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Ensuite, tous ces messages sont ajoutés à un <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. Pour cela, des priorités sont établies afin d'influencer l'ordre dans lequel la table de filtres de messages exécute les filtres. Plus la priorité est élevée, plus le filtre est exécuté tôt ; plus la priorité est faible, plus le filtre est exécuté tard. Un filtre de priorité 2 s'exécute donc avant un filtre de priorité 1. Si aucun niveau de priorité n'est spécifié, le niveau par défaut, 0, est appliqué. Une table de filtres de messages exécute tous les filtres d'un niveau de priorité donné avant de traiter le niveau de priorité inférieur suivant. Si une correspondance est trouvée à une priorité particulière, la table de filtres de messages cesse de rechercher des correspondances au niveau de priorité inférieur.  
  
> [!NOTE]
>  Si cet exemple indique comment utiliser des priorités de filtres de messages, il est généralement plus efficace et conforme aux bonnes pratiques de conception de concevoir et configurer vos filtres de sorte qu'ils ne nécessitent pas de priorités pour fonctionner correctement.  
  
 Le premier filtre à ajouter est XPath, avec une priorité 2. C'est le premier filtre de messages qui s'exécute. S'il trouve l'en-tête personnalisé, quels que soient les résultats que produiraient les autres filtres, le message est routé vers le point de terminaison Rounding Calculator.  
  
 Au niveau de priorité 1, deux filtres sont ajoutés. Là encore, ceux-ci ne s'exécutent que si le filtre XPath de priorité 2 ne trouve pas de message correspondant. Ces deux filtres montrent deux façons différentes de déterminer où le message a été adressé lorsqu'il est apparu. Étant donné que ces deux filtres vérifient en réalité si le message est arrivé à l'un des deux points de terminaison, ils peuvent être exécutés au même niveau de priorité, car ils ne retournent pas la valeur `true` tous les deux en même temps.  
  
 Enfin, au niveau de priorité 0 (priorité la plus faible), exécutez les filtres de messages RoundRobin. Étant donné que les filtres sont configurés avec le même nom de groupe, un seul d'entre eux à la fois recherche des correspondances. Comme tous les messages avec l'en-tête personnalisé ont été routés et adressés aux points de terminaison virtualisés spécifiques, les messages gérés par les filtres de messages RoundRobin sont uniquement ceux qui ont été adressés au point de terminaison de routeur par défaut (Default Router), sans l'en-tête personnalisé. Étant donné que ces messages déclenchent un message pour chaque appel, la moitié des opérations va au point de terminaison Regular Calculator et l'autre moitié au point de terminaison Rounding Calculator.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez AdvancedFilters.sln.  
  
2.  Pour ouvrir **l’Explorateur de solutions**, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.  
  
3.  Appuyez sur F5 ou CTRL+MAJ+B dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Si vous souhaitez lancer automatiquement les projets nécessaires lorsque vous appuyez sur F5, cliquez sur la solution et sélectionnez **propriétés**. Sélectionnez le **projet de démarrage** nœud sous **propriétés communes** dans le volet gauche. Sélectionnez le **plusieurs projets de démarrage** case d’option et tous les projets d’avoir défini la **Démarrer** action.  
  
    2.  Si vous générez le projet avec CTRL+MAJ+B, vous devez démarrer les applications suivantes :  
  
        1.  Client Calculator (./CalculatorClient/bin/client.exe)  
  
        2.  Service Calculator (./CalculatorService/bin/service.exe)  
  
        3.  Service Rounding Calculator (./RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (./RoutingService/bin/RoutingService.exe)  
  
4.  Dans la fenêtre de console du client Calculator, appuyez sur ENTRÉE pour démarrer le client. Le client retourne la liste des points de terminaison de destination possibles.  
  
5.  Choisissez un point de terminaison de destination en tapant la lettre qui lui est associée et appuyez sur ENTRÉE.  
  
6.  Ensuite, le client vous demande si vous souhaitez ajouter un en-tête personnalisé. Appuyez sur Y pour Oui ou N pour Non, puis sur ENTRÉE.  
  
7.  La sortie visible dépend des sélections que vous avez effectuées.  
  
    1.  Voici la sortie retournée si vous avez ajouté un en-tête personnalisé aux messages.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Voici la sortie retournée si vous avez choisi le point de terminaison Rounding Calculator sans en-tête personnalisé.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  Voici la sortie retournée si vous avez choisi le point de terminaison Regular Calculator sans en-tête personnalisé.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  Voici la sortie retournée si vous avez choisi le point de terminaison Default Router sans en-tête personnalisé.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  Le service Calculator et le service Rounding Calculator génèrent également un journal des opérations appelé dans leur fenêtre de console.  
  
9. Dans la fenêtre de console client, tapez `quit` et appuyez sur ENTRÉE pour quitter.  
  
10. Appuyez sur ENTRÉE dans les fenêtres de console des services pour les arrêter.  
  
## <a name="configurable-via-code-or-appconfig"></a>Configurable au moyen d'un code ou d'un fichier App.config  
 L'exemple est fourni en étant configuré de façon à utiliser un fichier App.config pour définir le comportement du routeur. Vous pouvez également renommer le fichier RoutingService\App.config afin qu'il ne soit pas reconnu et supprimer les marques de commentaire de l'appel de méthode à `ConfigureRouterViaCode()` dans RoutingService\routing.cs. Quelle que soit la méthode employée, le comportement de routeur obtenu est le même.  
  
### <a name="scenario"></a>Scénario  
 Cet exemple illustre l'utilisation du routeur en tant que routeur basé sur le contenu qui autorise l'exposition via un même point de terminaison de plusieurs types ou implémentations de services.  
  
### <a name="real-world-scenario"></a>Scénario réel  
 Contoso souhaite virtualiser tous ses services afin de n'exposer publiquement qu'un seul point de terminaison via lequel donner accès à différents types de services. Dans ce cas, la société utilise les fonctions de routage basé sur le contenu du service de routage afin de déterminer l'endroit où doivent être envoyées les demandes entrantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
