---
title: Commande dotnet publish - Interface CLI .NET Core
description: "La commande dotnet publish publie votre projet .NET Core dans un répertoire."
author: mairaw
ms.author: mairaw
ms.date: 09/01/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: e29d5269ab5e9e2c9fd08811552c09ec1c95363d
ms.sourcegitcommit: 3fd4e718d1bac9769fe0c1dd08ca1b2323ae272b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="dotnet-publish"></a><span data-ttu-id="a83a2-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a83a2-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a83a2-104">Name</span><span class="sxs-lookup"><span data-stu-id="a83a2-104">Name</span></span>

<span data-ttu-id="a83a2-105">`dotnet publish` - Empaquette l’application et ses dépendances dans un dossier en vue d’un déploiement sur un système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="a83a2-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a83a2-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="a83a2-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a83a2-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a83a2-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a83a2-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a83a2-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="a83a2-109">Description</span><span class="sxs-lookup"><span data-stu-id="a83a2-109">Description</span></span>

<span data-ttu-id="a83a2-110">`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="a83a2-110">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="a83a2-111">La sortie contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a83a2-111">The output will contain the following:</span></span>

* <span data-ttu-id="a83a2-112">Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.</span><span class="sxs-lookup"><span data-stu-id="a83a2-112">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="a83a2-113">Le fichier *.deps.json* qui contient toutes les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="a83a2-113">*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="a83a2-114">Le fichier *.runtime.config.json* qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, le type de garbage collection).</span><span class="sxs-lookup"><span data-stu-id="a83a2-114">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="a83a2-115">Les dépendances de l’application.</span><span class="sxs-lookup"><span data-stu-id="a83a2-115">The application's dependencies.</span></span> <span data-ttu-id="a83a2-116">Ces dernières sont copiées du cache NuGet vers le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="a83a2-116">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="a83a2-117">Le résultat de la commande `dotnet publish` est prêt pour le déploiement sur un système hôte (par exemple, un serveur, un PC, un Mac ou un ordinateur portable) et pour l’exécution ; c’est le seul moyen officiellement pris en charge de préparer l’application en vue de son déploiement.</span><span class="sxs-lookup"><span data-stu-id="a83a2-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="a83a2-118">En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="a83a2-118">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="a83a2-119">Pour plus d’informations, consultez la page [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="a83a2-119">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="a83a2-120">Pour connaître la structure des répertoires d’une application publiée, consultez la page [Structure de répertoires](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="a83a2-120">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

## <a name="arguments"></a><span data-ttu-id="a83a2-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="a83a2-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a83a2-122">Projet à publier. S’il n’est pas spécifié, la valeur utilisée par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="a83a2-122">The project to publish, which defaults to the current directory if not specified.</span></span>

## <a name="options"></a><span data-ttu-id="a83a2-123">Options</span><span class="sxs-lookup"><span data-stu-id="a83a2-123">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a83a2-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a83a2-124">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a83a2-125">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="a83a2-125">Defines the build configuration.</span></span> <span data-ttu-id="a83a2-126">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="a83a2-126">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a83a2-127">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="a83a2-127">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a83a2-128">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a83a2-128">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="a83a2-129">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="a83a2-129">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a83a2-130">Cette opération équivaut à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="a83a2-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="a83a2-131">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="a83a2-131">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="a83a2-132">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="a83a2-132">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="a83a2-133">Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="a83a2-133">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="a83a2-134">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="a83a2-134">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="a83a2-135">Cette option est disponible à partir du SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="a83a2-135">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="a83a2-136">Ignore les références entre projets et restaure uniquement le projet racine.</span><span class="sxs-lookup"><span data-stu-id="a83a2-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="a83a2-137">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="a83a2-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a83a2-138">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="a83a2-138">Specifies the path for the output directory.</span></span> <span data-ttu-id="a83a2-139">Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]* pour un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="a83a2-139">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="a83a2-140">Si un chemin d’accès relatif est fourni, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="a83a2-140">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="a83a2-141">Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="a83a2-141">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="a83a2-142">Si un identificateur de runtime est spécifié, sa valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="a83a2-142">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="a83a2-143">Pour plus d’informations sur les différents types de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="a83a2-143">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a83a2-144">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="a83a2-144">Publishes the application for a given runtime.</span></span> <span data-ttu-id="a83a2-145">Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="a83a2-145">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="a83a2-146">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a83a2-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="a83a2-147">Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="a83a2-147">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a83a2-148">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="a83a2-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a83a2-149">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a83a2-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a83a2-150">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a83a2-150">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a83a2-151">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a83a2-151">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a83a2-152">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="a83a2-152">Defines the build configuration.</span></span> <span data-ttu-id="a83a2-153">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="a83a2-153">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a83a2-154">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="a83a2-154">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a83a2-155">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a83a2-155">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="a83a2-156">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="a83a2-156">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="a83a2-157">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="a83a2-157">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="a83a2-158">Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="a83a2-158">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="a83a2-159">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="a83a2-159">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="a83a2-160">Cette option est disponible à partir du SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="a83a2-160">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a83a2-161">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="a83a2-161">Specifies the path for the output directory.</span></span> <span data-ttu-id="a83a2-162">Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]* pour un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="a83a2-162">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="a83a2-163">Si un chemin d’accès relatif est fourni, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="a83a2-163">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a83a2-164">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="a83a2-164">Publishes the application for a given runtime.</span></span> <span data-ttu-id="a83a2-165">Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="a83a2-165">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="a83a2-166">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a83a2-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="a83a2-167">Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="a83a2-167">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a83a2-168">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="a83a2-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a83a2-169">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a83a2-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a83a2-170">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a83a2-170">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a83a2-171">Exemples</span><span class="sxs-lookup"><span data-stu-id="a83a2-171">Examples</span></span>

<span data-ttu-id="a83a2-172">Publier le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="a83a2-172">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="a83a2-173">Publier l’application à l’aide du fichier projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="a83a2-173">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`
    
<span data-ttu-id="a83a2-174">Publier le projet dans le répertoire actif à l’aide du framework `netcoreapp1.1` :</span><span class="sxs-lookup"><span data-stu-id="a83a2-174">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`
    
<span data-ttu-id="a83a2-175">Publier l’application actuelle à l’aide du framework `netcoreapp1.1` et du runtime pour `OS X 10.10` (vous devez lister cet identificateur de runtime dans le fichier projet) :</span><span class="sxs-lookup"><span data-stu-id="a83a2-175">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a><span data-ttu-id="a83a2-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a83a2-176">See also</span></span>

* [<span data-ttu-id="a83a2-177">Frameworks cibles</span><span class="sxs-lookup"><span data-stu-id="a83a2-177">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="a83a2-178">Catalogue d’identificateurs de runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="a83a2-178">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
