---
title: Commande dotnet migrate - Interface CLI .NET Core
description: "La commande dotnet migrate permet de migrer un projet et l’ensemble de ses dépendances."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 7fad6bf67dfe7b0d6f70ce527a153080aa17d888
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-migrate"></a><span data-ttu-id="862b9-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="862b9-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="862b9-104">Name</span><span class="sxs-lookup"><span data-stu-id="862b9-104">Name</span></span>

<span data-ttu-id="862b9-105">`dotnet migrate` : migre un projet .NET Core Preview 2 vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="862b9-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="862b9-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="862b9-106">Synopsis</span></span>

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a><span data-ttu-id="862b9-107">Description</span><span class="sxs-lookup"><span data-stu-id="862b9-107">Description</span></span>

<span data-ttu-id="862b9-108">La commande `dotnet migrate` migre un projet *project.json* Preview 2 valide vers un projet *csproj* SDK .NET Core 1.0 valide.</span><span class="sxs-lookup"><span data-stu-id="862b9-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span> 

<span data-ttu-id="862b9-109">Par défaut, la commande migre le projet racine et toutes les références de projet qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="862b9-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="862b9-110">Ce comportement peut être désactivé à l’aide de l’option `--skip-project-references` au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="862b9-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span> 

<span data-ttu-id="862b9-111">La migration est effectuée sur les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="862b9-111">Migration is performed on the following:</span></span>

* <span data-ttu-id="862b9-112">Un projet unique en spécifiant le fichier *project.json* à migrer.</span><span class="sxs-lookup"><span data-stu-id="862b9-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="862b9-113">Tous les répertoires spécifiés dans le fichier *global.json* en passant un chemin du fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="862b9-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="862b9-114">Un fichier *solution.sln*, où il migre les projets référencés dans la solution.</span><span class="sxs-lookup"><span data-stu-id="862b9-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="862b9-115">Sur tous les sous-répertoires du répertoire donné de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="862b9-115">On all sub-directories of the given directory recursively.</span></span>

<span data-ttu-id="862b9-116">La commande `dotnet migrate` conserve le fichier *project.json* migré dans un répertoire `backup`, qu’elle crée s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="862b9-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="862b9-117">Ce comportement est remplacé à l’aide de l’option `--skip-backup`.</span><span class="sxs-lookup"><span data-stu-id="862b9-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="862b9-118">Par défaut, l’opération de migration affiche l’état du processus de migration dans la sortie standard (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="862b9-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="862b9-119">Si vous utilisez l’option `--report-file <REPORT_FILE>`, la sortie est enregistrée dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="862b9-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span> 

<span data-ttu-id="862b9-120">La commande `dotnet migrate` prend en charge uniquement les projets *project.json* Preview 2 valides.</span><span class="sxs-lookup"><span data-stu-id="862b9-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="862b9-121">Cela signifie que vous ne pouvez pas l’utiliser pour migrer des projets *project.json* DNX ou Preview 1 directement vers des projets MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="862b9-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="862b9-122">Vous devez tout d’abord migrer manuellement le projet vers un projet *project.json* Preview 2, puis utiliser la commande `dotnet migrate` pour migrer le projet.</span><span class="sxs-lookup"><span data-stu-id="862b9-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="862b9-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="862b9-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="862b9-124">Le chemin d’accès à l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="862b9-124">The path to one of the following:</span></span>

* <span data-ttu-id="862b9-125">Un fichier *project.json* à migrer.</span><span class="sxs-lookup"><span data-stu-id="862b9-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="862b9-126">Un fichier *global.json*, il migre les dossiers spécifiés vers *global.json*.</span><span class="sxs-lookup"><span data-stu-id="862b9-126">a *global.json* file, it will migrate the folders specified in *global.json*.</span></span>
* <span data-ttu-id="862b9-127">Un fichier *solution.sln*, il migre les projets référencés dans la solution.</span><span class="sxs-lookup"><span data-stu-id="862b9-127">a *solution.sln* file, it will migrate the projects referenced in the solution.</span></span>
* <span data-ttu-id="862b9-128">Un répertoire à migrer, il recherche de manière récursive les fichiers *project.json* à migrer.</span><span class="sxs-lookup"><span data-stu-id="862b9-128">a directory to migrate, it will recursively search for *project.json* files to migrate.</span></span>

<span data-ttu-id="862b9-129">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="862b9-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="862b9-130">Options</span><span class="sxs-lookup"><span data-stu-id="862b9-130">Options</span></span>

`-h|--help`

<span data-ttu-id="862b9-131">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="862b9-131">Prints out a short help for the command.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="862b9-132">Fichier csproj de modèle à utiliser pour la migration.</span><span class="sxs-lookup"><span data-stu-id="862b9-132">Template csproj file to use for migration.</span></span> <span data-ttu-id="862b9-133">Par défaut, le même modèle que celui déposé par `dotnet new console` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="862b9-133">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="862b9-134">Version du package de SDK à référencer dans l’application migrée.</span><span class="sxs-lookup"><span data-stu-id="862b9-134">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="862b9-135">La valeur par défaut est la version du SDK dans `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="862b9-135">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="862b9-136">Chemin du fichier xproj à utiliser.</span><span class="sxs-lookup"><span data-stu-id="862b9-136">The path to the xproj file to use.</span></span> <span data-ttu-id="862b9-137">Requis quand il existe plusieurs xproj dans un répertoire de projet.</span><span class="sxs-lookup"><span data-stu-id="862b9-137">Required when there is more than one xproj in a project directory.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="862b9-138">Ignore la migration des références de projet.</span><span class="sxs-lookup"><span data-stu-id="862b9-138">Skip migrating project references.</span></span> <span data-ttu-id="862b9-139">Par défaut, les références de projet sont migrées de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="862b9-139">By default, project references are migrated recursively.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="862b9-140">Génère un rapport de migration dans un fichier, en plus de le faire dans la console.</span><span class="sxs-lookup"><span data-stu-id="862b9-140">Output migration report to a file in addition to the console.</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="862b9-141">Génère le fichier de rapport de migration au format JSON plutôt que sous la forme de messages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="862b9-141">Output migration report file as JSON rather than user messages.</span></span>

`--skip-backup`

<span data-ttu-id="862b9-142">Ignore le déplacement de *project.json*, *global.json* et *\\*.xproj* vers un répertoire `backup` après la migration.</span><span class="sxs-lookup"><span data-stu-id="862b9-142">Skip moving *project.json*, *global.json*, and *\\*.xproj* to a `backup` directory after successful migration.</span></span>

## <a name="examples"></a><span data-ttu-id="862b9-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="862b9-143">Examples</span></span>

<span data-ttu-id="862b9-144">Migrer un projet et toutes ses dépendances de projet à projet vers le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="862b9-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="862b9-145">Migrer tous les projets que le fichier *global.json* contient :</span><span class="sxs-lookup"><span data-stu-id="862b9-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="862b9-146">Migrer uniquement le projet actuel et aucune dépendance de projet à projet (P2P).</span><span class="sxs-lookup"><span data-stu-id="862b9-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="862b9-147">En outre, utilisez une version de Kit de développement logiciel (SDK) spécifique :</span><span class="sxs-lookup"><span data-stu-id="862b9-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
