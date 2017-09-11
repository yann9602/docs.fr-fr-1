---
title: Commande dotnet-run - Interface CLI .NET Core
description: "La commande dotnet-run fournit une option pratique pour exécuter votre application à partir du code source."
keywords: "dotnet-run, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f0a6fce4f83808076b7cbcabdaa948badde2cf80
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-run"></a><span data-ttu-id="ff9f5-104">dotnet-run</span><span class="sxs-lookup"><span data-stu-id="ff9f5-104">dotnet-run</span></span>

## <a name="name"></a><span data-ttu-id="ff9f5-105">Nom</span><span class="sxs-lookup"><span data-stu-id="ff9f5-105">Name</span></span> 

<span data-ttu-id="ff9f5-106">`dotnet-run` - Exécute le code source sans commandes explicites de compilation ou de démarrage.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-106">`dotnet-run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ff9f5-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="ff9f5-107">Synopsis</span></span>

`dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]] [-h|--help]`

## <a name="description"></a><span data-ttu-id="ff9f5-108">Description</span><span class="sxs-lookup"><span data-stu-id="ff9f5-108">Description</span></span>

<span data-ttu-id="ff9f5-109">La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="ff9f5-110">Elle est utile pour le développement itératif rapide en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="ff9f5-111">Elle dépend de la commande [`dotnet build`](dotnet-build.md) pour générer le code.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="ff9f5-112">Les conditions requises pour la génération, par exemple le fait que le projet doit être restauré en premier, s’appliquent également à `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span> 

<span data-ttu-id="ff9f5-113">Les fichiers de sortie sont écrits dans l’emplacement par défaut, à savoir `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="ff9f5-114">Par exemple, si vous avez une application `netcoreapp1.0` et que vous exécutez `dotnet run`, la sortie est placée dans `bin/Debug/netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-114">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="ff9f5-115">Les fichiers sont remplacés, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-115">Files are overwritten as needed.</span></span> <span data-ttu-id="ff9f5-116">Les fichiers temporaires sont placés dans le répertoire `obj`.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-116">Temporary files are placed in the `obj` directory.</span></span> 

<span data-ttu-id="ff9f5-117">Si le projet spécifie plusieurs frameworks, l’exécution de `dotnet run` entraîne une erreur, sauf si l’option `-f|--framework <FRAMEWORK>` est utilisée pour spécifier le framework.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="ff9f5-118">La commande `dotnet run` est utilisée pour des projets, et pas pour des assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="ff9f5-119">Si vous tentez d’exécuter plutôt une DLL d’applications dépendantes du framework, vous devez utiliser [dotnet](dotnet.md) sans commande.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="ff9f5-120">Par exemple, pour exécuter `myapp.dll`, utilisez :</span><span class="sxs-lookup"><span data-stu-id="ff9f5-120">For example, to run `myapp.dll`, use:</span></span>
 
```
dotnet myapp.dll
```

<span data-ttu-id="ff9f5-121">Pour plus d’informations sur le pilote `dotnet`, consultez la rubrique [Outils en ligne de commande (CLI) .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="ff9f5-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="ff9f5-122">Pour exécuter l’application, la commande `dotnet run` résout les dépendances de l’application externes au runtime partagé à partir du cache NuGet.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-122">In order to run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="ff9f5-123">Dans la mesure où elle utilise la mise en cache des dépendances, il n’est pas recommandé d’utiliser `dotnet run` pour exécuter des applications en production.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="ff9f5-124">[Créez plutôt un déploiement](../deploying/index.md) à l’aide de la commande [`dotnet publish`](dotnet-publish.md) et déployez le résultat publié.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span> 

## <a name="options"></a><span data-ttu-id="ff9f5-125">Options</span><span class="sxs-lookup"><span data-stu-id="ff9f5-125">Options</span></span>

`--`

<span data-ttu-id="ff9f5-126">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="ff9f5-127">Tous les arguments après celui-ci sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-127">All arguments after this one are passed to the application run.</span></span> 

`-h|--help`

<span data-ttu-id="ff9f5-128">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-128">Prints out a short help for the command.</span></span>

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="ff9f5-129">Configuration à utiliser pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-129">Configuration to use for building the project.</span></span> <span data-ttu-id="ff9f5-130">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-130">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ff9f5-131">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="ff9f5-132">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-132">The framework must be specified in the project file.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="ff9f5-133">Spécifie le chemin d’accès et le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-133">Specifies the path and name of the project file.</span></span> <span data-ttu-id="ff9f5-134">(Voir la REMARQUE.) Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-134">(See the NOTE.) It defaults to the current directory if not specified.</span></span>

> [!NOTE]
> <span data-ttu-id="ff9f5-135">Utilisez le chemin d’accès et le nom du fichier projet avec l’option `-p|--project`.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-135">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="ff9f5-136">Une régression dans l’interface CLI empêche de fournir un chemin d’accès de dossier pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="ff9f5-136">A regression in the CLI prevents providing a folder path at this time.</span></span> <span data-ttu-id="ff9f5-137">Pour plus d’informations et pour suivre ce problème, consultez la page [dotnet run -p, impossible de démarrer un projet (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="ff9f5-137">For more information and to track this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

## <a name="examples"></a><span data-ttu-id="ff9f5-138">Exemples</span><span class="sxs-lookup"><span data-stu-id="ff9f5-138">Examples</span></span>

<span data-ttu-id="ff9f5-139">Exécutez le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="ff9f5-139">Run the project in the current directory:</span></span>

`dotnet run` 

<span data-ttu-id="ff9f5-140">Exécutez le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="ff9f5-140">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="ff9f5-141">Exécuter le projet situé dans le répertoire actif (l’argument `--help` de cet exemple est passé à l’application, puisque l’argument `--` est utilisé) :</span><span class="sxs-lookup"><span data-stu-id="ff9f5-141">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`

