---
title: "Microservices hébergés dans Docker - C#"
description: "Apprenez à créer des services principaux ASP.NET qui s’exécutent dans des conteneurs Docker"
keywords: .NET, .NET Core, Docker, C#, ASP.NET, Microservice
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5585db33fb5020ed18c26f32ce0b63f97353d20f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="a576b-104">Microservices hébergés dans Docker</span><span class="sxs-lookup"><span data-stu-id="a576b-104">Microservices hosted in Docker</span></span>

## <a name="introduction"></a><span data-ttu-id="a576b-105">Introduction</span><span class="sxs-lookup"><span data-stu-id="a576b-105">Introduction</span></span>

<span data-ttu-id="a576b-106">Ce didacticiel détaille les tâches nécessaires pour générer et déployer un microservice ASP.NET Core dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-106">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="a576b-107">Au cours de ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="a576b-107">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="a576b-108">Générer une application ASP.NET Core à l’aide de Yeoman</span><span class="sxs-lookup"><span data-stu-id="a576b-108">How to generate an ASP.NET Core application using Yeoman</span></span>
* <span data-ttu-id="a576b-109">Guide de création d’un environnement de développement Docker</span><span class="sxs-lookup"><span data-stu-id="a576b-109">How to create a development Docker environment</span></span>
* <span data-ttu-id="a576b-110">Créer une image Docker basée sur une image existante.</span><span class="sxs-lookup"><span data-stu-id="a576b-110">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="a576b-111">Déployer votre service dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-111">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="a576b-112">Au passage, vous verrez également certaines fonctionnalités du langage C# :</span><span class="sxs-lookup"><span data-stu-id="a576b-112">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="a576b-113">Conversion des objets C# en charges utiles JSON.</span><span class="sxs-lookup"><span data-stu-id="a576b-113">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="a576b-114">Création d’objets de transfert de données immuables</span><span class="sxs-lookup"><span data-stu-id="a576b-114">How to build immutable Data Transfer Objects</span></span>
* <span data-ttu-id="a576b-115">Traitement des demandes HTTP entrantes et création de la réponse HTTP</span><span class="sxs-lookup"><span data-stu-id="a576b-115">How to process incoming HTTP Requests and generate the HTTP Response</span></span>
* <span data-ttu-id="a576b-116">Guide pratique de travail avec les types valeur Nuallable</span><span class="sxs-lookup"><span data-stu-id="a576b-116">How to work with nullable value types</span></span>

<span data-ttu-id="a576b-117">Vous pouvez [afficher ou télécharger l’exemple d’application](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a576b-117">You can [view or download the sample app](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="a576b-118">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="a576b-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="why-docker"></a><span data-ttu-id="a576b-119">Pourquoi Docker ?</span><span class="sxs-lookup"><span data-stu-id="a576b-119">Why Docker?</span></span>

<span data-ttu-id="a576b-120">Docker facilite la création d’images de machine standard pour héberger vos services dans un centre de données ou dans le cloud public.</span><span class="sxs-lookup"><span data-stu-id="a576b-120">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="a576b-121">Docker vous permet de configurer l’image et de la répliquer en fonction des besoins pour mettre à l’échelle l’installation de votre application.</span><span class="sxs-lookup"><span data-stu-id="a576b-121">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="a576b-122">Tout le code de ce didacticiel fonctionne dans n’importe quel environnement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a576b-122">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="a576b-123">Les tâches supplémentaires pour une installation Docker fonctionneront pour une application ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a576b-123">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="a576b-124">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a576b-124">Prerequisites</span></span>
<span data-ttu-id="a576b-125">Vous devez configurer votre ordinateur pour exécuter .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a576b-125">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="a576b-126">Vous trouverez les instructions d’installation sur la page de [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="a576b-126">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="a576b-127">Vous pouvez exécuter cette application sur Windows, Ubuntu Linux, Mac OS ou dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-127">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="a576b-128">Vous devez installer l’éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="a576b-128">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="a576b-129">Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/), un éditeur open source et multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="a576b-129">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="a576b-130">Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.</span><span class="sxs-lookup"><span data-stu-id="a576b-130">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="a576b-131">Vous devez également installer le moteur Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-131">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="a576b-132">Consultez la [page d’installation de Docker](http://www.docker.com/products/docker) pour obtenir des instructions pour votre plateforme.</span><span class="sxs-lookup"><span data-stu-id="a576b-132">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="a576b-133">Docker peut être installé dans de nombreuses distributions Linux, Mac OS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="a576b-133">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="a576b-134">La page mentionnée ci-dessus contient des sections pour chacune des installations disponibles.</span><span class="sxs-lookup"><span data-stu-id="a576b-134">The page referenced above contains sections to each of the available installations.</span></span>

<span data-ttu-id="a576b-135">La plupart des composants à installer le sont par un gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="a576b-135">Most components to be installed are done by a package manager.</span></span> <span data-ttu-id="a576b-136">Si vous disposez du gestionnaire de packages de node.js `npm` installé, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="a576b-136">If you have node.js's package manager `npm` installed you can skip this step.</span></span> <span data-ttu-id="a576b-137">Sinon, installez la dernière version de NodeJs à partir de [nodejs.org](https://nodejs.org), ce qui installe le gestionnaire de packages npm.</span><span class="sxs-lookup"><span data-stu-id="a576b-137">Otherwise install the latest NodeJs from [nodejs.org](https://nodejs.org) which will install the npm package manager.</span></span> 

