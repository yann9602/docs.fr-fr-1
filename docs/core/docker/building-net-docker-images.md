---
title: "Création d’images Docker .NET Core"
description: "Présentation des images Docker et de .NET Core"
keywords: .NET, .NET Core, Docker
author: spboyer
ms.author: shboyer
ms.date: 08/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.translationtype: HT
ms.sourcegitcommit: 2762cdc983465979a530192716c33de7044dd1ed
ms.openlocfilehash: 252b67a528b9cc666a5353b7c4a4c7e2c488e7af
ms.contentlocale: fr-fr
ms.lasthandoff: 08/04/2017

---
 

#<a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="b2f5e-104">Création d’images Docker pour les applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2f5e-104">Building Docker Images for .NET Core Applications</span></span>

<span data-ttu-id="b2f5e-105">Pour comprendre comment utiliser .NET Core et Docker ensemble, nous devons d’abord examiner les différentes images Docker qui sont proposées et comment choisir celle qui convient.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-105">In order to get an understanding of how to use .NET Core and Docker together, we must first get to know the different Docker images that are offered and when is the right use case for them.</span></span> <span data-ttu-id="b2f5e-106">Nous allons ici parcourir les variantes proposées, créer une API Web Core ASP.NET, utiliser les outils Docker Yeoman pour créer un conteneur pouvant être débogué, et regarder comment Visual Studio Code peut apporter une aide au cours du processus.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-106">Here we will walk through the variations offered, build an ASP.NET Core Web API, use the Yeoman Docker tools to create a debuggable container as well as peek at how Visual Studio Code can assist in the process.</span></span> 

## <a name="docker-image-optimizations"></a><span data-ttu-id="b2f5e-107">Optimisations des images Docker</span><span class="sxs-lookup"><span data-stu-id="b2f5e-107">Docker Image Optimizations</span></span>

<span data-ttu-id="b2f5e-108">Lors de la création d’images Docker pour les développeurs, nous nous sommes concentrés sur trois scénarios principaux :</span><span class="sxs-lookup"><span data-stu-id="b2f5e-108">When building Docker images for developers, we focused on three main scenarios:</span></span>

- <span data-ttu-id="b2f5e-109">Images utilisées pour développer des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2f5e-109">Images used to develop .NET Core apps</span></span>
- <span data-ttu-id="b2f5e-110">Images utilisées pour générer des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2f5e-110">Images used to build .NET Core apps</span></span>
- <span data-ttu-id="b2f5e-111">Images utilisées pour exécuter des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2f5e-111">Images used to run .NET Core apps</span></span>

