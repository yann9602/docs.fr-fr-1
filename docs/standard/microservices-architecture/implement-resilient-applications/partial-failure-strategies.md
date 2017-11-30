---
title: "Stratégies de gestion des défaillances partielles"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Stratégies de gestion des défaillances partielles"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ff3bed530b13a9b1822c7cccf5a4d47df6fc6239
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="strategies-for-handling-partial-failure"></a>Stratégies de gestion des défaillances partielles

Stratégies pour gérer les défaillances partielles sont les suivantes.

**Utiliser la communication asynchrone (par exemple, la communication basée sur message) sur microservices interne**. Il est vivement conseillé ne pas de créer des longues chaînes d’appels HTTP synchrones entre la microservices interne, car cette conception incorrecte cesser la cause principale des pannes incorrects. Au contraire, à l’exception des communications entre les applications clientes et de premier niveau de microservices ou des passerelles API affinée frontales, il est recommandé d’utiliser uniquement (basée sur le message) communication asynchrone qu’une seule fois après la demande initiale / cycle de réponse, entre le microservices interne. Cohérence éventuelle et les architectures de pilotée par événements permettent de réduire les répercussions. Ces approches appliquent un niveau plus élevé d’autonomie de microservice et par conséquent éviter le problème indiqué ici.

**Utiliser les nouvelles tentatives avec interruption exponentielle**. Cette technique permet d’éviter un court et échecs intermittents en effectuant l’appel de tentatives d’un certain nombre de fois, au cas où le service n’était pas disponible uniquement pour une courte période. Cela peut se produire en raison de problèmes réseau intermittents ou lorsqu’un microservice/conteneur est déplacé vers un autre nœud dans un cluster. Toutefois, si ces nouvelles tentatives ne sont pas conçus correctement avec les disjoncteurs, il peut aggraver les effets ripple, finalement même entraînant un [par déni de Service (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Pour contourner les délais d’attente réseau**. En règle générale, les clients doivent être conçus pour ne pas se bloquer indéfiniment et à toujours utiliser des délais d’attente pendant l’attente d’une réponse. À l’aide de délais d’attente garantit que ressources sont jamais liés indéfiniment.

**Utilisez le modèle de disjoncteur**. Dans cette approche, le processus client suit le nombre de demandes ayant échoué. Si le taux d’erreur dépasse la limite configurée, un aller-retour « disjoncteur » afin que d’autres tentatives échouent immédiatement. (Si un grand nombre de demandes échouent, qui propose le service n’est pas disponible et qu’il est inutile d’envoyer des requêtes.) Après une période de délai d’attente, le client doit réessayer et, si les nouvelles requêtes réussissent, fermez le disjoncteur.

**Fournir de secours**. Dans cette approche, le processus client exécute la logique de secours en cas d’échec d’une demande, comme le retour de données mises en cache ou une valeur par défaut. Est une approche appropriée pour les requêtes, il est plus complexe pour les mises à jour ou de commandes.

**Limiter le nombre de demandes en file d’attente**. Les clients doivent également imposer une limite supérieure du nombre de demandes en suspens qui un microservice client peut envoyer à un service particulier. Si la limite est atteinte, il est probablement inutile de faire des demandes supplémentaires, et ces tentatives doivent échouer immédiatement. En termes d’implémentation, la Polly [cloisonnement Isolation](https://github.com/App-vNext/Polly/wiki/Bulkhead) stratégie peut être utilisée pour satisfaire à cette exigence. Cette approche est essentiellement une limitation de la parallélisation avec [SemaphoreSlim](https://docs.microsoft.com/dotnet/api/system.threading.semaphoreslim?view=netcore-1.1) comme implémentation. Il permet également à un « queue » à l’extérieur du cloisonnement. Vous pouvez proactive ont une charge excessive même avant l’exécution (par exemple, étant donné que la capacité est considéré comme complet). Cela rend plus rapidement qu’un disjoncteur serait, étant donné que le disjoncteur attend que les échecs de sa réponse à certains scénarios d’échec. L’objet BulkheadPolicy dans Polly expose quelle le cloisonnement sont de la file d’attente et offre des événements de dépassement de capacité par conséquent, peuvent également servir pour piloter la mise à l’échelle horizontale automatisée.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Modèles de résilience**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Ajout de résilience et optimisation des performances**
    [*https://msdn.microsoft.com/en-us/library/jj591574.aspx*](https://msdn.microsoft.com/en-us/library/jj591574.aspx)

-   **Cloisonnement.** Référentiel GitHub. Implémentation de la stratégie de Polly. \
    [*https://github.com/app-vNext/Polly/Wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   **Conception d’applications résilientes Azure**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)

-   **Gestion d’erreurs transitoires**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults>


>[!div class="step-by-step"]
[Précédente] (handle-partielle-failure.md) [suivant] (implémentez-tentatives-exponentielle-backoff.md)