<span data-ttu-id="a576b-138">À ce stade, vous devrez installer un certain nombre d’outils de ligne de commande qui prennent en charge le développement avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a576b-138">At this point you will need to install a number of command line tools that support ASP.NET core development.</span></span> <span data-ttu-id="a576b-139">Les modèles de ligne de commande utilisent Yeoman, Bower, Grunt et Gulp.</span><span class="sxs-lookup"><span data-stu-id="a576b-139">The command line templates use Yeoman, Bower, Grunt, and Gulp.</span></span> <span data-ttu-id="a576b-140">Si vous les avez déjà installés, c’est parfait, sinon saisissez ce qui suit dans votre interpréteur de commandes préféré :</span><span class="sxs-lookup"><span data-stu-id="a576b-140">If you have them installed that is good, otherwise type the following into your favorite shell:</span></span>

`npm install -g yo bower grunt-cli gulp`

<span data-ttu-id="a576b-141">L’option `-g` indique qu’il s’agit d’une installation globale, et que ces outils sont disponibles à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="a576b-141">The `-g` option indicates that it is a global install, and those tools are available system wide.</span></span> <span data-ttu-id="a576b-142">(Une installation locale définit la portée du package sur un projet unique).</span><span class="sxs-lookup"><span data-stu-id="a576b-142">(A local install scopes the package to a single project).</span></span> <span data-ttu-id="a576b-143">Une fois que vous avez installé les outils de base, vous devez installer les générateurs de modèle yeoman ASP.NET :</span><span class="sxs-lookup"><span data-stu-id="a576b-143">Once you've installed those core tools, you need to install the yeoman asp.net template generators:</span></span>

`npm install -g generator-aspnet`

## <a name="create-the-application"></a><span data-ttu-id="a576b-144">Création de l’application</span><span class="sxs-lookup"><span data-stu-id="a576b-144">Create the Application</span></span>

<span data-ttu-id="a576b-145">Maintenant que vous avez installé tous les outils, créez une nouvelle application asp.net.</span><span class="sxs-lookup"><span data-stu-id="a576b-145">Now that you've installed all the tools, create a new asp.net core application.</span></span> <span data-ttu-id="a576b-146">Pour utiliser le générateur de ligne de commande, exécutez la commande yeoman suivante dans votre interpréteur de commandes préféré :</span><span class="sxs-lookup"><span data-stu-id="a576b-146">To use the command line generator, execute the following yeoman command in your favorite shell:</span></span>

`yo aspnet`

<span data-ttu-id="a576b-147">Cette commande vous invite à sélectionner le type d’application que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="a576b-147">This command prompts you to select what Type of application you want to create.</span></span> <span data-ttu-id="a576b-148">Pour ce microservice, vous souhaitez obtenir l’application web la plus simple et légère possible, sélectionnez donc « Application Web vide ».</span><span class="sxs-lookup"><span data-stu-id="a576b-148">For this microservice, you want the simplest, most lightweight web application possible, so select 'Empty Web Application'.</span></span> <span data-ttu-id="a576b-149">Le modèle vous demandera un nom.</span><span class="sxs-lookup"><span data-stu-id="a576b-149">The template will prompt you for a name.</span></span> <span data-ttu-id="a576b-150">Sélectionnez « WeatherMicroservice ».</span><span class="sxs-lookup"><span data-stu-id="a576b-150">Select 'WeatherMicroservice'.</span></span> 

<span data-ttu-id="a576b-151">Le modèle crée huit fichiers pour vous :</span><span class="sxs-lookup"><span data-stu-id="a576b-151">The template creates eight files for you:</span></span>

* <span data-ttu-id="a576b-152">Un .gitignore personnalisé pour les applications ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a576b-152">A .gitignore, customized for asp.net core applications.</span></span>
* <span data-ttu-id="a576b-153">Un fichier Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="a576b-153">A Startup.cs file.</span></span> <span data-ttu-id="a576b-154">Cela contient la base de l’application.</span><span class="sxs-lookup"><span data-stu-id="a576b-154">This contains the basis of the application.</span></span>
* <span data-ttu-id="a576b-155">Un fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="a576b-155">A Program.cs file.</span></span> <span data-ttu-id="a576b-156">Cela contient le point d’entrée de l’application.</span><span class="sxs-lookup"><span data-stu-id="a576b-156">This contains the entry point of the application.</span></span>
* <span data-ttu-id="a576b-157">Un fichier WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="a576b-157">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="a576b-158">Il s’agit du fichier de génération de l’application.</span><span class="sxs-lookup"><span data-stu-id="a576b-158">This is the build file for the application.</span></span>
* <span data-ttu-id="a576b-159">Un Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a576b-159">A Dockerfile.</span></span> <span data-ttu-id="a576b-160">Ce script crée une image Docker pour l’application.</span><span class="sxs-lookup"><span data-stu-id="a576b-160">This script creates a Docker image for the application.</span></span>
* <span data-ttu-id="a576b-161">Un README.md.</span><span class="sxs-lookup"><span data-stu-id="a576b-161">A README.md.</span></span> <span data-ttu-id="a576b-162">Il contient des liens vers d’autres ressources de base d’ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a576b-162">This contains links to other asp.net core resources.</span></span>
* <span data-ttu-id="a576b-163">Un fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="a576b-163">A web.config file.</span></span> <span data-ttu-id="a576b-164">Les informations de configuration de base s’y trouvent.</span><span class="sxs-lookup"><span data-stu-id="a576b-164">This contains basic configuration information.</span></span>
* <span data-ttu-id="a576b-165">Un fichier runtimeconfig.template.json.</span><span class="sxs-lookup"><span data-stu-id="a576b-165">A runtimeconfig.template.json file.</span></span> <span data-ttu-id="a576b-166">Il contient les paramètres de débogage utilisés par l’EDI.</span><span class="sxs-lookup"><span data-stu-id="a576b-166">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="a576b-167">Vous pouvez maintenant exécuter l’application générée par le modèle.</span><span class="sxs-lookup"><span data-stu-id="a576b-167">Now you can run the template generated application.</span></span> <span data-ttu-id="a576b-168">Vous pouvez le faire à l’aide d’une série d’outils en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a576b-168">That's done using a series of tools from the command line.</span></span> <span data-ttu-id="a576b-169">La commande `dotnet` exécute les outils nécessaires pour le développement .NET.</span><span class="sxs-lookup"><span data-stu-id="a576b-169">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="a576b-170">Chaque verbe exécute une commande différente</span><span class="sxs-lookup"><span data-stu-id="a576b-170">Each verb executes a different command</span></span>

