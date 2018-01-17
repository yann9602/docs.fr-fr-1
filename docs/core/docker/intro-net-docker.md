---
title: "Introduction à .NET et à Docker"
description: "Présentation de Docker et de .NET Core"
keywords: .NET, .NET Core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.workload: dotnetcore
ms.openlocfilehash: 8c6daabb3040998d3376ad022790c16b9629233f
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2018
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="bdde8-104">Introduction à .NET et à Docker</span><span class="sxs-lookup"><span data-stu-id="bdde8-104">Introduction to .NET and Docker</span></span>

<span data-ttu-id="bdde8-105">Cet article fournit une introduction et un contexte conceptuel à l’utilisation de .NET sur Docker.</span><span class="sxs-lookup"><span data-stu-id="bdde8-105">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span>

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="bdde8-106">Docker : empaquetage d’applications pour leur déploiement et leur exécution partout</span><span class="sxs-lookup"><span data-stu-id="bdde8-106">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="bdde8-107">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) est une plateforme ouverte qui permet aux développeurs et aux administrateurs de créer des [images](https://docs.docker.com/glossary/?term=image), de livrer et d’exécuter des applications distribuées dans un environnement peu isolé appelé un [conteneur](https://www.docker.com/what-container).</span><span class="sxs-lookup"><span data-stu-id="bdde8-107">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="bdde8-108">Cette approche permet une gestion efficace du cycle de vie des applications entre les environnements de développement, d’assurance qualité et de production.</span><span class="sxs-lookup"><span data-stu-id="bdde8-108">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="bdde8-109">La [plateforme Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) utilise le [moteur Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) pour générer et empaqueter rapidement des applications sous forme d’[images Docker](https://docs.docker.com/glossary/?term=image) créées à l’aide de fichiers écrits au format [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) qui est ensuite déployé et exécuté dans un [conteneur en couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="bdde8-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="bdde8-110">Vous pouvez créer vos propres [images en couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) en tant que fichiers Dockerfile ou utiliser des images existant déjà dans un [Registre](https://docs.docker.com/glossary/?term=registry), comme [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span><span class="sxs-lookup"><span data-stu-id="bdde8-110">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="bdde8-111">La [relation entre les conteneurs, les images et les Registres Docker](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) est un concept important pour la [conception et création d’applications ou de microservices en conteneur](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span><span class="sxs-lookup"><span data-stu-id="bdde8-111">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="bdde8-112">Cette approche réduit considérablement le temps nécessaire entre le développement et le déploiement.</span><span class="sxs-lookup"><span data-stu-id="bdde8-112">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="bdde8-113">Informations (et vidéos) supplémentaires</span><span class="sxs-lookup"><span data-stu-id="bdde8-113">Further reading (and watching)</span></span>

* [<span data-ttu-id="bdde8-114">Conteneurs Windows : développement d’applications modernes avec un contrôle d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="bdde8-114">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="bdde8-115">Vue d’ensemble de Docker</span><span class="sxs-lookup"><span data-stu-id="bdde8-115">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="bdde8-116">Dockerfile sur les conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="bdde8-116">Dockerfile on Windows Containers</span></span>](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile.md)
* [<span data-ttu-id="bdde8-117">Meilleures pratiques pour l’écriture de fichiers Dockerfile</span><span class="sxs-lookup"><span data-stu-id="bdde8-117">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="bdde8-118">Création d’images Docker pour les applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="bdde8-118">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="bdde8-119">Obtention d’images .NET Docker</span><span class="sxs-lookup"><span data-stu-id="bdde8-119">Getting .NET Docker images</span></span>

<span data-ttu-id="bdde8-120">Les images officielles .NET Docker sont créées et optimisées par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bdde8-120">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="bdde8-121">Elles sont accessibles dans les référentiels de Microsoft sur Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="bdde8-121">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="bdde8-122">Chaque référentiel peut contenir plusieurs images, selon les versions de .NET et les versions du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="bdde8-122">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="bdde8-123">La plupart des référentiels d’images fournissent un balisage complet pour vous aider à sélectionner à la fois une version de Framework spécifique et un système d’exploitation (distribution de Linux ou version de Windows).</span><span class="sxs-lookup"><span data-stu-id="bdde8-123">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="bdde8-124">Recommandations basées sur des scénarios</span><span class="sxs-lookup"><span data-stu-id="bdde8-124">Scenario based guidance</span></span>

<span data-ttu-id="bdde8-125">L’intention de Microsoft en termes de référentiels .NET est de disposer de référentiels granulaires et précis, qui représentent une charge de travail ou un scénario spécifique.</span><span class="sxs-lookup"><span data-stu-id="bdde8-125">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="bdde8-126">Les images `microsoft/aspnetcore` sont optimisées pour les applications ASP.NET Core sur Docker, ce qui permet un démarrage plus rapide des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="bdde8-126">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="bdde8-127">Les images .NET Core (`microsoft/dotnet`) sont conçues pour les applications console basées sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bdde8-127">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="bdde8-128">Par exemple, les traitements par lots, Azure WebJobs et d’autres scénarios de console devraient utiliser des images .NET Core optimisées.</span><span class="sxs-lookup"><span data-stu-id="bdde8-128">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="bdde8-129">Le scénario horizontal le plus évident pour l’utilisation de Docker et d’applications .NET est celui du déploiement et de l’hébergement de la production.</span><span class="sxs-lookup"><span data-stu-id="bdde8-129">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="bdde8-130">Notons toutefois que la production est seulement un scénario parmi d’autres qui s’avèrent tout aussi utiles.</span><span class="sxs-lookup"><span data-stu-id="bdde8-130">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="bdde8-131">Bien que ces scénarios ne soient pas spécifiques de .NET, ils devraient s’appliquer à la plupart des plateformes de développeurs.</span><span class="sxs-lookup"><span data-stu-id="bdde8-131">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="bdde8-132">**Installation à faible friction** : vous pouvez essayer .NET sans installation locale.</span><span class="sxs-lookup"><span data-stu-id="bdde8-132">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="bdde8-133">Téléchargez simplement une image Docker contenant .NET.</span><span class="sxs-lookup"><span data-stu-id="bdde8-133">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="bdde8-134">**Développement dans un conteneur** : vous pouvez développer dans un environnement cohérent, en utilisant des environnements de développement et de production similaires (pour éviter des problèmes tels que l’état global sur les machines de développeurs).</span><span class="sxs-lookup"><span data-stu-id="bdde8-134">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="bdde8-135">Visual Studio Tools pour Docker permet même de démarrer un conteneur directement à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bdde8-135">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="bdde8-136">**Tests dans un conteneur** : vous pouvez tester dans un conteneur, ce qui permet de réduire les défaillances dues à des environnements mal configurés ou à d’autres modifications apportées depuis le dernier test.</span><span class="sxs-lookup"><span data-stu-id="bdde8-136">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="bdde8-137">**Génération dans un conteneur** : vous pouvez générer du code dans un conteneur, ce qui évite d’avoir à configurer correctement les ordinateurs de build partagés pour plusieurs environnements, en adoptant à la place une approche « BYOC » (apportez votre propre conteneur).</span><span class="sxs-lookup"><span data-stu-id="bdde8-137">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="bdde8-138">**Déploiement dans tous les environnements** : vous pouvez déployer une image sur l’ensemble de vos environnements.</span><span class="sxs-lookup"><span data-stu-id="bdde8-138">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="bdde8-139">Cette approche permet de réduire les défaillances dues à des différences de configuration, en modifiant généralement le comportement de l’image via la configuration externe (par exemple, variables d’environnement injectées).</span><span class="sxs-lookup"><span data-stu-id="bdde8-139">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="bdde8-140">[Recommandations générales](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) pour choisir entre .NET Core et .NET Framework pour le développement de conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="bdde8-140">[General guidance](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="bdde8-141">Scénarios de développement Docker courants</span><span class="sxs-lookup"><span data-stu-id="bdde8-141">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="bdde8-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="bdde8-142">.NET Core</span></span>

<span data-ttu-id="bdde8-143">**Ressources .NET Core**</span><span class="sxs-lookup"><span data-stu-id="bdde8-143">**.NET Core resources**</span></span>

 <span data-ttu-id="bdde8-144">Choisissez les exemples de .NET Core en fonction des scénarios qui vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="bdde8-144">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="bdde8-145">Toutes les instructions des exemples décrivent comment cibler des images Docker Windows ou Linux à partir d’ordinateurs hôtes Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="bdde8-145">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="bdde8-146">Les exemples utilisent .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="bdde8-146">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="bdde8-147">Ils utilisent une [build Docker en plusieurs étapes ](https://github.com/dotnet/announcements/issues/18) et des [balises Docker multi-arch](https://github.com/dotnet/announcements/issues/14) lorsque nécessaire.</span><span class="sxs-lookup"><span data-stu-id="bdde8-147">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="bdde8-148">Images .NET Core sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-148">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="bdde8-149">Dockeriser une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="bdde8-149">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="bdde8-150">Cet exemple de Docker .NET Core montre comment [utiliser Docker dans votre processus de développement .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span><span class="sxs-lookup"><span data-stu-id="bdde8-150">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="bdde8-151">L’exemple s’applique aux conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="bdde8-151">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="bdde8-152">Cet exemple de Docker .NET Core montre un modèle des meilleures pratiques pour la [création d’images Docker pour les applications .NET Core pour la production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="bdde8-152">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="bdde8-153">L’exemple s’applique aux conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="bdde8-153">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="bdde8-154">Cet [exemple de Docker .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) montre un modèle des meilleures pratiques pour la création d’images Docker pour les [applications .NET Core autonomes](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="bdde8-154">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](../deploying/index.md).</span></span> <span data-ttu-id="bdde8-155">Il sert pour le plus petit conteneur de production, sans tirer avantage du [partage d’images de base entre les conteneurs](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span><span class="sxs-lookup"><span data-stu-id="bdde8-155">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="bdde8-156">Les couches inférieures de Docker peuvent néanmoins être partagées.</span><span class="sxs-lookup"><span data-stu-id="bdde8-156">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="bdde8-157">ARM32 / Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="bdde8-157">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="bdde8-158">Annonce de builds ARM32 de Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="bdde8-158">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="bdde8-159">Images .NET Core pour ARM32 / Raspberry Pi sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-159">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="bdde8-160">Exemples de .NET Core Docker pour ARM32 / Pi Raspberry sur GitHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-160">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="bdde8-161">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bdde8-161">.NET Framework</span></span>

* [<span data-ttu-id="bdde8-162">Images .NET Framework sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-162">.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet-framework/)

<span data-ttu-id="bdde8-163">Ce référentiel contient des exemples qui illustrent différentes configurations de .NET Framework Docker.</span><span class="sxs-lookup"><span data-stu-id="bdde8-163">This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="bdde8-164">Vous pouvez utiliser ces images comme base pour vos propres images Docker.</span><span class="sxs-lookup"><span data-stu-id="bdde8-164">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="bdde8-165">**.NET Framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="bdde8-165">**.NET Framework 4.7**</span></span>

<span data-ttu-id="bdde8-166">[L’exemple dotnet-framework:4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) illustre l’utilisation de base de « hello world » de [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span><span class="sxs-lookup"><span data-stu-id="bdde8-166">The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span></span> <span data-ttu-id="bdde8-167">Il vous montre comment vous pouvez générer et déployer l’application en vous basant sur l’[image Docker du .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="bdde8-167">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span></span>

<span data-ttu-id="bdde8-168">**.NET Framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="bdde8-168">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="bdde8-169">L’[exemple dotnet-framework:4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) illustre l’utilisation de base de « hello world » du [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span><span class="sxs-lookup"><span data-stu-id="bdde8-169">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span></span> <span data-ttu-id="bdde8-170">Il vous montre comment vous pouvez générer et déployer l’application en vous basant sur l’[image Docker du .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span><span class="sxs-lookup"><span data-stu-id="bdde8-170">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span></span>

<span data-ttu-id="bdde8-171">**.NET Framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="bdde8-171">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="bdde8-172">L’[exemple dotnet-framework:3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) illustre l’utilisation de base de « hello world » du [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span><span class="sxs-lookup"><span data-stu-id="bdde8-172">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span></span> <span data-ttu-id="bdde8-173">Il vous montre comment vous pouvez générer et déployer un projet en vous basant sur .NET Framework 3.5 dans Docker.</span><span class="sxs-lookup"><span data-stu-id="bdde8-173">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="bdde8-174">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bdde8-174">ASP.NET Core</span></span>

* <span data-ttu-id="bdde8-175">[Cet exemple d’ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) montre un modèle des meilleures pratiques pour la création d’images Docker pour les applications ASP.NET Core pour la production.</span><span class="sxs-lookup"><span data-stu-id="bdde8-175">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="bdde8-176">L’exemple s’applique aux conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="bdde8-176">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="bdde8-177">Images ASP.NET Core sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-177">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="bdde8-178">Images ASP.NET Core sur GitHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-178">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="bdde8-179">ASP.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bdde8-179">ASP.NET Framework</span></span>

* [<span data-ttu-id="bdde8-180">Images ASP.NET Framework sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-180">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="bdde8-181">Application de Web Forms ASP.NET sur l’exemple de .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="bdde8-181">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="bdde8-182">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="bdde8-182">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="bdde8-183">Images Windows Communication Framework (WCF) sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-183">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="bdde8-184">Images Windows Communication Framework (WCF) sur GitHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-184">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

* [<span data-ttu-id="bdde8-185">Exemples de Docker Windows Communication Framework (WCF) utilisant .NET Full Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="bdde8-185">Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="bdde8-186">Internet Information Server (IIS)</span><span class="sxs-lookup"><span data-stu-id="bdde8-186">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="bdde8-187">Images Internet Information Server (IIS) sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-187">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="bdde8-188">Images Internet Information Server (IIS) sur GitHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-188">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="bdde8-189">Interagir avec d’autres images de conteneur de pile Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdde8-189">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="bdde8-190">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="bdde8-190">Microsoft SQL Server</span></span>

* [<span data-ttu-id="bdde8-191">Exécuter l’image de conteneur de Microsoft SQL Server pour Linux 2017 avec Docker Quickstart</span><span class="sxs-lookup"><span data-stu-id="bdde8-191">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="bdde8-192">Microsoft SQL Server pour les images Linux sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-192">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="bdde8-193">Microsoft SQL Server pour les images de conteneur Windows sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-193">Microsoft SQL Server for Windows Containers images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="bdde8-194">Images de Microsoft SQL Server Express Edition pour les conteneurs Windows sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-194">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="bdde8-195">Images de Microsoft SQL Server Developer Edition pour les conteneurs Windows sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-195">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="bdde8-196">Agent Visual Studio Team Services (VSTS)</span><span class="sxs-lookup"><span data-stu-id="bdde8-196">Visual Studio Team Services (VSTS) agent</span></span>

* [<span data-ttu-id="bdde8-197">Images de l’agent Visual Studio Team Services (VSTS) sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-197">Visual Studio Team Services (VSTS) agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="bdde8-198">Images de l’agent Visual Studio Team Services (VSTS) sur GitHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-198">Visual Studio Team Services (VSTS) agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="bdde8-199">Agent Linux Operations Management Suite (OMS)</span><span class="sxs-lookup"><span data-stu-id="bdde8-199">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="bdde8-200">Vue d’ensemble de l’agent Linux Operations Management Suite (OMS)</span><span class="sxs-lookup"><span data-stu-id="bdde8-200">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [<span data-ttu-id="bdde8-201">Images Operations Management Suite (OMS) sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-201">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="bdde8-202">Images Operations Management Suite (OMS) sur GitHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-202">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="bdde8-203">Interface de ligne de commande (CLI) Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="bdde8-203">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="bdde8-204">Images de l’interface de ligne de commande (CLI) Microsoft Azure sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-204">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cli/) 

* [<span data-ttu-id="bdde8-205">Images de l’interface de ligne de commande (CLI) Microsoft Azure sur GitHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-205">Microsoft Azure Command-Line Interface (CLI) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

> [!NOTE]
> <span data-ttu-id="bdde8-206">Si vous ne disposez pas d’abonnement Azure, [inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour obtenir un compte gratuit pendant 30 jours et 200 dollars US en crédits Azure pour essayer une combinaison quelconque de services Azure.</span><span class="sxs-lookup"><span data-stu-id="bdde8-206">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="bdde8-207">Émulateur Microsoft Azure Cosmos DB (uniquement pour les conteneurs Windows)</span><span class="sxs-lookup"><span data-stu-id="bdde8-207">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="bdde8-208">Images de l’émulateur Microsoft Azure Cosmos DB sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="bdde8-208">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="bdde8-209">Utiliser l’émulateur Azure Cosmos DB pour le développement et le test locaux</span><span class="sxs-lookup"><span data-stu-id="bdde8-209">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](/azure/cosmos-db/local-emulator.md#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="bdde8-210">Exploration du riche écosystème de développement Docker</span><span class="sxs-lookup"><span data-stu-id="bdde8-210">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="bdde8-211">Maintenant que vous en avez appris plus sur la plateforme Docker et les différentes images Docker, l’étape suivante consiste à explorer le riche écosystème Docker.</span><span class="sxs-lookup"><span data-stu-id="bdde8-211">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="bdde8-212">Les liens suivants vous montrent comment les outils Microsoft complètent le développement de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="bdde8-212">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="bdde8-213">Utilisation conjointe de .NET et Docker</span><span class="sxs-lookup"><span data-stu-id="bdde8-213">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [<span data-ttu-id="bdde8-214">Conception et développement d’applications .NET à plusieurs conteneurs et basées sur des microservices</span><span class="sxs-lookup"><span data-stu-id="bdde8-214">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [<span data-ttu-id="bdde8-215">Extension Docker dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bdde8-215">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile)
* [<span data-ttu-id="bdde8-216">Découvrez comment utiliser Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="bdde8-216">Learn how to use Azure Service Fabric</span></span>](/azure/service-fabric/index.md)
* [<span data-ttu-id="bdde8-217">Exemple pour bien démarrer avec Service Fabric</span><span class="sxs-lookup"><span data-stu-id="bdde8-217">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="bdde8-218">Avantages des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="bdde8-218">Benefits of Windows Containers</span></span>](/virtualization/windowscontainers/about/index.md#video-overview)
* [<span data-ttu-id="bdde8-219">Utilisation des outils Docker dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bdde8-219">Working with Visual Studio Docker Tools</span></span>](/aspnet/core/publishing/visual-studio-tools-for-docker/index.md)
* [<span data-ttu-id="bdde8-220">Déploiement d’images Docker à partir du Registre de conteneurs Azure dans Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="bdde8-220">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="bdde8-221">Débogage avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bdde8-221">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [<span data-ttu-id="bdde8-222">Prise en main de Visual Studio pour Mac, les conteneurs et le code serverless dans le cloud</span><span class="sxs-lookup"><span data-stu-id="bdde8-222">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="bdde8-223">Bien démarrer avec Docker et Visual Studio pour Mac Lab</span><span class="sxs-lookup"><span data-stu-id="bdde8-223">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="bdde8-224">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="bdde8-224">Next steps</span></span>

* [<span data-ttu-id="bdde8-225">Découvrir les concepts de base de Docker avec .NET Core</span><span class="sxs-lookup"><span data-stu-id="bdde8-225">Learn Docker Basics with .NET Core</span></span>](docker-basics-dotnet-core.md)
* [<span data-ttu-id="bdde8-226">Création d’images Docker .NET Core</span><span class="sxs-lookup"><span data-stu-id="bdde8-226">Building .NET Core Docker Images</span></span>](building-net-docker-images.md)
