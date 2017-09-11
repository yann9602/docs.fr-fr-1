---
title: Commande dotnet-sln - Interface CLI .NET Core
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
keywords: dotnet-sln, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 04/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 606929fbcafddf47abf5da6d3c8ce97d5af06909
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-sln"></a><span data-ttu-id="d879e-104">dotnet-sln</span><span class="sxs-lookup"><span data-stu-id="d879e-104">dotnet-sln</span></span>

## <a name="name"></a><span data-ttu-id="d879e-105">Nom</span><span class="sxs-lookup"><span data-stu-id="d879e-105">Name</span></span>

<span data-ttu-id="d879e-106">`dotnet-sln` : Modifie un fichier solution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d879e-106">`dotnet-sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d879e-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="d879e-107">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d879e-108">Description</span><span class="sxs-lookup"><span data-stu-id="d879e-108">Description</span></span>

<span data-ttu-id="d879e-109">La commande `dotnet sln` offre un moyen pratique d’ajouter, de supprimer et de lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="d879e-109">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="d879e-110">Commandes</span><span class="sxs-lookup"><span data-stu-id="d879e-110">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="d879e-111">Ajoute un ou plusieurs projets au fichier solution.</span><span class="sxs-lookup"><span data-stu-id="d879e-111">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="d879e-112">Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="d879e-112">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="d879e-113">Supprime un ou plusieurs projets du fichier solution.</span><span class="sxs-lookup"><span data-stu-id="d879e-113">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="d879e-114">Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="d879e-114">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="d879e-115">Liste tous les projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="d879e-115">List all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="d879e-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="d879e-116">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="d879e-117">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d879e-117">Solution file to use.</span></span> <span data-ttu-id="d879e-118">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="d879e-118">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="d879e-119">S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="d879e-119">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="d879e-120">Options</span><span class="sxs-lookup"><span data-stu-id="d879e-120">Options</span></span>

`-h|--help`

<span data-ttu-id="d879e-121">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="d879e-121">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="d879e-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="d879e-122">Examples</span></span>

<span data-ttu-id="d879e-123">Ajouter un projet C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="d879e-123">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="d879e-124">Supprimer un projet C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="d879e-124">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="d879e-125">Ajouter plusieurs projets C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="d879e-125">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="d879e-126">Supprimer plusieurs projets C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="d879e-126">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="d879e-127">Ajouter plusieurs projets C# à une solution avec un modèle d’utilisation des caractères génériques :</span><span class="sxs-lookup"><span data-stu-id="d879e-127">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="d879e-128">Supprimer plusieurs projets C# d’une solution avec un modèle d’utilisation des caractères génériques :</span><span class="sxs-lookup"><span data-stu-id="d879e-128">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

