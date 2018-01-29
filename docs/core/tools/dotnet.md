---
title: Commande dotnet - Interface CLI .NET Core
description: "Découvrez la commande dotnet (le pilote générique des outils .NET Core CLI) et comment l’utiliser."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2eea7d13994bfddc89d8f3513308a6620c53c88c
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="3fe1a-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="3fe1a-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3fe1a-104">Name</span><span class="sxs-lookup"><span data-stu-id="3fe1a-104">Name</span></span>

<span data-ttu-id="3fe1a-105">`dotnet` - Pilote général pour l’exécution des commandes de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3fe1a-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="3fe1a-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3fe1a-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3fe1a-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3fe1a-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3fe1a-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="3fe1a-109">Description</span><span class="sxs-lookup"><span data-stu-id="3fe1a-109">Description</span></span>

<span data-ttu-id="3fe1a-110">`dotnet` est un pilote générique pour la chaîne d’outils de l’interface de ligne de commande (CLI).</span><span class="sxs-lookup"><span data-stu-id="3fe1a-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="3fe1a-111">Appelé seul, il fournit des instructions d’utilisation succinctes.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="3fe1a-112">Chaque fonctionnalité est implémentée comme une commande.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="3fe1a-113">Pour utiliser la fonctionnalité, la commande est spécifiée après `dotnet`, comme dans [`dotnet build`](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="3fe1a-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="3fe1a-114">Tous les arguments qui suivent la commande sont ses arguments propres.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="3fe1a-115">Le seul cas où la commande `dotnet` est utilisée seule est l’exécution d’applications [dépendantes du framework](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="3fe1a-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="3fe1a-116">Spécifiez une DLL d’application après le verbe `dotnet` pour exécuter l’application (par exemple, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="3fe1a-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="3fe1a-117">Options</span><span class="sxs-lookup"><span data-stu-id="3fe1a-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3fe1a-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3fe1a-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="3fe1a-119">Chemin du fichier *deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="3fe1a-120">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="3fe1a-121">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="3fe1a-122">Version du runtime .NET Core installé à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="3fe1a-123">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-123">Prints out a short help for the command.</span></span> <span data-ttu-id="3fe1a-124">Si vous l’utilisez avec `dotnet`, elle affiche également la liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="3fe1a-125">Affiche des informations détaillées sur l’environnement et les outils CLI, telles que le système d’exploitation actuel, le SHA de validation de la version, etc.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="3fe1a-126">Effectue une restauration par progression en l’absence de framework candidat partagé.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="3fe1a-127">Active la sortie détaillée.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="3fe1a-128">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3fe1a-129">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3fe1a-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="3fe1a-130">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="3fe1a-131">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="3fe1a-132">Version du runtime .NET Core installé à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="3fe1a-133">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-133">Prints out a short help for the command.</span></span> <span data-ttu-id="3fe1a-134">Si vous l’utilisez avec `dotnet`, elle affiche également la liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="3fe1a-135">Affiche des informations détaillées sur l’environnement et les outils CLI, telles que le système d’exploitation actuel, le SHA de validation de la version, etc.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="3fe1a-136">Active la sortie détaillée.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="3fe1a-137">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="3fe1a-138">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="3fe1a-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="3fe1a-139">Général</span><span class="sxs-lookup"><span data-stu-id="3fe1a-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3fe1a-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3fe1a-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="3fe1a-141">Commande</span><span class="sxs-lookup"><span data-stu-id="3fe1a-141">Command</span></span>                             | <span data-ttu-id="3fe1a-142">Fonction</span><span class="sxs-lookup"><span data-stu-id="3fe1a-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3fe1a-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3fe1a-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="3fe1a-144">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3fe1a-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3fe1a-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="3fe1a-146">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="3fe1a-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="3fe1a-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="3fe1a-148">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="3fe1a-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3fe1a-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="3fe1a-150">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3fe1a-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3fe1a-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="3fe1a-152">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3fe1a-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3fe1a-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="3fe1a-154">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3fe1a-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3fe1a-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="3fe1a-156">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3fe1a-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3fe1a-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="3fe1a-158">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3fe1a-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3fe1a-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="3fe1a-160">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3fe1a-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3fe1a-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="3fe1a-162">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3fe1a-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3fe1a-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="3fe1a-164">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3fe1a-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="3fe1a-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="3fe1a-166">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="3fe1a-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3fe1a-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="3fe1a-168">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3fe1a-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3fe1a-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="3fe1a-170">Commande</span><span class="sxs-lookup"><span data-stu-id="3fe1a-170">Command</span></span>                             | <span data-ttu-id="3fe1a-171">Fonction</span><span class="sxs-lookup"><span data-stu-id="3fe1a-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3fe1a-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3fe1a-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="3fe1a-173">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3fe1a-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3fe1a-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="3fe1a-175">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="3fe1a-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3fe1a-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="3fe1a-177">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3fe1a-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3fe1a-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="3fe1a-179">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3fe1a-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3fe1a-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="3fe1a-181">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3fe1a-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3fe1a-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="3fe1a-183">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3fe1a-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3fe1a-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="3fe1a-185">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3fe1a-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3fe1a-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="3fe1a-187">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3fe1a-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3fe1a-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="3fe1a-189">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3fe1a-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3fe1a-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="3fe1a-191">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3fe1a-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3fe1a-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="3fe1a-193">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="3fe1a-194">Références de projets</span><span class="sxs-lookup"><span data-stu-id="3fe1a-194">Project references</span></span>

<span data-ttu-id="3fe1a-195">Commande</span><span class="sxs-lookup"><span data-stu-id="3fe1a-195">Command</span></span> | <span data-ttu-id="3fe1a-196">Fonction</span><span class="sxs-lookup"><span data-stu-id="3fe1a-196">Function</span></span>
--- | ---
[<span data-ttu-id="3fe1a-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="3fe1a-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="3fe1a-198">Ajoute une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-198">Add a project reference.</span></span>
[<span data-ttu-id="3fe1a-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="3fe1a-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="3fe1a-200">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-200">List project references.</span></span>
[<span data-ttu-id="3fe1a-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="3fe1a-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="3fe1a-202">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="3fe1a-203">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="3fe1a-203">NuGet packages</span></span>

<span data-ttu-id="3fe1a-204">Commande</span><span class="sxs-lookup"><span data-stu-id="3fe1a-204">Command</span></span> | <span data-ttu-id="3fe1a-205">Fonction</span><span class="sxs-lookup"><span data-stu-id="3fe1a-205">Function</span></span>
--- | ---
[<span data-ttu-id="3fe1a-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="3fe1a-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="3fe1a-207">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-207">Add a NuGet package.</span></span>
[<span data-ttu-id="3fe1a-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="3fe1a-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="3fe1a-209">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="3fe1a-210">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="3fe1a-210">NuGet commands</span></span>

<span data-ttu-id="3fe1a-211">Commande</span><span class="sxs-lookup"><span data-stu-id="3fe1a-211">Command</span></span> | <span data-ttu-id="3fe1a-212">Fonction</span><span class="sxs-lookup"><span data-stu-id="3fe1a-212">Function</span></span>
--- | ---
[<span data-ttu-id="3fe1a-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="3fe1a-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="3fe1a-214">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="3fe1a-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="3fe1a-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="3fe1a-216">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="3fe1a-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="3fe1a-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="3fe1a-218">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="3fe1a-219">Exemples</span><span class="sxs-lookup"><span data-stu-id="3fe1a-219">Examples</span></span>

<span data-ttu-id="3fe1a-220">Initialisez un exemple d’application console .NET Core qui peut être compilé et exécuté :</span><span class="sxs-lookup"><span data-stu-id="3fe1a-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="3fe1a-221">Restaurez les dépendances d’une application donnée :</span><span class="sxs-lookup"><span data-stu-id="3fe1a-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="3fe1a-222">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="3fe1a-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="3fe1a-223">Exécuter une application dépendante du framework nommée `myapp.dll` :</span><span class="sxs-lookup"><span data-stu-id="3fe1a-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="3fe1a-224">Variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="3fe1a-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="3fe1a-225">Cache du package principal.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-225">The primary package cache.</span></span> <span data-ttu-id="3fe1a-226">S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%HOME%\NuGet\Packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="3fe1a-227">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="3fe1a-228">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="3fe1a-229">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `1`, `yes` ou `false`) ; définie sur `true` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="3fe1a-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="3fe1a-230">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="3fe1a-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>
