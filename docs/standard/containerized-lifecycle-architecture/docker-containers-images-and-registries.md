---
title: Registres, des images et des conteneurs docker
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0cccead8833c63f19b359f830f555e7ff31daa1a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="ca2f8-104">Registres, des images et des conteneurs docker</span><span class="sxs-lookup"><span data-stu-id="ca2f8-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="ca2f8-105">Lorsque vous utilisez Docker, vous créez une application ou le service et le package il et ses dépendances dans une image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-105">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="ca2f8-106">Une image est une représentation statique de l’application ou service de configuration et ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="ca2f8-107">Pour exécuter l’application ou le service, l’image de l’application est instancié pour créer un conteneur, qui est exécuté sur l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-107">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="ca2f8-108">Les conteneurs sont initialement testées dans un environnement de développement ou un PC.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="ca2f8-109">Stocker des images dans un Registre, qui agit comme une bibliothèque d’images.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-109">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="ca2f8-110">Vous avez besoin d’un Registre lors du déploiement vers orchestrators de production.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-110">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="ca2f8-111">Docker conserve un registre public via [Hub d’ancrage](https://hub.docker.com/); autres éditeurs proposent des registres pour les différentes collections d’images.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-111">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="ca2f8-112">Également, les entreprises peuvent avoir un Registre privé local pour leurs propres images Docker.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-112">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="ca2f8-113">Figure 1-4 indique comment les images et les registres dans Docker se rapportent à d’autres composants.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-113">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="ca2f8-114">Il montre également les offres de Registre plusieurs provenant de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-114">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="ca2f8-115">Classification de la figure 1-4 : de Docker termes et concepts</span><span class="sxs-lookup"><span data-stu-id="ca2f8-115">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="ca2f8-116">En plaçant des images dans un Registre, vous pouvez stocker les bits d’application statique et immuable, y compris toutes leurs dépendances, au niveau d’une infrastructure.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-116">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="ca2f8-117">Vous pouvez version puis et déployer des images dans plusieurs environnements et donc fournissent une unité de déploiement cohérent.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-117">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="ca2f8-118">Les registres de l’image privée, hébergé localement ou dans le cloud, sont recommandés pour les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ca2f8-118">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="ca2f8-119">Vos images ne doivent pas être partagés publiquement en raison de la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="ca2f8-120">Vous souhaitez avoir une latence réseau minimum entre vos images et votre environnement de déploiement choisi.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="ca2f8-121">Par exemple, si votre environnement de production est Azure, vous souhaiterez probablement stocker vos images dans le Registre de conteneur Azure afin que la latence du réseau sera minime.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-121">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="ca2f8-122">De la même façon, si votre environnement de production sur site, vous souhaiterez ont un local Docker Trusted Registre disponibles dans le même réseau local.</span><span class="sxs-lookup"><span data-stu-id="ca2f8-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="ca2f8-123">[Précédente] (docker-terminology.md) [suivant] (Docker-application-du cycle de vie/index.md)</span><span class="sxs-lookup"><span data-stu-id="ca2f8-123">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>