<span data-ttu-id="a576b-171">La première étape consiste à restaurer toutes les dépendances :</span><span class="sxs-lookup"><span data-stu-id="a576b-171">The first step is to restore all the dependencies:</span></span>

```console
dotnet restore
```

<span data-ttu-id="a576b-172">La restauration Dotnet utilise le gestionnaire de packages NuGet pour installer tous les packages dans le répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="a576b-172">Dotnet restore uses the NuGet package manager to install all the necessary packages into the application directory.</span></span> <span data-ttu-id="a576b-173">Il génère également un fichier project.json.lock.</span><span class="sxs-lookup"><span data-stu-id="a576b-173">It also generates a project.json.lock file.</span></span> <span data-ttu-id="a576b-174">Ce fichier contient des informations sur chaque package référencé.</span><span class="sxs-lookup"><span data-stu-id="a576b-174">This file contains information about each package that is referenced.</span></span> <span data-ttu-id="a576b-175">Après la restauration de toutes les dépendances, vous générez l’application :</span><span class="sxs-lookup"><span data-stu-id="a576b-175">After restoring all the dependencies, you build the application:</span></span>

```console
dotnet build
```

<span data-ttu-id="a576b-176">Et une fois que vous générez l’application, vous l’exécutez à partir de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="a576b-176">And once you build the application, you run it from the command line:</span></span>

```console
dotnet run
```

<span data-ttu-id="a576b-177">La configuration par défaut écoute le port http://localhost:5000.</span><span class="sxs-lookup"><span data-stu-id="a576b-177">The default configuration listens to http://localhost:5000.</span></span> <span data-ttu-id="a576b-178">Vous pouvez ouvrir un navigateur et accéder à cette page pour voir un « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="a576b-178">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="a576b-179">« Operation Not Found! ».</span><span class="sxs-lookup"><span data-stu-id="a576b-179">message.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="a576b-180">Anatomie d’une application ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a576b-180">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="a576b-181">Maintenant que vous avez créé l’application, nous allons voir comment cette fonctionnalité est implémentée.</span><span class="sxs-lookup"><span data-stu-id="a576b-181">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="a576b-182">Deux des fichiers générés sont particulièrement intéressants à ce stade : project.json et Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="a576b-182">There are two of the generated files that are particularly interesting at this point: project.json and Startup.cs.</span></span> 

<span data-ttu-id="a576b-183">Project.json qui contient des informations sur le projet.</span><span class="sxs-lookup"><span data-stu-id="a576b-183">Project.json contains information about the project.</span></span> <span data-ttu-id="a576b-184">Ces deux nœuds, que vous utiliserez souvent, sont des « dépendances » et des « frameworks ».</span><span class="sxs-lookup"><span data-stu-id="a576b-184">The two nodes you'll often work with are 'dependencies' and 'frameworks'.</span></span> <span data-ttu-id="a576b-185">Le nœud de dépendances répertorie tous les packages qui sont nécessaires pour cette application.</span><span class="sxs-lookup"><span data-stu-id="a576b-185">The dependencies node lists all the packages that are needed for this application.</span></span>
<span data-ttu-id="a576b-186">À ce stade, il s’agit d’un petit nœud, qui ne nécessite que les packages qui exécutent le serveur Web.</span><span class="sxs-lookup"><span data-stu-id="a576b-186">At the moment, this is a small node, needing only the packages that run the web server.</span></span>

<span data-ttu-id="a576b-187">Le nœud « frameworks » spécifie les versions et les configurations du .NET Framework qui va exécuter cette application.</span><span class="sxs-lookup"><span data-stu-id="a576b-187">The 'frameworks' node specifies the versions and configurations of the .NET framework that will run this application.</span></span>

<span data-ttu-id="a576b-188">L’application est implémentée dans Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="a576b-188">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="a576b-189">Ce fichier contient la classe de démarrage.</span><span class="sxs-lookup"><span data-stu-id="a576b-189">This file contains the startup class.</span></span>

