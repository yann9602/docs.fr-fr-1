---
title: "Moderniser du cycle de vie de votre application avec l’élément de configuration/CD pipelines et les outils DevOps dans le cloud"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Moderniser du cycle de vie de votre application avec l’élément de configuration/CD pipelines et les outils DevOps dans le cloud"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 2799f203cec2b01d2c9ff1a60ece801dc5939104
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="8a2eb-103">Moderniser du cycle de vie de votre application avec l’élément de configuration/CD pipelines et les outils DevOps dans le cloud</span><span class="sxs-lookup"><span data-stu-id="8a2eb-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="8a2eb-104">Les entreprises d’aujourd'hui doivent innover à un rythme rapide pour être concurrentiel sur le marché.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="8a2eb-105">Fourniture de haute qualité, des applications modernes requiert les outils DevOps et processus critiques pour implémenter ce cycle constant d’innovation.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="8a2eb-106">Avec les outils DevOps appropriés, les développeurs peuvent simplifier le déploiement continu et obtenir plus rapidement des applications innovantes dans les mains d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="8a2eb-107">Bien que les pratiques de déploiement et d’intégration continues sont bien établies, l’introduction de conteneurs introduit considérations relatives à la nouvelle, en particulier lorsque vous travaillez avec des applications de conteneur multiples.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="8a2eb-108">Visual Studio Team Services prend en charge l’intégration continue et déploiement d’applications de conteneur multiples à une variété d’environnements à travers les tâches de déploiement officiels Team Services :</span><span class="sxs-lookup"><span data-stu-id="8a2eb-108">Visual Studio Team Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Team Services deployment tasks:</span></span>

-   <span data-ttu-id="8a2eb-109">[Déployer à la version autonome de machine virtuelle d’hôte Docker](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux ou Windows Server 2016 ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="8a2eb-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="8a2eb-110">Déployer sur l’infrastructure de Service</span><span class="sxs-lookup"><span data-stu-id="8a2eb-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="8a2eb-111">Déployer sur le Service de conteneur Azure – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="8a2eb-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="8a2eb-112">Mais vous pouvez également déployer sur [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou contrôleur de domaine/système d’exploitation à l’aide de tâches de script basé sur Team Services.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Team Services script-based tasks.</span></span>

<span data-ttu-id="8a2eb-113">Pour continuer à faciliter l’agilité de déploiement, ces outils fournissent excellent développement-test-production déploiement expériences pour les charges de travail conteneur, avec un choix de développement et des solutions de l’élément de configuration/CD.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="8a2eb-114">Figure 4-12 montre un pipeline de déploiement continu qui se déploie sur un cluster Kubernetes dans le Service de conteneur Azure.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Pipeline d’un déploiement continu Visual Studio Team Services, déploiement vers un cluster Kubernetes](./media/image12.png)

> <span data-ttu-id="8a2eb-116">**Figure 4-12.**</span><span class="sxs-lookup"><span data-stu-id="8a2eb-116">**Figure 4-12.**</span></span> <span data-ttu-id="8a2eb-117">Pipeline d’un déploiement continu Visual Studio Team Services, déploiement vers un cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="8a2eb-117">Visual Studio Team Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="8a2eb-118">[Précédent](modernize-your-apps-with-monitoring-and-telemetry.md)
[Suivant](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="8a2eb-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
