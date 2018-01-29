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
ms.workload:
- dotnetcore
ms.openlocfilehash: 2b1a57fe264eda0a4d3186c7be8b0de01bd5f0a9
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="567d3-104">Création d’images Docker pour les applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="567d3-104">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="567d3-105">Dans ce didacticiel, nous nous concentrons sur l’utilisation de .NET Core sur Docker.</span><span class="sxs-lookup"><span data-stu-id="567d3-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="567d3-106">Tout d’abord, nous explorons les différentes images Docker proposées et gérées par Microsoft, ainsi que les cas d’usage.</span><span class="sxs-lookup"><span data-stu-id="567d3-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="567d3-107">Nous découvrons ensuite comment générer et dockeriser une application ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="567d3-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="567d3-108">Au cours de ce didacticiel, vous apprenez à :</span><span class="sxs-lookup"><span data-stu-id="567d3-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="567d3-109">Découvrir les images Docker Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="567d3-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="567d3-110">Obtenir un exemple d’application ASP.NET Core à dockeriser</span><span class="sxs-lookup"><span data-stu-id="567d3-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="567d3-111">Exécuter l’exemple d’application ASP.NET localement</span><span class="sxs-lookup"><span data-stu-id="567d3-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="567d3-112">Générer et exécuter l’exemple avec Docker pour des conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="567d3-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="567d3-113">Générer et exécuter l’exemple avec Docker pour des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="567d3-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="567d3-114">Optimisations des images Docker</span><span class="sxs-lookup"><span data-stu-id="567d3-114">Docker Image Optimizations</span></span>

<span data-ttu-id="567d3-115">Lors de la création d’images Docker pour les développeurs, nous nous sommes concentrés sur trois scénarios principaux :</span><span class="sxs-lookup"><span data-stu-id="567d3-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="567d3-116">Images utilisées pour développer des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="567d3-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="567d3-117">Images utilisées pour générer des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="567d3-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="567d3-118">Images utilisées pour exécuter des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="567d3-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="567d3-119">Pourquoi trois images ?</span><span class="sxs-lookup"><span data-stu-id="567d3-119">Why three images?</span></span>
<span data-ttu-id="567d3-120">Lors du développement, de la génération et de l’exécution d’applications en conteneur, nous avons des priorités différentes.</span><span class="sxs-lookup"><span data-stu-id="567d3-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="567d3-121">**Développement :** la priorité porte sur la rapidité avec laquelle vous pouvez apporter des modifications de façon itérative, et la possibilité de déboguer les modifications.</span><span class="sxs-lookup"><span data-stu-id="567d3-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="567d3-122">La taille de l’image est moins importante que la possibilité d’apporter des modifications à votre code et de les voir rapidement.</span><span class="sxs-lookup"><span data-stu-id="567d3-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="567d3-123">**Génération :** cette image contient tous les éléments nécessaires pour compiler votre application, ce qui inclut le compilateur et toutes les autres dépendances pour optimiser les fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="567d3-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="567d3-124">L’image de build vous permet de créer les ressources que vous placez dans une image de production.</span><span class="sxs-lookup"><span data-stu-id="567d3-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="567d3-125">Cette image est destinée à être utilisée dans une intégration continue ou dans un environnement de génération.</span><span class="sxs-lookup"><span data-stu-id="567d3-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="567d3-126">Cette approche permet à un agent de build de compiler et générer l’application (avec toutes les dépendances requises) dans une instance d’image de build.</span><span class="sxs-lookup"><span data-stu-id="567d3-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="567d3-127">L’agent de build doit seulement savoir comment exécuter cette image Docker.</span><span class="sxs-lookup"><span data-stu-id="567d3-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="567d3-128">**Production :** la rapidité avec laquelle vous pouvez déployer et démarrer votre image.</span><span class="sxs-lookup"><span data-stu-id="567d3-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="567d3-129">Comme cette image est de petite taille, les performances réseau entre votre Registre Docker et vos hôtes Docker sont optimisées.</span><span class="sxs-lookup"><span data-stu-id="567d3-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="567d3-130">Le contenu est prêt à s’exécuter, ce qui permet d’obtenir le temps le plus court entre l’exécution Docker et les résultats du traitement.</span><span class="sxs-lookup"><span data-stu-id="567d3-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="567d3-131">La compilation de code dynamique n’est pas nécessaire dans le modèle Docker.</span><span class="sxs-lookup"><span data-stu-id="567d3-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="567d3-132">Le contenu que vous placez dans cette image est limité aux fichiers binaires et au contenu nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="567d3-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="567d3-133">Par exemple, la sortie `dotnet publish` contient :</span><span class="sxs-lookup"><span data-stu-id="567d3-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="567d3-134">les fichiers binaires compilés</span><span class="sxs-lookup"><span data-stu-id="567d3-134">the compiled binaries</span></span>
    * <span data-ttu-id="567d3-135">les fichiers .js et .css</span><span class="sxs-lookup"><span data-stu-id="567d3-135">.js and .css files</span></span>