<span data-ttu-id="a576b-190">Les deux méthodes sont appelées par l’infrastructure ASP.NET Core pour configurer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="a576b-190">The two methods are called by the asp.net core infrastructure to configure and run the application.</span></span> <span data-ttu-id="a576b-191">La méthode `ConfigureServices` décrit les services qui sont nécessaires pour cette application.</span><span class="sxs-lookup"><span data-stu-id="a576b-191">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="a576b-192">Vous créez un microservice épuré, vous n’avez donc pas besoin de configurer de dépendances.</span><span class="sxs-lookup"><span data-stu-id="a576b-192">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="a576b-193">La méthode `Configure` configure les gestionnaires pour les requêtes HTTP entrantes.</span><span class="sxs-lookup"><span data-stu-id="a576b-193">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="a576b-194">Le modèle génère un gestionnaire simple qui répond à une demande dont le texte est « Hello World! ».</span><span class="sxs-lookup"><span data-stu-id="a576b-194">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="a576b-195">Créer un microservice</span><span class="sxs-lookup"><span data-stu-id="a576b-195">Build a microservice</span></span>

<span data-ttu-id="a576b-196">Le service que vous vous apprêtez à générer fournira des rapports météorologiques depuis n’importe où dans le monde.</span><span class="sxs-lookup"><span data-stu-id="a576b-196">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="a576b-197">Dans une application de production, vous appelleriez un service pour récupérer des données météorologiques.</span><span class="sxs-lookup"><span data-stu-id="a576b-197">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="a576b-198">Pour notre exemple, nous allons générer des prévisions météorologiques aléatoires.</span><span class="sxs-lookup"><span data-stu-id="a576b-198">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="a576b-199">Il existe un certain nombre de tâches que vous devez effectuer pour implémenter notre service météo aléatoire :</span><span class="sxs-lookup"><span data-stu-id="a576b-199">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="a576b-200">Analyser la requête entrante pour lire la latitude et la longitude.</span><span class="sxs-lookup"><span data-stu-id="a576b-200">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="a576b-201">Générer des données de prévision aléatoires.</span><span class="sxs-lookup"><span data-stu-id="a576b-201">Generate some random forecast data.</span></span>
* <span data-ttu-id="a576b-202">Convertir ces données de prévision aléatoires d’objets C# en paquets JSON.</span><span class="sxs-lookup"><span data-stu-id="a576b-202">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="a576b-203">Définir l’en-tête de réponse pour indiquer que votre service renvoie JSON.</span><span class="sxs-lookup"><span data-stu-id="a576b-203">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="a576b-204">Écrivez la réponse.</span><span class="sxs-lookup"><span data-stu-id="a576b-204">Write the response.</span></span>

<span data-ttu-id="a576b-205">Les sections suivantes décrivent chacune de ces étapes.</span><span class="sxs-lookup"><span data-stu-id="a576b-205">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="a576b-206">Analyse de la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="a576b-206">Parsing the Query String.</span></span>

<span data-ttu-id="a576b-207">Vous commencerez par analyser la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="a576b-207">You'll begin by parsing the query string.</span></span> <span data-ttu-id="a576b-208">Le service acceptera les arguments 'lat' et 'longs' sur la chaîne de requête dans ce formulaire :</span><span class="sxs-lookup"><span data-stu-id="a576b-208">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

`http://localhost:5000/?lat=-35.55&long=-12.35`  

<span data-ttu-id="a576b-209">Toutes les modifications que vous devez apporter se trouvent dans l’expression lambda définie comme argument de `app.Run` dans votre classe de démarrage.</span><span class="sxs-lookup"><span data-stu-id="a576b-209">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="a576b-210">L’argument de l’expression lambda est le `HttpContext` pour la demande.</span><span class="sxs-lookup"><span data-stu-id="a576b-210">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="a576b-211">Une de ses propriétés est l’objet `Request`.</span><span class="sxs-lookup"><span data-stu-id="a576b-211">One of its properties is the `Request` object.</span></span> <span data-ttu-id="a576b-212">L’objet `Request` a une propriété `Query` qui contient un dictionnaire de toutes les valeurs dans la chaîne de requête pour la demande.</span><span class="sxs-lookup"><span data-stu-id="a576b-212">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="a576b-213">La première addition consiste à rechercher les valeurs de latitude et longitude :</span><span class="sxs-lookup"><span data-stu-id="a576b-213">The first addition is to find the latitude and longitude values:</span></span>

<span data-ttu-id="a576b-214">[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString " lit les variables à partir de la chaîne de requête")]</span><span class="sxs-lookup"><span data-stu-id="a576b-214">[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]</span></span>

