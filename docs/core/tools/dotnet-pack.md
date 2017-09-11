---
title: Commande dotnet-pack - Interface CLI .NET Core
description: "La commande dotnet-pack crée des packages NuGet pour votre projet .NET Core."
keywords: "dotnet-pack, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 04b967fdf6578098caae8c21604c5d6160eb6775
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-pack"></a><span data-ttu-id="bd15c-104">dotnet-pack</span><span class="sxs-lookup"><span data-stu-id="bd15c-104">dotnet-pack</span></span>

## <a name="name"></a><span data-ttu-id="bd15c-105">Nom</span><span class="sxs-lookup"><span data-stu-id="bd15c-105">Name</span></span>

<span data-ttu-id="bd15c-106">`dotnet-pack` : Place le code dans un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="bd15c-106">`dotnet-pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bd15c-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="bd15c-107">Synopsis</span></span>

`dotnet pack [<PROJECT>] [-o|--output] [--no-build] [--include-symbols] [--include-source] [-c|--configuration] [--version-suffix <VERSION_SUFFIX>] [-s|--serviceable] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="bd15c-108">Description</span><span class="sxs-lookup"><span data-stu-id="bd15c-108">Description</span></span>

<span data-ttu-id="bd15c-109">La commande `dotnet pack` génère le projet et crée les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="bd15c-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="bd15c-110">Le résultat de cette commande est un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="bd15c-110">The result of this command is a NuGet package.</span></span> <span data-ttu-id="bd15c-111">Si l’option `--include-symbols` est présente, un autre package contenant les symboles de débogage est créé.</span><span class="sxs-lookup"><span data-stu-id="bd15c-111">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span> 

<span data-ttu-id="bd15c-112">Les dépendances NuGet du projet empaqueté sont ajoutées dans le fichier *.nuspec*, pour pouvoir être correctement résolues lors de l’installation du package.</span><span class="sxs-lookup"><span data-stu-id="bd15c-112">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="bd15c-113">Les références entre projets ne sont pas empaquetées à l’intérieur du projet.</span><span class="sxs-lookup"><span data-stu-id="bd15c-113">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="bd15c-114">Actuellement, vous devez disposer d’un package par projet si vous avez des dépendances entre projets.</span><span class="sxs-lookup"><span data-stu-id="bd15c-114">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="bd15c-115">Par défaut, `dotnet pack` génère d’abord le projet.</span><span class="sxs-lookup"><span data-stu-id="bd15c-115">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="bd15c-116">Pour éviter ce comportement, passez l’option `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="bd15c-116">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="bd15c-117">Elle est souvent utile dans les scénarios de build d’intégration continue, pour lesquels vous savez que le code a déjà été créé.</span><span class="sxs-lookup"><span data-stu-id="bd15c-117">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="bd15c-118">Vous pouvez fournir des propriétés MSBuild à la commande `dotnet pack` pour le processus de compression.</span><span class="sxs-lookup"><span data-stu-id="bd15c-118">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="bd15c-119">Pour plus d’informations, consultez [Propriétés des métadonnées NuGet](csproj.md#nuget-metadata-properties) et [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="bd15c-119">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="arguments"></a><span data-ttu-id="bd15c-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="bd15c-120">Arguments</span></span>

`PROJECT` 
    
<span data-ttu-id="bd15c-121">Projet à empaqueter.</span><span class="sxs-lookup"><span data-stu-id="bd15c-121">The project to pack.</span></span> <span data-ttu-id="bd15c-122">Il s’agit du chemin d’accès d’un [fichier csproj](csproj.md) ou d’un répertoire.</span><span class="sxs-lookup"><span data-stu-id="bd15c-122">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="bd15c-123">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="bd15c-123">If omitted, it defaults to the current directory.</span></span> 

## <a name="options"></a><span data-ttu-id="bd15c-124">Options</span><span class="sxs-lookup"><span data-stu-id="bd15c-124">Options</span></span>

`-h|--help`

<span data-ttu-id="bd15c-125">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="bd15c-125">Prints out a short help for the command.</span></span>  

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="bd15c-126">Place les packages générés dans le répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="bd15c-126">Places the built packages in the directory specified.</span></span> 

`--no-build`

<span data-ttu-id="bd15c-127">Ne génère pas le projet avant de créer le package.</span><span class="sxs-lookup"><span data-stu-id="bd15c-127">Don't build the project before packing.</span></span> 

`--include-symbols`

<span data-ttu-id="bd15c-128">Génère les symboles `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="bd15c-128">Generates the symbols `nupkg`.</span></span> 

`--include-source`

<span data-ttu-id="bd15c-129">Inclut les fichiers sources dans le package NuGet.</span><span class="sxs-lookup"><span data-stu-id="bd15c-129">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="bd15c-130">Les fichiers sources sont inclus dans le dossier `src` de `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="bd15c-130">The sources files are included in the `src` folder within the `nupkg`.</span></span> 

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="bd15c-131">Configuration à utiliser lors de la génération du projet.</span><span class="sxs-lookup"><span data-stu-id="bd15c-131">Configuration to use when building the project.</span></span> <span data-ttu-id="bd15c-132">Si elle n’est pas spécifiée, la configuration par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="bd15c-132">If not specified, configuration defaults to `Debug`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="bd15c-133">Définit la valeur de la propriété MSBuild `$(VersionSuffix)` dans le projet.</span><span class="sxs-lookup"><span data-stu-id="bd15c-133">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-s|--serviceable`

<span data-ttu-id="bd15c-134">Définit l’indicateur d’un état pouvant faire l’objet d’une maintenance dans le package.</span><span class="sxs-lookup"><span data-stu-id="bd15c-134">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="bd15c-135">Pour plus d’informations, consultez [Blog .NET : .NET 4.5.1 prend en charge les mises à jour de sécurité de Microsoft pour les bibliothèques NuGet .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="bd15c-135">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="bd15c-136">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="bd15c-136">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bd15c-137">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bd15c-137">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="bd15c-138">Exemples</span><span class="sxs-lookup"><span data-stu-id="bd15c-138">Examples</span></span>

<span data-ttu-id="bd15c-139">Empaquetez le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="bd15c-139">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="bd15c-140">Empaqueter le projet `app1` :</span><span class="sxs-lookup"><span data-stu-id="bd15c-140">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="bd15c-141">Empaqueter le projet dans le répertoire actif et placer les packages résultants dans le dossier `nupkgs` :</span><span class="sxs-lookup"><span data-stu-id="bd15c-141">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="bd15c-142">Empaqueter le projet dans le répertoire actif du dossier `nupkgs` et ignorer l’étape de génération :</span><span class="sxs-lookup"><span data-stu-id="bd15c-142">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="bd15c-143">Avec le suffixe de version du projet configuré comme `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` dans le fichier *.csproj*, empaqueter le projet actif et mettre à jour la version du package obtenue avec le suffixe donné :</span><span class="sxs-lookup"><span data-stu-id="bd15c-143">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="bd15c-144">Affectez `2.1.0` à la version du package à l’aide de la propriété MSBuild `PackageVersion` :</span><span class="sxs-lookup"><span data-stu-id="bd15c-144">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

