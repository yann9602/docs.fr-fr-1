---
title: Commande dotnet restore - Interface CLI .NET Core
description: "Découvrez comment restaurer les dépendances et les outils spécifiques du projet avec la commande dotnet restore."
keywords: "dotnet-restore, CLI, commande CLI, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 11/30/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: dc93e0554d422ddf42ac54dd94223f0285451e85
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-restore"></a><span data-ttu-id="56a36-104">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="56a36-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="56a36-105">Name</span><span class="sxs-lookup"><span data-stu-id="56a36-105">Name</span></span>

<span data-ttu-id="56a36-106">`dotnet restore` : Restaure les dépendances et les outils d’un projet.</span><span class="sxs-lookup"><span data-stu-id="56a36-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="56a36-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="56a36-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="56a36-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="56a36-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="56a36-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="56a36-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="56a36-110">Description</span><span class="sxs-lookup"><span data-stu-id="56a36-110">Description</span></span>

<span data-ttu-id="56a36-111">La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="56a36-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="56a36-112">Par défaut, la restauration des dépendances et celle des outils sont effectuées en parallèle.</span><span class="sxs-lookup"><span data-stu-id="56a36-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="56a36-113">Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages.</span><span class="sxs-lookup"><span data-stu-id="56a36-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="56a36-114">Les flux sont généralement fournis par le fichier de configuration *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="56a36-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="56a36-115">Un fichier de configuration par défaut est fourni lors de l’installation des outils CLI.</span><span class="sxs-lookup"><span data-stu-id="56a36-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="56a36-116">Vous pouvez spécifier d’autres flux en créant votre propre fichier *NuGet.config* dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="56a36-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="56a36-117">Vous pouvez également spécifier des flux supplémentaires par appel dans une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="56a36-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="56a36-118">Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`.</span><span class="sxs-lookup"><span data-stu-id="56a36-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="56a36-119">Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation (par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows).</span><span class="sxs-lookup"><span data-stu-id="56a36-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="56a36-120">Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.</span><span class="sxs-lookup"><span data-stu-id="56a36-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="56a36-121">Le comportement de la commande `dotnet restore` est affecté par certains paramètres du fichier *Nuget.Config*, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="56a36-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="56a36-122">Par exemple, si vous définissez `globalPackagesFolder` dans *NuGet.Config*, les packages NuGet restaurés sont placés dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="56a36-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="56a36-123">Cette méthode permet également de spécifier l’option `--packages` sur la commande `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="56a36-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="56a36-124">Pour plus d’informations, consultez [Informations de référence sur NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="56a36-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="56a36-125">`dotnet restore` implicite</span><span class="sxs-lookup"><span data-stu-id="56a36-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="56a36-126">À compter de .NET Core 2.0, `dotnet restore` est au besoin exécuté implicitement quand vous exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="56a36-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="56a36-127">Dans la plupart des cas, vous n’avez plus besoin d’utiliser explicitement la commande `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="56a36-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span> 

<span data-ttu-id="56a36-128">Dans certains cas, l’exécution implicite de `dotnet restore` pose problème.</span><span class="sxs-lookup"><span data-stu-id="56a36-128">In some cases, it is inconvenient for `dotnet restore` to run implicitly.</span></span> <span data-ttu-id="56a36-129">Par exemple, certains systèmes automatisés, comme les systèmes de génération, doivent appeler explicitement `dotnet restore` pour contrôler quand la restauration a lieu afin de pouvoir contrôler l’utilisation du réseau.</span><span class="sxs-lookup"><span data-stu-id="56a36-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="56a36-130">Pour empêcher l’exécution implicite de `dotnet restore`, vous pouvez utiliser le commutateur `--no-restore` avec l’une de ces commandes afin de désactiver la restauration implicite.</span><span class="sxs-lookup"><span data-stu-id="56a36-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` switch with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="56a36-131">Arguments</span><span class="sxs-lookup"><span data-stu-id="56a36-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="56a36-132">Chemin facultatif du fichier projet à restaurer.</span><span class="sxs-lookup"><span data-stu-id="56a36-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="56a36-133">Options</span><span class="sxs-lookup"><span data-stu-id="56a36-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="56a36-134">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="56a36-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="56a36-135">Fichier de configuration NuGet (*NuGet.config*) à utiliser pour l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="56a36-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="56a36-136">Désactive la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="56a36-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="56a36-137">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="56a36-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="56a36-138">Cette opération équivaut à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="56a36-138">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="56a36-139">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="56a36-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="56a36-140">N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.</span><span class="sxs-lookup"><span data-stu-id="56a36-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="56a36-141">Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="56a36-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="56a36-142">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="56a36-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="56a36-143">Spécifie le répertoire des packages restaurés.</span><span class="sxs-lookup"><span data-stu-id="56a36-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="56a36-144">Spécifie un runtime pour la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="56a36-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="56a36-145">Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="56a36-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="56a36-146">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="56a36-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="56a36-147">Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="56a36-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="56a36-148">Spécifie la source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="56a36-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="56a36-149">Cela remplace toutes les sources spécifiées dans le(s) fichier(s) *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="56a36-149">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="56a36-150">Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="56a36-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="56a36-151">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="56a36-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="56a36-152">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="56a36-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="56a36-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="56a36-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="56a36-154">Fichier de configuration NuGet (*NuGet.config*) à utiliser pour l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="56a36-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="56a36-155">Désactive la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="56a36-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="56a36-156">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="56a36-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="56a36-157">N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.</span><span class="sxs-lookup"><span data-stu-id="56a36-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="56a36-158">Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="56a36-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="56a36-159">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="56a36-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="56a36-160">Spécifie le répertoire des packages restaurés.</span><span class="sxs-lookup"><span data-stu-id="56a36-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="56a36-161">Spécifie un runtime pour la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="56a36-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="56a36-162">Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="56a36-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="56a36-163">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="56a36-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="56a36-164">Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="56a36-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="56a36-165">Spécifie la source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="56a36-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="56a36-166">Cela remplace toutes les sources spécifiées dans le(s) fichier(s) *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="56a36-166">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="56a36-167">Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="56a36-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="56a36-168">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="56a36-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="56a36-169">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="56a36-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="56a36-170">Exemples</span><span class="sxs-lookup"><span data-stu-id="56a36-170">Examples</span></span>

<span data-ttu-id="56a36-171">Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="56a36-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="56a36-172">Restaurez des dépendances et des outils pour le projet `app1` se trouvant à l’emplacement donné :</span><span class="sxs-lookup"><span data-stu-id="56a36-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="56a36-173">Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif en utilisant le chemin d’accès de fichier fourni comme source :</span><span class="sxs-lookup"><span data-stu-id="56a36-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="56a36-174">Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif en utilisant les deux chemins d’accès de fichiers fournis comme sources :</span><span class="sxs-lookup"><span data-stu-id="56a36-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="56a36-175">Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif et afficher uniquement une sortie minimale :</span><span class="sxs-lookup"><span data-stu-id="56a36-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
