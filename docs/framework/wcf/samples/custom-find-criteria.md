---
title: Custom Find Criteria
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d49661ff91477f2f53d180a10ae1c9b3b632461f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-find-criteria"></a>Custom Find Criteria
Cet exemple montre comment créer une correspondance de portée personnalisée à l'aide de la logique et comment implémenter un service de découverte personnalisé. Les clients utilisent la fonctionnalité de correspondance de portée personnalisée pour affiner et mieux tirer parti de la fonctionnalité de recherche système de la découverte WCF. Le scénario couvert par cet exemple est le suivant :  
  
1.  Un client recherche un service de calculatrice.  
  
2.  Pour affiner sa recherche, le client doit utiliser une règle de correspondance de portée personnalisée.  
  
3.  D'après cette règle, un service répond au client si son point de terminaison correspond à l'une quelconque des portées spécifiées par le client.  
  
## <a name="demonstrates"></a>Démonstrations  
  
-   Création d'un service de découverte personnalisé  
  
-   Implémentation d'une correspondance de portée personnalisée par algorithme  
  
## <a name="discussion"></a>Discussion  
 Le client recherche de type « Ou » correspondant aux critères. Un service répond si les portées de ses points de terminaison correspondent à l'une des portées fournies par le client. Dans ce cas, le client recherche un service de calculatrice dont la portée figure dans la liste suivante :  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Pour cela, le client indique aux services d'utiliser une règle de correspondance de portée personnalisée en passant une correspondance de portée personnalisée par URI. Pour faciliter la mise en correspondance de portée personnalisée, le service doit utiliser un service de découverte personnalisé qui comprend la règle de correspondance de portée personnalisée et implémente la logique associée.  
  
 Dans le projet client, ouvrez le fichier Program.cs. Notez que le champ `ScopeMatchBy` de l'objet `FindCriteria` a pour valeur un URI spécifique. Cet identificateur est envoyé au service. Si le service ne comprend pas cette règle, il ignore la demande de recherche du client.  
  
 Ouvrez le projet de service. L'implémentation du service de découverte personnalisé utilise trois fichiers :  
  
1.  **AsyncResult.cs**: c’est l’implémentation de la `AsyncResult` qui est requis par les méthodes de découverte.  
  
2.  **CustomDiscoveryService.cs**: ce fichier implémente le service de découverte personnalisé. L'implémentation étend la classe <xref:System.ServiceModel.Discovery.DiscoveryService> et substitue les méthodes nécessaires. Notez l'implémentation de la méthode <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A>. Cette méthode vérifie si la règle de correspondance de portée personnalisée a été spécifiée par le client. Il s'agit de l'URI personnalisé que le client a spécifié précédemment. Si la règle personnalisée est spécifiée, le chemin d’accès du code qui implémente la logique de correspondance « Ou » est suivi.  
  
     Cette logique personnalisée parcourt toutes les portées sur chacun des points de terminaison dont le service dispose. Si l'une des portées du point de terminaison correspond à l'une des portées fournies par le client, le service de découverte ajoute ce point de terminaison à la réponse renvoyée au client.  
  
3.  **CustomDiscoveryExtension.cs**: la dernière étape de l’implémentation du service de découverte consiste à connecter cette implémentation personnalisé détection du service de l’hôte de service. La classe d'assistance utilisée ici est la classe `CustomDiscoveryExtension`. Cette classe étend la classe <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension>. L'utilisateur doit substituer la méthode <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A>. Dans ce cas, la méthode retourne une instance du service de découverte personnalisé créé auparavant. `PublishedEndpoints` est un <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> qui contient tous les points de terminaison d'application qui sont ajoutés à <xref:System.ServiceModel.ServiceHost>. Le service de découverte personnalisé l'utilise pour remplir sa liste interne. Un utilisateur peut aussi ajouter d'autres métadonnées de points de terminaison.  
  
 Enfin, ouvrez Program.cs. Notez que <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> et `CustomDiscoveryExtension` sont tous deux ajoutés à l'hôte. Lorsque cette opération a été effectuée et que l'hôte dispose d'un point de terminaison sur lequel recevoir des messages de découverte, l'application peut utiliser le service de découverte personnalisé.  
  
 Observez que le client peut trouver le service sans connaître son adresse.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez la solution qui contient le projet.  
  
2.  Générez le projet.  
  
3.  Exécutez l'application de service.  
  
4.  Exécutez l'application cliente.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
