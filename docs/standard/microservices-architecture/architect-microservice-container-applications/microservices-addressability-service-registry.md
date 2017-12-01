---
title: "Microservices adressabilité et le Registre de service"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Microservices adressabilité et le Registre de service"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 19a0200dadfb90a455de690d880f4eeae4772ed7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a>Microservices adressabilité et le Registre de service

Chaque microservice possède un nom unique (URL) qui est utilisé pour résoudre son emplacement. Votre microservice doit être adressable partout où il est en cours d’exécution. Si vous devez penser à propos de l’ordinateur sur lequel s’exécute un microservice particulier, choses peuvent devenir rapidement. De la même façon que le DNS résout une URL vers un ordinateur spécifique, votre microservice doit avoir un nom unique afin que son emplacement actuel est détectable. Microservices nécessitent un nom adressable qui les rendre indépendantes de l’infrastructure qui s’exécutent sur. Cela implique qu’il existe une interaction entre la façon dont votre service est déployé et comment il est découvert, car il doit exister un [Registre du service](http://microservices.io/patterns/service-registry.html). De la même façon, lorsqu’un ordinateur tombe en panne, le service de Registre doit être en mesure d’indiquer où le service est en cours d’exécution.

Le [modèle de service du Registre](http://microservices.io/patterns/service-registry.html) est une partie essentielle de découverte de service. Le Registre est une base de données qui contient les emplacements réseau des instances de service. Un Registre de service doit être hautement disponible et à jour. Les clients peut mettre en cache les emplacements réseau obtenus à partir du Registre de service. Toutefois, ces informations vont finalement obsolètes et les clients ne peuvent plus détecter les instances de service. Par conséquent, un Registre de service se compose d’un cluster de serveurs qui utilisent un protocole de réplication pour maintenir la cohérence.

Dans certains environnements de déploiement de microservice (appelés clusters, pour être traitées dans une section ultérieure), découverte de service est intégrée. Par exemple, dans un environnement de Service de conteneur Azure, Kubernetes et le contrôleur de domaine/système d’exploitation avec Marathon peuvent gérer l’enregistrement d’instance de service et la désinscription. Elles sont également exécutées un proxy sur chaque hôte de cluster qui joue le rôle de routeur de découverte côté serveur. Un autre exemple est Azure Service Fabric, qui fournit également un Registre de service via son Service d’affectation de noms de l’emploi.

Notez qu’il existe certain chevauchement entre le Registre de service et le modèle de passerelle API, qui vous aide à résoudre ce problème. Par exemple, le [Service Fabric Reverse Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) est un type d’implémentation d’une passerelle API qui est basé sur le Service d’affectation de noms de Service Fabrice et qui permet de résoudre la résolution d’adresse pour les services internes.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Chris Richardson. Modèle : Registre de Service**
    *http://microservices.io/patterns/service-registry.html*

-   **Auth0. Le Registre de Service**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabriel Schenker. Détection du service**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Précédente] (mettre à jour-microservice-apis.md) [suivant] (microservice-based-composite-ui-shape-layout.md)