<span data-ttu-id="567d3-136">Il est utile d’inclure la sortie de la commande `dotnet publish` dans votre image de production si vous voulez conserver sa taille au minimum.</span><span class="sxs-lookup"><span data-stu-id="567d3-136">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="567d3-137">Certaines images .NET Core partagent des couches entre différentes balises pour que le téléchargement de la dernière balise soit un processus relativement simple.</span><span class="sxs-lookup"><span data-stu-id="567d3-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="567d3-138">Si vous avez déjà une version antérieure sur votre ordinateur, cette architecture diminue l’espace disque nécessaire.</span><span class="sxs-lookup"><span data-stu-id="567d3-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="567d3-139">Quand plusieurs applications utilisent des images communes sur le même ordinateur, la mémoire est partagée entre ces images.</span><span class="sxs-lookup"><span data-stu-id="567d3-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="567d3-140">Les images doivent être identiques pour être partagées.</span><span class="sxs-lookup"><span data-stu-id="567d3-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="567d3-141">Variantes des images Docker</span><span class="sxs-lookup"><span data-stu-id="567d3-141">Docker image variations</span></span>

<span data-ttu-id="567d3-142">Pour atteindre les objectifs ci-dessus, nous fournissons des variantes d’images sous [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="567d3-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="567d3-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Cette image contient le kit SDK .NET Core, qui inclut .NET Core et les outils en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="567d3-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="567d3-144">Cette image est adaptée au **scénario de développement**.</span><span class="sxs-lookup"><span data-stu-id="567d3-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="567d3-145">Vous utilisez cette image pour le développement local, le débogage et les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="567d3-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="567d3-146">Cette image peut également être utilisée pour vos scénarios de **génération**.</span><span class="sxs-lookup"><span data-stu-id="567d3-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="567d3-147">L’utilisation de `microsoft/dotnet:sdk` vous donne toujours la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="567d3-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="567d3-148">Si vous ne savez pas de quoi vous avez besoin, vous pouvez utiliser l’image `microsoft/dotnet:<version>-sdk`.</span><span class="sxs-lookup"><span data-stu-id="567d3-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="567d3-149">En tant qu’image « de facto », elle est conçue pour être utilisée comme conteneur jetable (montez votre code source et démarrez le conteneur pour démarrer votre application) et comme image de base à partir de laquelle générer d’autres images.</span><span class="sxs-lookup"><span data-stu-id="567d3-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="567d3-150">`microsoft/dotnet:<version>-runtime` : cette image contient .NET Core (runtime et bibliothèques) et est optimisée pour l’exécution des applications .NET Core en **production**.</span><span class="sxs-lookup"><span data-stu-id="567d3-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="567d3-151">Images alternatives</span><span class="sxs-lookup"><span data-stu-id="567d3-151">Alternative images</span></span>

<span data-ttu-id="567d3-152">En plus des scénarios de développement, de génération et de production optimisés, nous fournissons des images supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="567d3-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="567d3-153">`microsoft/dotnet:<version>-runtime-deps` : l’image **runtime-deps** contient le système d’exploitation avec toutes les dépendances natives nécessaires à .NET Core.</span><span class="sxs-lookup"><span data-stu-id="567d3-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="567d3-154">Cette image est destinée aux [applications autonomes](https://docs.microsoft.com/dotnet/core/deploying/index).</span><span class="sxs-lookup"><span data-stu-id="567d3-154">This image is for [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index).</span></span>

<span data-ttu-id="567d3-155">Versions les plus récentes de chaque variante :</span><span class="sxs-lookup"><span data-stu-id="567d3-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="567d3-156">`microsoft/dotnet` ou `microsoft/dotnet:latest` (alias pour l’image du kit SDK)</span><span class="sxs-lookup"><span data-stu-id="567d3-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="567d3-157">Exemples à explorer</span><span class="sxs-lookup"><span data-stu-id="567d3-157">Samples to explore</span></span>

* <span data-ttu-id="567d3-158">[Cet exemple d’ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) montre un modèle des meilleures pratiques pour la création d’images Docker pour les applications ASP.NET Core pour la production.</span><span class="sxs-lookup"><span data-stu-id="567d3-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="567d3-159">L’exemple s’applique aux conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="567d3-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="567d3-160">Cet exemple de Docker .NET Core montre un modèle des meilleures pratiques pour la [création d’images Docker pour les applications .NET Core pour la production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="567d3-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="567d3-161">Votre première application Docker ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="567d3-161">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="567d3-162">Pour ce didacticiel, utilisons un exemple d’application Docker ASP.NET Core pour l’application à dockeriser.</span><span class="sxs-lookup"><span data-stu-id="567d3-162">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="567d3-163">Cet exemple d’application Docker ASP.NET Core montre un modèle de bonnes pratiques de création d’images Docker pour les applications ASP.NET Core destinées à la production.</span><span class="sxs-lookup"><span data-stu-id="567d3-163">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="567d3-164">L’exemple s’applique aux conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="567d3-164">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="567d3-165">L’exemple de fichier Dockerfile crée une image Docker d’application ASP.NET Core basée sur l’image de base Docker de runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="567d3-165">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="567d3-166">Il utilise la [fonctionnalité de build en plusieurs étapes Docker](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) pour :</span><span class="sxs-lookup"><span data-stu-id="567d3-166">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="567d3-167">Générer l’exemple dans un conteneur selon l’image de base Docker de build ASP.NET Core **la plus grande**</span><span class="sxs-lookup"><span data-stu-id="567d3-167">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="567d3-168">Copier le résultat de la build finale dans une image Docker basée sur l’image de base Docker de runtime ASP.NET Core **la plus petite**</span><span class="sxs-lookup"><span data-stu-id="567d3-168">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="567d3-169">L’image de build contient les outils requis pour créer des applications, contrairement à l’image de runtime.</span><span class="sxs-lookup"><span data-stu-id="567d3-169">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="567d3-170">Prérequis</span><span class="sxs-lookup"><span data-stu-id="567d3-170">Prerequisites</span></span>

<span data-ttu-id="567d3-171">Pour générer et exécuter, installez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="567d3-171">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="567d3-172">Kit SDK .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="567d3-172">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="567d3-173">Installez le [Kit SDK .NET Core 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="567d3-173">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="567d3-174">Installez votre éditeur de code favori, si ce n’est pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="567d3-174">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="567d3-175">Vous avez besoin d’installer un éditeur de code ?</span><span class="sxs-lookup"><span data-stu-id="567d3-175">Need to install a code editor?</span></span> <span data-ttu-id="567d3-176">Essayez [Visual Studio](https://visualstudio.com/downloads) !</span><span class="sxs-lookup"><span data-stu-id="567d3-176">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="567d3-177">Installation du client Docker</span><span class="sxs-lookup"><span data-stu-id="567d3-177">Installing Docker Client</span></span>

<span data-ttu-id="567d3-178">Installez la version [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou ultérieure du client Docker.</span><span class="sxs-lookup"><span data-stu-id="567d3-178">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="567d3-179">Le client Docker peut être installé dans :</span><span class="sxs-lookup"><span data-stu-id="567d3-179">The Docker client can be installed in:</span></span>

* <span data-ttu-id="567d3-180">Distributions Linux</span><span class="sxs-lookup"><span data-stu-id="567d3-180">Linux distributions</span></span>

   * [<span data-ttu-id="567d3-181">CentOS</span><span class="sxs-lookup"><span data-stu-id="567d3-181">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="567d3-182">Debian</span><span class="sxs-lookup"><span data-stu-id="567d3-182">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="567d3-183">Fedora</span><span class="sxs-lookup"><span data-stu-id="567d3-183">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="567d3-184">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="567d3-184">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="567d3-185">macOS</span><span class="sxs-lookup"><span data-stu-id="567d3-185">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="567d3-186">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="567d3-186">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="567d3-187">Installation de Git pour un dépôt d’exemples</span><span class="sxs-lookup"><span data-stu-id="567d3-187">Installing Git for sample repository</span></span>

* <span data-ttu-id="567d3-188">Installez [git](https://git-scm.com/download) si vous souhaitez cloner le dépôt.</span><span class="sxs-lookup"><span data-stu-id="567d3-188">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="567d3-189">Obtention de l’exemple d’application</span><span class="sxs-lookup"><span data-stu-id="567d3-189">Getting the sample application</span></span>

<span data-ttu-id="567d3-190">La façon la plus simple d’obtenir l’exemple consiste à cloner le [dépôt d’exemples](https://github.com/dotnet/dotnet-docker-samples) avec git, en utilisant les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="567d3-190">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="567d3-191">Vous pouvez également télécharger le dépôt (qui est petit) comme un fichier zip à partir du dépôt d’exemples Docker .NET Core.</span><span class="sxs-lookup"><span data-stu-id="567d3-191">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="567d3-192">Exécuter l’application ASP.NET localement</span><span class="sxs-lookup"><span data-stu-id="567d3-192">Run the ASP.NET app locally</span></span>

<span data-ttu-id="567d3-193">Pour établir un point de référence, avant de mettre l’application dans un conteneur, exécutez l’application localement.</span><span class="sxs-lookup"><span data-stu-id="567d3-193">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="567d3-194">Vous pouvez générer et exécuter l’application localement avec le kit SDK .NET Core 2.0 à l’aide des commandes suivantes (les instructions supposent la racine du dépôt) :</span><span class="sxs-lookup"><span data-stu-id="567d3-194">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="567d3-195">Une fois que l’application démarre, accédez à **http://localhost:5000** dans votre navigateur web.</span><span class="sxs-lookup"><span data-stu-id="567d3-195">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="567d3-196">Générer et exécuter l’exemple avec Docker pour des conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="567d3-196">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="567d3-197">Vous pouvez générer et exécuter l’exemple dans Docker avec des conteneurs Linux à l’aide des commandes suivantes (les instructions supposent la racine du dépôt) :</span><span class="sxs-lookup"><span data-stu-id="567d3-197">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="567d3-198">L’argument `docker run` '-p' mappe le port 5000 sur votre ordinateur local au port 80 dans le conteneur (la forme de mappage de port est `host:container`).</span><span class="sxs-lookup"><span data-stu-id="567d3-198">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="567d3-199">Pour plus d’informations, consultez la référence [docker run](https://docs.docker.com/engine/reference/commandline/exec/) dans les paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="567d3-199">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="567d3-200">Une fois que l’application démarre, accédez à **http://localhost:5000** dans votre navigateur web.</span><span class="sxs-lookup"><span data-stu-id="567d3-200">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="567d3-201">Générer et exécuter l’exemple avec Docker pour des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="567d3-201">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="567d3-202">Vous pouvez générer et exécuter l’exemple dans Docker avec des conteneurs Windows à l’aide des commandes suivantes (les instructions supposent la racine du dépôt) :</span><span class="sxs-lookup"><span data-stu-id="567d3-202">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="567d3-203">Vous devez accéder directement à **l’adresse IP de conteneur** (par opposition à http://localhost) dans votre navigateur lors de l’utilisation de conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="567d3-203">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="567d3-204">Vous pouvez obtenir l’adresse IP de votre conteneur en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="567d3-204">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="567d3-205">Ouvrez une autre invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="567d3-205">Open up another command prompt.</span></span>
* <span data-ttu-id="567d3-206">Exécutez `docker ps` pour voir vos conteneurs en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="567d3-206">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="567d3-207">Le conteneur « aspnetcore_sample » doit être visible.</span><span class="sxs-lookup"><span data-stu-id="567d3-207">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="567d3-208">Exécutez `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="567d3-208">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="567d3-209">Copiez l’adresse IP de conteneur et collez-la dans votre navigateur (par exemple, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="567d3-209">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="567d3-210">Docker exec prend en charge l’identification des conteneurs avec le nom ou le hachage.</span><span class="sxs-lookup"><span data-stu-id="567d3-210">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="567d3-211">Dans notre exemple, le nom (aspnetcore_sample) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="567d3-211">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="567d3-212">Consultez l’exemple suivant illustrant comment obtenir l’adresse IP d’un conteneur Windows en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="567d3-212">See the following example of how to get the IP address of a running Windows container.</span></span>

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

> [!NOTE]
> <span data-ttu-id="567d3-213">Docker exec exécute une nouvelle commande dans un conteneur en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="567d3-213">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="567d3-214">Pour plus d’informations, consultez la [référence docker exec](https://docs.docker.com/engine/reference/commandline/exec/) dans les paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="567d3-214">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="567d3-215">Vous pouvez générer une application qui est prête à être déployée en production localement à l’aide de la commande [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="567d3-215">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!NOTE]
> <span data-ttu-id="567d3-216">L’argument -c release génère l’application en mode mise en production (la valeur par défaut est le mode débogage).</span><span class="sxs-lookup"><span data-stu-id="567d3-216">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="567d3-217">Pour plus d’informations, consultez la [référence dotnet run](../tools/dotnet-run.md) dans les paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="567d3-217">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="567d3-218">Vous pouvez exécuter l’application sur **Windows** à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="567d3-218">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="567d3-219">Vous pouvez exécuter l’application sur **Linux** ou **macOS** à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="567d3-219">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="567d3-220">Images Docker utilisées dans cet exemple</span><span class="sxs-lookup"><span data-stu-id="567d3-220">Docker Images used in this sample</span></span>

<span data-ttu-id="567d3-221">Les images Docker suivantes sont utilisées dans cet exemple</span><span class="sxs-lookup"><span data-stu-id="567d3-221">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="567d3-222">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="567d3-222">Congratulations!</span></span> <span data-ttu-id="567d3-223">Vous venez de :</span><span class="sxs-lookup"><span data-stu-id="567d3-223">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="567d3-224">Découvrir les images Docker Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="567d3-224">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="567d3-225">Obtenir un exemple d’application ASP.NET Core à dockeriser</span><span class="sxs-lookup"><span data-stu-id="567d3-225">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="567d3-226">Exécuter l’exemple d’application ASP.NET localement</span><span class="sxs-lookup"><span data-stu-id="567d3-226">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="567d3-227">Générer et exécuter l’exemple avec Docker pour des conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="567d3-227">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="567d3-228">Générer et exécuter l’exemple avec Docker pour des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="567d3-228">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="567d3-229">**Étapes suivantes**</span><span class="sxs-lookup"><span data-stu-id="567d3-229">**Next Steps**</span></span>

<span data-ttu-id="567d3-230">Voici quelques étapes suivantes que vous pouvez effectuer :</span><span class="sxs-lookup"><span data-stu-id="567d3-230">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="567d3-231">Utilisation des outils Docker dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="567d3-231">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="567d3-232">Déploiement d’images Docker à partir du Registre de conteneurs Azure dans Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="567d3-232">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="567d3-233">Débogage avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="567d3-233">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="567d3-234">Prise en main de Visual Studio pour Mac, les conteneurs et le code serverless dans le cloud</span><span class="sxs-lookup"><span data-stu-id="567d3-234">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="567d3-235">Bien démarrer avec Docker et Visual Studio pour Mac Lab</span><span class="sxs-lookup"><span data-stu-id="567d3-235">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="567d3-236">Si vous ne disposez pas d’abonnement Azure, [inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour obtenir un compte gratuit pendant 30 jours et 200 dollars US en crédits Azure pour essayer une combinaison quelconque de services Azure.</span><span class="sxs-lookup"><span data-stu-id="567d3-236">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
