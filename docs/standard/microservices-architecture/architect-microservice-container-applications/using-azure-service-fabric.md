---
title: "À l’aide d’Azure Service Fabric"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | À l’aide d’Azure Service Fabric"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa15f9cf9bc60e9e70607da921f2ce2c75e39ec2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="using-azure-service-fabric"></a>À l’aide d’Azure Service Fabric

Azure Service Fabric a été créée à partir de passage de Microsoft proposant des produits de zone, qui ont été généralement monolithiques de style, la fourniture de services. L’expérience de création et d’exploitation de grands services à grande échelle, telles que la base de données SQL Azure, base de données Azure Cosmos, Azure Service Bus ou principal du Cortana, la forme Service Fabric. La plateforme a évolué au fil du temps comme services plus adopté. Surtout, Service Fabric dû exécuter non seulement dans Azure, mais également dans les déploiements de Windows Server autonome.

Le Service Fabric vise à résoudre des problèmes de génération et exécution d’un service et utilisant les ressources d’infrastructure efficacement, afin que les équipes de résoudre les problèmes d’entreprise à l’aide d’une approche de microservices.

Service Fabric fournit deux grands domaines pour vous aider à créer des applications qui utilisent une approche de microservices :

-   Une plateforme qui fournit des services pour déployer, mettre à l’échelle, mettre à niveau, détecter, redémarrez les services ayant échouées, découvrir l’emplacement du service, gérer l’état et surveiller l’intégrité du système. Ces services système activer en vigueur la plupart des caractéristiques de microservices décrit précédemment.

