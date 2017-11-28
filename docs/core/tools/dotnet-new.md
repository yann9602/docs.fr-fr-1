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
ms.openlocfilehash: d64881380febee08414f57a36ed92079e8d69ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="39772-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="39772-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="39772-105">Nom</span><span class="sxs-lookup"><span data-stu-id="39772-105">Name</span></span>

<span data-ttu-id="39772-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="39772-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="39772-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="39772-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="39772-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="39772-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="39772-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="39772-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="39772-110">Description</span><span class="sxs-lookup"><span data-stu-id="39772-110">Description</span></span>

<span data-ttu-id="39772-111">La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide.</span><span class="sxs-lookup"><span data-stu-id="39772-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="39772-112">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="39772-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="39772-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="39772-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="39772-114">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="39772-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="39772-115">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="39772-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="39772-116">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="39772-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="39772-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="39772-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="39772-118">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="39772-118">The command contains a default list of templates.</span></span> <span data-ttu-id="39772-119">Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="39772-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="39772-120">Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="39772-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="39772-121">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="39772-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="39772-122">Description du modèle</span><span class="sxs-lookup"><span data-stu-id="39772-122">Template description</span></span>                          | <span data-ttu-id="39772-123">Nom du modèle</span><span class="sxs-lookup"><span data-stu-id="39772-123">Template name</span></span>  | <span data-ttu-id="39772-124">Langages</span><span class="sxs-lookup"><span data-stu-id="39772-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="39772-125">Application console</span><span class="sxs-lookup"><span data-stu-id="39772-125">Console application</span></span>                          | <span data-ttu-id="39772-126">console</span><span class="sxs-lookup"><span data-stu-id="39772-126">console</span></span>        | <span data-ttu-id="39772-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="39772-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="39772-128">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="39772-128">Class library</span></span>                                | <span data-ttu-id="39772-129">classlib</span><span class="sxs-lookup"><span data-stu-id="39772-129">classlib</span></span>       | <span data-ttu-id="39772-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="39772-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="39772-131">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="39772-131">Unit test project</span></span>                            | <span data-ttu-id="39772-132">mstest</span><span class="sxs-lookup"><span data-stu-id="39772-132">mstest</span></span>         | <span data-ttu-id="39772-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="39772-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="39772-134">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="39772-134">xUnit test project</span></span>                           | <span data-ttu-id="39772-135">xunit</span><span class="sxs-lookup"><span data-stu-id="39772-135">xunit</span></span>          | <span data-ttu-id="39772-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="39772-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="39772-137">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="39772-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="39772-138">web</span><span class="sxs-lookup"><span data-stu-id="39772-138">web</span></span>            | <span data-ttu-id="39772-139">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="39772-139">[C#], F#</span></span>      |
| <span data-ttu-id="39772-140">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="39772-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="39772-141">mvc</span><span class="sxs-lookup"><span data-stu-id="39772-141">mvc</span></span>            | <span data-ttu-id="39772-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="39772-142">[C#], F#</span></span>      |
| <span data-ttu-id="39772-143">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39772-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="39772-144">razor</span><span class="sxs-lookup"><span data-stu-id="39772-144">razor</span></span>          | <span data-ttu-id="39772-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="39772-145">[C#]</span></span>          |
| <span data-ttu-id="39772-146">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="39772-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="39772-147">angular</span><span class="sxs-lookup"><span data-stu-id="39772-147">angular</span></span>        | <span data-ttu-id="39772-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="39772-148">[C#]</span></span>          |
| <span data-ttu-id="39772-149">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="39772-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="39772-150">react</span><span class="sxs-lookup"><span data-stu-id="39772-150">react</span></span>          | <span data-ttu-id="39772-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="39772-151">[C#]</span></span>          |
| <span data-ttu-id="39772-152">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="39772-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="39772-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="39772-153">reactredux</span></span>     | <span data-ttu-id="39772-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="39772-154">[C#]</span></span>          |
| <span data-ttu-id="39772-155">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39772-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="39772-156">webapi</span><span class="sxs-lookup"><span data-stu-id="39772-156">webapi</span></span>         | <span data-ttu-id="39772-157">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="39772-157">[C#], F#</span></span>      |
| <span data-ttu-id="39772-158">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="39772-158">global.json file</span></span>                             | <span data-ttu-id="39772-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="39772-159">globaljson</span></span>     |               |
| <span data-ttu-id="39772-160">Config NuGet</span><span class="sxs-lookup"><span data-stu-id="39772-160">Nuget config</span></span>                                 | <span data-ttu-id="39772-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="39772-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="39772-162">config web</span><span class="sxs-lookup"><span data-stu-id="39772-162">Web config</span></span>                                   | <span data-ttu-id="39772-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="39772-163">webconfig</span></span>      |               |
| <span data-ttu-id="39772-164">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="39772-164">Solution file</span></span>                                | <span data-ttu-id="39772-165">sln</span><span class="sxs-lookup"><span data-stu-id="39772-165">sln</span></span>            |               |
| <span data-ttu-id="39772-166">Page Razor</span><span class="sxs-lookup"><span data-stu-id="39772-166">Razor page</span></span>                                   | <span data-ttu-id="39772-167">page</span><span class="sxs-lookup"><span data-stu-id="39772-167">page</span></span>           |               |
| <span data-ttu-id="39772-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="39772-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="39772-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="39772-169">viewimports</span></span>    |               |
| <span data-ttu-id="39772-170">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="39772-170">MVC ViewStart</span></span>                                | <span data-ttu-id="39772-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="39772-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="39772-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="39772-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="39772-173">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="39772-173">The command contains a default list of templates.</span></span> <span data-ttu-id="39772-174">Utilisez `dotnet new -all` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="39772-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="39772-175">Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="39772-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="39772-176">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="39772-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="39772-177">Description du modèle</span><span class="sxs-lookup"><span data-stu-id="39772-177">Template description</span></span>  | <span data-ttu-id="39772-178">Nom du modèle</span><span class="sxs-lookup"><span data-stu-id="39772-178">Template name</span></span>  | <span data-ttu-id="39772-179">Langages</span><span class="sxs-lookup"><span data-stu-id="39772-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="39772-180">Application console</span><span class="sxs-lookup"><span data-stu-id="39772-180">Console application</span></span>  | <span data-ttu-id="39772-181">console</span><span class="sxs-lookup"><span data-stu-id="39772-181">console</span></span>        | <span data-ttu-id="39772-182">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="39772-182">[C#], F#</span></span>  |
| <span data-ttu-id="39772-183">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="39772-183">Class library</span></span>        | <span data-ttu-id="39772-184">classlib</span><span class="sxs-lookup"><span data-stu-id="39772-184">classlib</span></span>       | <span data-ttu-id="39772-185">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="39772-185">[C#], F#</span></span>  |
| <span data-ttu-id="39772-186">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="39772-186">Unit test project</span></span>    | <span data-ttu-id="39772-187">mstest</span><span class="sxs-lookup"><span data-stu-id="39772-187">mstest</span></span>         | <span data-ttu-id="39772-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="39772-188">[C#], F#</span></span>  |
| <span data-ttu-id="39772-189">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="39772-189">xUnit test project</span></span>   | <span data-ttu-id="39772-190">xunit</span><span class="sxs-lookup"><span data-stu-id="39772-190">xunit</span></span>          | <span data-ttu-id="39772-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="39772-191">[C#], F#</span></span>  |
| <span data-ttu-id="39772-192">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="39772-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="39772-193">web</span><span class="sxs-lookup"><span data-stu-id="39772-193">web</span></span>            | <span data-ttu-id="39772-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="39772-194">[C#]</span></span>      |
| <span data-ttu-id="39772-195">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39772-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="39772-196">mvc</span><span class="sxs-lookup"><span data-stu-id="39772-196">mvc</span></span>            | <span data-ttu-id="39772-197">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="39772-197">[C#], F#</span></span>  |
| <span data-ttu-id="39772-198">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39772-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="39772-199">webapi</span><span class="sxs-lookup"><span data-stu-id="39772-199">webapi</span></span>         | <span data-ttu-id="39772-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="39772-200">[C#]</span></span>      |
| <span data-ttu-id="39772-201">Config NuGet</span><span class="sxs-lookup"><span data-stu-id="39772-201">Nuget config</span></span>         | <span data-ttu-id="39772-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="39772-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="39772-203">config web</span><span class="sxs-lookup"><span data-stu-id="39772-203">Web config</span></span>           | <span data-ttu-id="39772-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="39772-204">webconfig</span></span>      |           |
| <span data-ttu-id="39772-205">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="39772-205">Solution file</span></span>        | <span data-ttu-id="39772-206">sln</span><span class="sxs-lookup"><span data-stu-id="39772-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="39772-207">Options</span><span class="sxs-lookup"><span data-stu-id="39772-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="39772-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="39772-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="39772-209">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="39772-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="39772-210">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="39772-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="39772-211">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="39772-211">Prints out help for the command.</span></span> <span data-ttu-id="39772-212">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="39772-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="39772-213">Installe un pack source ou de modèle à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="39772-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="39772-214">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="39772-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="39772-215">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="39772-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="39772-216">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="39772-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="39772-217">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="39772-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="39772-218">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="39772-218">The language of the template to create.</span></span> <span data-ttu-id="39772-219">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="39772-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="39772-220">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="39772-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="39772-221">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="39772-221">The name for the created output.</span></span> <span data-ttu-id="39772-222">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="39772-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="39772-223">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="39772-223">Location to place the generated output.</span></span> <span data-ttu-id="39772-224">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="39772-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="39772-225">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="39772-225">Filters templates based on available types.</span></span> <span data-ttu-id="39772-226">Les valeurs prédéfinies sont « project », « item » ou « other ».</span><span class="sxs-lookup"><span data-stu-id="39772-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="39772-227">Désinstalle un pack source ou de modèle au `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="39772-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="39772-228">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="39772-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="39772-229">Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="39772-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="39772-230">En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.</span><span class="sxs-lookup"><span data-stu-id="39772-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="39772-231">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="39772-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="39772-232">Affiche tous les modèles pour un type de projet spécifique lors de l’exécution dans le contexte de la commande `dotnet new` seule.</span><span class="sxs-lookup"><span data-stu-id="39772-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="39772-233">Lors de l’exécution dans le contexte d’un modèle spécifique, comme `dotnet new web -all`, `-all` est interprété comme un indicateur de création forcée.</span><span class="sxs-lookup"><span data-stu-id="39772-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="39772-234">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="39772-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="39772-235">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="39772-235">Prints out help for the command.</span></span> <span data-ttu-id="39772-236">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="39772-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="39772-237">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="39772-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="39772-238">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="39772-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="39772-239">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="39772-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="39772-240">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="39772-240">The language of the template to create.</span></span> <span data-ttu-id="39772-241">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="39772-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="39772-242">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="39772-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="39772-243">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="39772-243">The name for the created output.</span></span> <span data-ttu-id="39772-244">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="39772-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="39772-245">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="39772-245">Location to place the generated output.</span></span> <span data-ttu-id="39772-246">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="39772-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="39772-247">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="39772-247">Template options</span></span>

<span data-ttu-id="39772-248">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="39772-248">Each project template may have additional options available.</span></span> <span data-ttu-id="39772-249">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="39772-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="39772-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="39772-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="39772-251">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="39772-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="39772-252">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="39772-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="39772-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="39772-253">**classlib**</span></span>

<span data-ttu-id="39772-254">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="39772-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="39772-255">Valeurs : `netcoreapp2.0` pour créer une bibliothèque de classes .NET Core ou `netstandard2.0` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="39772-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="39772-256">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="39772-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="39772-257">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="39772-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="39772-258">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="39772-258">**mstest, xunit**</span></span>

<span data-ttu-id="39772-259">`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="39772-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="39772-260">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="39772-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="39772-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="39772-261">**globaljson**</span></span>

<span data-ttu-id="39772-262">`--sdk-version <VERSION_NUMBER>` : spécifie la version du SDK .NET Core à utiliser dans le fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="39772-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="39772-263">**web**</span><span class="sxs-lookup"><span data-stu-id="39772-263">**web**</span></span>

<span data-ttu-id="39772-264">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="39772-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="39772-265">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="39772-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="39772-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="39772-266">**webapi**</span></span>

<span data-ttu-id="39772-267">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="39772-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="39772-268">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="39772-268">The possible values are:</span></span>

- <span data-ttu-id="39772-269">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="39772-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="39772-270">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="39772-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="39772-271">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="39772-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="39772-272">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="39772-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="39772-273">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="39772-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="39772-274">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="39772-275">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="39772-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="39772-276">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="39772-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="39772-277">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="39772-278">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="39772-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="39772-279">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="39772-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="39772-280">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="39772-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="39772-281">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="39772-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="39772-282">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="39772-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="39772-283">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="39772-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="39772-284">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="39772-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="39772-285">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="39772-286">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="39772-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="39772-287">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="39772-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="39772-288">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="39772-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="39772-289">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="39772-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="39772-290">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="39772-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="39772-291">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="39772-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="39772-292">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="39772-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="39772-293">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="39772-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="39772-294">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="39772-295">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="39772-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="39772-296">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="39772-296">**mvc, razor**</span></span>

<span data-ttu-id="39772-297">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="39772-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="39772-298">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="39772-298">The possible values are:</span></span>

- <span data-ttu-id="39772-299">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="39772-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="39772-300">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="39772-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="39772-301">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="39772-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="39772-302">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="39772-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="39772-303">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="39772-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="39772-304">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="39772-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="39772-305">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="39772-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="39772-306">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="39772-307">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="39772-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="39772-308">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="39772-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="39772-309">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="39772-310">`-rp|--reset-password-policy-id <ID>` : ID de stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="39772-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="39772-311">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="39772-312">`-ep|--edit-profile-policy-id <ID>` : ID de stratégie de modification du profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="39772-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="39772-313">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="39772-314">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="39772-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="39772-315">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="39772-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="39772-316">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="39772-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="39772-317">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="39772-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="39772-318">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="39772-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="39772-319">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="39772-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="39772-320">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="39772-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="39772-321">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="39772-322">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="39772-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="39772-323">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="39772-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="39772-324">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="39772-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="39772-325">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="39772-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="39772-326">`--callback-path <PATH>` : chemin de demande dans le chemin de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="39772-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="39772-327">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="39772-328">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="39772-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="39772-329">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="39772-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="39772-330">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="39772-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="39772-331">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="39772-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="39772-332">`--use-browserlink` : inclut BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="39772-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="39772-333">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="39772-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="39772-334">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="39772-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="39772-335">`--no-restore` : n’effectue pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="39772-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="39772-336">**page**</span><span class="sxs-lookup"><span data-stu-id="39772-336">**page**</span></span>

<span data-ttu-id="39772-337">`-na|--namespace <NAMESPACE_NAME>` : espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="39772-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="39772-338">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="39772-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="39772-339">`-np|--no-pagemodel` : crée la page sans modèle de page.</span><span class="sxs-lookup"><span data-stu-id="39772-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="39772-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="39772-340">**viewimports**</span></span>

<span data-ttu-id="39772-341">`-na|--namespace <NAMESPACE_NAME>` : espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="39772-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="39772-342">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="39772-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="39772-343">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="39772-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="39772-344">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="39772-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="39772-345">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="39772-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="39772-346">Valeurs : `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="39772-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="39772-347">La valeur par défaut est `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="39772-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="39772-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="39772-348">**classlib**</span></span>

<span data-ttu-id="39772-349">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="39772-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="39772-350">Valeurs : `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` à `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="39772-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="39772-351">La valeur par défaut est `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="39772-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="39772-352">**mvc**</span><span class="sxs-lookup"><span data-stu-id="39772-352">**mvc**</span></span>

<span data-ttu-id="39772-353">`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="39772-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="39772-354">Valeurs : `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="39772-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="39772-355">La valeur par défaut est `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="39772-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="39772-356">`-au|--auth` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="39772-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="39772-357">Valeurs : `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="39772-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="39772-358">La valeur par défaut est `None`.</span><span class="sxs-lookup"><span data-stu-id="39772-358">The default value is `None`.</span></span>

<span data-ttu-id="39772-359">`-uld|--use-local-db` : spécifie s’il convient ou non d’utiliser LocalDB au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="39772-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="39772-360">Valeurs : `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="39772-360">Values: `true` or `false`.</span></span> <span data-ttu-id="39772-361">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="39772-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="39772-362">Exemples</span><span class="sxs-lookup"><span data-stu-id="39772-362">Examples</span></span>

<span data-ttu-id="39772-363">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="39772-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="39772-364">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié (disponible uniquement avec le SDK .NET Core 2.0 ou ultérieur) :</span><span class="sxs-lookup"><span data-stu-id="39772-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="39772-365">Créez un projet d’application ASP.NET Core C# MVC dans le répertoire actif sans authentification ciblant .NET Core 2.0 :</span><span class="sxs-lookup"><span data-stu-id="39772-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="39772-366">Créez une application xUnit ciblant .NET Core 2.0 :</span><span class="sxs-lookup"><span data-stu-id="39772-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="39772-367">Répertoriez tous les modèles disponibles pour MVC :</span><span class="sxs-lookup"><span data-stu-id="39772-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="39772-368">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39772-368">See also</span></span>

[<span data-ttu-id="39772-369">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="39772-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="39772-370">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="39772-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="39772-371">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="39772-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="39772-372">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="39772-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
