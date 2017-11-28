---
title: Commande dotnet sln - Interface CLI .NET Core
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 5071cb80be0fb14829a0fdffd0f5a2d2371b6ba8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-sln"></a><span data-ttu-id="2b3e3-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="2b3e3-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2b3e3-104">Nom</span><span class="sxs-lookup"><span data-stu-id="2b3e3-104">Name</span></span>

<span data-ttu-id="2b3e3-105">`dotnet-sln` : Modifie un fichier solution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-105">`dotnet-sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2b3e3-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="2b3e3-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2b3e3-107">Description</span><span class="sxs-lookup"><span data-stu-id="2b3e3-107">Description</span></span>

<span data-ttu-id="2b3e3-108">La commande `dotnet sln` offre un moyen pratique d’ajouter, de supprimer et de lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="2b3e3-109">Commandes</span><span class="sxs-lookup"><span data-stu-id="2b3e3-109">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="2b3e3-110">Ajoute un ou plusieurs projets au fichier solution.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-110">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="2b3e3-111">Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-111">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="2b3e3-112">Supprime un ou plusieurs projets du fichier solution.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-112">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="2b3e3-113">Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="2b3e3-114">Liste tous les projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-114">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="2b3e3-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="2b3e3-115">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="2b3e3-116">Fichier solution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-116">Solution file to use.</span></span> <span data-ttu-id="2b3e3-117">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-117">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="2b3e3-118">S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-118">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="2b3e3-119">Options</span><span class="sxs-lookup"><span data-stu-id="2b3e3-119">Options</span></span>

`-h|--help`

<span data-ttu-id="2b3e3-120">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="2b3e3-120">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="2b3e3-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="2b3e3-121">Examples</span></span>

<span data-ttu-id="2b3e3-122">Ajouter un projet C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="2b3e3-122">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="2b3e3-123">Supprimer un projet C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="2b3e3-123">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="2b3e3-124">Ajouter plusieurs projets C# à une solution :</span><span class="sxs-lookup"><span data-stu-id="2b3e3-124">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="2b3e3-125">Supprimer plusieurs projets C# d’une solution :</span><span class="sxs-lookup"><span data-stu-id="2b3e3-125">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="2b3e3-126">Ajouter plusieurs projets C# à une solution avec un modèle d’utilisation des caractères génériques :</span><span class="sxs-lookup"><span data-stu-id="2b3e3-126">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="2b3e3-127">Supprimer plusieurs projets C# d’une solution avec un modèle d’utilisation des caractères génériques :</span><span class="sxs-lookup"><span data-stu-id="2b3e3-127">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`