---
title: "Processus de développement des applications basées sur Docker"
description: "Architecture des microservices .NET pour les applications .NET en conteneur | Processus de développement des applications basées sur Docker"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 97dfa3261c8ddc7a869b0991673b7a8d298972dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="11a64-104">Processus de développement des applications basées sur Docker</span><span class="sxs-lookup"><span data-stu-id="11a64-104">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="11a64-105">*Développez des applications .NET en conteneur comme vous le souhaitez, soit dans un environnement de développement intégré (IDE) avec Visual Studio et Visual Studio Tools pour Docker, soit avec une interface CLI/un éditeur avec une interface CLI Docker et Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="11a64-105">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="11a64-106">Environnement de développement pour les applications Docker</span><span class="sxs-lookup"><span data-stu-id="11a64-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="11a64-107">Choix des outils de développement : IDE ou éditeur</span><span class="sxs-lookup"><span data-stu-id="11a64-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="11a64-108">Que vous préfériez un IDE complet et puissant ou un éditeur léger et agile, Microsoft propose des outils que vous pouvez utiliser pour développer des applications Docker.</span><span class="sxs-lookup"><span data-stu-id="11a64-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="11a64-109">**Visual Studio (pour Windows)**.</span><span class="sxs-lookup"><span data-stu-id="11a64-109">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="11a64-110">Pour développer des applications basées sur Docker, utilisez Visual Studio 2017 ou ultérieur, qui est fourni avec des outils intégrés pour Docker.</span><span class="sxs-lookup"><span data-stu-id="11a64-110">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="11a64-111">Les outils pour Docker vous permettent de développer, exécuter et valider vos applications directement dans l’environnement Docker cible.</span><span class="sxs-lookup"><span data-stu-id="11a64-111">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="11a64-112">Vous pouvez appuyer sur F5 pour exécuter et déboguer votre application (conteneur unique ou plusieurs conteneurs) directement dans un hôte Docker, ou appuyer sur Ctrl+F5 pour modifier et actualiser votre application sans avoir à régénérer le conteneur.</span><span class="sxs-lookup"><span data-stu-id="11a64-112">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="11a64-113">Ceci est le meilleur choix pour le développement d’applications basées sur Docker.</span><span class="sxs-lookup"><span data-stu-id="11a64-113">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="11a64-114">**Visual Studio pour Mac**.</span><span class="sxs-lookup"><span data-stu-id="11a64-114">**Visual Studio for Mac**.</span></span> <span data-ttu-id="11a64-115">Il s’agit d’un IDE, une évolution de Xamarin Studio, qui s’exécute sur macOS et prend en charge le développement d’applications Docker.</span><span class="sxs-lookup"><span data-stu-id="11a64-115">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="11a64-116">Ce choix est recommandé pour les développeurs qui travaillent sur des ordinateurs Mac et qui veulent utiliser un IDE puissant.</span><span class="sxs-lookup"><span data-stu-id="11a64-116">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="11a64-117">**Visual Studio Code et interface CLI Docker**.</span><span class="sxs-lookup"><span data-stu-id="11a64-117">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="11a64-118">Si vous préférez un éditeur léger et multiplateforme qui prend en charge n’importe quel langage de développement, vous pouvez utiliser Microsoft Visual Studio Code (VS Code) et l’interface CLI Docker.</span><span class="sxs-lookup"><span data-stu-id="11a64-118">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="11a64-119">Il s’agit d’une approche de développement multiplateforme pour Mac, Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="11a64-119">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="11a64-120">En installant les outils [Docker Community Edition (CE)](https://www.docker.com/community-edition), vous pouvez utiliser une seule interface CLI Docker pour générer des applications pour Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="11a64-120">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="11a64-121">De plus, Visual Studio Code prend en charge les extensions pour Docker comme IntelliSense pour les Dockerfiles et les tâches de raccourci afin d’exécuter des commandes Docker à partir de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="11a64-121">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="11a64-122">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="11a64-122">Additional resources</span></span>

-   <span data-ttu-id="11a64-123">**Visual Studio Tools pour Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="11a64-123">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="11a64-124">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="11a64-124">**Visual Studio Code**.</span></span> <span data-ttu-id="11a64-125">Site officiel.</span><span class="sxs-lookup"><span data-stu-id="11a64-125">Official site.</span></span>
    [<span data-ttu-id="11a64-126">*https://code.visualstudio.com/download*</span><span class="sxs-lookup"><span data-stu-id="11a64-126">*https://code.visualstudio.com/download*</span></span>](https://code.visualstudio.com/download)

-   <span data-ttu-id="11a64-127">**Docker Community Edition (CE) pour Mac et Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="11a64-127">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="11a64-128">Langages et frameworks .NET pour conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="11a64-128">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="11a64-129">Comme indiqué dans les sections précédentes de ce guide, vous pouvez utiliser .NET Framework, .NET Core ou le projet Mono open source pour développer des applications .NET Docker en conteneur.</span><span class="sxs-lookup"><span data-stu-id="11a64-129">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="11a64-130">Vous pouvez développer en C\#, F\# ou Visual Basic quand vous ciblez des conteneurs Linux ou Windows, selon le .NET Framework en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="11a64-130">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="11a64-131">Pour plus d’informations sur les langages .NET, consultez le billet de blog [Stratégie de langage .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="11a64-131">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="11a64-132">[Précédent] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="11a64-132">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>
