---
title: "Orchestration microservices et applications multi conteneur pour une haute évolutivité et la disponibilité"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Orchestration microservices et applications multi conteneur pour une haute évolutivité et la disponibilité"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ec33901a0ddc9e5b58263440b0e4399e687c6904
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orchestration microservices et applications multi conteneur pour une haute évolutivité et la disponibilité

À l’aide d’orchestrators pour les applications de l’environnement de production est essentiel si votre application est basée sur microservices ou simplement distribuée sur plusieurs conteneurs. Introduit précédemment, dans une approche basée sur les microservice, chaque microservice possède son modèle et les données afin qu’il soit autonome à partir d’un développement et un point de vue du déploiement. Toutefois, même si vous avez une application plus classique qui est composée de plusieurs services (par exemple, SOA), vous devez également plusieurs conteneurs ou services comprenant une application unique qui doivent être déployés en tant qu’un système distribué. Ces types de systèmes sont complexes à monter en charge et gérer ; Par conséquent, vous devez absolument orchestrateur si vous souhaitez disposer d’une application conteneur multi prêt pour la production et évolutive.

Figure 4-23 illustre un déploiement dans un cluster d’une application composée de plusieurs microservices (conteneurs).

![](./media/image23.PNG)

**Figure 4-23**. Un cluster de conteneurs

Il ressemble à une approche logique. Mais comment vous équilibrage de charge de gestion, de routage et d’orchestration de ces composés applications ?

Le moteur Docker brut dans des hôtes Docker uniques répond aux besoins de la gestion des instances d’image unique sur un ordinateur hôte, mais il n’était pas lorsqu’il s’agit de la gestion de plusieurs conteneurs sont déployés sur plusieurs ordinateurs hôtes pour les applications distribuées plus complexes. Dans la plupart des cas, vous avez besoin d’une plateforme de gestion des conteneurs, les conteneurs de montée en puissance parallèle avec plusieurs instances par une image de démarrage, les suspendre ou les arrêter si nécessaire, et automatiquement idéalement également contrôler comment accéder aux ressources, telles que le réseau et les données stockage.

Pour aller au-delà de la gestion des conteneurs individuels ou les applications composées très simples et déplacer vers les grandes applications d’entreprise avec microservices, vous devez activer orchestration et le clustering des plateformes.

À partir d’un point de vue architecture et le développement, si vous générez des grandes entreprises composées d’applications basées sur des microservices, il est important de comprendre les plateformes et les produits qui prennent en charge des scénarios avancés suivants :

**Clusters et orchestrators**. Lorsque vous devez faire évoluer des applications sur plusieurs hôtes Docker, comme lors d’une grande application microservice, il est essentiel de pouvoir gérer tous ces ordinateurs hôtes en tant qu’un seul cluster en faisant abstraction de la complexité de la plateforme sous-jacente. C’est ce que les clusters de conteneur et orchestrators fournir. Exemples d’orchestrators sont Azure Service Fabric, Kubernetes, Docker Swarm et mésosphère contrôleur de domaine/système d’exploitation. Les trois dernières orchestrators open source sont disponibles dans Azure via le Service de conteneur Azure.

**Planificateurs**. *Planification* signifie la capacité d’un administrateur pour lancer des conteneurs dans un cluster afin qu’ils fournissent également une interface utilisateur. Un planificateur de cluster a plusieurs responsabilités : à utiliser efficacement les ressources du cluster, pour définir les contraintes fournis par l’utilisateur, aux conteneurs efficacement d’équilibrer la charge entre les nœuds ou des ordinateurs hôtes et être robustes face à des erreurs tout en offrant une haute disponibilité.

Les concepts d’un cluster et un planificateur sont étroitement liés, les produits fournis par différents fournisseurs souvent fournissent les deux ensembles de fonctionnalités. La liste suivante montre la plate-forme plus importante et les choix d’un logiciel pour les clusters et des planificateurs. Ces orchestrators sont généralement proposées dans des clouds publics comme Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Plateformes logicielles de clustering de conteneur, d’orchestration et de planification

Kubernetes

