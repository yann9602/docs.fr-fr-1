---
title: Architecture en microservices
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Architecture de Microservices
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5ede1f0ad19270ca6b7556ff1bb7e4cf8ccf7cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="microservices-architecture"></a>Architecture en microservices

Comme son nom l’indique, une architecture de microservices est une approche pour la création d’une application serveur comme un ensemble de services de petits. Chaque service s’exécute dans son propre processus et communique avec d’autres processus à l’aide des protocoles tels que HTTP/HTTPS, WebSockets, ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Chaque microservice implémente un domaine spécifique de bout en bout ou une fonctionnalité dans une certaine limite de contexte, et chacune doit être développée de manière autonome et être pouvant être déployées indépendamment. Enfin, chaque microservice doit posséder son modèle de données de domaine connexes et une logique de domaine (souveraineté et gestion des données décentralisé) basé sur les technologies de stockage de données différentes (SQL, NoSQL) et les différents langages de programmation.

Quelle taille doit être un microservice ? Lorsque vous développez un microservice, taille ne doit pas être le point important. Au lieu de cela, le point important doit être créer faiblement couplés services afin que vous ayez l’autonomie des équipes de développement, déploiement et mise à l’échelle pour chaque service. Bien entendu, lors de l’identification et la conception de microservices, vous devez tenter de les rendre plus petit possible tant que vous n’avez pas trop de dépendances directes avec les autres microservices. Plus important que la taille de la microservice est son indépendance provenant d’autres services et la cohésion interne, qu'il doit avoir.

Pourquoi une architecture microservices ? En bref, il fournit une souplesse à long terme. Microservices activer une gestion facilitée dans les systèmes complexes et volumineux hautement évolutive en vous permettant de créer des applications basées sur de nombreux services pouvant être déployées indépendamment, ayant chacune des cycles de vie granulaire et autonomes.

Offre un autre avantage, microservices peuvent évoluer indépendamment. Au lieu d’avoir une seule application monolithique qui vous devez monter en charge en tant qu’unité, vous pouvez faire évoluer des microservices spécifique à la place. De cette façon, vous pouvez faire évoluer la zone fonctionnelle nécessitant plus le traitement d’alimentation de bande passante réseau pour prendre en charge à la demande, au lieu de montée en puissance parallèle d’autres zones de l’application que vous n’avez pas besoin de mettre à l’échelle. Cela signifie que les économies, car vous avez besoin de moins de matériel.

![](./media/image6.png)

**Figure 4-6**. Déploiement monolithique par rapport à l’approche de microservices

Comme le montre la Figure 4-6, l’approche de microservices permet de modifications agiles et une itération rapide de chaque microservice, étant donné que vous pouvez modifier des zones spécifiques, petite d’applications complexes, volumineuses et évolutives.

Architecture d’intégration continue d’Active des applications microservices affinées et pratiques de livraison continue. Elle accélère également la remise de nouvelles fonctions dans l’application. Composition de granularité fine des applications vous permet également pour exécuter et tester des microservices de manière isolée et leur évolution autonome tout en conservant les contrats claires entre eux. Tant que vous ne modifiez pas les contrats ou les interfaces, vous pouvez modifier l’implémentation interne de n’importe quel microservice ou ajouter de nouvelles fonctionnalités sans interruption des autres microservices.

Les aspects importants pour permettre la réussite de passer en production avec un système basé sur des microservices sont les suivantes :

-   Vérifications de surveillance et de contrôle d’intégrité de l’infrastructure et les services.

-   Infrastructure évolutive pour les services (autrement dit, le cloud et l’orchestrators).

-   Conception de la sécurité et de l’implémentation à plusieurs niveaux : authentification, autorisation, gestion de clés secrètes, une communication sécurisée, etc..

-   Livraison rapide d’application, généralement avec les différentes équipes en mettant l’accent sur différents microservices.

-   DevOps et l’élément de configuration/CD pratiques et l’infrastructure.

Parmi ceux-ci, uniquement les trois premières sont couverts ou introduites dans ce guide. Ces deux derniers points, qui sont liées au cycle de vie des applications, sont traités dans les autres [placées dans des conteneurs Docker cycle de vie Application avec Microsoft Platform et outils](https://aka.ms/dockerlifecycleebook) livres.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Mark Russinovich. Microservices : Revolution une application par le nuage**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Martin Fowler. Microservices**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)

-   **Martin Fowler. Conditions préalables de Microservice**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson. Segment de Cloud Computing**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Cesar de la Torre. Placées dans des conteneurs Docker cycle de vie Application avec Microsoft Platform et outils** (livre électronique téléchargeable) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[Précédente] (service-oriented-architecture.md) [suivant] (données-souveraineté-par-microservice.md)
