---
title: "Moment de déployer des conteneurs Windows dans le Service de conteneur Azure (autrement dit, Kubernetes)"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Moment de déployer des conteneurs Windows dans le Service de conteneur Azure (autrement dit, Kubernetes)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: f5ba7aa2cf14e7ca9f3a1f3eb12bbe236dca7e97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="9e24d-103">Moment de déployer des conteneurs Windows dans le Service de conteneur Azure (autrement dit, Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="9e24d-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="9e24d-104">Service de conteneur Azure permet d’optimiser la configuration des outils open source populaires et technologies utilisées spécifiquement pour Azure.</span><span class="sxs-lookup"><span data-stu-id="9e24d-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="9e24d-105">Vous obtenez une solution ouverte qui offre la portabilité de vos conteneurs et lors de la configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="9e24d-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="9e24d-106">Vous sélectionnez la taille, le nombre d’hôtes et les outils d’orchestrator.</span><span class="sxs-lookup"><span data-stu-id="9e24d-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="9e24d-107">Service de conteneur Azure gère l’infrastructure pour vous.</span><span class="sxs-lookup"><span data-stu-id="9e24d-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="9e24d-108">Si vous utilisez déjà orchestrators open source comme Kubernetes, Docker Swarm ou contrôleur de domaine/système d’exploitation, vous n’avez pas besoin de modifier vos méthodes de gestion existant pour déplacer les charges de travail conteneur dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="9e24d-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="9e24d-109">Utilisez les outils de gestion d’application que vous êtes déjà familiarisé avec et se connectez via les points de terminaison API standards pour l’orchestrateur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="9e24d-109">Use the application management tools that you're already familiar with, and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="9e24d-110">Tous ces orchestrators sont déjà rodées environnements Si vous utilisez des conteneurs Linux Docker, mais ils également prise en charge des conteneurs Windows comme de 2017 (certaines précédemment, d’autres plus récente, en fonction de l’orchestrateur).</span><span class="sxs-lookup"><span data-stu-id="9e24d-110">All these orchestrators are mature environments if you are using Linux Docker containers, but they also support Windows Containers as of 2017 (some earlier, some more recently, depending on the orchestrator).</span></span>

<span data-ttu-id="9e24d-111">Par exemple, dans Kubernetes, prise en charge les conteneurs est natif (acteur), à l’aide de conteneurs Windows sur Kubernetes est également très efficace et fiable (dans l’aperçu jusqu’au début se situent 2017).</span><span class="sxs-lookup"><span data-stu-id="9e24d-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also very effective and reliable (in preview until early fall 2017).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="9e24d-112">[Précédent](when-to-deploy-windows-containers-to-service-fabric.md)
[Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="9e24d-112">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