![https://PBS.twimg.com/Media/BT\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes est un produit open source qui fournit des fonctionnalités qui s’étend de l’infrastructure de cluster et le conteneur de la planification des capacités orchestrant ces opérations. Il vous permet d’automatiser les opérations de conteneurs d’applications, de mise à l’échelle et de déploiement pour tous les clusters d’ordinateurs hôtes.
>
> Kubernetes fournit une infrastructure orientée conteneur qui regroupe des conteneurs d’applications dans des unités logiques pour faciliter la gestion et la découverte.
>
> Kubernetes est déjà rodée dans Linux, moins mature dans Windows.

Docker essaim

![http://rancher.com/WP-Content/Themes/rancher-2016/Assets/images/swarm.png?v=2016-07-10-AM](./media/image25.png)

> Docker essaim vous permet de planifier des conteneurs Docker et le cluster. À l’aide d’essaim, vous pouvez activer un pool d’hôtes Docker dans un hôte Docker virtuel unique. Les clients peuvent envoyer des demandes API à Swarm de la même façon qu'ils faire aux hôtes, ce qui signifie que qu’essaim facilite pour les applications à l’échelle sur plusieurs hôtes.
>
> Docker essaim est un produit à partir de Docker, la société.
>
> Version de docker 1.12 ou plus tard pouvant s’exécuter en Mode natif et intégrées Swarm.

Mésosphère contrôleur de domaine/système d’exploitation

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> Mésosphère Enterprise contrôleur de domaine/système d’exploitation (basée sur Apache Mesos) est une plateforme de l’environnement de production pour l’exécution des conteneurs et des applications distribuées.
>
> Contrôleur de domaine/système d’exploitation fonctionne en faisant abstraction d’une collection de ressources disponibles dans le cluster et la disposition de ces ressources pour les composants générés par-dessus. Marathon est généralement utilisé comme un planificateur intégré à un contrôleur de domaine/système d’exploitation.
>
> Contrôleur de domaine/système d’exploitation est déjà rodée dans Linux, moins mature dans Windows.

Azure Service Fabric

![https://Azure.Microsoft.com/svghandler/service-Fabric?Width=600&Height=315](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) est une plateforme de microservices de Microsoft pour la création d’applications. Il s’agit d’un [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de services et crée des clusters d’ordinateurs. L’infrastructure de service peut déployer des services en tant que conteneurs ou en tant que processus simples. Il peut même combinaison de services dans des processus avec les services dans les conteneurs au sein de la même application et le cluster.
>
> Fournit de l’infrastructure de service supplémentaires et facultatifs normative [Service Fabric, modèles de programmation ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) comme [services avec état](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) et [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> Service Fabric est déjà rodée dans Windows (évolution des années dans Windows), moins mature dans Linux. 
> Les conteneurs Linux et Windows sont pris en charge dans l’infrastructure de Service depuis 2017.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>À l’aide basée sur le conteneur d’orchestrators dans Microsoft Azure

Plusieurs fournisseurs de cloud computing proposent une prise en charge des conteneurs Docker ainsi que les clusters de Docker et prise en charge de l’orchestration, y compris Microsoft Azure, Amazon EC2 conteneur de Service et le moteur de conteneur de Google. Microsoft Azure offre Docker la prise en charge des clusters et orchestrator via conteneur de Service (ACS) Azure, comme expliqué dans la section suivante.

Un autre choix est d’utiliser Microsoft Azure Service Fabric (plateforme microservices), qui prend également en charge Docker basé sur les conteneurs Linux et Windows. L’infrastructure de service s’exécute sur Azure ou de n’importe quel autre cloud et s’exécute également [local](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>À l’aide du Service de conteneur Azure

Un cluster de Docker regroupe plusieurs hôtes Docker et les expose sous un hôte Docker virtuel unique, afin de déployer plusieurs conteneurs dans le cluster. Le cluster gère tous les plomberie de gestion complexes, telles que l’évolutivité, intégrité et ainsi de suite. Figure 4-24 représente la façon dont un cluster de Docker pour les applications composées mappe au conteneur de Service (ACS) Azure.

ACS permet de simplifier la création, la configuration et la gestion d’un cluster d’ordinateurs virtuels qui sont préconfigurés pour exécuter des applications en conteneur. À l’aide d’une configuration optimisée des outils de planification et d’orchestration open source populaires, ACS vous permet d’utiliser vos compétences ou dessiner sur un corps important et croissant d’expertise de communauté pour déployer et gérer les applications basées sur le conteneur sur Microsoft Azure .

Service de conteneur Azure permet d’optimiser la configuration des outils open source de la gestion de clusters Docker et les technologies populaire spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité de vos conteneurs et configuration de votre application. Vous sélectionnez la taille, le nombre d’hôtes et les outils d’orchestrator et Service de conteneur gère tout le reste.

![](./media/image28.png)

**Figure 4-24**. Clustering de choix dans le conteneur de Service Azure

ACS s’appuie sur les images Docker pour vous assurer que vos conteneurs d’applications sont entièrement portables. Il prend en charge de votre choix des plateformes open source orchestration comme contrôleur de domaine/système d’exploitation (développé par Apache Mesos), Kubernetes (créé à l’origine par Google) et Docker Swarm, pour vous assurer que ces applications peuvent être mis à l’échelle et même des dizaines de milliers de conteneurs.

Le service de conteneur Azure permet de tirer parti des fonctionnalités de niveau entreprise de Azure tout en conservant la portabilité des applications, y compris au niveau des couches d’orchestration.

![](./media/image29.png)

**Figure 4-25**. Orchestrators dans ACS

Comme indiqué dans la Figure 4-25, le Service de conteneur Azure est simplement l’infrastructure fournie par Azure pour déployer le contrôleur de domaine/système d’exploitation, Kubernetes ou Docker Swarm, mais des services ACS n’implémente pas de n’importe quel orchestrator supplémentaire. Par conséquent, ACS n’est pas un orchestrator donc uniquement une infrastructure qui tire parti des orchestrators open source existants pour les conteneurs.

À partir d’un point de vue de l’utilisation, de Service de conteneur Azure vise à fournir un environnement d’hébergement de conteneur à l’aide de technologies et outils open source populaires. À cette fin, elle expose les points de terminaison API standards pour votre orchestrator choisi. À l’aide de ces points de terminaison, vous pouvez exploiter tout logiciel qui peut communiquer avec ces points de terminaison. Par exemple, dans le cas le point de terminaison Docker Swarm, vous pouvez choisir d’utiliser l’interface de ligne de commande Docker (CLI). Pour le contrôleur de domaine/système d’exploitation, vous pouvez choisir d’utiliser l’interface CLI de contrôleur de domaine/système d’exploitation.

### <a name="getting-started-with-azure-container-service"></a>Mise en route avec le Service de conteneur Azure 

Pour commencer à utiliser le Service de conteneur Azure, vous déployez un cluster du Service de conteneur Azure à partir du portail Azure à l’aide d’un modèle Azure Resource Manager ou le [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Les modèles disponibles incluent [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), et [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Les modèles de démarrage rapide peuvent être modifiés pour inclure les configuration d’Azure supplémentaire ou avancée. Pour plus d’informations sur le déploiement d’un cluster du Service de conteneur Azure, consultez [déployer un cluster du Service de conteneur Azure](https://docs.microsoft.com/azure/container-service/container-service-deployment) sur le site Web Azure.

Il n’existe aucun frais pour les logiciels installés par défaut dans le cadre des services ACS. Toutes les options par défaut sont implémentées avec des logiciels open source.

ACS est actuellement disponible pour la série A Standard, D, DS, G et GS ordinateurs virtuels Linux dans Azure. Vous payez uniquement pour les instances de calcul que vous choisissez, ainsi que les autres ressources infrastructure sous-jacente consommés, telles que la mise en réseau et de stockage. Il n’existe aucun frais incrémentielles pour les services ACS lui-même.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Introduction au conteneur Docker hébergeant des solutions avec le Service de conteneur Azure**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Vue d’ensemble de docker essaim**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Vue d’ensemble du mode de swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Vue d’ensemble du contrôleur de domaine/système d’exploitation mésosphère**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes.** Le site officiel. \
    [*http://kubernetes.IO/*](http://kubernetes.io/)


>[!div class="step-by-step"]
[Précédente] (résilient-haute-disponibilité-microservices.md) [suivant] (à l’aide de-azure-service-fabric.md)