<span data-ttu-id="a576b-215">Les valeurs du dictionnaire de requêtes sont de type `StringValue`.</span><span class="sxs-lookup"><span data-stu-id="a576b-215">The Query dictionary values are `StringValue` type.</span></span> <span data-ttu-id="a576b-216">Ce type peut contenir une collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a576b-216">That type can contain a collection of strings.</span></span> <span data-ttu-id="a576b-217">Pour votre service météo, chaque valeur est une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="a576b-217">For your weather service, each value is a single string.</span></span> <span data-ttu-id="a576b-218">C’est pourquoi il y a un appel à `FirstOrDefault()` dans le code ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="a576b-218">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="a576b-219">Ensuite, vous devez convertir les chaînes en valeurs de type double.</span><span class="sxs-lookup"><span data-stu-id="a576b-219">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="a576b-220">La méthode que vous allez utiliser pour convertir la chaîne en double est `double.TryParse()` :</span><span class="sxs-lookup"><span data-stu-id="a576b-220">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="a576b-221">Cette méthode s’appuie sur les paramètres de sortie de C# pour indiquer si la chaîne d’entrée peut être convertie en double.</span><span class="sxs-lookup"><span data-stu-id="a576b-221">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="a576b-222">Si la chaîne constitue une représentation valide pour un double, la méthode retourne true et l’argument `result` contient la valeur.</span><span class="sxs-lookup"><span data-stu-id="a576b-222">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="a576b-223">Si la chaîne ne représente pas une valeur double valide, la méthode retourne false.</span><span class="sxs-lookup"><span data-stu-id="a576b-223">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="a576b-224">Vous pouvez adapter cette API à l’aide d’une *méthode d’extension* qui renvoie un *double Nullable*.</span><span class="sxs-lookup"><span data-stu-id="a576b-224">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="a576b-225">Un *type de valeur Nullable* est un type qui représente un type de valeur et peut également contenir un une valeur manquante ou Null.</span><span class="sxs-lookup"><span data-stu-id="a576b-225">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="a576b-226">Un type Nullable est représenté en ajoutant le caractère `?` à la déclaration de type.</span><span class="sxs-lookup"><span data-stu-id="a576b-226">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="a576b-227">Les méthodes d’extension sont des méthodes qui sont définies comme des méthodes statiques mais qui, en ajoutant le modificateur `this` sur le premier paramètre, peuvent être appelées comme si elles étaient des membres de cette classe.</span><span class="sxs-lookup"><span data-stu-id="a576b-227">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="a576b-228">Les méthodes d’extension peuvent être définies uniquement dans les classes statiques.</span><span class="sxs-lookup"><span data-stu-id="a576b-228">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="a576b-229">Voici la définition de la classe contenant la méthode d’extension pour l’analyse :</span><span class="sxs-lookup"><span data-stu-id="a576b-229">Here's the definition of the class containing the extension method for parse:</span></span>

<span data-ttu-id="a576b-230">[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "Essayer d’analyser une valeur Nullable")]</span><span class="sxs-lookup"><span data-stu-id="a576b-230">[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]</span></span>

<span data-ttu-id="a576b-231">L’expression `default(double?)` retourne la valeur par défaut pour le type `double?`.</span><span class="sxs-lookup"><span data-stu-id="a576b-231">The `default(double?)` expression returns the default value for the `double?` type.</span></span> <span data-ttu-id="a576b-232">Cette valeur par défaut est la valeur null (ou manquante).</span><span class="sxs-lookup"><span data-stu-id="a576b-232">That default value is the null (or missing) value.</span></span>

<span data-ttu-id="a576b-233">Vous pouvez utiliser cette méthode d’extension pour convertir les arguments de chaîne de requête en type double :</span><span class="sxs-lookup"><span data-stu-id="a576b-233">You can use this extension method to convert the query string arguments into the double type:</span></span>

