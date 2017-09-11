---
title: Commande dotnet-publish - Interface CLI .NET Core
description: "La commande dotnet-publish publie votre projet .NET Core dans un répertoire."
keywords: "dotnet-publish, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a8a37b1eacab13682d4f4a2bea2f9ea248cdd9eb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-publish"></a><span data-ttu-id="095e5-104">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="095e5-104">dotnet-publish</span></span>

## <a name="name"></a><span data-ttu-id="095e5-105">Nom</span><span class="sxs-lookup"><span data-stu-id="095e5-105">Name</span></span>

<span data-ttu-id="095e5-106">`dotnet-publish` - Empaquette l’application et ses dépendances dans un dossier en vue d’un déploiement sur un système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="095e5-106">`dotnet-publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="095e5-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="095e5-107">Synopsis</span></span>

`dotnet publish [<PROJECT>] [-f|--framework] [-r|--runtime] [-o|--output] [-c|--configuration] [--version-suffix] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="095e5-108">Description</span><span class="sxs-lookup"><span data-stu-id="095e5-108">Description</span></span>

<span data-ttu-id="095e5-109">`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="095e5-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="095e5-110">La sortie contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="095e5-110">The output will contain the following:</span></span>

* <span data-ttu-id="095e5-111">Le code de langage intermédiaire (IL) dans un assembly avec l’extension `*.dll`.</span><span class="sxs-lookup"><span data-stu-id="095e5-111">Intermediate Language (IL) code in an assembly with a `*.dll` extension.</span></span>
* <span data-ttu-id="095e5-112">Le fichier *\*.deps.json* qui contient toutes les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="095e5-112">*\*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="095e5-113">Le fichier *\*.runtime.config.json* qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, le type de garbage collection).</span><span class="sxs-lookup"><span data-stu-id="095e5-113">*\*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="095e5-114">Les dépendances de l’application.</span><span class="sxs-lookup"><span data-stu-id="095e5-114">The application's dependencies.</span></span> <span data-ttu-id="095e5-115">Ces dernières sont copiées du cache NuGet vers le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="095e5-115">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="095e5-116">Le résultat de la commande `dotnet publish` est prêt pour le déploiement sur un système hôte (par exemple, un serveur, un PC, un Mac ou un ordinateur portable) et pour l’exécution ; c’est le seul moyen officiellement pris en charge de préparer l’application en vue de son déploiement.</span><span class="sxs-lookup"><span data-stu-id="095e5-116">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="095e5-117">En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="095e5-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="095e5-118">Pour plus d’informations, consultez la page [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="095e5-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="095e5-119">Pour connaître la structure des répertoires d’une application publiée, consultez la page [Structure de répertoires](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="095e5-119">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

## <a name="arguments"></a><span data-ttu-id="095e5-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="095e5-120">Arguments</span></span>

`PROJECT` 

<span data-ttu-id="095e5-121">Projet à publier. S’il n’est pas spécifié, la valeur utilisée par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="095e5-121">The project to publish, which defaults to the current directory if not specified.</span></span> 

## <a name="options"></a><span data-ttu-id="095e5-122">Options</span><span class="sxs-lookup"><span data-stu-id="095e5-122">Options</span></span>

`-h|--help`

<span data-ttu-id="095e5-123">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="095e5-123">Prints out a short help for the command.</span></span>  

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="095e5-124">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="095e5-124">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="095e5-125">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="095e5-125">You must specify the target framework in the project file.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="095e5-126">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="095e5-126">Publishes the application for a given runtime.</span></span> <span data-ttu-id="095e5-127">Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="095e5-127">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="095e5-128">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="095e5-128">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="095e5-129">Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="095e5-129">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="095e5-130">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="095e5-130">Specifies the path for the output directory.</span></span> <span data-ttu-id="095e5-131">Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]* pour un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="095e5-131">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="095e5-132">Configuration à utiliser lors de la génération du projet.</span><span class="sxs-lookup"><span data-stu-id="095e5-132">Configuration to use when building the project.</span></span> <span data-ttu-id="095e5-133">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="095e5-133">The default value is `Debug`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="095e5-134">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="095e5-134">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="095e5-135">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="095e5-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="095e5-136">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="095e5-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="095e5-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="095e5-137">Examples</span></span>

<span data-ttu-id="095e5-138">Publier le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="095e5-138">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="095e5-139">Publier l’application à l’aide du fichier projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="095e5-139">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`
    
<span data-ttu-id="095e5-140">Publier le projet dans le répertoire actif à l’aide du framework `netcoreapp1.1` :</span><span class="sxs-lookup"><span data-stu-id="095e5-140">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`
    
<span data-ttu-id="095e5-141">Publier l’application actuelle à l’aide du framework `netcoreapp1.1` et du runtime pour `OS X 10.10` (vous devez lister cet identificateur de runtime dans le fichier projet) :</span><span class="sxs-lookup"><span data-stu-id="095e5-141">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a><span data-ttu-id="095e5-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="095e5-142">See also</span></span>

* [<span data-ttu-id="095e5-143">Frameworks cibles</span><span class="sxs-lookup"><span data-stu-id="095e5-143">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="095e5-144">Catalogue d’identificateurs de runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="095e5-144">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

