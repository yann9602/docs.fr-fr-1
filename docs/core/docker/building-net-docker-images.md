---
title: "Création d’images Docker .NET Core"
description: "Présentation des images Docker et de .NET Core"
keywords: .NET, .NET Core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="a75b7-104">Création d’images Docker pour les applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="a75b7-104">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="a75b7-105">Dans ce didacticiel, nous concentrer sur l’utilisation de .NET Core sur Docker.</span><span class="sxs-lookup"><span data-stu-id="a75b7-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="a75b7-106">Tout d’abord, nous explorons les images Docker différentes proposées et gérés par Microsoft et les cas d’usage.</span><span class="sxs-lookup"><span data-stu-id="a75b7-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="a75b7-107">Nous avons ensuite apprendre à générer et dockerize d’une application ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a75b7-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="a75b7-108">Au cours de ce didacticiel, vous apprendrez :</span><span class="sxs-lookup"><span data-stu-id="a75b7-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a75b7-109">En savoir plus sur Microsoft .NET Core Docker images</span><span class="sxs-lookup"><span data-stu-id="a75b7-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="a75b7-110">Obtenir un ASP.NET Core exemple d’application pour Dockerize</span><span class="sxs-lookup"><span data-stu-id="a75b7-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="a75b7-111">Exécuter l’exemple d’application ASP.NET localement</span><span class="sxs-lookup"><span data-stu-id="a75b7-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="a75b7-112">Générer et exécuter l’exemple avec Docker pour les conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="a75b7-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="a75b7-113">Générer et exécuter l’exemple avec des conteneurs Docker pour Windows</span><span class="sxs-lookup"><span data-stu-id="a75b7-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="a75b7-114">Optimisations des images Docker</span><span class="sxs-lookup"><span data-stu-id="a75b7-114">Docker Image Optimizations</span></span>

<span data-ttu-id="a75b7-115">Lors de la création d’images Docker pour les développeurs, nous nous sommes concentrés sur trois scénarios principaux :</span><span class="sxs-lookup"><span data-stu-id="a75b7-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="a75b7-116">Images utilisées pour développer des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="a75b7-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="a75b7-117">Images utilisées pour générer des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="a75b7-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="a75b7-118">Images utilisées pour exécuter des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="a75b7-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="a75b7-119">Pourquoi trois images ?</span><span class="sxs-lookup"><span data-stu-id="a75b7-119">Why three images?</span></span>
<span data-ttu-id="a75b7-120">Lorsque le développement, la création et exécution d’applications en conteneur, nous avons des priorités différentes.</span><span class="sxs-lookup"><span data-stu-id="a75b7-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="a75b7-121">**Développement :** les vues de la priorité sur itérer rapidement les modifications et la possibilité de déboguer les modifications.</span><span class="sxs-lookup"><span data-stu-id="a75b7-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="a75b7-122">La taille de l’image n’est pas aussi importante, au lieu de cela pourrez vous apporter des modifications à votre code et les afficher rapidement ?</span><span class="sxs-lookup"><span data-stu-id="a75b7-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="a75b7-123">**Build :** cette image contient tous les éléments nécessaires pour compiler votre application, ce qui inclut le compilateur et autres dépendances pour optimiser les fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="a75b7-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="a75b7-124">L’image de la build vous permet de créer les composants que vous placez dans une image de production.</span><span class="sxs-lookup"><span data-stu-id="a75b7-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="a75b7-125">L’image de la build doit être utilisé pour l’intégration continue, ou dans un environnement de génération.</span><span class="sxs-lookup"><span data-stu-id="a75b7-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="a75b7-126">Cette approche permet à un agent de build compiler et générer l’application (avec toutes les dépendances requises) dans une instance d’image de build.</span><span class="sxs-lookup"><span data-stu-id="a75b7-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="a75b7-127">L’agent de build doit seulement savoir comment exécuter cette image Docker.</span><span class="sxs-lookup"><span data-stu-id="a75b7-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="a75b7-128">**Production :** la vitesse à laquelle vous pouvez déployer et démarrer votre image ?</span><span class="sxs-lookup"><span data-stu-id="a75b7-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="a75b7-129">Cette image est petite afin d’optimiser les performances du réseau à partir de votre Registre Docker à vos hôtes Docker.</span><span class="sxs-lookup"><span data-stu-id="a75b7-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="a75b7-130">Le contenu est prêt à s’exécuter, ce qui permet d’obtenir le temps le plus court entre l’exécution Docker et les résultats du traitement.</span><span class="sxs-lookup"><span data-stu-id="a75b7-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="a75b7-131">Compilation de code dynamique n’est pas nécessaire dans le modèle de Docker.</span><span class="sxs-lookup"><span data-stu-id="a75b7-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="a75b7-132">Le contenu que vous placez dans cette image est limité aux fichiers binaires et au contenu nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="a75b7-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="a75b7-133">Par exemple, le `dotnet publish` sortie contient :</span><span class="sxs-lookup"><span data-stu-id="a75b7-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="a75b7-134">les fichiers binaires compilés</span><span class="sxs-lookup"><span data-stu-id="a75b7-134">the compiled binaries</span></span>
    * <span data-ttu-id="a75b7-135">fichiers .js et .css</span><span class="sxs-lookup"><span data-stu-id="a75b7-135">.js and .css files</span></span>


