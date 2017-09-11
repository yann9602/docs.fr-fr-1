---
title: "référence sur csproj"
description: "Découvrir les différences entre les fichiers csproj existants et les fichiers csproj .NET Core"
keywords: "référence, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 05/24/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 63c7a6f0aa3a926c7ae01ad6c434ecf296c81811
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="a42dc-104">Ajouts au format csproj pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="a42dc-104">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="a42dc-105">Ce document décrit les modifications qui ont été ajoutées aux fichiers projet dans le cadre du passage de *project.json* à *csproj* et [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="a42dc-105">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="a42dc-106">Pour plus d’informations de référence ou syntaxiques générales sur les fichiers projet, consultez la documentation sur les [fichiers projet MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).</span><span class="sxs-lookup"><span data-stu-id="a42dc-106">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="a42dc-107">Références de package implicites</span><span class="sxs-lookup"><span data-stu-id="a42dc-107">Implicit package references</span></span>
<span data-ttu-id="a42dc-108">Les métapackages sont référencés implicitement en fonction du ou des frameworks cibles spécifiés dans la propriété `<TargetFramework>` ou `<TargetFrameworks>` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-108">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="a42dc-109">`<TargetFrameworks>` est ignoré si `<TargetFramework>` est spécifié, indépendamment de l’ordre.</span><span class="sxs-lookup"><span data-stu-id="a42dc-109">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="a42dc-110">Recommandations</span><span class="sxs-lookup"><span data-stu-id="a42dc-110">Recommendations</span></span>
<span data-ttu-id="a42dc-111">Comme les métapackages `Microsoft.NETCore.App` ou `NetStandard.Library` sont implicitement référencés, voici les bonnes pratiques que nous recommandons :</span><span class="sxs-lookup"><span data-stu-id="a42dc-111">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="a42dc-112">N’incluez jamais de référence explicite aux métapackages `Microsoft.NETCore.App` ou `NetStandard.Library` via l’élément `<PackageReference>` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-112">Never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="a42dc-113">Si vous avez besoin d’une version spécifique du runtime, vous devez utiliser la propriété `<RuntimeFrameworkVersion>` dans votre projet (par exemple, `1.0.4`) au lieu de référencer le métapackage.</span><span class="sxs-lookup"><span data-stu-id="a42dc-113">If you need a specific version of the runtime, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="a42dc-114">Cela peut se produire si vous utilisez des [déploiements autonomes](../deploying/index.md#self-contained-deployments-scd) et que vous devez utiliser une version de correctif spécifique du runtime 1.0.0 LTS, par exemple.</span><span class="sxs-lookup"><span data-stu-id="a42dc-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="a42dc-115">Si vous avez besoin d’une version spécifique du métapackage `NetStandard.Library`, vous pouvez utiliser la propriété `<NetStandardImplicitPackageVersion>` et définir la version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="a42dc-115">If you need a specific version of the `NetStandard.Library` metapackage, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span> 

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="a42dc-116">Inclusions de compilation par défaut dans les projets .NET Core</span><span class="sxs-lookup"><span data-stu-id="a42dc-116">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="a42dc-117">Dans le cadre du passage au format *csproj* dans les dernières versions du SDK, nous avons déplacé les inclusions et exclusions par défaut pour les éléments de compilation et les ressources incorporées dans les fichiers de propriétés du SDK.</span><span class="sxs-lookup"><span data-stu-id="a42dc-117">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="a42dc-118">Cela signifie que vous n’avez plus besoin de spécifier ces éléments dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-118">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="a42dc-119">La principale raison de cette modification est de réduire l’encombrement de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-119">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="a42dc-120">Les valeurs par défaut qui sont présentes dans le SDK doivent couvrir la plupart des cas d’utilisation courants, il est donc inutile de les répéter dans chaque projet que vous créez.</span><span class="sxs-lookup"><span data-stu-id="a42dc-120">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="a42dc-121">Il en résulte des fichiers projet moins volumineux qui sont beaucoup plus faciles à comprendre et à modifier à la main, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a42dc-121">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="a42dc-122">Le tableau suivant montre les éléments et les modèles [Glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le SDK :</span><span class="sxs-lookup"><span data-stu-id="a42dc-122">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="a42dc-123">Élément</span><span class="sxs-lookup"><span data-stu-id="a42dc-123">Element</span></span>           | <span data-ttu-id="a42dc-124">Inclure Glob</span><span class="sxs-lookup"><span data-stu-id="a42dc-124">Include glob</span></span>                              | <span data-ttu-id="a42dc-125">Exclure Glob</span><span class="sxs-lookup"><span data-stu-id="a42dc-125">Exclude glob</span></span>                                                  | <span data-ttu-id="a42dc-126">Supprimer Glob</span><span class="sxs-lookup"><span data-stu-id="a42dc-126">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="a42dc-127">Compile</span><span class="sxs-lookup"><span data-stu-id="a42dc-127">Compile</span></span>           | <span data-ttu-id="a42dc-128">\*\*/\*.cs (ou autres extensions de langage)</span><span class="sxs-lookup"><span data-stu-id="a42dc-128">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="a42dc-129">\*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a42dc-129">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="a42dc-130">N/A</span><span class="sxs-lookup"><span data-stu-id="a42dc-130">N/A</span></span>                        |
| <span data-ttu-id="a42dc-131">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="a42dc-131">EmbeddedResource</span></span>  | <span data-ttu-id="a42dc-132">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="a42dc-132">\*\*/\*.resx</span></span>                              | <span data-ttu-id="a42dc-133">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a42dc-133">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="a42dc-134">N/A</span><span class="sxs-lookup"><span data-stu-id="a42dc-134">N/A</span></span>                        |
| <span data-ttu-id="a42dc-135">Aucun</span><span class="sxs-lookup"><span data-stu-id="a42dc-135">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="a42dc-136">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a42dc-136">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="a42dc-137">- \*\*/\*.cs ; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="a42dc-137">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="a42dc-138">Si vous avez des modèles Glob dans votre projet et que vous essayez de le générer à l’aide du dernier SDK, vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="a42dc-138">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="a42dc-139">Des éléments de compilation en double ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="a42dc-139">Duplicate Compile items were included.</span></span> <span data-ttu-id="a42dc-140">Le SDK .NET inclut des éléments de compilation de votre répertoire de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="a42dc-140">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="a42dc-141">Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-141">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="a42dc-142">Pour contourner cette erreur, vous pouvez supprimer les éléments `Compile` explicites qui correspondent à ceux répertoriés dans le tableau précédent ou vous pouvez définir la propriété `<EnableDefaultCompileItems>` sur `false`, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a42dc-142">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="a42dc-143">La définition de cette propriété sur `false` remplace l’inclusion implicite et le comportement est rétabli à celui des SDK précédents dans lesquels vous deviez spécifier les modèles Glob par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-143">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="a42dc-144">Ce changement ne modifie pas le mécanisme principal des autres inclusions.</span><span class="sxs-lookup"><span data-stu-id="a42dc-144">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="a42dc-145">Toutefois, si vous voulez, par exemple, spécifier certains fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes connus dans *csproj* correspondants (par exemple, l’élément `<Content>`).</span><span class="sxs-lookup"><span data-stu-id="a42dc-145">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

### <a name="recommendation"></a><span data-ttu-id="a42dc-146">Recommandation</span><span class="sxs-lookup"><span data-stu-id="a42dc-146">Recommendation</span></span>
<span data-ttu-id="a42dc-147">Avec csproj, nous vous recommandons de supprimer les modèles Glob par défaut de votre projet et d’ajouter uniquement des chemins de fichier avec des modèles Glob pour les artefacts dont votre application/bibliothèque a besoin dans différents scénarios (par exemple, runtime et mise en package NuGet).</span><span class="sxs-lookup"><span data-stu-id="a42dc-147">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="a42dc-148">Comment afficher la totalité du projet tel qu’il est perçu par MSBuild ?</span><span class="sxs-lookup"><span data-stu-id="a42dc-148">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="a42dc-149">Même si ces modifications csproj simplifient considérablement les fichiers projet, vous pouvez souhaiter voir le projet entièrement développé tel qu’il est perçu par MSBuild une fois le kit SDK et ses cibles inclus.</span><span class="sxs-lookup"><span data-stu-id="a42dc-149">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="a42dc-150">Prétraitez le projet avec [le commutateur `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande [`dotnet msbuild`](dotnet-msbuild.md), qui affiche les fichiers qui sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet :</span><span class="sxs-lookup"><span data-stu-id="a42dc-150">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="a42dc-151">Si le projet comporte plusieurs frameworks cibles, les résultats de la commande ne doivent se concentrer que sur un seul d'entre eux en le spécifiant en tant que propriété MSBuild :</span><span class="sxs-lookup"><span data-stu-id="a42dc-151">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="a42dc-152">Ajouts</span><span class="sxs-lookup"><span data-stu-id="a42dc-152">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="a42dc-153">Attribut Sdk</span><span class="sxs-lookup"><span data-stu-id="a42dc-153">Sdk attribute</span></span> 
<span data-ttu-id="a42dc-154">L’élément `<Project>` du fichier *.csproj* a un nouvel attribut nommé `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="a42dc-154">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="a42dc-155">`Sdk` spécifie le SDK à utiliser par le projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-155">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="a42dc-156">Le SDK, comme le décrit le [document de superposition](cli-msbuild-architecture.md), est un ensemble de [tâches](/visualstudio/msbuild/msbuild-tasks) et de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild pouvant générer du code .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a42dc-156">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="a42dc-157">Nous fournissons deux principaux SDK dans les outils .NET Core :</span><span class="sxs-lookup"><span data-stu-id="a42dc-157">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="a42dc-158">Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="a42dc-158">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="a42dc-159">Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="a42dc-159">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="a42dc-160">Vous devez définir l’attribut `Sdk` sur un de ces ID pour l’élément `<Project>` afin d’utiliser les outils .NET Core et générer votre code.</span><span class="sxs-lookup"><span data-stu-id="a42dc-160">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="a42dc-161">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a42dc-161">PackageReference</span></span>
<span data-ttu-id="a42dc-162">Élément qui spécifie une dépendance NuGet dans le projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-162">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="a42dc-163">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="a42dc-163">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="a42dc-164">Version</span><span class="sxs-lookup"><span data-stu-id="a42dc-164">Version</span></span>
<span data-ttu-id="a42dc-165">`Version` spécifie la version du package à restaurer.</span><span class="sxs-lookup"><span data-stu-id="a42dc-165">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="a42dc-166">L’attribut respecte les règles du schéma de [contrôle de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="a42dc-166">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="a42dc-167">Le comportement par défaut est une correspondance exacte entre les versions.</span><span class="sxs-lookup"><span data-stu-id="a42dc-167">The default behavior is an exact version match.</span></span> <span data-ttu-id="a42dc-168">Par exemple, la spécification `Version="1.2.3"` est équivalente à la notation `[1.2.3]` de NuGet pour la version du package 1.2.3 précisément.</span><span class="sxs-lookup"><span data-stu-id="a42dc-168">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="a42dc-169">IncludeAssets, ExcludeAssets et PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="a42dc-169">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="a42dc-170">L’attribut `IncludeAssets` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="a42dc-170">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="a42dc-171">L’attribut `ExcludeAssets` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` ne doivent pas être utilisées.</span><span class="sxs-lookup"><span data-stu-id="a42dc-171">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="a42dc-172">L’attribut `PrivateAssets` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` doivent être utilisées, mais sans être reprises dans le projet suivant.</span><span class="sxs-lookup"><span data-stu-id="a42dc-172">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="a42dc-173">`PrivateAssets` est équivalent à l’élément *project.json*/*xproj* `SuppressParent`.</span><span class="sxs-lookup"><span data-stu-id="a42dc-173">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="a42dc-174">Ces attributs peuvent contenir un ou plusieurs des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a42dc-174">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="a42dc-175">`Compile` : Le contenu du dossier lib est disponible pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="a42dc-175">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="a42dc-176">`Runtime` : Le contenu du dossier runtime est distribué.</span><span class="sxs-lookup"><span data-stu-id="a42dc-176">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="a42dc-177">`ContentFiles` : Le contenu du dossier *contentfiles* est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a42dc-177">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="a42dc-178">`Build` : Les propriétés/cibles du dossier de génération sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="a42dc-178">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="a42dc-179">`Native` : Le contenu des ressources natives est copié dans le dossier de sortie de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a42dc-179">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="a42dc-180">`Analyzers` : Les analyseurs sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="a42dc-180">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="a42dc-181">Sinon, l’attribut peut contenir :</span><span class="sxs-lookup"><span data-stu-id="a42dc-181">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="a42dc-182">`None` : Aucune ressource n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a42dc-182">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="a42dc-183">`All` : Toutes les ressources sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="a42dc-183">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="a42dc-184">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="a42dc-184">DotNetCliToolReference</span></span>
<span data-ttu-id="a42dc-185">L’élément `<DotNetCliToolReference>` spécifie l’outil CLI que l’utilisateur veut restaurer dans le contexte du projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-185">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="a42dc-186">Il constitue une alternative au nœud `tools` dans *project.json*.</span><span class="sxs-lookup"><span data-stu-id="a42dc-186">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="a42dc-187">Version</span><span class="sxs-lookup"><span data-stu-id="a42dc-187">Version</span></span>
<span data-ttu-id="a42dc-188">`Version` spécifie la version du package à restaurer.</span><span class="sxs-lookup"><span data-stu-id="a42dc-188">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="a42dc-189">L’attribut respecte les règles du schéma de [contrôle de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="a42dc-189">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="a42dc-190">Le comportement par défaut est une correspondance exacte entre les versions.</span><span class="sxs-lookup"><span data-stu-id="a42dc-190">The default behavior is an exact version match.</span></span> <span data-ttu-id="a42dc-191">Par exemple, la spécification `Version="1.2.3"` est équivalente à la notation `[1.2.3]` de NuGet pour la version du package 1.2.3 précisément.</span><span class="sxs-lookup"><span data-stu-id="a42dc-191">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="a42dc-192">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="a42dc-192">RuntimeIdentifiers</span></span>
<span data-ttu-id="a42dc-193">L’élément `<RuntimeIdentifiers>` permet de spécifier une liste délimitée par des points-virgules d’[identificateurs de runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-193">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a42dc-194">Les RID permettent de publier des déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="a42dc-194">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="a42dc-195">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="a42dc-195">RuntimeIdentifier</span></span>
<span data-ttu-id="a42dc-196">L’élément `<RuntimeIdentifier>` vous permet de spécifier un seul [identificateur de runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-196">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a42dc-197">Les RID permettent de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="a42dc-197">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="a42dc-198">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a42dc-198">PackageTargetFallback</span></span> 
<span data-ttu-id="a42dc-199">L’élément `<PackageTargetFallback>` vous permet de spécifier un jeu de cibles compatibles à utiliser lors de la restauration des packages.</span><span class="sxs-lookup"><span data-stu-id="a42dc-199">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="a42dc-200">Il est conçu pour permettre aux packages qui utilisent le [moniker du framework cible](/nuget/schema/target-frameworks) dotnet de fonctionner avec les packages qui ne déclarent pas de moniker du framework cible dotnet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-200">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="a42dc-201">Si votre projet utilise le moniker du framework cible dotnet, tous les packages dont il dépend doivent également avoir un moniker du framework cible dotnet, sauf si vous ajoutez `<PackageTargetFallback>` à votre projet pour permettre aux plateformes autres que dotnet d’être compatibles avec dotnet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-201">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="a42dc-202">L’exemple suivant fournit les solutions de secours pour toutes les cibles dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="a42dc-202">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="a42dc-203">L’exemple suivant spécifie les solutions de secours uniquement pour la cible `netcoreapp1.0` :</span><span class="sxs-lookup"><span data-stu-id="a42dc-203">The following example specifies the fallbacks only for the `netcoreapp1.0` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="a42dc-204">Propriétés de métadonnées NuGet</span><span class="sxs-lookup"><span data-stu-id="a42dc-204">NuGet metadata properties</span></span>
<span data-ttu-id="a42dc-205">Avec le passage à MSbuild, nous avons transféré les métadonnées d’entrée utilisées lors de la compression d’un package NuGet des fichiers *project.json* vers les fichiers *csproj*.</span><span class="sxs-lookup"><span data-stu-id="a42dc-205">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="a42dc-206">Les entrées sont des propriétés MSBuild qui doivent donc être placées dans un groupe `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="a42dc-206">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="a42dc-207">Voici la liste des propriétés qui sont utilisées comme entrées dans le processus de compression lors de l’utilisation de la commande `dotnet pack` ou de la cible MSBuild `Pack` qui fait partie du SDK.</span><span class="sxs-lookup"><span data-stu-id="a42dc-207">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="a42dc-208">IsPackable</span><span class="sxs-lookup"><span data-stu-id="a42dc-208">IsPackable</span></span>
<span data-ttu-id="a42dc-209">Valeur booléenne qui spécifie si le projet peut être compressé.</span><span class="sxs-lookup"><span data-stu-id="a42dc-209">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="a42dc-210">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="a42dc-210">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="a42dc-211">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="a42dc-211">PackageVersion</span></span>
<span data-ttu-id="a42dc-212">Spécifie la version du package obtenu.</span><span class="sxs-lookup"><span data-stu-id="a42dc-212">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="a42dc-213">Accepte toutes les formes de la chaîne de version NuGet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-213">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="a42dc-214">La valeur par défaut est la valeur de `$(Version)`, autrement dit, de la propriété `Version` dans le projet.</span><span class="sxs-lookup"><span data-stu-id="a42dc-214">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="a42dc-215">PackageId</span><span class="sxs-lookup"><span data-stu-id="a42dc-215">PackageId</span></span>
<span data-ttu-id="a42dc-216">Spécifie le nom du package obtenu.</span><span class="sxs-lookup"><span data-stu-id="a42dc-216">Specifies the name for the resulting package.</span></span> <span data-ttu-id="a42dc-217">Si non spécifié, l’opération `pack` utilise par défaut le `AssemblyName` ou le nom du répertoire comme nom du package.</span><span class="sxs-lookup"><span data-stu-id="a42dc-217">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="a42dc-218">Titre</span><span class="sxs-lookup"><span data-stu-id="a42dc-218">Title</span></span>
<span data-ttu-id="a42dc-219">Titre convivial du package, généralement utilisé dans les affichages de l’interface utilisateur comme sur nuget.org et dans le gestionnaire de package de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a42dc-219">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="a42dc-220">Si non spécifié, l’ID de package est utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="a42dc-220">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="a42dc-221">Auteurs</span><span class="sxs-lookup"><span data-stu-id="a42dc-221">Authors</span></span>
<span data-ttu-id="a42dc-222">Liste séparée par des points-virgules des auteurs de packages, qui correspondent aux noms de profil sur nuget.org.</span><span class="sxs-lookup"><span data-stu-id="a42dc-222">A semicolon-separated list of packages authors, matching the profile names on nuget.org.</span></span> <span data-ttu-id="a42dc-223">Ceux-ci sont affichés dans la galerie NuGet sur nuget.org et servent à croiser les références des packages de mêmes auteurs.</span><span class="sxs-lookup"><span data-stu-id="a42dc-223">These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="a42dc-224">Description</span><span class="sxs-lookup"><span data-stu-id="a42dc-224">Description</span></span>
<span data-ttu-id="a42dc-225">Description longue du package pour l’affichage de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a42dc-225">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="a42dc-226">Copyright</span><span class="sxs-lookup"><span data-stu-id="a42dc-226">Copyright</span></span>
<span data-ttu-id="a42dc-227">Détails de copyright pour le package.</span><span class="sxs-lookup"><span data-stu-id="a42dc-227">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="a42dc-228">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="a42dc-228">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="a42dc-229">Valeur booléenne qui spécifie si le client doit inviter l’utilisateur à accepter la licence du package avant d’installer le package.</span><span class="sxs-lookup"><span data-stu-id="a42dc-229">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="a42dc-230">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="a42dc-230">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="a42dc-231">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="a42dc-231">PackageLicenseUrl</span></span>
<span data-ttu-id="a42dc-232">URL vers la licence applicable au package.</span><span class="sxs-lookup"><span data-stu-id="a42dc-232">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="a42dc-233">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="a42dc-233">PackageProjectUrl</span></span>
<span data-ttu-id="a42dc-234">URL de la page d’accueil du package, souvent affichée dans l’interface utilisateur ainsi que sur nuget.org.</span><span class="sxs-lookup"><span data-stu-id="a42dc-234">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="a42dc-235">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="a42dc-235">PackageIconUrl</span></span>
<span data-ttu-id="a42dc-236">URL d’une image 64 x 64 avec un arrière-plan transparent à utiliser comme icône pour le package dans l’affichage de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a42dc-236">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="a42dc-237">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="a42dc-237">PackageReleaseNotes</span></span>
<span data-ttu-id="a42dc-238">Notes de publication du package.</span><span class="sxs-lookup"><span data-stu-id="a42dc-238">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="a42dc-239">PackageTags</span><span class="sxs-lookup"><span data-stu-id="a42dc-239">PackageTags</span></span>
<span data-ttu-id="a42dc-240">Liste de balises séparées par un point-virgule qui désigne le package.</span><span class="sxs-lookup"><span data-stu-id="a42dc-240">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="a42dc-241">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="a42dc-241">PackageOutputPath</span></span>
<span data-ttu-id="a42dc-242">Détermine le chemin de sortie dans lequel le package compressé est déposé.</span><span class="sxs-lookup"><span data-stu-id="a42dc-242">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="a42dc-243">La valeur par défaut est `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="a42dc-243">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="a42dc-244">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="a42dc-244">IncludeSymbols</span></span>
<span data-ttu-id="a42dc-245">Cette valeur booléenne indique si le package doit créer un package de symboles supplémentaire quand le projet est compressé.</span><span class="sxs-lookup"><span data-stu-id="a42dc-245">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="a42dc-246">Ce package a une extension *.symbols.nupkg* et copie les fichiers PDB avec la DLL et d’autres fichiers de sortie.</span><span class="sxs-lookup"><span data-stu-id="a42dc-246">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="a42dc-247">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="a42dc-247">IncludeSource</span></span>
<span data-ttu-id="a42dc-248">Cette valeur booléenne indique si le processus de compression doit créer un package source.</span><span class="sxs-lookup"><span data-stu-id="a42dc-248">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="a42dc-249">Le package source contient le code source de la bibliothèque ainsi que les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="a42dc-249">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="a42dc-250">Les fichiers sources sont placés dans le répertoire `src/ProjectName` dans le fichier de package obtenu.</span><span class="sxs-lookup"><span data-stu-id="a42dc-250">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="a42dc-251">IsTool</span><span class="sxs-lookup"><span data-stu-id="a42dc-251">IsTool</span></span>
<span data-ttu-id="a42dc-252">Spécifie si tous les fichiers de sortie sont copiés dans le dossier *tools* au lieu du dossier *lib*.</span><span class="sxs-lookup"><span data-stu-id="a42dc-252">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="a42dc-253">Notez que cela est différent d’un `DotNetCliTool` qui est spécifié en définissant `PackageType` dans le fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="a42dc-253">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="a42dc-254">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="a42dc-254">RepositoryUrl</span></span>
<span data-ttu-id="a42dc-255">Spécifie l’URL du dépôt où réside le code source du package et/ou à partir de laquelle il est généré.</span><span class="sxs-lookup"><span data-stu-id="a42dc-255">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="a42dc-256">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="a42dc-256">RepositoryType</span></span>
<span data-ttu-id="a42dc-257">Spécifie le type de dépôt.</span><span class="sxs-lookup"><span data-stu-id="a42dc-257">Specifies the type of the repository.</span></span> <span data-ttu-id="a42dc-258">La valeur par défaut est « git ».</span><span class="sxs-lookup"><span data-stu-id="a42dc-258">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="a42dc-259">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="a42dc-259">NoPackageAnalysis</span></span>
<span data-ttu-id="a42dc-260">Spécifie que le pack ne doit pas exécuter d’analyse du package après sa génération.</span><span class="sxs-lookup"><span data-stu-id="a42dc-260">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="a42dc-261">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="a42dc-261">MinClientVersion</span></span>
<span data-ttu-id="a42dc-262">Spécifie la version minimale du client NuGet qui peut installer ce package, appliquée par nuget.exe et le gestionnaire de package Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a42dc-262">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="a42dc-263">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="a42dc-263">IncludeBuildOutput</span></span>
<span data-ttu-id="a42dc-264">Ces valeurs booléennes spécifient si les assemblys de sortie de génération doivent être compressés dans le fichier *.nupkg* ou non.</span><span class="sxs-lookup"><span data-stu-id="a42dc-264">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="a42dc-265">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="a42dc-265">IncludeContentInPack</span></span>
<span data-ttu-id="a42dc-266">Cette valeur booléenne indique si tous les éléments qui ont un type `Content` sont automatiquement inclus dans le package obtenu.</span><span class="sxs-lookup"><span data-stu-id="a42dc-266">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="a42dc-267">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="a42dc-267">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="a42dc-268">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="a42dc-268">BuildOutputTargetFolder</span></span>
<span data-ttu-id="a42dc-269">Spécifie le dossier où placer les assemblys de sortie...</span><span class="sxs-lookup"><span data-stu-id="a42dc-269">Specifies the folder where to place the output assemblies..</span></span> <span data-ttu-id="a42dc-270">Les assemblys de sortie (et les autres fichiers de sortie) sont copiés dans les dossiers de leur framework respectif.</span><span class="sxs-lookup"><span data-stu-id="a42dc-270">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="a42dc-271">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="a42dc-271">ContentTargetFolders</span></span>
<span data-ttu-id="a42dc-272">Cette propriété spécifie l’emplacement par défaut où placer tous les fichiers de contenu si `PackagePath` n’est pas spécifié pour eux.</span><span class="sxs-lookup"><span data-stu-id="a42dc-272">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="a42dc-273">La valeur par défaut est « content;contentFiles ».</span><span class="sxs-lookup"><span data-stu-id="a42dc-273">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="a42dc-274">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="a42dc-274">NuspecFile</span></span>
<span data-ttu-id="a42dc-275">Chemin relatif ou absolu du fichier *.nuspec* utilisé pour la compression.</span><span class="sxs-lookup"><span data-stu-id="a42dc-275">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="a42dc-276">Si le fichier *.nuspec* est spécifié, il est utilisé **exclusivement** pour les informations de packaging et toutes les informations non utilisées dans les projets.</span><span class="sxs-lookup"><span data-stu-id="a42dc-276">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="a42dc-277">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="a42dc-277">NuspecBasePath</span></span>
<span data-ttu-id="a42dc-278">Chemin de base pour le fichier *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="a42dc-278">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="a42dc-279">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="a42dc-279">NuspecProperties</span></span>
<span data-ttu-id="a42dc-280">Liste de paires clé=valeur séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="a42dc-280">Semicolon separated list of key=value pairs.</span></span>