<span data-ttu-id="b2f5e-112">Pourquoi trois images ?</span><span class="sxs-lookup"><span data-stu-id="b2f5e-112">Why three images?</span></span>
<span data-ttu-id="b2f5e-113">Lors du développement, de la génération et de l’exécution d’applications en conteneur, nous avons des priorités différentes.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-113">When developing, building and running containerized applications, we have different priorities.</span></span>
- <span data-ttu-id="b2f5e-114">**Développement :** la rapidité avec laquelle vous pouvez apporter des modifications de façon itérative, et la possibilité de déboguer les modifications.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-114">**Development:**  How fast can you iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="b2f5e-115">La taille de l’image est moins importante que la possibilité d’apporter des modifications à votre code et de les voir rapidement.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-115">The size of the image isn't as important, rather can you make changes to your code and see them quickly.</span></span> <span data-ttu-id="b2f5e-116">Certains de nos outils, comme [yo docker](https://aka.ms/yodocker) destiné à Visual Studio Code, utilisent cette image pendant la phase de développement.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-116">Some of our tools, like [yo docker](https://aka.ms/yodocker) for use in Visual Studio Code use this image during development time.</span></span> 
- <span data-ttu-id="b2f5e-117">**Génération :** ce qui est nécessaire pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-117">**Build:** What's needed to compile your app.</span></span> <span data-ttu-id="b2f5e-118">Ceci inclut le compilateur et toutes les autres dépendances pour optimiser les fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-118">This includes the compiler and any other dependencies to optimize the binaries.</span></span> <span data-ttu-id="b2f5e-119">Cette image n’est pas l’image que vous déployez : il s’agit d’une image que vous utilisez pour générer le contenu que vous placez dans une image de production.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-119">This image isn't the image you deploy, rather it's an image you use to build the content you place into a production image.</span></span> <span data-ttu-id="b2f5e-120">Cette image est destinée à être utilisée dans votre intégration continue ou votre environnement de génération.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-120">This image would be used in your continuous integration, or build environment.</span></span> <span data-ttu-id="b2f5e-121">Par exemple, au lieu d’installer toutes les dépendances directement sur un agent de build, l’agent de build instancie une image de build pour compiler l’application avec toutes les dépendances nécessaires pour générer l’application contenue dans l’image.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-121">For instance, rather than installing all the dependencies directly on a build agent, the build agent would instance a build image to compile the application with all the dependencies required to build the app contained within the image.</span></span> <span data-ttu-id="b2f5e-122">L’agent de build doit seulement savoir comment exécuter cette image Docker.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-122">Your build agent only needs to know how to run this Docker image.</span></span> 
- <span data-ttu-id="b2f5e-123">**Production :** la rapidité avec laquelle vous pouvez déployer et démarrer votre image.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-123">**Production:** How fast you can deploy and start your image.</span></span> <span data-ttu-id="b2f5e-124">Cette image est de petite taille et elle peut donc transiter rapidement sur le réseau de votre Registre Docker à vos hôtes Docker.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-124">This image is small so it can quickly travel across the network from your Docker Registry to your Docker hosts.</span></span> <span data-ttu-id="b2f5e-125">Le contenu est prêt à s’exécuter, ce qui permet d’obtenir le temps le plus court entre l’exécution Docker et les résultats du traitement.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-125">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="b2f5e-126">Dans le modèle Docker non modifiable, la compilation dynamique du code n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-126">In the immutable Docker model, there's no need for dynamic compilation of code.</span></span> <span data-ttu-id="b2f5e-127">Le contenu que vous placez dans cette image est limité aux fichiers binaires et au contenu nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-127">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span> <span data-ttu-id="b2f5e-128">Par exemple, la sortie publiée en utilisant `dotnet publish`, qui contient les fichiers binaires, les images, et les fichiers .js et .css compilés.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-128">For example, the published output using `dotnet publish` which contains the compiled binaries, images, .js and .css files.</span></span> <span data-ttu-id="b2f5e-129">Au fil du temps, vous allez voir des images qui contiennent des packages prétraités avec JiT.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-129">Over time, you'll see images that contain pre-jitted packages.</span></span>  

<span data-ttu-id="b2f5e-130">Bien qu’il existe plusieurs versions de l’image .NET Core, elles partagent toutes une ou plusieurs couches.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-130">Though there are multiple versions of the .NET Core image, they all share one or more layers.</span></span> <span data-ttu-id="b2f5e-131">La quantité d’espace disque nécessaire pour stocker ou le delta à extraire de votre Registre sont beaucoup plus petits que la totalité car toutes les images partagent la même couche de base et potentiellement d’autres couches.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-131">The amount of disk space needed to store or the delta to pull from your registry is much smaller than the whole because all of the images share the same base layer and potentially others.</span></span>  

## <a name="docker-image-variations"></a><span data-ttu-id="b2f5e-132">Variantes des images Docker</span><span class="sxs-lookup"><span data-stu-id="b2f5e-132">Docker image variations</span></span>

