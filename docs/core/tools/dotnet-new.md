---
title: Commande dotnet new - Interface CLI .NET Core
description: "La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié."
keywords: "dotnet-new, CLI, commande CLI, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload:
- dotnetcore
ms.openlocfilehash: ea94c875ae6fe82d0e5d35ba8ca3fd47971fbbe6
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="fd268-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="fd268-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="fd268-105">Name</span><span class="sxs-lookup"><span data-stu-id="fd268-105">Name</span></span>

<span data-ttu-id="fd268-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="fd268-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fd268-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="fd268-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fd268-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="fd268-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fd268-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fd268-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="fd268-110">Description</span><span class="sxs-lookup"><span data-stu-id="fd268-110">Description</span></span>

<span data-ttu-id="fd268-111">La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide.</span><span class="sxs-lookup"><span data-stu-id="fd268-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="fd268-112">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="fd268-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="fd268-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="fd268-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="fd268-114">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="fd268-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="fd268-115">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="fd268-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="fd268-116">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="fd268-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fd268-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="fd268-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="fd268-118">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="fd268-118">The command contains a default list of templates.</span></span> <span data-ttu-id="fd268-119">Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="fd268-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="fd268-120">Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="fd268-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="fd268-121">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="fd268-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="fd268-122">Description du modèle</span><span class="sxs-lookup"><span data-stu-id="fd268-122">Template description</span></span>                          | <span data-ttu-id="fd268-123">Nom du modèle</span><span class="sxs-lookup"><span data-stu-id="fd268-123">Template name</span></span> | <span data-ttu-id="fd268-124">Langages</span><span class="sxs-lookup"><span data-stu-id="fd268-124">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="fd268-125">Application console</span><span class="sxs-lookup"><span data-stu-id="fd268-125">Console application</span></span>                          | `console`     | <span data-ttu-id="fd268-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fd268-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fd268-127">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="fd268-127">Class library</span></span>                                | `classlib`    | <span data-ttu-id="fd268-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fd268-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fd268-129">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="fd268-129">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="fd268-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fd268-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fd268-131">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="fd268-131">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="fd268-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fd268-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fd268-133">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="fd268-133">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="fd268-134">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fd268-134">[C#], F#</span></span>      |
| <span data-ttu-id="fd268-135">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="fd268-135">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="fd268-136">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fd268-136">[C#], F#</span></span>      |
| <span data-ttu-id="fd268-137">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fd268-137">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="fd268-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="fd268-138">[C#]</span></span>          |
| <span data-ttu-id="fd268-139">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="fd268-139">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="fd268-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="fd268-140">[C#]</span></span>          |
| <span data-ttu-id="fd268-141">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="fd268-141">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="fd268-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="fd268-142">[C#]</span></span>          |
| <span data-ttu-id="fd268-143">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="fd268-143">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="fd268-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="fd268-144">[C#]</span></span>          |
| <span data-ttu-id="fd268-145">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fd268-145">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="fd268-146">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fd268-146">[C#], F#</span></span>      |
| <span data-ttu-id="fd268-147">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="fd268-147">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="fd268-148">Config NuGet</span><span class="sxs-lookup"><span data-stu-id="fd268-148">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="fd268-149">config web</span><span class="sxs-lookup"><span data-stu-id="fd268-149">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="fd268-150">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="fd268-150">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="fd268-151">Page Razor</span><span class="sxs-lookup"><span data-stu-id="fd268-151">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="fd268-152">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="fd268-152">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="fd268-153">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="fd268-153">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fd268-154">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fd268-154">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="fd268-155">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="fd268-155">The command contains a default list of templates.</span></span> <span data-ttu-id="fd268-156">Utilisez `dotnet new -all` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="fd268-156">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="fd268-157">Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="fd268-157">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="fd268-158">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="fd268-158">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="fd268-159">Description du modèle</span><span class="sxs-lookup"><span data-stu-id="fd268-159">Template description</span></span>  | <span data-ttu-id="fd268-160">Nom du modèle</span><span class="sxs-lookup"><span data-stu-id="fd268-160">Template name</span></span> | <span data-ttu-id="fd268-161">Langages</span><span class="sxs-lookup"><span data-stu-id="fd268-161">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="fd268-162">Application console</span><span class="sxs-lookup"><span data-stu-id="fd268-162">Console application</span></span>  | `console`     | <span data-ttu-id="fd268-163">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fd268-163">[C#], F#</span></span>  |
| <span data-ttu-id="fd268-164">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="fd268-164">Class library</span></span>        | `classlib`    | <span data-ttu-id="fd268-165">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fd268-165">[C#], F#</span></span>  |
| <span data-ttu-id="fd268-166">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="fd268-166">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="fd268-167">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fd268-167">[C#], F#</span></span>  |
| <span data-ttu-id="fd268-168">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="fd268-168">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="fd268-169">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fd268-169">[C#], F#</span></span>  |
| <span data-ttu-id="fd268-170">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="fd268-170">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="fd268-171">[C#]</span><span class="sxs-lookup"><span data-stu-id="fd268-171">[C#]</span></span>      |
| <span data-ttu-id="fd268-172">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fd268-172">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="fd268-173">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fd268-173">[C#], F#</span></span>  |
| <span data-ttu-id="fd268-174">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fd268-174">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="fd268-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="fd268-175">[C#]</span></span>      |
| <span data-ttu-id="fd268-176">Config NuGet</span><span class="sxs-lookup"><span data-stu-id="fd268-176">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="fd268-177">config web</span><span class="sxs-lookup"><span data-stu-id="fd268-177">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="fd268-178">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="fd268-178">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="fd268-179">Options</span><span class="sxs-lookup"><span data-stu-id="fd268-179">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fd268-180">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="fd268-180">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="fd268-181">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="fd268-181">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="fd268-182">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-182">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="fd268-183">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="fd268-183">Prints out help for the command.</span></span> <span data-ttu-id="fd268-184">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="fd268-184">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="fd268-185">Installe un pack source ou de modèle à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="fd268-185">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="fd268-186">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="fd268-186">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="fd268-187">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="fd268-187">Lists templates containing the specified name.</span></span> <span data-ttu-id="fd268-188">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="fd268-188">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="fd268-189">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-189">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="fd268-190">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="fd268-190">The language of the template to create.</span></span> <span data-ttu-id="fd268-191">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="fd268-191">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="fd268-192">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="fd268-192">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="fd268-193">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="fd268-193">The name for the created output.</span></span> <span data-ttu-id="fd268-194">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="fd268-194">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fd268-195">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="fd268-195">Location to place the generated output.</span></span> <span data-ttu-id="fd268-196">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="fd268-196">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="fd268-197">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="fd268-197">Filters templates based on available types.</span></span> <span data-ttu-id="fd268-198">Les valeurs prédéfinies sont « project », « item » ou « other ».</span><span class="sxs-lookup"><span data-stu-id="fd268-198">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="fd268-199">Désinstalle un pack source ou de modèle au `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="fd268-199">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="fd268-200">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="fd268-200">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="fd268-201">Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="fd268-201">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="fd268-202">En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.</span><span class="sxs-lookup"><span data-stu-id="fd268-202">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fd268-203">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fd268-203">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="fd268-204">Affiche tous les modèles pour un type de projet spécifique lors de l’exécution dans le contexte de la commande `dotnet new` seule.</span><span class="sxs-lookup"><span data-stu-id="fd268-204">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="fd268-205">Lors de l’exécution dans le contexte d’un modèle spécifique, comme `dotnet new web -all`, `-all` est interprété comme un indicateur de création forcée.</span><span class="sxs-lookup"><span data-stu-id="fd268-205">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="fd268-206">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-206">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="fd268-207">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="fd268-207">Prints out help for the command.</span></span> <span data-ttu-id="fd268-208">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="fd268-208">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="fd268-209">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="fd268-209">Lists templates containing the specified name.</span></span> <span data-ttu-id="fd268-210">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="fd268-210">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="fd268-211">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-211">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="fd268-212">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="fd268-212">The language of the template to create.</span></span> <span data-ttu-id="fd268-213">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="fd268-213">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="fd268-214">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="fd268-214">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="fd268-215">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="fd268-215">The name for the created output.</span></span> <span data-ttu-id="fd268-216">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="fd268-216">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fd268-217">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="fd268-217">Location to place the generated output.</span></span> <span data-ttu-id="fd268-218">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="fd268-218">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="fd268-219">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="fd268-219">Template options</span></span>

<span data-ttu-id="fd268-220">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="fd268-220">Each project template may have additional options available.</span></span> <span data-ttu-id="fd268-221">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="fd268-221">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fd268-222">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="fd268-222">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="fd268-223">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="fd268-223">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="fd268-224">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-224">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="fd268-225">**classlib**</span><span class="sxs-lookup"><span data-stu-id="fd268-225">**classlib**</span></span>

<span data-ttu-id="fd268-226">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="fd268-226">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fd268-227">Valeurs : `netcoreapp2.0` pour créer une bibliothèque de classes .NET Core ou `netstandard2.0` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="fd268-227">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="fd268-228">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="fd268-228">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="fd268-229">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-229">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="fd268-230">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="fd268-230">**mstest, xunit**</span></span>

<span data-ttu-id="fd268-231">`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="fd268-231">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="fd268-232">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-232">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="fd268-233">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="fd268-233">**globaljson**</span></span>

<span data-ttu-id="fd268-234">`--sdk-version <VERSION_NUMBER>` : spécifie la version du SDK .NET Core à utiliser dans le fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="fd268-234">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="fd268-235">**web**</span><span class="sxs-lookup"><span data-stu-id="fd268-235">**web**</span></span>

<span data-ttu-id="fd268-236">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="fd268-236">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fd268-237">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-237">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="fd268-238">**webapi**</span><span class="sxs-lookup"><span data-stu-id="fd268-238">**webapi**</span></span>

<span data-ttu-id="fd268-239">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fd268-239">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fd268-240">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="fd268-240">The possible values are:</span></span>

- <span data-ttu-id="fd268-241">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="fd268-241">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fd268-242">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="fd268-242">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fd268-243">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="fd268-243">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fd268-244">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="fd268-244">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fd268-245">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="fd268-245">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fd268-246">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-246">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fd268-247">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="fd268-247">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fd268-248">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-248">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fd268-249">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-249">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fd268-250">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="fd268-250">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fd268-251">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="fd268-251">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fd268-252">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="fd268-252">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fd268-253">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-253">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fd268-254">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="fd268-254">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="fd268-255">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="fd268-255">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fd268-256">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="fd268-256">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fd268-257">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-257">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fd268-258">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="fd268-258">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fd268-259">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="fd268-259">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fd268-260">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="fd268-260">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fd268-261">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="fd268-261">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fd268-262">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="fd268-262">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fd268-263">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="fd268-263">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fd268-264">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="fd268-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fd268-265">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="fd268-265">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fd268-266">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-266">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fd268-267">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-267">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="fd268-268">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="fd268-268">**mvc, razor**</span></span>

<span data-ttu-id="fd268-269">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fd268-269">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fd268-270">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="fd268-270">The possible values are:</span></span>

- <span data-ttu-id="fd268-271">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="fd268-271">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fd268-272">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="fd268-272">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="fd268-273">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="fd268-273">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fd268-274">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="fd268-274">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fd268-275">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="fd268-275">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="fd268-276">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="fd268-276">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fd268-277">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="fd268-277">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fd268-278">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-278">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fd268-279">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="fd268-279">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="fd268-280">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-280">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fd268-281">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-281">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fd268-282">`-rp|--reset-password-policy-id <ID>` : ID de stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-282">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="fd268-283">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fd268-284">`-ep|--edit-profile-policy-id <ID>` : ID de stratégie de modification du profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-284">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="fd268-285">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fd268-286">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="fd268-286">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fd268-287">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="fd268-287">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="fd268-288">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="fd268-288">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fd268-289">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-289">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fd268-290">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="fd268-290">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="fd268-291">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="fd268-291">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fd268-292">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="fd268-292">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fd268-293">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-293">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="fd268-294">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="fd268-294">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fd268-295">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="fd268-295">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fd268-296">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="fd268-296">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="fd268-297">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="fd268-297">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fd268-298">`--callback-path <PATH>` : chemin de demande dans le chemin de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="fd268-298">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="fd268-299">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-299">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="fd268-300">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="fd268-300">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="fd268-301">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="fd268-301">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fd268-302">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="fd268-302">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fd268-303">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="fd268-303">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fd268-304">`--use-browserlink` : inclut BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-304">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="fd268-305">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="fd268-305">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fd268-306">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="fd268-306">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fd268-307">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="fd268-307">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="fd268-308">**page**</span><span class="sxs-lookup"><span data-stu-id="fd268-308">**page**</span></span>

<span data-ttu-id="fd268-309">`-na|--namespace <NAMESPACE_NAME>` : espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="fd268-309">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fd268-310">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="fd268-310">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="fd268-311">`-np|--no-pagemodel` : crée la page sans modèle de page.</span><span class="sxs-lookup"><span data-stu-id="fd268-311">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="fd268-312">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="fd268-312">**viewimports**</span></span>

<span data-ttu-id="fd268-313">`-na|--namespace <NAMESPACE_NAME>` : espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="fd268-313">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fd268-314">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="fd268-314">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fd268-315">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fd268-315">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="fd268-316">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="fd268-316">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="fd268-317">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="fd268-317">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fd268-318">Valeurs : `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="fd268-318">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="fd268-319">La valeur par défaut est `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="fd268-319">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="fd268-320">**classlib**</span><span class="sxs-lookup"><span data-stu-id="fd268-320">**classlib**</span></span>

<span data-ttu-id="fd268-321">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="fd268-321">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fd268-322">Valeurs : `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` à `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="fd268-322">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="fd268-323">La valeur par défaut est `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="fd268-323">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="fd268-324">**mvc**</span><span class="sxs-lookup"><span data-stu-id="fd268-324">**mvc**</span></span>

<span data-ttu-id="fd268-325">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="fd268-325">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fd268-326">Valeurs : `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="fd268-326">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="fd268-327">La valeur par défaut est `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="fd268-327">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="fd268-328">`-au|--auth` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fd268-328">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="fd268-329">Valeurs : `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="fd268-329">Values: `None` or `Individual`.</span></span> <span data-ttu-id="fd268-330">La valeur par défaut est `None`.</span><span class="sxs-lookup"><span data-stu-id="fd268-330">The default value is `None`.</span></span>

<span data-ttu-id="fd268-331">`-uld|--use-local-db` : spécifie s’il convient ou non d’utiliser LocalDB au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="fd268-331">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="fd268-332">Valeurs : `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="fd268-332">Values: `true` or `false`.</span></span> <span data-ttu-id="fd268-333">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="fd268-333">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="fd268-334">Exemples</span><span class="sxs-lookup"><span data-stu-id="fd268-334">Examples</span></span>

<span data-ttu-id="fd268-335">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="fd268-335">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="fd268-336">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié (disponible uniquement avec le SDK .NET Core 2.0 ou ultérieur) :</span><span class="sxs-lookup"><span data-stu-id="fd268-336">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="fd268-337">Créez un projet d’application ASP.NET Core C# MVC dans le répertoire actif sans authentification ciblant .NET Core 2.0 :</span><span class="sxs-lookup"><span data-stu-id="fd268-337">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="fd268-338">Créez une application xUnit ciblant .NET Core 2.0 :</span><span class="sxs-lookup"><span data-stu-id="fd268-338">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="fd268-339">Répertoriez tous les modèles disponibles pour MVC :</span><span class="sxs-lookup"><span data-stu-id="fd268-339">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="fd268-340">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd268-340">See also</span></span>

[<span data-ttu-id="fd268-341">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="fd268-341">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="fd268-342">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="fd268-342">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="fd268-343">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="fd268-343">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="fd268-344">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="fd268-344">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
