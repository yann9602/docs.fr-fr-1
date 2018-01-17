---
title: "Découvrir les concepts de base de Docker avec .NET Core"
description: Didacticiel de base .NET Core et Docker
keywords: .NET, .NET Core, Docker, didacticiel
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
ms.workload: dotnetcore
ms.openlocfilehash: 79ded2ce5de5100c18301127a2654f8791b8ed76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="ce4f7-104">Découvrir les concepts de base de Docker avec .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce4f7-104">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="ce4f7-105">Ce didacticiel vous apprend la création de conteneur Docker et les tâches de déploiement pour une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-105">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="ce4f7-106">Au cours de ce didacticiel, vous apprenez à :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ce4f7-107">Créer un fichier Dockerfile</span><span class="sxs-lookup"><span data-stu-id="ce4f7-107">How to create a Dockerfile</span></span>
> * <span data-ttu-id="ce4f7-108">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce4f7-108">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="ce4f7-109">Déployer votre application dans un conteneur Docker</span><span class="sxs-lookup"><span data-stu-id="ce4f7-109">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="ce4f7-110">La [plateforme Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) utilise le [moteur Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) pour générer et empaqueter rapidement des applications comme [images Docker](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-110">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="ce4f7-111">Ces images sont écrites au format [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) pour être déployées et exécutées dans un [conteneur en couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-111">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="ce4f7-112">.NET Core : la façon la plus simple de bien démarrer</span><span class="sxs-lookup"><span data-stu-id="ce4f7-112">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="ce4f7-113">Avant de créer l’image Docker, vous avez besoin d’une application à mettre en conteneur.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-113">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="ce4f7-114">Vous pouvez la créer sous Linux, MacOS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-114">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="ce4f7-115">La façon la plus rapide et la plus simple de procéder consiste à utiliser .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-115">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="ce4f7-116">Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-116">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="ce4f7-117">Vous pouvez créer des conteneurs Windows et Linux avec des [balises multi-arch](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-117">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="ce4f7-118">Votre première application Docker .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce4f7-118">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ce4f7-119">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ce4f7-119">Prerequisites</span></span>

<span data-ttu-id="ce4f7-120">Pour suivre ce didacticiel :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-120">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="ce4f7-121">Kit SDK .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ce4f7-121">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="ce4f7-122">Installez le [Kit SDK .NET Core 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-122">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="ce4f7-123">Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="ce4f7-124">Installez votre éditeur de code favori, si ce n’est pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-124">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="ce4f7-125">Vous avez besoin d’installer un éditeur de code ?</span><span class="sxs-lookup"><span data-stu-id="ce4f7-125">Need to install a code editor?</span></span> <span data-ttu-id="ce4f7-126">Essayez [Visual Studio](https://visualstudio.com/downloads) !</span><span class="sxs-lookup"><span data-stu-id="ce4f7-126">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="ce4f7-127">Installation du client Docker</span><span class="sxs-lookup"><span data-stu-id="ce4f7-127">Installing Docker Client</span></span>

<span data-ttu-id="ce4f7-128">Installez la version [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou ultérieure du client Docker.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-128">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="ce4f7-129">Le client Docker peut être installé dans :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-129">The Docker client can be installed in:</span></span>

* <span data-ttu-id="ce4f7-130">Distributions Linux</span><span class="sxs-lookup"><span data-stu-id="ce4f7-130">Linux distributions</span></span>

   * [<span data-ttu-id="ce4f7-131">CentOS</span><span class="sxs-lookup"><span data-stu-id="ce4f7-131">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="ce4f7-132">Debian</span><span class="sxs-lookup"><span data-stu-id="ce4f7-132">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="ce4f7-133">Fedora</span><span class="sxs-lookup"><span data-stu-id="ce4f7-133">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="ce4f7-134">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ce4f7-134">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="ce4f7-135">macOS</span><span class="sxs-lookup"><span data-stu-id="ce4f7-135">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="ce4f7-136">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-136">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="ce4f7-137">Créer une application console .NET Core 2.0 pour la dockerisation</span><span class="sxs-lookup"><span data-stu-id="ce4f7-137">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="ce4f7-138">Ouvrez une invite de commandes et créez un dossier nommé *Hello*.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-138">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="ce4f7-139">Accédez au dossier créé et tapez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-139">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="ce4f7-140">Suivons une procédure pas à pas rapide :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-140">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="ce4f7-141">[`dotnet new`](../tools/dotnet-new.md) crée un fichier projet `Hello.csproj` à jour avec les dépendances nécessaires pour générer une application console.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-141">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="ce4f7-142">Il crée également `Program.cs`, un fichier de base contenant le point d’entrée pour l’application.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-142">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="ce4f7-143">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="ce4f7-143">`Hello.csproj`:</span></span>

   <span data-ttu-id="ce4f7-144">Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-144">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="ce4f7-145">La balise `OutputType` spécifie que nous générons un fichier exécutable, autrement dit une application console.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-145">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="ce4f7-146">La balise `TargetFramework` spécifie l’implémentation .NET que nous ciblons.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-146">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="ce4f7-147">Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-147">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="ce4f7-148">Dans ce didacticiel, nous effectuons une génération pour .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-148">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="ce4f7-149">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="ce4f7-149">`Program.cs`:</span></span>

   <span data-ttu-id="ce4f7-150">Le programme commence par `using System`.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-150">The program starts by `using System`.</span></span> <span data-ttu-id="ce4f7-151">Cette instruction signifie « Placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ».</span><span class="sxs-lookup"><span data-stu-id="ce4f7-151">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="ce4f7-152">L’espace de noms `System` inclut des constructions de base, telles que `string`, ou des types numériques.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-152">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="ce4f7-153">Ensuite, nous définissons un espace de noms appelé `Hello`.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-153">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="ce4f7-154">Vous pouvez le modifier à votre gré.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-154">You can change namespace to anything you want.</span></span> <span data-ttu-id="ce4f7-155">Une classe nommée `Program` est définie dans cet espace de noms avec une méthode `Main` qui accepte un tableau de chaînes comme argument.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-155">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="ce4f7-156">Ce tableau contient la liste des arguments passés quand le programme compilé est appelé.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-156">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="ce4f7-157">Dans notre exemple, le programme écrit uniquement « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="ce4f7-157">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="ce4f7-158">dans la console.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-158">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="ce4f7-159">Dans .NET Core 2.x, **dotnet new** exécute la commande [`dotnet restore`](../tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-159">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="ce4f7-160">**Dotnet restore** restaure l’arborescence des dépendances avec un appel [NuGet](https://www.nuget.org/) (gestionnaire de package .NET).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-160">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="ce4f7-161">NuGet exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-161">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="ce4f7-162">il analyse le fichier *Hello.csproj* ;</span><span class="sxs-lookup"><span data-stu-id="ce4f7-162">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="ce4f7-163">il télécharge les dépendances de fichiers (ou les extrait du cache de votre ordinateur) ;</span><span class="sxs-lookup"><span data-stu-id="ce4f7-163">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="ce4f7-164">il écrit le fichier *obj/project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-164">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="ce4f7-165">Le fichier *project.assets.json* réunit le graphique des dépendances NuGet, les résolutions de liaisons et d’autres métadonnées d’application.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-165">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="ce4f7-166">Ce fichier requis est utilisé par d’autres outils, tels que [`dotnet build`](../tools/dotnet-build.md) et [`dotnet run`](../tools/dotnet-run.md), pour traiter correctement le code source.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-166">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="ce4f7-167">[`dotnet run`](../tools/dotnet-run.md) appelle [`dotnet build`](../tools/dotnet-build.md) pour confirmer une génération réussie, puis appelle `dotnet <assembly.dll>` pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-167">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="ce4f7-168">Pour les scénarios avancés, consultez [Déploiement d’applications .NET Core](../deploying/index.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-168">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="ce4f7-169">Dockeriser l’application .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce4f7-169">Dockerize the .NET Core application</span></span>

<span data-ttu-id="ce4f7-170">L’application console .NET Core Hello est exécutée correctement en local.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-170">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="ce4f7-171">Franchissons maintenant une étape supplémentaire pour générer et exécuter l’application dans Docker.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-171">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="ce4f7-172">Votre premier fichier Dockerfile</span><span class="sxs-lookup"><span data-stu-id="ce4f7-172">Your first Dockerfile</span></span>

<span data-ttu-id="ce4f7-173">Ouvrez votre éditeur de texte et c’est parti !</span><span class="sxs-lookup"><span data-stu-id="ce4f7-173">Open your text editor and let's get started!</span></span> <span data-ttu-id="ce4f7-174">Nous travaillons encore à partir du répertoire Hello dans lequel nous avons créé l’application.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-174">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="ce4f7-175">Ajoutez les instructions Docker suivantes pour les [conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) ou Linux à un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-175">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="ce4f7-176">Quand vous avez terminé, enregistrez-le à la racine de votre répertoire Hello comme **Dockerfile**, sans extension (vous devrez peut-être définir le type de fichier `All types (*.*)` ou un type similaire).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-176">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="ce4f7-177">Le fichier Dockerfile contient des instructions de génération Docker qui s’exécutent de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-177">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="ce4f7-178">La première instruction doit être [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-178">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="ce4f7-179">Cette instruction initialise une nouvelle étape de génération et définit l’image de base pour les instructions restantes.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-179">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="ce4f7-180">Les balises multi-arch extraient les conteneurs Windows ou Linux selon le [mode conteneur](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) Docker pour Windows.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-180">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="ce4f7-181">L’image de base pour notre exemple est l’image 2.0-sdk du dépôt microsoft/dotnet,</span><span class="sxs-lookup"><span data-stu-id="ce4f7-181">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="ce4f7-182">L’instruction [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) définit le répertoire de travail pour toute instruction Dockerfile RUN, CMD, ENTRYPOINT, COPY et ADD restante.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-182">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="ce4f7-183">Si le répertoire n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-183">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="ce4f7-184">Dans ce cas, WORKDIR est définie sur le répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-184">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="ce4f7-185">L’instruction [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) copie les nouveaux fichiers ou répertoires du chemin source et les ajoute au système de fichiers du conteneur de destination.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-185">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="ce4f7-186">Avec cette instruction, nous copions le fichier projet C# dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-186">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="ce4f7-187">L’instruction [**RUN**](https://docs.docker.com/engine/reference/builder/#run) exécute toutes les commandes dans une nouvelle couche sur l’image actuelle et valide les résultats.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-187">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="ce4f7-188">L’image validée obtenue est utilisée pour l’étape suivante dans le fichier Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-188">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="ce4f7-189">Nous exécutons **dotnet restore** pour obtenir les dépendances nécessaires du fichier projet C#.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-189">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="ce4f7-190">Cette instruction **COPY** copie le reste des fichiers dans notre conteneur dans de nouvelles [couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="ce4f7-190">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="ce4f7-191">Nous publions l’application avec cette instruction **RUN**.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-191">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="ce4f7-192">La commande [**dotnet publish**](../tools/dotnet-publish.md) compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-192">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="ce4f7-193">Notre application est publiée avec une configuration **Release** et une sortie vers le répertoire par défaut.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-193">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="ce4f7-194">L’instruction [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) permet d’exécuter le conteneur comme un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-194">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="ce4f7-195">Vous disposez maintenant d’un fichier Dockerfile qui :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-195">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="ce4f7-196">Copie votre application sur l’image</span><span class="sxs-lookup"><span data-stu-id="ce4f7-196">copies your app to the image</span></span>
* <span data-ttu-id="ce4f7-197">Ajoute les dépendances de votre application à l’image</span><span class="sxs-lookup"><span data-stu-id="ce4f7-197">your app's dependencies to the image</span></span>
* <span data-ttu-id="ce4f7-198">Génère l’application pour l’exécuter comme un fichier exécutable</span><span class="sxs-lookup"><span data-stu-id="ce4f7-198">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="ce4f7-199">Générer et exécuter l’application .NET Core 2.0 Hello</span><span class="sxs-lookup"><span data-stu-id="ce4f7-199">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="ce4f7-200">Commandes Docker essentielles</span><span class="sxs-lookup"><span data-stu-id="ce4f7-200">Essential Docker commands</span></span>

<span data-ttu-id="ce4f7-201">Ces commandes Docker sont essentielles :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-201">These Docker commands are essential:</span></span>

* [<span data-ttu-id="ce4f7-202">docker build</span><span class="sxs-lookup"><span data-stu-id="ce4f7-202">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="ce4f7-203">docker run</span><span class="sxs-lookup"><span data-stu-id="ce4f7-203">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="ce4f7-204">docker ps</span><span class="sxs-lookup"><span data-stu-id="ce4f7-204">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="ce4f7-205">docker stop</span><span class="sxs-lookup"><span data-stu-id="ce4f7-205">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="ce4f7-206">docker rm</span><span class="sxs-lookup"><span data-stu-id="ce4f7-206">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="ce4f7-207">docker rmi</span><span class="sxs-lookup"><span data-stu-id="ce4f7-207">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="ce4f7-208">docker image</span><span class="sxs-lookup"><span data-stu-id="ce4f7-208">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="ce4f7-209">Générer et exécuter</span><span class="sxs-lookup"><span data-stu-id="ce4f7-209">Build and run</span></span>

<span data-ttu-id="ce4f7-210">Vous avez écrit le fichier Dockerfile ; maintenant, Docker génère votre application, puis exécute le conteneur.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-210">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="ce4f7-211">La sortie de la commande `docker build` doit être similaire à la sortie de console suivante :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-211">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="ce4f7-212">Comme vous pouvez le voir dans la sortie, le moteur Docker a utilisé le fichier Dockerfile pour créer notre conteneur.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-212">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="ce4f7-213">La sortie de la commande `docker run` doit être similaire à la sortie de console suivante :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-213">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="ce4f7-214">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="ce4f7-214">Congratulations!</span></span> <span data-ttu-id="ce4f7-215">Vous venez de :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-215">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ce4f7-216">Créer une application .NET Core locale</span><span class="sxs-lookup"><span data-stu-id="ce4f7-216">Created a local .NET Core app</span></span>
> * <span data-ttu-id="ce4f7-217">Créer un fichier Dockerfile pour générer votre premier conteneur</span><span class="sxs-lookup"><span data-stu-id="ce4f7-217">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="ce4f7-218">Générer et exécuter votre application dockerisée</span><span class="sxs-lookup"><span data-stu-id="ce4f7-218">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="ce4f7-219">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ce4f7-219">Next Steps</span></span>

<span data-ttu-id="ce4f7-220">Voici quelques étapes suivantes que vous pouvez effectuer :</span><span class="sxs-lookup"><span data-stu-id="ce4f7-220">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="ce4f7-221">Introduction to .NET Docker Images Video</span><span class="sxs-lookup"><span data-stu-id="ce4f7-221">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="ce4f7-222">Visual Studio, Docker & Azure Container Instances better together!</span><span class="sxs-lookup"><span data-stu-id="ce4f7-222">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="ce4f7-223">Guides de démarrage rapide Docker pour Azure</span><span class="sxs-lookup"><span data-stu-id="ce4f7-223">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="ce4f7-224">Déployer votre application sur Docker pour Azure</span><span class="sxs-lookup"><span data-stu-id="ce4f7-224">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="ce4f7-225">Si vous ne disposez pas d’abonnement Azure, [inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour obtenir un compte gratuit pendant 30 jours et 200 dollars US en crédits Azure pour essayer une combinaison quelconque de services Azure.</span><span class="sxs-lookup"><span data-stu-id="ce4f7-225">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="ce4f7-226">Images Docker utilisées dans cet exemple</span><span class="sxs-lookup"><span data-stu-id="ce4f7-226">Docker Images used in this sample</span></span>

<span data-ttu-id="ce4f7-227">Les images Docker suivantes sont utilisées dans cet exemple</span><span class="sxs-lookup"><span data-stu-id="ce4f7-227">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="ce4f7-228">Ressources connexes</span><span class="sxs-lookup"><span data-stu-id="ce4f7-228">Related Resources</span></span>

* [<span data-ttu-id="ce4f7-229">Exemples Docker .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce4f7-229">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="ce4f7-230">Dockerfile sur les conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="ce4f7-230">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="ce4f7-231">Exemples Docker .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce4f7-231">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="ce4f7-232">ASP.NET Core sur DockerHub</span><span class="sxs-lookup"><span data-stu-id="ce4f7-232">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="ce4f7-233">Dockeriser une application .NET Core - Didacticiel Docker</span><span class="sxs-lookup"><span data-stu-id="ce4f7-233">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="ce4f7-234">Utilisation des outils Docker dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ce4f7-234">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="ce4f7-235">Déploiement d’images Docker à partir du Registre de conteneurs Azure dans Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="ce4f7-235">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)