---
title: Commande dotnet-new - Interface CLI .NET Core
description: "La commande dotnet-new crée de nouveaux projets .NET Core dans le répertoire actif."
keywords: "dotnet-new, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 56033295b2448b045d5a51dbd84d5429aed77451
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-new"></a><span data-ttu-id="5931b-104">dotnet-new</span><span class="sxs-lookup"><span data-stu-id="5931b-104">dotnet-new</span></span>

## <a name="name"></a><span data-ttu-id="5931b-105">Nom</span><span class="sxs-lookup"><span data-stu-id="5931b-105">Name</span></span>

<span data-ttu-id="5931b-106">`dotnet-new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="5931b-106">`dotnet-new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5931b-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="5931b-107">Synopsis</span></span>

```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5931b-108">Description</span><span class="sxs-lookup"><span data-stu-id="5931b-108">Description</span></span>

<span data-ttu-id="5931b-109">La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide.</span><span class="sxs-lookup"><span data-stu-id="5931b-109">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="5931b-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="5931b-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="5931b-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="5931b-111">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="5931b-112">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="5931b-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="5931b-113">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="5931b-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="5931b-114">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="5931b-114">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="5931b-115">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="5931b-115">The command contains a default list of templates.</span></span> <span data-ttu-id="5931b-116">Utilisez `dotnet new -all` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="5931b-116">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="5931b-117">Le tableau suivant présente les modèles préinstallés avec le SDK.</span><span class="sxs-lookup"><span data-stu-id="5931b-117">The following table shows the templates that come pre-installed with the SDK.</span></span> <span data-ttu-id="5931b-118">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="5931b-118">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="5931b-119">Description du modèle</span><span class="sxs-lookup"><span data-stu-id="5931b-119">Template description</span></span>  | <span data-ttu-id="5931b-120">Nom du modèle</span><span class="sxs-lookup"><span data-stu-id="5931b-120">Template name</span></span>  | <span data-ttu-id="5931b-121">Langages</span><span class="sxs-lookup"><span data-stu-id="5931b-121">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="5931b-122">Application console</span><span class="sxs-lookup"><span data-stu-id="5931b-122">Console application</span></span>  | <span data-ttu-id="5931b-123">console</span><span class="sxs-lookup"><span data-stu-id="5931b-123">console</span></span>        | <span data-ttu-id="5931b-124">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5931b-124">[C#], F#</span></span>  |
| <span data-ttu-id="5931b-125">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="5931b-125">Class library</span></span>        | <span data-ttu-id="5931b-126">classlib</span><span class="sxs-lookup"><span data-stu-id="5931b-126">classlib</span></span>       | <span data-ttu-id="5931b-127">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5931b-127">[C#], F#</span></span>  |
| <span data-ttu-id="5931b-128">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="5931b-128">Unit test project</span></span>    | <span data-ttu-id="5931b-129">mstest</span><span class="sxs-lookup"><span data-stu-id="5931b-129">mstest</span></span>         | <span data-ttu-id="5931b-130">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5931b-130">[C#], F#</span></span>  |
| <span data-ttu-id="5931b-131">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="5931b-131">xUnit test project</span></span>   | <span data-ttu-id="5931b-132">xunit</span><span class="sxs-lookup"><span data-stu-id="5931b-132">xunit</span></span>          | <span data-ttu-id="5931b-133">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5931b-133">[C#], F#</span></span>  |
| <span data-ttu-id="5931b-134">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="5931b-134">ASP.NET Core empty</span></span>   | <span data-ttu-id="5931b-135">web</span><span class="sxs-lookup"><span data-stu-id="5931b-135">web</span></span>            | <span data-ttu-id="5931b-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="5931b-136">[C#]</span></span>      |
| <span data-ttu-id="5931b-137">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5931b-137">ASP.NET Core web app</span></span> | <span data-ttu-id="5931b-138">mvc</span><span class="sxs-lookup"><span data-stu-id="5931b-138">mvc</span></span>            | <span data-ttu-id="5931b-139">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5931b-139">[C#], F#</span></span>  |
| <span data-ttu-id="5931b-140">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5931b-140">ASP.NET Core web api</span></span> | <span data-ttu-id="5931b-141">webapi</span><span class="sxs-lookup"><span data-stu-id="5931b-141">webapi</span></span>         | <span data-ttu-id="5931b-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="5931b-142">[C#]</span></span>      |
| <span data-ttu-id="5931b-143">Config NuGet</span><span class="sxs-lookup"><span data-stu-id="5931b-143">Nuget config</span></span>         | <span data-ttu-id="5931b-144">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="5931b-144">nugetconfig</span></span>    |           |
| <span data-ttu-id="5931b-145">config web</span><span class="sxs-lookup"><span data-stu-id="5931b-145">Web config</span></span>           | <span data-ttu-id="5931b-146">webconfig</span><span class="sxs-lookup"><span data-stu-id="5931b-146">webconfig</span></span>      |           |
| <span data-ttu-id="5931b-147">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="5931b-147">Solution file</span></span>        | <span data-ttu-id="5931b-148">sln</span><span class="sxs-lookup"><span data-stu-id="5931b-148">sln</span></span>            |           |

## <a name="options"></a><span data-ttu-id="5931b-149">Options</span><span class="sxs-lookup"><span data-stu-id="5931b-149">Options</span></span>

`-h|--help`

<span data-ttu-id="5931b-150">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5931b-150">Prints out help for the command.</span></span> <span data-ttu-id="5931b-151">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="5931b-151">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="5931b-152">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="5931b-152">Lists templates containing the specified name.</span></span> <span data-ttu-id="5931b-153">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="5931b-153">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5931b-154">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="5931b-154">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="5931b-155">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="5931b-155">The language of the template to create.</span></span> <span data-ttu-id="5931b-156">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="5931b-156">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5931b-157">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="5931b-157">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5931b-158">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="5931b-158">The name for the created output.</span></span> <span data-ttu-id="5931b-159">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5931b-159">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5931b-160">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="5931b-160">Location to place the generated output.</span></span> <span data-ttu-id="5931b-161">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="5931b-161">The default is the current directory.</span></span>

`-all|--show-all`

<span data-ttu-id="5931b-162">Affiche tous les modèles pour un type de projet spécifique lors de l’exécution dans le contexte de la commande `dotnet new` seule.</span><span class="sxs-lookup"><span data-stu-id="5931b-162">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="5931b-163">Lors de l’exécution dans le contexte d’un modèle spécifique, comme `dotnet new web -all`, `-all` est interprété comme un indicateur de création forcée.</span><span class="sxs-lookup"><span data-stu-id="5931b-163">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="5931b-164">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="5931b-164">This is required when the output directory already contains a project.</span></span>

## <a name="template-options"></a><span data-ttu-id="5931b-165">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="5931b-165">Template options</span></span>

<span data-ttu-id="5931b-166">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="5931b-166">Each project template may have additional options available.</span></span> <span data-ttu-id="5931b-167">Les modèles de base ont les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="5931b-167">The core templates have the following options:</span></span>

<span data-ttu-id="5931b-168">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="5931b-168">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="5931b-169">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="5931b-169">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5931b-170">Valeurs : `netcoreapp1.0` ou `netcoreapp1.1` (valeur par défaut : `netcoreapp1.0`)</span><span class="sxs-lookup"><span data-stu-id="5931b-170">Values: `netcoreapp1.0` or `netcoreapp1.1` (Default: `netcoreapp1.0`)</span></span>

<span data-ttu-id="5931b-171">**mvc**</span><span class="sxs-lookup"><span data-stu-id="5931b-171">**mvc**</span></span>

<span data-ttu-id="5931b-172">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="5931b-172">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5931b-173">Valeurs : `netcoreapp1.0` ou `netcoreapp1.1` (`Default: netcoreapp1.0`)</span><span class="sxs-lookup"><span data-stu-id="5931b-173">Values: `netcoreapp1.0` or `netcoreapp1.1` (`Default: netcoreapp1.0`)</span></span>

<span data-ttu-id="5931b-174">`-au|--auth` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5931b-174">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="5931b-175">Valeurs : `None` ou `Individual` (valeur par défaut : `None`)</span><span class="sxs-lookup"><span data-stu-id="5931b-175">Values: `None` or `Individual` (Default: `None`)</span></span>

<span data-ttu-id="5931b-176">`-uld|--use-local-db` : spécifie s’il convient ou non d’utiliser LocalDB au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="5931b-176">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="5931b-177">Valeurs : `true` ou `false` (valeur par défaut : `false`)</span><span class="sxs-lookup"><span data-stu-id="5931b-177">Values: `true` or `false` (Default: `false`)</span></span>

<span data-ttu-id="5931b-178">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5931b-178">**classlib**</span></span>

<span data-ttu-id="5931b-179">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="5931b-179">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5931b-180">Valeurs : `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` à `netstandard1.6` (valeur par défaut : `netstandard1.4`)</span><span class="sxs-lookup"><span data-stu-id="5931b-180">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6` (Default: `netstandard1.4`)</span></span>

## <a name="examples"></a><span data-ttu-id="5931b-181">Exemples</span><span class="sxs-lookup"><span data-stu-id="5931b-181">Examples</span></span>

<span data-ttu-id="5931b-182">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="5931b-182">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#` 
   
<span data-ttu-id="5931b-183">Créez un projet d’application ASP.NET Core C# MVC dans le répertoire actif sans authentification ciblant .NET Core 1.0 :</span><span class="sxs-lookup"><span data-stu-id="5931b-183">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 1.0:</span></span>  

`dotnet new mvc -au None -f netcoreapp1.0`
 
<span data-ttu-id="5931b-184">Créez une application xUnit ciblant .NET Core 1.1 :</span><span class="sxs-lookup"><span data-stu-id="5931b-184">Create a new xUnit application targeting .NET Core 1.1:</span></span>

`dotnet new xunit --framework netcoreapp1.1`

<span data-ttu-id="5931b-185">Répertoriez tous les modèles disponibles pour MVC :</span><span class="sxs-lookup"><span data-stu-id="5931b-185">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

