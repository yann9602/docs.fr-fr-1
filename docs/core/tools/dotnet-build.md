---
title: Commande dotnet-build - Interface CLI .NET Core
description: "La commande dotnet-build permet de générer un projet et l’ensemble de ses dépendances."
keywords: dotnet-build, CLI, commande CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2006b15978f384e53e43a0a2562e81d10582abd
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-build"></a><span data-ttu-id="f76ad-104">dotnet-build</span><span class="sxs-lookup"><span data-stu-id="f76ad-104">dotnet-build</span></span>

## <a name="name"></a><span data-ttu-id="f76ad-105">Nom</span><span class="sxs-lookup"><span data-stu-id="f76ad-105">Name</span></span>

<span data-ttu-id="f76ad-106">`dotnet-build` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="f76ad-106">`dotnet-build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f76ad-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="f76ad-107">Synopsis</span></span>

`dotnet build [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="f76ad-108">Description</span><span class="sxs-lookup"><span data-stu-id="f76ad-108">Description</span></span>

<span data-ttu-id="f76ad-109">La commande `dotnet build` génère le projet et ses dépendances dans un ensemble de fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="f76ad-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="f76ad-110">Les fichiers binaires incluent le code du projet dans des fichiers en langage intermédiaire (IL) avec une extension *.dll* et les fichiers de symboles utilisés pour le débogage avec une extension *.pdb*.</span><span class="sxs-lookup"><span data-stu-id="f76ad-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="f76ad-111">Un fichier JSON de dépendances (*\*.deps.json*) est généré. Il répertorie les dépendances de l’application.</span><span class="sxs-lookup"><span data-stu-id="f76ad-111">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="f76ad-112">Un fichier *\*.runtimeconfig.json* est généré. Il spécifie le runtime partagé et sa version pour l’application.</span><span class="sxs-lookup"><span data-stu-id="f76ad-112">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="f76ad-113">Si le projet a des dépendances tierces, comme des bibliothèques NuGet, elles sont résolues à partir du cache NuGet et ne sont pas disponibles avec la sortie générée du projet.</span><span class="sxs-lookup"><span data-stu-id="f76ad-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="f76ad-114">Par conséquent, le produit de `dotnet build` ne peut pas être transféré en l’état vers un autre ordinateur pour exécution.</span><span class="sxs-lookup"><span data-stu-id="f76ad-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="f76ad-115">Ce comportement contraste avec celui du .NET Framework dans lequel la génération d’un projet exécutable (une application) produit une sortie exécutable sur n’importe quel ordinateur où le .NET Framework est installé.</span><span class="sxs-lookup"><span data-stu-id="f76ad-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="f76ad-116">Pour obtenir un résultat similaire dans .NET Core, vous utilisez la commande [dotnet publish](dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="f76ad-116">To have a similar experience with .NET Core, you use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="f76ad-117">Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f76ad-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> 

<span data-ttu-id="f76ad-118">La génération requiert le fichier *project.assets.json* qui répertorie les dépendances de votre application.</span><span class="sxs-lookup"><span data-stu-id="f76ad-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="f76ad-119">Le fichier est créé lorsque vous exécutez [`dotnet restore`](dotnet-restore.md) avant de générer le projet.</span><span class="sxs-lookup"><span data-stu-id="f76ad-119">The file is created when you execute [`dotnet restore`](dotnet-restore.md) before building the project.</span></span> <span data-ttu-id="f76ad-120">Si le fichier de ressources est absent, les outils ne peuvent pas résoudre les assemblys de référence, ce qui entraîne des erreurs.</span><span class="sxs-lookup"><span data-stu-id="f76ad-120">Without the assets file in place, the tooling cannot resolve reference assemblies, which will result in errors.</span></span>

<span data-ttu-id="f76ad-121">La commande `dotnet build` utilise MSBuild pour générer le projet. Elle prend donc en charge les builds parallèles et les builds incrémentielles.</span><span class="sxs-lookup"><span data-stu-id="f76ad-121">`dotnet build` uses MSBuild to build the project; thus, it supports both parallel and incremental builds.</span></span> <span data-ttu-id="f76ad-122">Pour plus d’informations, consultez [Builds incrémentielles](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="f76ad-122">Refer to [Incremental Builds](/visualstudio/msbuild/incremental-builds) for more information.</span></span> 

<span data-ttu-id="f76ad-123">En plus de ses options, la commande `dotnet build` accepte des options MSBuild, comme `/p` pour définir des propriétés ou `/l` pour définir un enregistreur d’événements.</span><span class="sxs-lookup"><span data-stu-id="f76ad-123">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `/p` for setting properties or `/l` to define a logger.</span></span> <span data-ttu-id="f76ad-124">En savoir plus sur ces options dans les [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="f76ad-124">Learn more about these options in the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> 

<span data-ttu-id="f76ad-125">La possibilité d’exécuter le projet ou non est déterminée par la propriété `<OutputType>` dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="f76ad-125">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="f76ad-126">L’exemple suivant illustre un projet qui génère du code exécutable :</span><span class="sxs-lookup"><span data-stu-id="f76ad-126">The following example shows a project that will produce executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="f76ad-127">Pour générer une bibliothèque, omettez la propriété `<OutputType>`.</span><span class="sxs-lookup"><span data-stu-id="f76ad-127">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="f76ad-128">La principale différence dans la sortie générée est que la DLL de langage intermédiaire pour une bibliothèque ne contient pas de points d’entrée et ne peut pas être exécutée.</span><span class="sxs-lookup"><span data-stu-id="f76ad-128">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span> 

## <a name="arguments"></a><span data-ttu-id="f76ad-129">Arguments</span><span class="sxs-lookup"><span data-stu-id="f76ad-129">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f76ad-130">Fichier projet à générer.</span><span class="sxs-lookup"><span data-stu-id="f76ad-130">The project file to build.</span></span> <span data-ttu-id="f76ad-131">Si vous ne spécifiez pas de fichier projet, MSBuild recherche dans le répertoire de travail actuel un fichier avec une extension se terminant par *proj* et l’utilise.</span><span class="sxs-lookup"><span data-stu-id="f76ad-131">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="f76ad-132">Options</span><span class="sxs-lookup"><span data-stu-id="f76ad-132">Options</span></span>

`-h|--help`

<span data-ttu-id="f76ad-133">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f76ad-133">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f76ad-134">Répertoire dans lequel placer les fichiers binaires générés.</span><span class="sxs-lookup"><span data-stu-id="f76ad-134">Directory in which to place the built binaries.</span></span> <span data-ttu-id="f76ad-135">Vous devez également définir `--framework` lorsque vous spécifiez cette option.</span><span class="sxs-lookup"><span data-stu-id="f76ad-135">You also need to define `--framework` when you specify this option.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f76ad-136">Compile pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="f76ad-136">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f76ad-137">Le framework doit être défini dans le [fichier projet](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="f76ad-137">The framework must be defined in the [project file](csproj.md).</span></span>

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="f76ad-138">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="f76ad-138">Defines the build configuration.</span></span> <span data-ttu-id="f76ad-139">En cas d’omission, la configuration de build est définie par défaut sur `Debug`.</span><span class="sxs-lookup"><span data-stu-id="f76ad-139">If omitted, the build configuration defaults to `Debug`.</span></span> <span data-ttu-id="f76ad-140">Utiliser `Release` pour créer une configuration Release.</span><span class="sxs-lookup"><span data-stu-id="f76ad-140">Use `Release` build a Release configuration.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="f76ad-141">Spécifie le runtime cible.</span><span class="sxs-lookup"><span data-stu-id="f76ad-141">Specifies the target runtime.</span></span> <span data-ttu-id="f76ad-142">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="f76ad-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="f76ad-143">Définit le suffixe de version pour un astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="f76ad-143">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="f76ad-144">Le format respecte les instructions de version de NuGet.</span><span class="sxs-lookup"><span data-stu-id="f76ad-144">The format follows NuGet's version guidelines.</span></span>

`--no-incremental`

<span data-ttu-id="f76ad-145">Marque la build comme unsafe pour la génération incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="f76ad-145">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="f76ad-146">Cela désactive la compilation incrémentielle et force une régénération du graphique de dépendance du projet.</span><span class="sxs-lookup"><span data-stu-id="f76ad-146">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-dependencies`

<span data-ttu-id="f76ad-147">Ignore les références entre projets (P2P) et génère uniquement le projet racine spécifié pour la génération.</span><span class="sxs-lookup"><span data-stu-id="f76ad-147">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f76ad-148">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="f76ad-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f76ad-149">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f76ad-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="f76ad-150">Exemples</span><span class="sxs-lookup"><span data-stu-id="f76ad-150">Examples</span></span>

<span data-ttu-id="f76ad-151">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="f76ad-151">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="f76ad-152">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="f76ad-152">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="f76ad-153">Générer un projet et ses dépendances pour un runtime spécifique (dans cet exemple, Ubuntu 16.04) :</span><span class="sxs-lookup"><span data-stu-id="f76ad-153">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

