---
title: "Gérer les environnements de production Docker"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c962543004c88b0a6413cc22d8bdddf954af66f8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="manage-production-docker-environments"></a>Gérer les environnements de production Docker

Gestion du cluster et l’orchestration est le processus de contrôle d’un groupe d’hôtes. Ceci peut impliquer un ajout et suppression d’ordinateurs hôtes à partir d’un cluster, l’obtention d’informations sur l’état actuel des hôtes et des conteneurs et de démarrage et arrêt des processus. Gestion du cluster et orchestration sont étroitement liés à la planification, car le planificateur doit avoir accès à chaque hôte du cluster afin de planifier les services. Pour cette raison, le même outil est souvent utilisé pour les deux sens.

## <a name="container-service-and-management-tools"></a>Outils de gestion des services et des conteneurs

Service de conteneur fournit un déploiement rapide de solutions de clustering et d’orchestration de conteneur d’open source populaires. Il utilise des images de Docker pour vous assurer que vos conteneurs d’applications sont entièrement portables. En utilisant le Service de conteneur, vous pouvez déployer le contrôleur de domaine/système d’exploitation (développé par mésosphère et Apache Mesos) et Docker Swarm clusters avec des modèles Azure Resource Manager ou le portail Azure pour vous assurer que vous pouvez adapter ces applications à des milliers, même des dizaines de milliers, de conteneurs.

Vous déployez ces clusters à l’aide de groupes de mise à l’échelle de machines virtuelles Azure, et les clusters de tirer parti des offres de mise en réseau et de stockage Azure. Pour accéder au Service de conteneur, vous avez besoin d’un abonnement Azure. Avec le Service de conteneur, vous pouvez tirer parti des fonctionnalités de niveau entreprise de Azure tout en conservant la portabilité des applications, y compris au niveau des couches d’orchestration.

Le tableau 6-1 répertorie les outils de gestion courants liés à leurs orchestrators, planificateurs et de plateforme de clustering.

Outils de gestion de Docker tableau 6-1 :


| Outils de gestion      | Description           | Orchestrators connexes |
|-----------------------|-----------------------|-----------------------|
| Service de conteneur\(gestion de l’interface utilisateur dans le portail Azure) | [Service de conteneur](https://azure.microsoft.com/en-us/services/container-service/) fournit une solution simple pour obtenir démarré moyen [déployer un cluster de conteneur dans Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) selon orchestrators populaires tels que mésosphère DC/OS, Kubernetes et Docker Swarm. <br /><br /> Service de conteneur permet d’optimiser la configuration de ces plateformes. Vous devez simplement sélectionner la taille, le nombre d’hôtes et le choix des outils d’orchestrator et Service de conteneur gère tout le reste. | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker essaim |
| Plan de contrôle Universal docker\(en local ou cloud) | [Plan de contrôle Universal docker](https://docs.docker.com/v1.11/ucp/overview/) est la solution de gestion de cluster à l’échelle de l’entreprise à partir de Docker. Il vous permet de gérer votre cluster à partir d’un emplacement unique. <br /><br /> Plan de contrôle Universal docker est inclus dans le cadre du produit commercial nommé Docker de centre de données qui fournit les Docker Swarm, Docker Universal plan de contrôle et du Registre de confiance de Docker. <br /><br /> Centre de données docker peut être installée localement ou configuré à partir d’un cloud public comme Azure. | Docker Swarm\(pris en charge par le Service de conteneur) |
| Docker Cloud\(également appelé Tutum ; cloud SaaS) | [Docker Cloud](https://docs.docker.com/docker-cloud/) est un service de gestion hébergé (SaaS) qui fournit des capacités d’orchestration et un Registre Docker avec la build et des fonctions de test pour les images d’application Dockerized, outils pour vous aider à configurer et gérer votre infrastructure d’hôte, fonctionnalités de déploiement et pour vous aider à automatiser le déploiement de vos images à votre infrastructure concrète. Vous pouvez vous connecter à votre compte SaaS Docker Cloud à votre infrastructure de l’exécution d’un cluster de Docker Swarm de Service de conteneur. | Docker Swarm\(pris en charge par le Service de conteneur) |
| Marathon de mésosphère\(en local ou cloud) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) est une plateforme de conteneur à l’échelle de la production d’orchestration et le planificateur pour du mésosphère contrôleur de domaine/système d’exploitation et Apache Mesos. <br /><br /> Il fonctionne avec Mesos (contrôleur de domaine/système d’exploitation est basé sur Apache Mesos) à long terme de contrôle des services et fournit un [l’interface utilisateur web pour la gestion des processus et le conteneur](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Il fournit un outil de gestion de l’interface utilisateur web | Contrôleur de domaine/système d’exploitation de mésosphère\(basée sur Apache Mesos ; pris en charge par le Service de conteneur) |
| Google Kubernetes | [Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access) couvre l’orchestration, la planification et infrastructure de cluster. C’est une plate-forme open source pour l’automatisation des opérations de conteneurs d’applications, de mise à l’échelle et de déploiement pour tous les clusters d’ordinateurs hôtes, en fournissant une infrastructure orientée conteneur. | Google Kubernetes\(pris en charge par le Service de conteneur) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Un autre choix pour la gestion et de déploiement de cluster est Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/) est une plate-forme de microservices Microsoft qui inclut l’orchestration de conteneur, ainsi que des développeurs de programmation des modèles pour créer des applications hautement évolutives microservices. L’infrastructure de service prend en charge Docker dans les versions preview Linux en cours, comme dans le [aperçu Service Fabric sur Linux](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)et pour les conteneurs Windows [dans la prochaine version](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Voici les outils de gestion de l’infrastructure de Service :

-   [Portail Azure pour Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) opérations liées au cluster (création/mise à jour/suppression) un cluster ou de configurer son infrastructure (machines virtuelles, équilibrage de charge, la mise en réseau, etc..)

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) est un outil d’interface utilisateur web spécialisées qui fournit des analyses et certaines opérations sur le cluster Service Fabric à partir du point de vue de nœuds/machines virtuelles et à partir de l’application et les services de point de vue.


>[!div class="step-by-step"]
[Précédente] (run-microservices-based-applications-in-production.md) [suivant] (analyse-placées dans des conteneurs-application-services.md)
