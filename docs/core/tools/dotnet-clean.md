---
title: Commande dotnet clean - Interface CLI .NET Core
description: "La commande dotnet clean nettoie le répertoire actif."
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: f56ccc485884114262cd1364cf9398e302f2c48a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-clean"></a><span data-ttu-id="87c2a-103">dotnet-clean</span><span class="sxs-lookup"><span data-stu-id="87c2a-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="87c2a-104">Name</span><span class="sxs-lookup"><span data-stu-id="87c2a-104">Name</span></span>

<span data-ttu-id="87c2a-105">`dotnet clean` : Nettoie la sortie d’un projet.</span><span class="sxs-lookup"><span data-stu-id="87c2a-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="87c2a-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="87c2a-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="87c2a-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="87c2a-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="87c2a-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="87c2a-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="87c2a-109">Description</span><span class="sxs-lookup"><span data-stu-id="87c2a-109">Description</span></span>

<span data-ttu-id="87c2a-110">La commande `dotnet clean` nettoie la sortie de la génération précédente.</span><span class="sxs-lookup"><span data-stu-id="87c2a-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="87c2a-111">Comme elle est implémentée en tant que [cible MSBuild](/visualstudio/msbuild/msbuild-targets), le projet est évalué lorsque la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="87c2a-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="87c2a-112">Seules les sorties créées lors de la génération sont nettoyées.</span><span class="sxs-lookup"><span data-stu-id="87c2a-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="87c2a-113">Les dossiers de sortie intermédiaire (*obj*) et de sortie finale (*bin*) sont tous deux nettoyés.</span><span class="sxs-lookup"><span data-stu-id="87c2a-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="87c2a-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="87c2a-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="87c2a-115">Le projet MSBuild à nettoyer.</span><span class="sxs-lookup"><span data-stu-id="87c2a-115">The MSBuild project to clean.</span></span> <span data-ttu-id="87c2a-116">Si vous ne spécifiez pas de fichier projet, MSBuild recherche dans le répertoire de travail actuel un fichier avec une extension se terminant par *proj* et l’utilise.</span><span class="sxs-lookup"><span data-stu-id="87c2a-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="87c2a-117">Options</span><span class="sxs-lookup"><span data-stu-id="87c2a-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="87c2a-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="87c2a-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="87c2a-119">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="87c2a-119">Defines the build configuration.</span></span> <span data-ttu-id="87c2a-120">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="87c2a-120">The default value is `Debug`.</span></span> <span data-ttu-id="87c2a-121">Cette option est uniquement requise durant le nettoyage si vous l’avez spécifiée au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="87c2a-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="87c2a-122">Le [framework](../../standard/frameworks.md) spécifié au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="87c2a-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="87c2a-123">Le framework doit être défini dans le [fichier projet](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="87c2a-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="87c2a-124">Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.</span><span class="sxs-lookup"><span data-stu-id="87c2a-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="87c2a-125">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="87c2a-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="87c2a-126">Répertoire dans lequel les sorties générées sont placées.</span><span class="sxs-lookup"><span data-stu-id="87c2a-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="87c2a-127">Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.</span><span class="sxs-lookup"><span data-stu-id="87c2a-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="87c2a-128">Nettoie le dossier de sortie du runtime spécifié.</span><span class="sxs-lookup"><span data-stu-id="87c2a-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="87c2a-129">Cette option est utilisée à la création d’un [déploiement autonome](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="87c2a-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="87c2a-130">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="87c2a-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="87c2a-131">Niveaux autorisés : q[uiet], m[inimal], n[ormal], d[etailed] et diag[nostic].</span><span class="sxs-lookup"><span data-stu-id="87c2a-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="87c2a-132">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="87c2a-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="87c2a-133">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="87c2a-133">Defines the build configuration.</span></span> <span data-ttu-id="87c2a-134">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="87c2a-134">The default value is `Debug`.</span></span> <span data-ttu-id="87c2a-135">Cette option est uniquement requise durant le nettoyage si vous l’avez spécifiée au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="87c2a-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="87c2a-136">Le [framework](../../standard/frameworks.md) spécifié au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="87c2a-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="87c2a-137">Le framework doit être défini dans le [fichier projet](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="87c2a-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="87c2a-138">Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.</span><span class="sxs-lookup"><span data-stu-id="87c2a-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="87c2a-139">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="87c2a-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="87c2a-140">Répertoire dans lequel les sorties générées sont placées.</span><span class="sxs-lookup"><span data-stu-id="87c2a-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="87c2a-141">Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.</span><span class="sxs-lookup"><span data-stu-id="87c2a-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="87c2a-142">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="87c2a-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="87c2a-143">Niveaux autorisés : q[uiet], m[inimal], n[ormal], d[etailed] et diag[nostic].</span><span class="sxs-lookup"><span data-stu-id="87c2a-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="87c2a-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="87c2a-144">Examples</span></span>

<span data-ttu-id="87c2a-145">Nettoyez une génération par défaut du projet :</span><span class="sxs-lookup"><span data-stu-id="87c2a-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="87c2a-146">Nettoyez un projet généré à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="87c2a-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