<span data-ttu-id="b2f5e-133">Pour atteindre les objectifs ci-dessus, nous fournissons des variantes d’images sous [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="b2f5e-133">To achieve the goals above, we provide image variants under [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

- <span data-ttu-id="b2f5e-134">`microsoft/dotnet:<version>-sdk` : c’est-à-dire **microsoft/dotnet:1.0.0-preview2-sdk**, cette image contient le SDK .NET Core, qui inclut le .NET Core et les outils de ligne de commande (CLI).</span><span class="sxs-lookup"><span data-stu-id="b2f5e-134">`microsoft/dotnet:<version>-sdk` : that is **microsoft/dotnet:1.0.0-preview2-sdk**, this image contains the .NET Core SDK which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="b2f5e-135">Cette image est adaptée au **scénario de développement**.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-135">This image maps to the **development scenario**.</span></span> <span data-ttu-id="b2f5e-136">Vous utilisez cette image pour le développement local, le débogage et les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-136">You would use this image for local development, debugging and unit testing.</span></span> <span data-ttu-id="b2f5e-137">Par exemple, tous les développements que vous faites, avant d’archiver votre code.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-137">For example, all the development you do, before you check in your code.</span></span> <span data-ttu-id="b2f5e-138">Cette image peut également être utilisée pour vos scénarios de **génération**.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-138">This image can also be used for your **build** scenarios.</span></span>

- <span data-ttu-id="b2f5e-139">`microsoft/dotnet:<version>-core` : c’est-à-dire **microsoft/dotnet:1.0.0-core**, image qui exécute des [applications .NET Core portables](../deploying/index.md) et qui est optimisée pour l’exécution de votre application en **production**.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-139">`microsoft/dotnet:<version>-core` : that is **microsoft/dotnet:1.0.0-core**, image which runs [portable .NET Core applications](../deploying/index.md) and it is optimized for running your application in **production**.</span></span> <span data-ttu-id="b2f5e-140">Elle ne contient pas le SDK et est destinée à prendre la sortie optimisée de `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-140">It does not contain the SDK, and is meant to take the optimized output of `dotnet publish`.</span></span> <span data-ttu-id="b2f5e-141">Le runtime portable est adapté aux scénarios de conteneur Docker car l’exécution de plusieurs conteneurs bénéficie des couches d’image partagées.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-141">The portable runtime is well suited for Docker container scenarios as running multiple containers benefit from shared image layers.</span></span>  

## <a name="alternative-images"></a><span data-ttu-id="b2f5e-142">Images alternatives</span><span class="sxs-lookup"><span data-stu-id="b2f5e-142">Alternative images</span></span>

<span data-ttu-id="b2f5e-143">En plus des scénarios de développement, de génération et de production optimisés, nous fournissons des images supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="b2f5e-143">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

- <span data-ttu-id="b2f5e-144">`microsoft/dotnet:<version>-onbuild` : c’est-à-dire **microsoft/dotnet:1.0.0-preview2-onbuild**, qui contient des déclencheurs [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild).</span><span class="sxs-lookup"><span data-stu-id="b2f5e-144">`microsoft/dotnet:<version>-onbuild` : that is **microsoft/dotnet:1.0.0-preview2-onbuild**, contains [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild) triggers.</span></span> <span data-ttu-id="b2f5e-145">La génération effectue une opération [COPY](https://docs.docker.com/engine/reference/builder/#/copy) sur votre application, exécute `dotnet restore` et crée une instruction [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` pour exécuter l’application quand l’image Docker est exécutée.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-145">The build will [COPY](https://docs.docker.com/engine/reference/builder/#/copy) your application, run `dotnet restore` and create an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` instruction to run the application when the Docker image is run.</span></span> <span data-ttu-id="b2f5e-146">Bien que ce ne soit pas une image optimisée pour la production, elle peut être pratique pour copier simplement le code source dans une image et l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-146">While not an optimized image for production, some may find it useful to simply copy their source code into an image and run it.</span></span> 

- <span data-ttu-id="b2f5e-147">`microsoft/dotnet:<version>-core-deps` : c’est-à-dire **microsoft/dotnet:1.0.0-core-deps**. Si vous voulez exécuter des applications autonomes, utilisez cette image.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-147">`microsoft/dotnet:<version>-core-deps` : that is **microsoft/dotnet:1.0.0-core-deps**, if you wish to run self-contained applications use this image.</span></span> <span data-ttu-id="b2f5e-148">Il contient le système d’exploitation avec toutes les dépendances natives nécessaires à .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-148">It contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="b2f5e-149">Cette image peut également être utilisée comme image de base pour vos propres builds CoreFX ou CoreCLR personnalisées.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-149">This image can also be used as a base image for your own custom CoreFX or CoreCLR builds.</span></span> <span data-ttu-id="b2f5e-150">Alors que la variante **onbuild** est optimisée simplement pour placer votre code dans une image et l’exécuter, cette image est optimisée pour que seules les dépendances de système d’exploitation nécessaires à l’exécution des applications .NET Core ayant le runtime .NET soient packagées avec l’application.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-150">While the **onbuild** variant is optimized to simply place your code in an image and run it, this image is optimized to have only the operating system dependencies required to run .NET Core apps that have the .NET runtime packaged with the application.</span></span> <span data-ttu-id="b2f5e-151">Cette image n’est en général pas optimisée pour l’exécution de plusieurs conteneurs .NET Core sur le même hôte car chaque image inclut le runtime .NET Core dans l’application. Vous ne tirez donc pas parti de la disposition en couches de l’image.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-151">This image isn't generally optimized for running multiple .NET Core containers on the same host, as each image carries the .NET Core runtime within the application, and you will not benefit from image layering.</span></span>   

<span data-ttu-id="b2f5e-152">Versions les plus récentes de chaque variante :</span><span class="sxs-lookup"><span data-stu-id="b2f5e-152">Latest versions of each variant:</span></span>

- <span data-ttu-id="b2f5e-153">`microsoft/dotnet` ou `microsoft/dotnet:latest` (inclut le SDK)</span><span class="sxs-lookup"><span data-stu-id="b2f5e-153">`microsoft/dotnet` or `microsoft/dotnet:latest` (includes SDK)</span></span>
- `microsoft/dotnet:onbuild`
- `microsoft/dotnet:core`
- `microsoft/dotnet:core-deps`

<span data-ttu-id="b2f5e-154">Voici une liste des images provenant d’une commande `docker pull <imagename>` sur une machine de développement pour montrer les différentes tailles.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-154">Here is a list of the images after a `docker pull <imagename>` on a development machine to show the various sizes.</span></span> <span data-ttu-id="b2f5e-155">Notez que la variante de développement/génération, `microsoft/dotnet:1.0.0-preview2-sdk`, est d’une taille plus importante car elle contient le SDK pour développer et générer votre application.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-155">Notice, the development/build variant, `microsoft/dotnet:1.0.0-preview2-sdk` is larger as it contains the SDK to develop and build your application.</span></span> <span data-ttu-id="b2f5e-156">La variante de production, `microsoft/dotnet:core`, est plus petite car elle ne contient que le runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-156">The production variant, `microsoft/dotnet:core` is smaller, as it only contains the .NET Core runtime.</span></span> <span data-ttu-id="b2f5e-157">L’image minimale qui peut être utilisée sur Linux, `core-deps`, est relativement plus petite, mais votre application doit copier avec elle une copie privée du runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-157">The minimal image capable of being used on Linux, `core-deps`, is quite smaller, however your application will need to copy a private copy of the .NET runtime with it.</span></span> <span data-ttu-id="b2f5e-158">Comme les conteneurs sont déjà des barrières d’isolation privées, vous perdez cette optimisation lors de l’exécution de plusieurs conteneurs basés sur .NET.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-158">Since containers are already private isolation barriers, you will lose that optimization when running multiple dotnet based containers.</span></span> 

```
REPOSITORY          TAG                     IMAGE ID            SIZE
microsoft/dotnet    1.0.0-preview2-onbuild  19b6a6c4b1db        540.4 MB
microsoft/dotnet    onbuild                 19b6a6c4b1db        540.4 MB
microsoft/dotnet    1.0.0-preview2-sdk      a92c3d9ad0e7        540.4 MB
microsoft/dotnet    core                    5224a9f2a2aa        253.2 MB
microsoft/dotnet    1.0.0-core-deps         c981a2eebe0e        166.2 MB
microsoft/dotnet    core-deps               c981a2eebe0e        166.2 MB
microsoft/dotnet    latest                  03c10abbd08a        540.4 MB
microsoft/dotnet    1.0.0-core              b8da4a1fd280        253.2 MB
```

## <a name="prerequisites"></a><span data-ttu-id="b2f5e-159">Prérequis</span><span class="sxs-lookup"><span data-stu-id="b2f5e-159">Prerequisites</span></span>

<span data-ttu-id="b2f5e-160">Pour générer et exécuter, plusieurs éléments doivent être installés :</span><span class="sxs-lookup"><span data-stu-id="b2f5e-160">To build and run, you'll need a few things installed:</span></span>

- [<span data-ttu-id="b2f5e-161">.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2f5e-161">.NET Core</span></span>](http://dot.net)
- <span data-ttu-id="b2f5e-162">[Docker](https://www.docker.com/products/docker), pour exécuter vos conteneurs Docker localement</span><span class="sxs-lookup"><span data-stu-id="b2f5e-162">[Docker](https://www.docker.com/products/docker) to run your Docker containers locally</span></span>
- [<span data-ttu-id="b2f5e-163">Node.js</span><span class="sxs-lookup"><span data-stu-id="b2f5e-163">Node.js</span></span>](https://nodejs.org/)
- <span data-ttu-id="b2f5e-164">[Générateur yeoman pour ASP.NET](https://github.com/omnisharp/generator-aspnet) pour la création de l’application API Web</span><span class="sxs-lookup"><span data-stu-id="b2f5e-164">[Yeoman generator for ASP.NET](https://github.com/omnisharp/generator-aspnet) for creating the Web API application</span></span>
- <span data-ttu-id="b2f5e-165">[Générateur yeoman pour Docker](http://aka.ms/yodocker) de Microsoft</span><span class="sxs-lookup"><span data-stu-id="b2f5e-165">[Yeoman generator for Docker](http://aka.ms/yodocker) from Microsoft</span></span>

<span data-ttu-id="b2f5e-166">Installer les générateurs Yeoman pour ASP.NET Core et Docker avec npm</span><span class="sxs-lookup"><span data-stu-id="b2f5e-166">Install the Yeoman generators for ASP.NET Core and Docker using npm</span></span> 

```
npm install -g yo generator-aspnet generator-docker
```

> [!NOTE]
> <span data-ttu-id="b2f5e-167">Cet exemple utilise [Visual Studio Code](http://code.visualstudio.com) pour l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-167">This sample will be using [Visual Studio Code](http://code.visualstudio.com) for the editor.</span></span>

## <a name="creating-the-web-api-application"></a><span data-ttu-id="b2f5e-168">Création de l’application API Web</span><span class="sxs-lookup"><span data-stu-id="b2f5e-168">Creating the Web API application</span></span>

<span data-ttu-id="b2f5e-169">Pour établir un point de référence, avant de mettre l’application dans un conteneur, exécutez l’application localement.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-169">For a reference point, before we containerize the application, first run the application locally.</span></span> 

<span data-ttu-id="b2f5e-170">L’application terminée se trouve dans le [dépôt dotnet/docs sur GitHub](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images).</span><span class="sxs-lookup"><span data-stu-id="b2f5e-170">The finished application is located in the [dotnet/docs repository on GitHub](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images).</span></span> <span data-ttu-id="b2f5e-171">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b2f5e-171">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="b2f5e-172">Créez un répertoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-172">Create a directory for your application.</span></span>

<span data-ttu-id="b2f5e-173">Ouvrez une session de commande ou une session Terminal Server dans ce répertoire, et utilisez le générateur Yeoman ASP.NET en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="b2f5e-173">Open a command or terminal session in that directory and use the ASP.NET Yeoman generator by typing the following:</span></span>
```
yo aspnet
```

<span data-ttu-id="b2f5e-174">Sélectionnez **Application API Web** et tapez **api** pour le nom de l’application, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-174">Select **Web API Application** and type **api** for the name of the app and tap enter.</span></span>  <span data-ttu-id="b2f5e-175">Une fois l’application structurée, accédez au répertoire `/api` et restaurez les dépendances NuGet en utilisant `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-175">Once the application is scaffolded, change to the `/api` directory and restore the NuGet dependencies using `dotnet restore`.</span></span>

```
cd api
dotnet restore
```

<span data-ttu-id="b2f5e-176">Tester l’application en utilisant `dotnet run` et en accédant à **http://localhost:5000/api/values.**</span><span class="sxs-lookup"><span data-stu-id="b2f5e-176">Test the application using `dotnet run` and browsing to **http://localhost:5000/api/values**</span></span>

```javascript
[
    "value1",
    "value2"
]
```

<span data-ttu-id="b2f5e-177">Utilisez `Ctrl+C` pour arrêter l’application.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-177">Use `Ctrl+C` to stop the application.</span></span>

## <a name="adding-docker-support"></a><span data-ttu-id="b2f5e-178">Ajout de la prise en charge de Docker</span><span class="sxs-lookup"><span data-stu-id="b2f5e-178">Adding Docker support</span></span>

<span data-ttu-id="b2f5e-179">L’ajout de la prise en charge de Docker au projet s’effectue en utilisant le générateur Yeoman de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-179">Adding Docker support to the project is achieved using the Yeoman generator from Microsoft.</span></span> <span data-ttu-id="b2f5e-180">Il prend actuellement en charge les projets .NET Core, Node.js et Go en créant un fichier Dockerfile et des scripts qui permettent la génération et l’exécution de projets dans des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-180">It currently supports .NET Core, Node.js and Go projects by creating a Dockerfile and scripts that help build and run projects inside containers.</span></span> <span data-ttu-id="b2f5e-181">Des fichiers spécifiques à Visual Studio Code sont également ajoutés (launch.json, tasks.json) pour la prise en charge du débogage et de la palette de commandes de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-181">Visual Studio Code specific files are also added (launch.json, tasks.json) for editor debugging and command palette support.</span></span>

```console
$ yo docker

     _-----_     ╭──────────────────────────╮
    |       |    │   Welcome to the Docker  │
    |--(o)--|    │        generator!        │
   `---------´   │     Let's add Docker     │
    ( _´U`_ )    │  container magic to your │
    /___A___\   /│           app!           │
     |  ~  |     ╰──────────────────────────╯
   __'.___.'__
 ´   `  |° ´ Y `

? What language is your project using? (Use arrow keys)
❯ .NET Core
  Golang
  Node.js
```

- <span data-ttu-id="b2f5e-182">Sélectionnez `.NET Core` comme type de projet</span><span class="sxs-lookup"><span data-stu-id="b2f5e-182">Select `.NET Core` as the project type</span></span>
- <span data-ttu-id="b2f5e-183">`rtm` pour la version de .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2f5e-183">`rtm` for the version of .NET Core</span></span>
- <span data-ttu-id="b2f5e-184">`Y` le projet utilise un serveur web</span><span class="sxs-lookup"><span data-stu-id="b2f5e-184">`Y` the project uses a web server</span></span>
- <span data-ttu-id="b2f5e-185">`5000` est le port sur lequel l’application API Web écoute (http://localhost:5000)</span><span class="sxs-lookup"><span data-stu-id="b2f5e-185">`5000` is the port the Web API application is listening on (http://localhost:5000)</span></span>
- <span data-ttu-id="b2f5e-186">`api` pour le nom de l’image</span><span class="sxs-lookup"><span data-stu-id="b2f5e-186">`api` for the image name</span></span>
- <span data-ttu-id="b2f5e-187">`api` pour le nom du service</span><span class="sxs-lookup"><span data-stu-id="b2f5e-187">`api` for the service name</span></span>
- <span data-ttu-id="b2f5e-188">`api` pour le projet de composition</span><span class="sxs-lookup"><span data-stu-id="b2f5e-188">`api` for the compose project</span></span> 
- <span data-ttu-id="b2f5e-189">`Y` pour remplacer le fichier Dockerfile actuel</span><span class="sxs-lookup"><span data-stu-id="b2f5e-189">`Y` to overwrite the current Dockerfile</span></span>

<span data-ttu-id="b2f5e-190">Lorsque le générateur a terminé, les fichiers suivants sont ajoutés au projet</span><span class="sxs-lookup"><span data-stu-id="b2f5e-190">When the generator is complete, the following files are added to the project</span></span>

- <span data-ttu-id="b2f5e-191">.vscode/launch.json</span><span class="sxs-lookup"><span data-stu-id="b2f5e-191">.vscode/launch.json</span></span>
- <span data-ttu-id="b2f5e-192">Dockerfile.debug</span><span class="sxs-lookup"><span data-stu-id="b2f5e-192">Dockerfile.debug</span></span>
- <span data-ttu-id="b2f5e-193">Dockerfile</span><span class="sxs-lookup"><span data-stu-id="b2f5e-193">Dockerfile</span></span>
- <span data-ttu-id="b2f5e-194">docker-compose.debug.yml</span><span class="sxs-lookup"><span data-stu-id="b2f5e-194">docker-compose.debug.yml</span></span>
- <span data-ttu-id="b2f5e-195">docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="b2f5e-195">docker-compose.yml</span></span>
- <span data-ttu-id="b2f5e-196">dockerTask.ps1</span><span class="sxs-lookup"><span data-stu-id="b2f5e-196">dockerTask.ps1</span></span>
- <span data-ttu-id="b2f5e-197">dockerTask.sh</span><span class="sxs-lookup"><span data-stu-id="b2f5e-197">dockerTask.sh</span></span>
- <span data-ttu-id="b2f5e-198">.vscode/tasks.json</span><span class="sxs-lookup"><span data-stu-id="b2f5e-198">.vscode/tasks.json</span></span>

<span data-ttu-id="b2f5e-199">Le générateur crée deux fichiers Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-199">The generator creates two Dockerfiles.</span></span>

<span data-ttu-id="b2f5e-200">**Dockerfile.Debug** : ce fichier est basé sur l’image **microsoft/dotnet:1.0.0-preview2-sdk** qui, comme vous pouvez le voir dans la liste des variantes d’images, inclut le SDK, CLI et .NET Core, et qui est l’image utilisée pour le développement et le débogage (F5).</span><span class="sxs-lookup"><span data-stu-id="b2f5e-200">**Dockerfile.debug** - this file is based on the **microsoft/dotnet:1.0.0-preview2-sdk** image which if you note from the list of image variants, includes the SDK, CLI and .NET Core and will be the image used for development and debugging (F5).</span></span> <span data-ttu-id="b2f5e-201">L’inclusion de tous ces composants produit une image plus grande, avec une taille d’environ 540 Mo.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-201">Including all of these components produces a larger image with a size roughly of 540MB.</span></span>

<span data-ttu-id="b2f5e-202">**Dockerfile** : cette image est l’image publiée, basée sur **microsoft/dotnet:1.0.0-core** et qui doit être utilisé pour la production.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-202">**Dockerfile** - this image is the release image based on **microsoft/dotnet:1.0.0-core** and should be used for production.</span></span> <span data-ttu-id="b2f5e-203">Cette image une fois générée a une taille approximative de 253 Mo.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-203">This image when built is approximately 253 MB.</span></span>

### <a name="creating-the-docker-images"></a><span data-ttu-id="b2f5e-204">Création des images Docker</span><span class="sxs-lookup"><span data-stu-id="b2f5e-204">Creating the Docker images</span></span>
<span data-ttu-id="b2f5e-205">En utilisant le script `dockerTask.sh` ou `dockerTask.ps1`, nous pouvons générer ou composer l’image et le conteneur pour l’application **api** pour un environnement spécifique.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-205">Using the `dockerTask.sh` or `dockerTask.ps1` script, we can build or compose the image and container for the **api** application for a specific environment.</span></span> <span data-ttu-id="b2f5e-206">Générez l’image **debug** en exécutant la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-206">Build the **debug** image by running the following command.</span></span>

```bash
./dockerTask.sh build debug
```

<span data-ttu-id="b2f5e-207">L’image génère l’application ASP.NET, exécute `dotnet restore`, ajoute le débogueur à l’image, définit un `ENTRYPOINT` et enfin copie l’application dans l’image.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-207">The image will build the ASP.NET application, run `dotnet restore`, add the debugger to the image, set an `ENTRYPOINT` and finally copy the app to the image.</span></span> <span data-ttu-id="b2f5e-208">Le résultat est une image Docker nommée *api* avec `TAG` ayant la valeur *debug*.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-208">The result is a Docker image named *api* with a `TAG` of *debug*.</span></span>  <span data-ttu-id="b2f5e-209">Affichez les images sur l’ordinateur en utilisant `docker images`.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-209">See the images on the machine using `docker images`.</span></span>

```bash
docker images

REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        a few seconds ago   779.8 MB
```

<span data-ttu-id="b2f5e-210">Une autre façon de générer l’image et d’exécuter l’application au sein du conteneur Docker consiste à ouvrir l’application dans Visual Studio Code et à utiliser les outils de débogage.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-210">Another way to generate the image and run the application within the Docker container is to open the application in Visual Studio Code and use the debugging tools.</span></span> 

<span data-ttu-id="b2f5e-211">Sélectionnez l’icône de débogage dans la barre d’affichage sur le côté gauche de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-211">Select the debugging icon in the View Bar on the left side of Visual Studio Code.</span></span>

![icône de débogage de Visual Studio Code](./media/building-net-docker-images/debugging_debugicon.png)

<span data-ttu-id="b2f5e-213">Cliquez ensuite sur l’icône de lecture ou sur F5 pour générer l’image et démarrer l’application au sein du conteneur.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-213">Then tap the play icon or F5 to generate the image and start the application within the container.</span></span> <span data-ttu-id="b2f5e-214">L’API Web est lancée en utilisant votre navigateur par défaut à l’adresse http://localhost:5000.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-214">The Web API will be launched using your default web browser at http://localhost:5000.</span></span>

![Outils de débogage Docker de Visual Studio Code](./media/building-net-docker-images/docker-tools-vscode-f5.png)

<span data-ttu-id="b2f5e-216">Vous pouvez définir des points d’arrêt dans votre application, exécuter pas à pas, etc., comme si l’application s’exécutait localement sur votre machine de développement et non pas à l’intérieur du conteneur.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-216">You may set break points in your application, step through, etc. just as if the application was running locally on your development machine as opposed to inside the container.</span></span> <span data-ttu-id="b2f5e-217">L’intérêt de déboguer dans le conteneur est qu’il s’agit de la même image que celle qui sera déployée dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-217">The benefit to debugging within the container is this is the same image that would be deployed to a production environment.</span></span>

<span data-ttu-id="b2f5e-218">La création de l’image de version ou de production nécessite simplement l’exécution de la commande à partir du terminal en passant le nom de l’environnement `release`.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-218">Creating the release or production image requires simply running the command from the terminal passing the `release` environment name.</span></span>

```bash
./dockerTask build release
```

<span data-ttu-id="b2f5e-219">La commande crée l’image à partir de l’image de base **microsoft/dotnet:core** plus petite, [EXPOSE](https://docs.docker.com/engine/reference/builder/#/expose) le port 5000, définit le [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) pour `dotnet api.dll` et la copie dans le répertoire `/app`.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-219">The command creates the image based on the smaller **microsoft/dotnet:core** base image, [EXPOSE](https://docs.docker.com/engine/reference/builder/#/expose) port 5000, sets the [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) for `dotnet api.dll` and copies it to the `/app` directory.</span></span> <span data-ttu-id="b2f5e-220">Il n’existe pas de débogueur, SDK ou `dotnet restore` aboutissant à une image beaucoup plus petite.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-220">There is no debugger, SDK or `dotnet restore` resulting in a much smaller image.</span></span> <span data-ttu-id="b2f5e-221">L’image est nommée **api** avec `TAG` ayant la valeur **latest**.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-221">The image is named **api** with a `TAG` of **latest**.</span></span>

```
REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        1 hour ago        779.8 MB
api                 latest               ef17184c8de6        1 hour ago        260.7 MB
```

## <a name="summary"></a><span data-ttu-id="b2f5e-222">Résumé</span><span class="sxs-lookup"><span data-stu-id="b2f5e-222">Summary</span></span>

<span data-ttu-id="b2f5e-223">L’utilisation du générateur Docker pour ajouter les fichiers nécessaires à l’application API Web a simplifié le processus de création des versions de développement et de production des images.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-223">Using the Docker generator to add the necessary files to our Web API application made the process simple to create the development and production versions of the images.</span></span>  <span data-ttu-id="b2f5e-224">Les outils sont multiplateformes : ils fournissent également un script PowerShell pour obtenir les mêmes résultats sur Windows, et Visual Studio Code permet le débogage pas à pas de l’application au sein du conteneur.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-224">The tooling is cross platform by also providing a PowerShell script to accomplish the same results on Windows and Visual Studio Code integration providing step through debugging of the application within the container.</span></span> <span data-ttu-id="b2f5e-225">En comprenant les variantes des images et les scénarios cibles, vous pouvez optimiser votre processus de développement interne, tout en obtenant des images optimisées pour les déploiements de production.</span><span class="sxs-lookup"><span data-stu-id="b2f5e-225">By understanding the image variants and the target scenarios, you can optimize your inner-loop development process, while achieving optimized images for production deployments.</span></span>  