<span data-ttu-id="a75b7-136">La raison pour inclure la `dotnet publish` sortie de la commande dans votre image de production consiste à conserver son ' taille au minimum.</span><span class="sxs-lookup"><span data-stu-id="a75b7-136">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="a75b7-137">Certaines images .NET Core partagent des couches entre des balises différentes afin de télécharger la dernière balise est un processus relativement simples.</span><span class="sxs-lookup"><span data-stu-id="a75b7-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="a75b7-138">Si vous avez déjà une version antérieure sur votre ordinateur, cette architecture diminue l’espace disque nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a75b7-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="a75b7-139">Lorsque plusieurs applications utilisent des images communes sur le même ordinateur, la mémoire est partagée entre les images courantes.</span><span class="sxs-lookup"><span data-stu-id="a75b7-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="a75b7-140">Les images doivent être identiques pour être partagés.</span><span class="sxs-lookup"><span data-stu-id="a75b7-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="a75b7-141">Variantes des images Docker</span><span class="sxs-lookup"><span data-stu-id="a75b7-141">Docker image variations</span></span>

<span data-ttu-id="a75b7-142">Pour atteindre les objectifs ci-dessus, nous fournissons des variantes d’image sous [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="a75b7-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="a75b7-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Cette image contient le SDK .NET Core, qui inclut le .NET Core et les outils de ligne de commande (CLI).</span><span class="sxs-lookup"><span data-stu-id="a75b7-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="a75b7-144">Cette image est adaptée au **scénario de développement**.</span><span class="sxs-lookup"><span data-stu-id="a75b7-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="a75b7-145">Vous utilisez cette image pour le développement local, de débogage et de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="a75b7-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="a75b7-146">Cette image peut également être utilisée pour vos scénarios de **génération**.</span><span class="sxs-lookup"><span data-stu-id="a75b7-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="a75b7-147">À l’aide de `microsoft/dotnet:sdk` vous donne toujours la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="a75b7-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="a75b7-148">Si vous ne savez pas vos besoins, vous souhaitez utiliser le `microsoft/dotnet:<version>-sdk` image.</span><span class="sxs-lookup"><span data-stu-id="a75b7-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="a75b7-149">Comme « fait », il est conçu pour être utilisé comme une clause throw conteneur absent (monter votre code source et démarrez le conteneur pour démarrer votre application) et en tant que l’image de base pour créer d’autres images à partir de.</span><span class="sxs-lookup"><span data-stu-id="a75b7-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="a75b7-150">`microsoft/dotnet:<version>-runtime`: Cette image contient le .NET Core (runtime et bibliothèques) et est optimisée pour l’exécution des applications .NET Core dans **production**.</span><span class="sxs-lookup"><span data-stu-id="a75b7-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="a75b7-151">Images alternatives</span><span class="sxs-lookup"><span data-stu-id="a75b7-151">Alternative images</span></span>

<span data-ttu-id="a75b7-152">En plus des scénarios de développement, de génération et de production optimisés, nous fournissons des images supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="a75b7-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="a75b7-153">`microsoft/dotnet:<version>-runtime-deps`: Le **Dép. de runtime** image contient le système d’exploitation avec toutes les dépendances natives requis par le .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a75b7-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="a75b7-154">Cette image est pour [applications autonomes](https://docs.microsoft.com/dotnet/core/deploying/index).</span><span class="sxs-lookup"><span data-stu-id="a75b7-154">This image is for [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index).</span></span>

<span data-ttu-id="a75b7-155">Versions les plus récentes de chaque variante :</span><span class="sxs-lookup"><span data-stu-id="a75b7-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="a75b7-156">`microsoft/dotnet`ou `microsoft/dotnet:latest` (alias pour l’image du Kit de développement logiciel)</span><span class="sxs-lookup"><span data-stu-id="a75b7-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="a75b7-157">Pour Explorer les exemples</span><span class="sxs-lookup"><span data-stu-id="a75b7-157">Samples to explore</span></span>

* <span data-ttu-id="a75b7-158">[Cet exemple ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) illustre un modèle pratique meilleures pour générer des images Docker pour ASP.NET Core des applications de production.</span><span class="sxs-lookup"><span data-stu-id="a75b7-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="a75b7-159">L’exemple fonctionne avec les conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="a75b7-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="a75b7-160">Cet exemple de .NET Core Docker montre un modèle pratique meilleures pour [génération Docker images pour les applications .NET Core pour la production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="a75b7-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="a75b7-161">Votre première application ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="a75b7-161">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="a75b7-162">Pour ce didacticiel, vous permet d’utiliser un exemple d’application ASP.NET Core Docker pour l’application que vous souhaitez dockerize.</span><span class="sxs-lookup"><span data-stu-id="a75b7-162">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="a75b7-163">Cet exemple d’application ASP.NET Core Docker illustre un modèle de pratiques meilleures pour générer des images Docker pour ASP.NET Core des applications de production.</span><span class="sxs-lookup"><span data-stu-id="a75b7-163">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="a75b7-164">L’exemple fonctionne avec les conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="a75b7-164">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="a75b7-165">L’exemple de fichier Dockerfile crée une image Docker d’application ASP.NET Core basés sur l’image de base ASP.NET Core Runtime Docker.</span><span class="sxs-lookup"><span data-stu-id="a75b7-165">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="a75b7-166">Elle utilise le [multi-étapes Docker build fonctionnalité](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) à :</span><span class="sxs-lookup"><span data-stu-id="a75b7-166">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="a75b7-167">Générez l’exemple dans un conteneur selon le **supérieure** image de base ASP.NET Core génération Docker</span><span class="sxs-lookup"><span data-stu-id="a75b7-167">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="a75b7-168">copie le résultat de la version finale dans une image Docker basée sur le **plus petits** image de base ASP.NET Core Docker Runtime</span><span class="sxs-lookup"><span data-stu-id="a75b7-168">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!Note]
> <span data-ttu-id="a75b7-169">L’image de build contient les outils requis pour créer des applications n’est pas le cas de l’image d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a75b7-169">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a75b7-170">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a75b7-170">Prerequisites</span></span>

<span data-ttu-id="a75b7-171">Pour générer et exécuter, installez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a75b7-171">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="a75b7-172">.NET core SDK 2.0</span><span class="sxs-lookup"><span data-stu-id="a75b7-172">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="a75b7-173">Installer [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="a75b7-173">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="a75b7-174">Installez votre éditeur favori de code, si vous n’avez pas déjà.</span><span class="sxs-lookup"><span data-stu-id="a75b7-174">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="a75b7-175">Vous avez besoin pour installer un éditeur de code ?</span><span class="sxs-lookup"><span data-stu-id="a75b7-175">Need to install a code editor?</span></span> <span data-ttu-id="a75b7-176">Essayez [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="a75b7-176">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="a75b7-177">L’installation du Client Docker</span><span class="sxs-lookup"><span data-stu-id="a75b7-177">Installing Docker Client</span></span>

<span data-ttu-id="a75b7-178">Installer [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou une version ultérieure du client Docker.</span><span class="sxs-lookup"><span data-stu-id="a75b7-178">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="a75b7-179">Le client Docker peut être installé dans :</span><span class="sxs-lookup"><span data-stu-id="a75b7-179">The Docker client can be installed in:</span></span>

* <span data-ttu-id="a75b7-180">Distributions Linux</span><span class="sxs-lookup"><span data-stu-id="a75b7-180">Linux distributions</span></span>

   * [<span data-ttu-id="a75b7-181">CentOS</span><span class="sxs-lookup"><span data-stu-id="a75b7-181">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="a75b7-182">Debian</span><span class="sxs-lookup"><span data-stu-id="a75b7-182">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="a75b7-183">Fedora</span><span class="sxs-lookup"><span data-stu-id="a75b7-183">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="a75b7-184">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a75b7-184">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="a75b7-185">macOS</span><span class="sxs-lookup"><span data-stu-id="a75b7-185">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="a75b7-186">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="a75b7-186">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="a75b7-187">L’installation de Git pour le dépôt d’exemples</span><span class="sxs-lookup"><span data-stu-id="a75b7-187">Installing Git for sample repository</span></span>

* <span data-ttu-id="a75b7-188">Installer [git](https://git-scm.com/download) si vous souhaitez cloner le référentiel.</span><span class="sxs-lookup"><span data-stu-id="a75b7-188">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="a75b7-189">Mise en route de l’exemple d’application</span><span class="sxs-lookup"><span data-stu-id="a75b7-189">Getting the sample application</span></span>

<span data-ttu-id="a75b7-190">Pour obtenir l’exemple le plus simple est en clonant la [référentiel d’exemples](https://github.com/dotnet/dotnet-docker-samples) avec git, utilisez la procédure suivante :</span><span class="sxs-lookup"><span data-stu-id="a75b7-190">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="a75b7-191">Vous pouvez également télécharger le référentiel (elle est petite) comme un fichier zip à partir du référentiel d’exemples .NET Core Docker.</span><span class="sxs-lookup"><span data-stu-id="a75b7-191">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="a75b7-192">Exécutez l’application ASP.NET localement</span><span class="sxs-lookup"><span data-stu-id="a75b7-192">Run the ASP.NET app locally</span></span>

<span data-ttu-id="a75b7-193">Pour établir un point de référence, avant de mettre l’application dans un conteneur, exécutez l’application localement.</span><span class="sxs-lookup"><span data-stu-id="a75b7-193">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="a75b7-194">Vous pouvez générer et exécuter l’application localement avec le .NET Core 2.0 SDK à l’aide des commandes suivantes (les instructions supposent la racine du référentiel) :</span><span class="sxs-lookup"><span data-stu-id="a75b7-194">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="a75b7-195">Une fois que l’application démarre, visitez **http://localhost : 5000** dans votre navigateur web.</span><span class="sxs-lookup"><span data-stu-id="a75b7-195">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="a75b7-196">Générer et exécuter l’exemple avec Docker pour les conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="a75b7-196">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="a75b7-197">Vous pouvez générer et exécuter l’exemple dans Docker à l’aide de conteneurs Linux à l’aide des commandes suivantes (les instructions supposent la racine du référentiel) :</span><span class="sxs-lookup"><span data-stu-id="a75b7-197">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] <span data-ttu-id="a75b7-198">Le `docker run` '-p' argument mappages de port 5000 sur votre ordinateur local vers le port 80 dans le conteneur (la forme de mappage de port est `host:container`).</span><span class="sxs-lookup"><span data-stu-id="a75b7-198">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="a75b7-199">Pour plus d’informations, consultez la [docker exécuter](https://docs.docker.com/engine/reference/commandline/exec/) référence sur les paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a75b7-199">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="a75b7-200">Une fois que l’application démarre, visitez **http://localhost : 5000** dans votre navigateur web.</span><span class="sxs-lookup"><span data-stu-id="a75b7-200">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="a75b7-201">Générer et exécuter l’exemple avec des conteneurs Docker pour Windows</span><span class="sxs-lookup"><span data-stu-id="a75b7-201">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="a75b7-202">Vous pouvez générer et exécuter l’exemple dans Docker à l’aide de conteneurs Windows à l’aide des commandes suivantes (les instructions supposent la racine du référentiel) :</span><span class="sxs-lookup"><span data-stu-id="a75b7-202">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="a75b7-203">Vous devez naviguer jusqu'à la **adresse IP de conteneur** (par opposition à http://localhost) dans votre navigateur directement lors de l’utilisation de conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="a75b7-203">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="a75b7-204">Vous pouvez obtenir l’adresse IP de votre conteneur en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="a75b7-204">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="a75b7-205">Ouvrez une autre invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="a75b7-205">Open up another command prompt.</span></span>
* <span data-ttu-id="a75b7-206">Exécutez `docker ps` pour voir vos conteneurs en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a75b7-206">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="a75b7-207">Le conteneur « aspnetcore_sample » doit être visible.</span><span class="sxs-lookup"><span data-stu-id="a75b7-207">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="a75b7-208">Exécutez `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="a75b7-208">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="a75b7-209">Copiez l’adresse IP de conteneur et le coller dans votre navigateur (par exemple, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="a75b7-209">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!Note]
> <span data-ttu-id="a75b7-210">Exec de docker prend en charge l’identification des conteneurs avec le nom ou le hachage.</span><span class="sxs-lookup"><span data-stu-id="a75b7-210">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="a75b7-211">Dans notre exemple, le nom (aspnetcore_sample) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a75b7-211">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="a75b7-212">Consultez l’exemple suivant illustrant comment obtenir l’adresse IP d’un conteneur Windows en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a75b7-212">See the following example of how to get the IP address of a running Windows container.</span></span>

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> <span data-ttu-id="a75b7-213">Exec de docker s’exécute une commande dans un conteneur en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a75b7-213">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="a75b7-214">Pour plus d’informations, consultez la [référence exec de docker](https://docs.docker.com/engine/reference/commandline/exec/) sur les paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a75b7-214">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="a75b7-215">Vous pouvez générer une application qui est prête à déployer en production localement à l’aide de la [dotnet publier](../tools/dotnet-publish.md) commande.</span><span class="sxs-lookup"><span data-stu-id="a75b7-215">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!Note]
> <span data-ttu-id="a75b7-216">L’argument de version - c génère l’application en mode version finale (la valeur par défaut est le mode débogage).</span><span class="sxs-lookup"><span data-stu-id="a75b7-216">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="a75b7-217">Pour plus d’informations, consultez la [dotnet exécuter référence](../tools/dotnet-run.md) sur les paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a75b7-217">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="a75b7-218">Vous pouvez exécuter l’application sur **Windows** à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="a75b7-218">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="a75b7-219">Vous pouvez exécuter l’application sur **Linux** ou **macOS** à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="a75b7-219">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="a75b7-220">Docker Images utilisées dans cet exemple</span><span class="sxs-lookup"><span data-stu-id="a75b7-220">Docker Images used in this sample</span></span>

<span data-ttu-id="a75b7-221">Les images Docker suivantes sont utilisées dans cet exemple</span><span class="sxs-lookup"><span data-stu-id="a75b7-221">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="a75b7-222">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="a75b7-222">Congratulations!</span></span> <span data-ttu-id="a75b7-223">Vous devez simplement :</span><span class="sxs-lookup"><span data-stu-id="a75b7-223">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a75b7-224">Appris sur les images de Microsoft .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="a75b7-224">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="a75b7-225">Vous avez une ASP.NET Core exemple d’application pour Dockerize</span><span class="sxs-lookup"><span data-stu-id="a75b7-225">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="a75b7-226">Exécution de l’exemple d’application ASP.NET localement</span><span class="sxs-lookup"><span data-stu-id="a75b7-226">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="a75b7-227">Créer et exécuter l’exemple avec Docker pour les conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="a75b7-227">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="a75b7-228">Créer et exécuter l’exemple avec des conteneurs Docker pour Windows</span><span class="sxs-lookup"><span data-stu-id="a75b7-228">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="a75b7-229">**Étapes suivantes**</span><span class="sxs-lookup"><span data-stu-id="a75b7-229">**Next Steps**</span></span>

<span data-ttu-id="a75b7-230">Voici quelques astuces que vous pouvez effectuer :</span><span class="sxs-lookup"><span data-stu-id="a75b7-230">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="a75b7-231">Utilisation des outils de Visual Studio Docker</span><span class="sxs-lookup"><span data-stu-id="a75b7-231">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="a75b7-232">Déploiement d’Images Docker à partir du Registre de conteneur Azure pour les Instances du conteneur Azure</span><span class="sxs-lookup"><span data-stu-id="a75b7-232">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="a75b7-233">Débogage avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a75b7-233">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="a75b7-234">Prise en mains avec Visual Studio pour Mac, les conteneurs et sans code dans le cloud</span><span class="sxs-lookup"><span data-stu-id="a75b7-234">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="a75b7-235">Prise en main Docker et Visual Studio pour Mac Lab</span><span class="sxs-lookup"><span data-stu-id="a75b7-235">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> <span data-ttu-id="a75b7-236">Si vous n’avez pas d’un abonnement Azure, [Inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour un compte gratuit de 30 jours et un get 200 $ de crédits Azure permettant de tester n’importe quelle combinaison de services Azure.</span><span class="sxs-lookup"><span data-stu-id="a75b7-236">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
