---
title: Commande dotnet-clean - Interface CLI .NET Core
description: "La commande dotnet-clean nettoie le répertoire actif."
keywords: "dotnet-clean, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 10222781d5bff596d1b7883bc73097758e878235
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-clean"></a><span data-ttu-id="61ec4-104">dotnet-clean</span><span class="sxs-lookup"><span data-stu-id="61ec4-104">dotnet-clean</span></span>

## <a name="name"></a><span data-ttu-id="61ec4-105">Nom</span><span class="sxs-lookup"><span data-stu-id="61ec4-105">Name</span></span>

<span data-ttu-id="61ec4-106">`dotnet-clean` : Nettoie la sortie d’un projet.</span><span class="sxs-lookup"><span data-stu-id="61ec4-106">`dotnet-clean` - Cleans the output of a project.</span></span> 

## <a name="synopsis"></a><span data-ttu-id="61ec4-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="61ec4-107">Synopsis</span></span>

`dotnet clean [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="61ec4-108">Description</span><span class="sxs-lookup"><span data-stu-id="61ec4-108">Description</span></span>

<span data-ttu-id="61ec4-109">La commande `dotnet clean` nettoie la sortie de la génération précédente.</span><span class="sxs-lookup"><span data-stu-id="61ec4-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="61ec4-110">Comme elle est implémentée en tant que [cible MSBuild](/visualstudio/msbuild/msbuild-targets), le projet est évalué lorsque la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="61ec4-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="61ec4-111">Seules les sorties créées lors de la génération sont nettoyées.</span><span class="sxs-lookup"><span data-stu-id="61ec4-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="61ec4-112">Les dossiers de sortie intermédiaire (*obj*) et de sortie finale (*bin*) sont tous deux nettoyés.</span><span class="sxs-lookup"><span data-stu-id="61ec4-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="61ec4-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="61ec4-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="61ec4-114">Le projet MSBuild à nettoyer.</span><span class="sxs-lookup"><span data-stu-id="61ec4-114">The MSBuild project to clean.</span></span> <span data-ttu-id="61ec4-115">Si vous ne spécifiez pas de fichier projet, MSBuild recherche dans le répertoire de travail actuel un fichier avec une extension se terminant par *proj* et l’utilise.</span><span class="sxs-lookup"><span data-stu-id="61ec4-115">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="61ec4-116">Options</span><span class="sxs-lookup"><span data-stu-id="61ec4-116">Options</span></span>

`-h|--help`

<span data-ttu-id="61ec4-117">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="61ec4-117">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="61ec4-118">Répertoire dans lequel les sorties générées sont placées.</span><span class="sxs-lookup"><span data-stu-id="61ec4-118">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="61ec4-119">Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.</span><span class="sxs-lookup"><span data-stu-id="61ec4-119">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="61ec4-120">Le [framework](../../standard/frameworks.md) spécifié au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="61ec4-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="61ec4-121">Le framework doit être défini dans le [fichier projet](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="61ec4-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="61ec4-122">Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.</span><span class="sxs-lookup"><span data-stu-id="61ec4-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="61ec4-123">Définit la configuration.</span><span class="sxs-lookup"><span data-stu-id="61ec4-123">Defines the configuration.</span></span> <span data-ttu-id="61ec4-124">Si aucune valeur n’est spécifiée, la valeur utilisée par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="61ec4-124">If omitted, it defaults to `Debug`.</span></span> <span data-ttu-id="61ec4-125">Cette propriété est uniquement requise lors du nettoyage si vous l’avez spécifiée lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="61ec4-125">This property is only required when cleaning if you specified it during build time.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="61ec4-126">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="61ec4-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="61ec4-127">Niveaux autorisés : q[uiet], m[inimal], n[ormal], d[etailed] et diag[nostic].</span><span class="sxs-lookup"><span data-stu-id="61ec4-127">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

## <a name="examples"></a><span data-ttu-id="61ec4-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="61ec4-128">Examples</span></span>

<span data-ttu-id="61ec4-129">Nettoyez une génération par défaut du projet :</span><span class="sxs-lookup"><span data-stu-id="61ec4-129">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="61ec4-130">Nettoyez un projet généré à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="61ec4-130">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`

