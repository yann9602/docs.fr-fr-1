---
title: "Créer des services résilients prêts pour le cloud. Adopter les erreurs temporaires dans le cloud"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Créer des services résilients prêts pour le cloud. Adopter les erreurs temporaires dans le cloud"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aaf1ef968600a56d91267c6c12efa90d99446dd7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Créer des services résilients prêts pour le cloud : adopter les erreurs temporaires dans le cloud 

La résilience est la capacité à surmonter les défaillances et à continuer de fonctionner. Résilience n’est pas sur ce qui évite les échecs, mais accepte le fait que les erreurs se produisent et puis répond leur d’une manière qui évite les temps d’arrêt ou perte de données. La résilience vise à remettre l’application dans un état entièrement fonctionnel après une défaillance.

Votre application est prête pour le cloud quand, au minimum, il implémente un modèle basé sur les logiciels de résilience, plutôt qu’un modèle basé sur le matériel. Votre application de cloud doit adopter les défaillances partielles certainement se produit. Vous devez concevoir ou partiellement refactoriser votre application si vous souhaitez obtenir la résilience aux défaillances partielles attendus. Il doit être conçu pour faire face à des défaillances partielles, telles que les pannes réseau temporaires et des nœuds ou des machines virtuelles en panne dans le cloud. Conteneurs même déplacés vers un autre nœud dans un cluster orchestrator peuvent provoquer l’échec de courte intermittente dans l’application.

## <a name="handling-partial-failure"></a>Gestion des défaillances partielles

Dans une application basée sur le cloud, il existe un risque de permanente de défaillance partielle. Par exemple, une instance unique de site Web ou un conteneur peut échouer, ou il peut être indisponible ou ne répond pas pendant une courte période. Ou bien, un ordinateur virtuel ou un serveur unique peut se bloquer.

Étant donné que les clients et services sont des processus distincts, un service n’est peut-être pas en mesure de répondre en temps voulu pour une demande du client. Le service peut être surchargé et répondre très lentement aux demandes, ou il peut simplement être accessible pour une courte période en raison de problèmes de réseau.

Par exemple, considérez une application .NET monolithique qui accède à une base de données dans la base de données SQL Azure. Si la base de données SQL Azure ou tout autre service tiers ne répond pas pour une brève fois (une base de données SQL Azure peut-être être déplacé vers un autre nœud ou un serveur et ne pas répondre pendant quelques secondes), lorsque l’utilisateur tente d’effectuer aucune action, l’application peut se bloquer et afficher w une exception au même moment.

Un scénario similaire peut se produire dans une application qui consomme des services HTTP. Le réseau ou le service lui-même peut-être pas disponible dans le cloud lors d’une défaillance courte et temporaire.

Une application résistante comme celui illustré dans la Figure 4-9 doit implémenter des techniques telles que « nouvelles tentatives avec interruption exponentielle » pour donner la possibilité de gérer les défaillances temporaires dans les ressources de l’application. Vous devez également utiliser « disjoncteurs » dans vos applications. Un disjoncteur arrête une application à partir de la tentative d’accès à une ressource lorsqu’il est réellement une défaillance. En utilisant un disjoncteur, l’application évite de provoquer un déni de service à lui-même.

![Défaillances partielles gérées par les nouvelles tentatives avec interruption exponentielle](./media/image9.png)

> **Figure 4-9.** Défaillances partielles gérées par les nouvelles tentatives avec interruption exponentielle

Vous pouvez utiliser ces techniques pour les ressources HTTP et les ressources de base de données. Dans la Figure 4-9, l’application est basée sur une architecture à 3 couches, vous avez besoin de ces techniques au niveau des services (HTTP) et au niveau de la couche données (TCP). Dans une application monolithique qui utilise uniquement un niveau d’application unique en plus de la base de données (aucun des services supplémentaires ou microservices), la gestion des erreurs temporaires au niveau de la connexion de base de données peuvent être suffisant. Dans ce scénario, généralement simplement une configuration particulière de la connexion de base de données est requise.

Lors de l’implémentation des communications souples qui accèdent à la base de données, selon la version de .NET que vous utilisez, il peut être très simple (par exemple, [avec Entity Framework 6 ou version ultérieure](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), il vous suffit de la configuration de la connexion de base de données). Ou bien, vous devrez peut-être utiliser des bibliothèques supplémentaires, comme le [bloc applicatif de pannes gestion](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (pour les versions antérieures de .NET), ou même implémenter votre propre bibliothèque.

Lors de l’implémentation de tentatives HTTP et les disjoncteurs, la recommandation pour .NET consiste à utiliser le [Polly](https://github.com/App-vNext/Polly) bibliothèque qui cible le .NET 4.0, .NET 4.5 et .NET 1.1 Standard, qui inclut la prise en charge .NET Core.

Pour savoir comment implémenter des stratégies pour gérer les défaillances partielles dans le cloud, consultez les références suivantes.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Implémentation de la communication résiliente pour gérer une défaillance partielle**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies)

-   **Entity Framework résilience et nouvelle tentative logique de connexion (version 6 et versions ultérieure)**

    [https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)

-   **Le bloc d’Application de gestion d’erreurs transitoires**

<!-- -->

-   [https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)

-   **Bibliothèque Polly pour les communications HTTP résiliente**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
[Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Suivant](modernize-your-apps-with-monitoring-and-telemetry.md)