<span data-ttu-id="a576b-234">[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Utiliser la méthode d’extension TryParse")]</span><span class="sxs-lookup"><span data-stu-id="a576b-234">[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]</span></span>

<span data-ttu-id="a576b-235">Pour tester facilement le code d’analyse, mettez à jour la réponse pour inclure les valeurs des arguments :</span><span class="sxs-lookup"><span data-stu-id="a576b-235">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

<span data-ttu-id="a576b-236">[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Écrire la réponse de sortie")]</span><span class="sxs-lookup"><span data-stu-id="a576b-236">[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]</span></span>

<span data-ttu-id="a576b-237">À ce stade, vous pouvez exécuter l’application web et voir si votre code d’analyse fonctionne.</span><span class="sxs-lookup"><span data-stu-id="a576b-237">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="a576b-238">Ajoutez des valeurs à la requête web dans un navigateur, et vous devriez voir les résultats de la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="a576b-238">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="a576b-239">Générer des prévisions météorologiques aléatoires</span><span class="sxs-lookup"><span data-stu-id="a576b-239">Build a random weather forecast</span></span>

<span data-ttu-id="a576b-240">La tâche suivante consiste à créer des prévisions météorologiques aléatoires.</span><span class="sxs-lookup"><span data-stu-id="a576b-240">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="a576b-241">Commençons avec un conteneur de données qui contient les valeurs que vous souhaiteriez pour les prévisions météorologiques :</span><span class="sxs-lookup"><span data-stu-id="a576b-241">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

<span data-ttu-id="a576b-242">Ensuite, générez un constructeur qui définit de façon aléatoire ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="a576b-242">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="a576b-243">Ce constructeur utilise les valeurs de latitude et de longitude pour amorcer le générateur de nombres aléatoires.</span><span class="sxs-lookup"><span data-stu-id="a576b-243">This constructor uses the values for the latitude and longitude to seed the Random number generator.</span></span> <span data-ttu-id="a576b-244">Cela signifie que la prévision pour un même emplacement est la même.</span><span class="sxs-lookup"><span data-stu-id="a576b-244">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="a576b-245">Si vous modifiez les arguments pour la latitude et la longitude, vous obtiendrez une prévision différente (parce que vous démarrez avec une valeur initiale différente.)</span><span class="sxs-lookup"><span data-stu-id="a576b-245">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed.)</span></span>

<span data-ttu-id="a576b-246">[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Constructeur de rapport météorologique")]</span><span class="sxs-lookup"><span data-stu-id="a576b-246">[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]</span></span>

<span data-ttu-id="a576b-247">Vous pouvez maintenant générer des prévisions sur 5 jours dans votre méthode de réponse :</span><span class="sxs-lookup"><span data-stu-id="a576b-247">You can now generate the 5-day forecast in your response method:</span></span>

<span data-ttu-id="a576b-248">[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Générer un bulletin météorologique aléatoire")]</span><span class="sxs-lookup"><span data-stu-id="a576b-248">[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]</span></span>

### <a name="build-the-json-response"></a><span data-ttu-id="a576b-249">Générez la réponse JSON.</span><span class="sxs-lookup"><span data-stu-id="a576b-249">Build the JSON response.</span></span>

<span data-ttu-id="a576b-250">La tâche de code final sur le serveur consiste à convertir le tableau WeatherReport en un paquet JSON, et de renvoyer cela au client.</span><span class="sxs-lookup"><span data-stu-id="a576b-250">The final code task on the server is to convert the WeatherReport array into a JSON packet, and send that back to the client.</span></span> <span data-ttu-id="a576b-251">Commençons par créer le paquet JSON.</span><span class="sxs-lookup"><span data-stu-id="a576b-251">Let's start by creating the JSON packet.</span></span> <span data-ttu-id="a576b-252">Vous allez ajouter le sérialiseur JSON NewtonSoft à la liste des dépendances.</span><span class="sxs-lookup"><span data-stu-id="a576b-252">You'll add the NewtonSoft JSON Serializer to the list of dependencies.</span></span> <span data-ttu-id="a576b-253">Pour ce faire, utilisez l’interface CLI `dotnet` :</span><span class="sxs-lookup"><span data-stu-id="a576b-253">You can do that using the `dotnet` CLI:</span></span>

```
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="a576b-254">Ensuite, vous pouvez utiliser la classe `JsonConvert` pour écrire l’objet dans une chaîne :</span><span class="sxs-lookup"><span data-stu-id="a576b-254">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

<span data-ttu-id="a576b-255">[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convertir les objets en JSON")]</span><span class="sxs-lookup"><span data-stu-id="a576b-255">[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]</span></span>

<span data-ttu-id="a576b-256">Le code ci-dessus convertit l’objet de prévision (une liste d’objets `WeatherForecast`) en un paquet JSON.</span><span class="sxs-lookup"><span data-stu-id="a576b-256">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON packet.</span></span> <span data-ttu-id="a576b-257">Une fois que vous avez construit le paquet de réponse, vous définissez le type de contenu `application/json` et écrivez la chaîne.</span><span class="sxs-lookup"><span data-stu-id="a576b-257">After you've constructed the response packet, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="a576b-258">Maintenant, l’application s’exécute et renvoie des prévisions aléatoires.</span><span class="sxs-lookup"><span data-stu-id="a576b-258">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="a576b-259">Créer une image Docker</span><span class="sxs-lookup"><span data-stu-id="a576b-259">Build a Docker image</span></span>

<span data-ttu-id="a576b-260">La dernière tâche consiste à exécuter l’application dans Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-260">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="a576b-261">Nous allons créer un conteneur Docker qui exécute une image Docker qui représente l’application.</span><span class="sxs-lookup"><span data-stu-id="a576b-261">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="a576b-262">Une ***image Docker*** est un fichier qui définit l’environnement d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="a576b-262">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="a576b-263">Un ***conteneur Docker*** représente une instance en cours d’exécution d’une image Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-263">A ***Docker Container*** represents a running instance of a Docker image.</span></span>

<span data-ttu-id="a576b-264">Par analogie, vous pouvez considérer *l’Image Docker* comme une *classe* et le *conteneur Docker* comme un objet ou une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="a576b-264">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="a576b-265">Le fichier Dockerfile créé par le modèle asp.net prend en charge nos besoins.</span><span class="sxs-lookup"><span data-stu-id="a576b-265">The Dockerfile created by the asp.net template will serve for our purposes.</span></span> <span data-ttu-id="a576b-266">Attardons-nous sur son contenu.</span><span class="sxs-lookup"><span data-stu-id="a576b-266">Let's go over its contents.</span></span>

<span data-ttu-id="a576b-267">La première ligne indique l’image source :</span><span class="sxs-lookup"><span data-stu-id="a576b-267">The first line specifies the source image:</span></span>

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

<span data-ttu-id="a576b-268">Docker vous permet de configurer une image d’ordinateur basée sur un modèle source.</span><span class="sxs-lookup"><span data-stu-id="a576b-268">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="a576b-269">Cela signifie que vous n’êtes pas obligé de fournir tous les paramètres de la machine lorsque vous démarrez. Il vous suffit de fournir les modifications éventuelles.</span><span class="sxs-lookup"><span data-stu-id="a576b-269">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="a576b-270">Les modifications apportées ici serviront à inclure notre application.</span><span class="sxs-lookup"><span data-stu-id="a576b-270">The changes here will be to include our application.</span></span>

<span data-ttu-id="a576b-271">Dans ce premier exemple, nous allons utiliser la version `1.1-sdk-msbuild` de l’image dotnet.</span><span class="sxs-lookup"><span data-stu-id="a576b-271">In this first sample, we'll use the `1.1-sdk-msbuild` version of the dotnet image.</span></span> <span data-ttu-id="a576b-272">Il s’agit du moyen le plus simple de créer un environnement Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-272">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="a576b-273">Cette image inclut le composant d’exécution principal dotnet et le kit de développement logiciel dotnet.</span><span class="sxs-lookup"><span data-stu-id="a576b-273">This image include the dotnet core runtime, and the dotnet SDK.</span></span> <span data-ttu-id="a576b-274">Cela facilite la mise en route et la création, mais génère aussi une image plus grande.</span><span class="sxs-lookup"><span data-stu-id="a576b-274">That makes it easier to get started and build, but does create a larger image.</span></span>

<span data-ttu-id="a576b-275">Les cinq lignes suivantes configurent et génèrent votre application :</span><span class="sxs-lookup"><span data-stu-id="a576b-275">The next five lines setup and build your application:</span></span>

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="a576b-276">Cela copie le fichier de projet à partir du répertoire actuel sur la machine virtuelle Docker et restaure tous les packages.</span><span class="sxs-lookup"><span data-stu-id="a576b-276">This will copy the project file from the  current directory to the docker VM, and restore all the packages.</span></span> <span data-ttu-id="a576b-277">L’utilisation de l’interface de ligne de commande dotnet signifie que l’image Docker doit inclure le kit de développement logiciel .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a576b-277">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="a576b-278">Après cela, le reste de votre application est copié et le la commande dotnet publish génère et crée un package de votre application.</span><span class="sxs-lookup"><span data-stu-id="a576b-278">After that, the rest of your application gets copied, and the dotnet publish command builds and packages your application.</span></span>

<span data-ttu-id="a576b-279">La dernière ligne du fichier exécute l’application :</span><span class="sxs-lookup"><span data-stu-id="a576b-279">The final line of the file runs the application:</span></span>

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

<span data-ttu-id="a576b-280">Ce port configuré est référencé dans l’argument `--server.urls` sur `dotnet` sur la dernière ligne du fichier Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-280">This configured port is referenced in the `--server.urls` argument to `dotnet` on the last  line of the Dockerfile.</span></span> <span data-ttu-id="a576b-281">La commande `ENTRYPOINT` informe Docker des options de commande et de la ligne de commande qui démarrent le service.</span><span class="sxs-lookup"><span data-stu-id="a576b-281">The `ENTRYPOINT` command informs Docker  what command and command line options start the service.</span></span> 

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="a576b-282">Génération et exécution de l’image dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="a576b-282">Building and running the image in a container.</span></span>

<span data-ttu-id="a576b-283">Nous allons créer une image et exécuter le service à l’intérieur d’un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-283">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="a576b-284">Nous ne voulons pas que tous les fichiers de votre répertoire local soient copiés dans l’image.</span><span class="sxs-lookup"><span data-stu-id="a576b-284">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="a576b-285">Au lieu de cela, nous allons développer l’application dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="a576b-285">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="a576b-286">Vous allez créer un fichier `.dockerignore` pour spécifier les répertoires qui ne sont pas copiés dans l’image.</span><span class="sxs-lookup"><span data-stu-id="a576b-286">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="a576b-287">Nous ne souhaitons copier aucune des ressources build.</span><span class="sxs-lookup"><span data-stu-id="a576b-287">You don't want any of the build assets copied.</span></span> <span data-ttu-id="a576b-288">Spécifiez les répertoires build et publish dans le fichier `.dockerignore` :</span><span class="sxs-lookup"><span data-stu-id="a576b-288">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="a576b-289">Vous générez l’image avec la commande docker build.</span><span class="sxs-lookup"><span data-stu-id="a576b-289">You build the image using the docker build command.</span></span> <span data-ttu-id="a576b-290">Exécutez la commande suivante à partir du répertoire qui contient votre code.</span><span class="sxs-lookup"><span data-stu-id="a576b-290">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="a576b-291">Cette commande génère l’image de conteneur sur la base de toutes les informations de votre fichier Docker.</span><span class="sxs-lookup"><span data-stu-id="a576b-291">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="a576b-292">L’argument `-t` fournit une balise ou un nom pour cette image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="a576b-292">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="a576b-293">Dans la ligne de commande ci-dessus, la balise utilisée pour le conteneur Docker est `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="a576b-293">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="a576b-294">Lorsque cette commande est terminée, vous disposez d’un conteneur prêt à exécuter votre nouveau service.</span><span class="sxs-lookup"><span data-stu-id="a576b-294">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="a576b-295">Exécutez la commande suivante pour démarrer le conteneur et lancer votre service :</span><span class="sxs-lookup"><span data-stu-id="a576b-295">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

<span data-ttu-id="a576b-296">L’option `-d` consiste à exécuter le conteneur de façon détachée du terminal actuel.</span><span class="sxs-lookup"><span data-stu-id="a576b-296">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="a576b-297">Cela signifie que vous ne verrez pas le résultat de la commande dans votre terminal.</span><span class="sxs-lookup"><span data-stu-id="a576b-297">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="a576b-298">L’option `-p` indique le mappage de port entre le service et la machine hôte.</span><span class="sxs-lookup"><span data-stu-id="a576b-298">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="a576b-299">Ici, elle indique que toute requête entrante sur le port 80 doit être transférée vers le port 5000 sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="a576b-299">Here it says that any incoming request on port 80 should be forwarded to port 5000 on the container.</span></span> <span data-ttu-id="a576b-300">5000 correspond au port sur lequel votre service écoute venant des arguments de ligne de commande spécifiés dans le fichier Docker ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="a576b-300">Using 5000 matches the port your service is listening on from the command line arguments specified in the Dockerfile above.</span></span> <span data-ttu-id="a576b-301">L’argument `--name` nomme votre conteneur en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a576b-301">The `--name` argument names your running container.</span></span> <span data-ttu-id="a576b-302">Il s’agit d’un nom convivial que vous pouvez utiliser pour travailler avec ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="a576b-302">It's a convenient name you can use to work with that container.</span></span> 

<span data-ttu-id="a576b-303">Vous pouvez voir si l’image est en cours d’exécution avec la commande :</span><span class="sxs-lookup"><span data-stu-id="a576b-303">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="a576b-304">Si votre conteneur est en cours d’exécution, vous verrez une ligne qui répertorie les processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a576b-304">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="a576b-305">(Il peut s’agir de la seule).</span><span class="sxs-lookup"><span data-stu-id="a576b-305">(It may be the only one).</span></span>

<span data-ttu-id="a576b-306">Vous pouvez tester votre service en ouvrant un navigateur et en accédant à localhost et en spécifiant une latitude et une longitude :</span><span class="sxs-lookup"><span data-stu-id="a576b-306">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="a576b-307">Attachement à un conteneur en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="a576b-307">Attaching to a running container</span></span>

<span data-ttu-id="a576b-308">Lorsque vous avez exécuté votre service dans une fenêtre de commande, vous pouvez voir les informations de diagnostic imprimées pour chaque demande.</span><span class="sxs-lookup"><span data-stu-id="a576b-308">When you ran your sevice in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="a576b-309">Ces informations ne s’affichent pas lorsque votre conteneur s’exécute en mode détaché.</span><span class="sxs-lookup"><span data-stu-id="a576b-309">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="a576b-310">La commande attach de Docker vous permet de vous attacher à un conteneur en cours d’exécution afin de voir les informations du journal.</span><span class="sxs-lookup"><span data-stu-id="a576b-310">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="a576b-311">Exécutez cette commande à partir d’une fenêtre de commande :</span><span class="sxs-lookup"><span data-stu-id="a576b-311">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="a576b-312">L’argument `--sig-proxy=false` signifie que les commandes `Ctrl-C` ne sont pas envoyées au processus de conteneur, mais arrêtent plutôt la commande `docker attach`.</span><span class="sxs-lookup"><span data-stu-id="a576b-312">The `--sig-proxy=false` argument means that `Ctrl-C` commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="a576b-313">Le dernier argument est le nom donné au conteneur dans la commande `docker run`.</span><span class="sxs-lookup"><span data-stu-id="a576b-313">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="a576b-314">Vous pouvez également utiliser l’ID de conteneur affecté au Docker pour faire référence à n’importe quel conteneur.</span><span class="sxs-lookup"><span data-stu-id="a576b-314">You can also use the docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="a576b-315">Si vous n’avez pas spécifié de nom pour votre conteneur dans `docker run`, vous devez utiliser l’ID de conteneur.</span><span class="sxs-lookup"><span data-stu-id="a576b-315">If you didn't specify a name for your container in `docker run` you must use the container id.</span></span>

<span data-ttu-id="a576b-316">Ouvrez un navigateur et accédez à votre service.</span><span class="sxs-lookup"><span data-stu-id="a576b-316">Open a browser and navigate to your service.</span></span> <span data-ttu-id="a576b-317">Vous verrez les messages de diagnostic dans la fenêtre de commande à partir du conteneur en cours d’exécution attaché.</span><span class="sxs-lookup"><span data-stu-id="a576b-317">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="a576b-318">Appuyez sur `Ctrl-C` pour arrêter le processus d’attachement.</span><span class="sxs-lookup"><span data-stu-id="a576b-318">Press `Ctrl-C` to stop the attach process.</span></span>

<span data-ttu-id="a576b-319">Lorsque vous avez terminé de manipuler votre conteneur, vous pouvez l’arrêter :</span><span class="sxs-lookup"><span data-stu-id="a576b-319">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="a576b-320">Le conteneur et l’image sont toujours disponibles pour vous permettre de redémarrer.</span><span class="sxs-lookup"><span data-stu-id="a576b-320">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="a576b-321">Si vous souhaitez supprimer le conteneur de votre machine, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="a576b-321">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="a576b-322">Si vous souhaitez supprimer des images inutilisées dans votre machine, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="a576b-322">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="a576b-323">Conclusion</span><span class="sxs-lookup"><span data-stu-id="a576b-323">Conclusion</span></span> 

<span data-ttu-id="a576b-324">Dans ce didacticiel, vous avez généré un microservice de base ASP.NET et ajouté quelques fonctionnalités simples.</span><span class="sxs-lookup"><span data-stu-id="a576b-324">In this tutorial, you built an asp.net core microservice, and added a few simple features.</span></span>

<span data-ttu-id="a576b-325">Vous avez construit une image de conteneur Docker pour ce service et exécuté ce conteneur sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="a576b-325">You built a docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="a576b-326">Vous avez attaché une fenêtre de terminal au service et vu les messages de diagnostic à partir de votre service.</span><span class="sxs-lookup"><span data-stu-id="a576b-326">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="a576b-327">En chemin, vous avez vu plusieurs fonctionnalités du langage C# en action.</span><span class="sxs-lookup"><span data-stu-id="a576b-327">Along the way, you saw several features of the C# language in action.</span></span>

