---
title: Registres, des images et des conteneurs docker
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Registres, des images et des conteneurs docker
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="5f28d-104">Registres, des images et des conteneurs docker</span><span class="sxs-lookup"><span data-stu-id="5f28d-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="5f28d-105">Lorsque vous utilisez Docker, un développeur crée une application ou de service et de packages, il et ses dépendances dans une image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="5f28d-105">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="5f28d-106">Une image est une représentation statique de l’application ou service de configuration et ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="5f28d-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="5f28d-107">Pour exécuter l’application ou le service, l’image de l’application est instancié pour créer un conteneur, qui est exécuté sur l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="5f28d-107">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="5f28d-108">Les conteneurs sont initialement testées dans un environnement de développement ou un PC.</span><span class="sxs-lookup"><span data-stu-id="5f28d-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="5f28d-109">Les développeurs doivent stocker des images dans un Registre, qui agit comme une bibliothèque d’images et est nécessaire lors du déploiement vers orchestrators de production.</span><span class="sxs-lookup"><span data-stu-id="5f28d-109">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="5f28d-110">Docker conserve un registre public via [Hub d’ancrage](https://hub.docker.com/); autres éditeurs proposent des registres pour les différentes collections d’images.</span><span class="sxs-lookup"><span data-stu-id="5f28d-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="5f28d-111">Également, les entreprises peuvent avoir un Registre privé local pour leurs propres images Docker.</span><span class="sxs-lookup"><span data-stu-id="5f28d-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="5f28d-112">Figure 2-4 indique comment les images et les registres dans Docker se rapportent à d’autres composants.</span><span class="sxs-lookup"><span data-stu-id="5f28d-112">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="5f28d-113">Il montre également les offres de Registre plusieurs provenant de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="5f28d-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="5f28d-114">**Figure 2-4**.</span><span class="sxs-lookup"><span data-stu-id="5f28d-114">**Figure 2-4**.</span></span> <span data-ttu-id="5f28d-115">Taxonomie de Docker termes et concepts</span><span class="sxs-lookup"><span data-stu-id="5f28d-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="5f28d-116">Placer des images dans un Registre vous permet de stocker les bits d’application statique et immuable, y compris toutes leurs dépendances au niveau de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="5f28d-116">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="5f28d-117">Ces images peuvent ensuite être créée et déployée dans plusieurs environnements et par conséquent fournissent une unité de déploiement cohérent.</span><span class="sxs-lookup"><span data-stu-id="5f28d-117">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="5f28d-118">Les registres de l’image privée, soit hébergé localement ou dans le cloud, sont recommandé lorsque :</span><span class="sxs-lookup"><span data-stu-id="5f28d-118">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="5f28d-119">Vos images ne doivent pas être partagés publiquement en raison de la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="5f28d-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="5f28d-120">Vous souhaitez avoir une latence réseau minimum entre vos images et votre environnement de déploiement choisi.</span><span class="sxs-lookup"><span data-stu-id="5f28d-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="5f28d-121">Par exemple, si votre environnement de production est cloud Azure, vous souhaiterez probablement stocker vos images dans le Registre de conteneur Azure afin que la latence du réseau sera minime.</span><span class="sxs-lookup"><span data-stu-id="5f28d-121">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="5f28d-122">De la même façon, si votre environnement de production sur site, vous souhaiterez ont un local Docker Trusted Registre disponibles dans le même réseau local.</span><span class="sxs-lookup"><span data-stu-id="5f28d-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="5f28d-123">[Précédente] (docker-terminology.md) [suivant] (.. /NET-Core-NET-Framework-Containers/index.MD)</span><span class="sxs-lookup"><span data-stu-id="5f28d-123">[Previous] (docker-terminology.md) [Next] (../net-core-net-framework-containers/index.md)</span></span>
