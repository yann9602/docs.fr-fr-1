---
title: Commande dotnet restore - Interface CLI .NET Core
description: "Découvrez comment restaurer les dépendances et les outils spécifiques du projet avec la commande dotnet restore."
keywords: "dotnet-restore, CLI, commande CLI, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: 019461964ba63d874ce86511474aa37b4342bbc4
ms.openlocfilehash: 86de979257d4e1be3a29d8876494b7f4966e5b1c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/29/2017

---
# <a name="dotnet-restore"></a><span data-ttu-id="01c9d-104">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="01c9d-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="01c9d-105">Name</span><span class="sxs-lookup"><span data-stu-id="01c9d-105">Name</span></span>

<span data-ttu-id="01c9d-106">`dotnet restore` : Restaure les dépendances et les outils d’un projet.</span><span class="sxs-lookup"><span data-stu-id="01c9d-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="01c9d-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="01c9d-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="01c9d-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="01c9d-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="01c9d-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="01c9d-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="01c9d-110">Description</span><span class="sxs-lookup"><span data-stu-id="01c9d-110">Description</span></span>

<span data-ttu-id="01c9d-111">La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="01c9d-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="01c9d-112">Par défaut, la restauration des dépendances et celle des outils sont effectuées en parallèle.</span><span class="sxs-lookup"><span data-stu-id="01c9d-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

<span data-ttu-id="01c9d-113">Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages.</span><span class="sxs-lookup"><span data-stu-id="01c9d-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="01c9d-114">Les flux sont généralement fournis par le fichier de configuration *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="01c9d-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="01c9d-115">Un fichier de configuration par défaut est fourni lors de l’installation des outils CLI.</span><span class="sxs-lookup"><span data-stu-id="01c9d-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="01c9d-116">Vous pouvez spécifier d’autres flux en créant votre propre fichier *NuGet.config* dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="01c9d-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="01c9d-117">Vous pouvez également spécifier des flux supplémentaires par appel dans une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="01c9d-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="01c9d-118">Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`.</span><span class="sxs-lookup"><span data-stu-id="01c9d-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="01c9d-119">Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation (par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows).</span><span class="sxs-lookup"><span data-stu-id="01c9d-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="01c9d-120">Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.</span><span class="sxs-lookup"><span data-stu-id="01c9d-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="01c9d-121">Le comportement de la commande `dotnet restore` est affecté par certains paramètres du fichier *Nuget.Config*, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="01c9d-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="01c9d-122">Par exemple, si vous définissez `globalPackagesFolder` dans *NuGet.Config*, les packages NuGet restaurés sont placés dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="01c9d-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="01c9d-123">Cette méthode permet également de spécifier l’option `--packages` sur la commande `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="01c9d-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="01c9d-124">Pour plus d’informations, consultez [Informations de référence sur NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="01c9d-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="arguments"></a><span data-ttu-id="01c9d-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="01c9d-125">Arguments</span></span>

`ROOT`

<span data-ttu-id="01c9d-126">Chemin facultatif du fichier projet à restaurer.</span><span class="sxs-lookup"><span data-stu-id="01c9d-126">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="01c9d-127">Options</span><span class="sxs-lookup"><span data-stu-id="01c9d-127">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="01c9d-128">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="01c9d-128">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="01c9d-129">Fichier de configuration NuGet (*NuGet.config*) à utiliser pour l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="01c9d-129">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="01c9d-130">Désactive la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="01c9d-130">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="01c9d-131">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="01c9d-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="01c9d-132">Cette opération équivaut à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="01c9d-132">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="01c9d-133">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="01c9d-133">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="01c9d-134">N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.</span><span class="sxs-lookup"><span data-stu-id="01c9d-134">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="01c9d-135">Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="01c9d-135">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="01c9d-136">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="01c9d-136">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="01c9d-137">Spécifie le répertoire des packages restaurés.</span><span class="sxs-lookup"><span data-stu-id="01c9d-137">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="01c9d-138">Spécifie un runtime pour la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="01c9d-138">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="01c9d-139">Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="01c9d-139">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="01c9d-140">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="01c9d-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="01c9d-141">Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="01c9d-141">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="01c9d-142">Spécifie la source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="01c9d-142">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="01c9d-143">Cela remplace toutes les sources spécifiées dans le(s) fichier(s) *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="01c9d-143">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="01c9d-144">Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="01c9d-144">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="01c9d-145">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="01c9d-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="01c9d-146">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="01c9d-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="01c9d-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="01c9d-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="01c9d-148">Fichier de configuration NuGet (*NuGet.config*) à utiliser pour l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="01c9d-148">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="01c9d-149">Désactive la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="01c9d-149">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="01c9d-150">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="01c9d-150">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="01c9d-151">N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.</span><span class="sxs-lookup"><span data-stu-id="01c9d-151">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="01c9d-152">Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="01c9d-152">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="01c9d-153">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="01c9d-153">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="01c9d-154">Spécifie le répertoire des packages restaurés.</span><span class="sxs-lookup"><span data-stu-id="01c9d-154">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="01c9d-155">Spécifie un runtime pour la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="01c9d-155">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="01c9d-156">Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="01c9d-156">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="01c9d-157">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="01c9d-157">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="01c9d-158">Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="01c9d-158">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="01c9d-159">Spécifie la source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="01c9d-159">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="01c9d-160">Cela remplace toutes les sources spécifiées dans le(s) fichier(s) *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="01c9d-160">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="01c9d-161">Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="01c9d-161">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="01c9d-162">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="01c9d-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="01c9d-163">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="01c9d-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="01c9d-164">Exemples</span><span class="sxs-lookup"><span data-stu-id="01c9d-164">Examples</span></span>

<span data-ttu-id="01c9d-165">Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="01c9d-165">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="01c9d-166">Restaurez des dépendances et des outils pour le projet `app1` se trouvant à l’emplacement donné :</span><span class="sxs-lookup"><span data-stu-id="01c9d-166">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="01c9d-167">Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif en utilisant le chemin d’accès de fichier fourni comme source :</span><span class="sxs-lookup"><span data-stu-id="01c9d-167">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="01c9d-168">Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif en utilisant les deux chemins d’accès de fichiers fournis comme sources :</span><span class="sxs-lookup"><span data-stu-id="01c9d-168">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="01c9d-169">Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif et afficher uniquement une sortie minimale :</span><span class="sxs-lookup"><span data-stu-id="01c9d-169">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`