-   API de programmation, ou des infrastructures, pour vous aider à créer des applications en tant que microservices : [fiables acteurs et des services fiables](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Bien entendu, vous pouvez choisir n’importe quel code pour générer votre microservice, mais ces API que le travail plus simple, et ils s’intègrent à la plate-forme à un niveau inférieur. De cette manière, vous pouvez obtenir le contrôle d’intégrité et les informations de diagnostic ou vous pouvez tirer parti de gestion d’état fiable.

L’infrastructure de service est indépendant en ce qui concerne la façon dont vous générez votre service, et vous pouvez utiliser n’importe quelle technologie. Toutefois, il fournit des API de programmation intégrés qui facilitent la build microservices.

Comme indiqué dans la Figure 4-26, vous pouvez créer et exécuter des microservices dans l’infrastructure de Service en tant que processus simples ou en tant que conteneurs Docker. Il est également possible de combiner basée sur le conteneur de microservices avec basé sur le processus de microservices au sein du même cluster Service Fabric.

![](./media/image30.png)

**Figure 4-26**. Déploiement de microservices en tant que processus ou en tant que conteneurs dans Azure Service Fabric

Les clusters service Fabric basés sur les hôtes Linux et Windows peuvent exécuter les conteneurs Docker Linux et Windows, respectivement.

Pour obtenir des informations récentes sur la prise en charge des conteneurs dans Azure Service Fabric, consultez [Service Fabric et conteneurs](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric est un bon exemple d’une plateforme où vous pouvez définir une autre architecture logique (entreprise microservices ou limitées de contextes) que l’implémentation physique qui ont été introduits dans la [architecture logique et physique architecture](#logical-architecture-versus-physical-architecture) section. Par exemple, si vous implémentez [Reliable Services avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) dans [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), qui ont été introduit dans la section [sans état et avec état microservices](#stateless-versus-stateful-microservices) une version ultérieure, vous pouvez avoir un concept de microservice métier avec plusieurs services physiques.

Comme indiqué dans la Figure 4-27, en pensant à partir d’un point de vue logique/business microservice, lors de l’implémentation d’un Service avec état fiable Service Fabric, vous généralement devrez implémenter deux niveaux de services. Le premier est le service de fiable avec état principal, qui gère plusieurs partitions (chaque partition est un service avec état). Le deuxième est le service frontal, ou le service de passerelle, responsable de l’agrégation de routage et les données sur plusieurs partitions ou les instances de service avec état. Ce service de passerelle gère également la communication de côté client avec des boucles de réessayer l’accès au service principal.
Il est appelé un service de passerelle si vous implémentez votre service personnalisée ou alternatevely, vous pouvez également utiliser l’infrastructure de Service out of box [service de Proxy inverse](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**Figure 4-27**. Microservice d’entreprise avec plusieurs instances de service avec état et une passerelle personnalisée frontale

Dans tous les cas, lorsque vous utilisez Service Fabric Reliable Services avec état, vous avez également un microservice (contexte délimité) logique ou d’entreprise qui est généralement constitué de plusieurs services physiques. Chacun d’eux, le service de passerelle et le service de la Partition peut être implémentée en tant que services de l’API Web ASP.NET, comme indiqué dans la Figure 4-26.

Dans l’infrastructure de Service, vous pouvez regrouper et déployer des groupes de services en tant qu’un [Application Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), qui est l’unité d’empaquetage et de déploiement pour le cluster ou d’orchestrator. Par conséquent, l’Application de l’infrastructure de Service peut être mappée à cette commerciales autonomes et la limite de microservice logique ou le contexte délimité, ainsi, donc vous pouvez déployer ces services de manière autonome.

## <a name="service-fabric-and-containers"></a>L’infrastructure de service et les conteneurs

En ce qui concerne les conteneurs dans l’infrastructure de Service, vous pouvez également déployer des services dans les images de conteneur au sein d’un cluster Service Fabric. Comme le montre la Figure 4-28, la plupart du temps il sera uniquement un conteneur par le service.

![](./media/image32.png)

**Figure 4-28**. Microservice d’entreprise avec plusieurs services (conteneurs) dans le Service Fabric

Toutefois, les conteneurs dite « annexe » (deux conteneurs qui doivent être déployées ensemble dans le cadre d’un service logique) sont également possibles dans le Service Fabric. Le point essentiel est qu’un microservice d’entreprise est la limite logique autour des éléments soudées plusieurs. Dans de nombreux cas, il peut être un service unique avec un seul modèle de données, mais dans d’autres cas, vous pouvez avoir services plusieurs physiques.

À compter de mid 2017, dans l’infrastructure de Service vous ne pouvez pas déployer SF fiable avec état Services sur les conteneurs, vous pouvez uniquement déployer les services sans état et les services d’acteur dans des conteneurs. Notez toutefois que vous pouvez combiner des services dans les processus et services dans des conteneurs dans la même application de Service Fabric, comme indiqué dans la Figure 4-29.

![](./media/image33.png)

**Figure 4-29**. Microservice d’entreprise mappé à une application de Service Fabric des conteneurs et des services avec état

Pour plus d’informations sur la prise en charge de conteneur dans Azure Service Fabric, consultez [Service Fabric et conteneurs](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Sans état et avec état microservices

Comme mentionné précédemment, chaque microservice (contexte délimité logique) doit posséder son modèle de domaine (données et logique). Dans le cas de microservices sans état, les bases de données sera externes, en utilisant les options relationnelles telles que SQL Server ou les options de NoSQL comme MongoDB ou de la base de données Azure Cosmos.

Mais les services eux-mêmes peuvent également être avec état dans l’infrastructure de Service, ce qui signifie que les données se trouvent dans le microservice. Ces données existe peut-être pas seulement sur le même serveur, mais dans le processus de microservice, dans la mémoire et conservées sur les disques durs et répliquées vers d’autres nœuds. Figure 4-30 montre les différentes approches.

![](./media/image34.png)

**Figure 4-30**. Sans état et avec état microservices

Une approche sans état est parfaitement valide et est plus facile à implémenter que microservices avec état, étant donné que l’approche est similaire aux modèles traditionnels et bien connus. Mais sans état microservices imposer la latence entre les processus et sources de données. Elles impliquent également pièces plus lorsque vous essayez d’améliorer les performances des files d’attente et de cache supplémentaire. Le résultat est que vous pouvez se retrouver avec des architectures complexes qui ont trop de niveaux.

En revanche, [microservices avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) peut excel dans les scénarios avancés, car il n’existe pas de latence entre la logique de domaine et les données. Le traitement des données lourd, jeu précédent termine, bases de données en tant que service, et tous les autres scénarios de faible latence tirer parti des services avec état, qui permettent à l’état local pour un accès plus rapide.

Les services et sans état sont complémentaires. Par exemple, vous pouvez voir dans la Figure 4-30, dans le diagramme de droite, qu’un service sans état peut être fractionné en plusieurs partitions. Pour accéder à ces partitions, vous devrez peut-être un service sans état agissant comme un service de passerelle qui sait comment résoudre chaque partition en fonction des clés de partition.

Les services avec état ont des inconvénients. Ils imposent un niveau de complexité qui permet de montée en puissance parallèle. Fonctionnalité qui serait généralement être implémentée par les systèmes de base de données externe doit être abordée pour des tâches telles que la réplication des données entre microservices avec état et le partitionnement des données. Toutefois, c’est une des zones où un orchestrator que [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) avec son [des services fiables avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) peut aider au plus, en ce qui simplifie le développement et le cycle de vie de l’état à l’aide de microservices les [API des Services fiables](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) et [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Les autres infrastructures de microservice qui autorisent les services avec état, qui prennent en charge le modèle d’acteur et qui améliorent la tolérance de panne et la latence entre la logique métier et les données sont Microsoft [Orléans](https://github.com/dotnet/orleans), de Microsoft Research et [ Akka.NET](http://getakka.net/). Les deux infrastructures actuellement Améliorez leur prise en charge de Docker.

Notez que les conteneurs Docker sont eux-mêmes sans état. Si vous souhaitez implémenter un service avec état, vous besoin d’un des infrastructures supplémentaires des recommandations et de niveau supérieur notées précédemment. 

>[!div class="step-by-step"]
[Précédente] (scalable-available-multi-container-microservice-applications.md) [suivant] (.. /docker-Application-Development-Process/index.MD)
