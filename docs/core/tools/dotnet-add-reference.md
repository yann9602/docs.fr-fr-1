---
title: Commande dotnet-add reference - Interface CLI .NET Core
description: "La commande dotnet-add reference est une option pratique pour ajouter des références entre projets."
keywords: dotnet-add, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e2a3efd-443c-4f23-a1b1-a662a5387879
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 98491efc183ad62f47275d0832a32dde5899373d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-add-reference"></a><span data-ttu-id="dae8d-104">dotnet-add reference</span><span class="sxs-lookup"><span data-stu-id="dae8d-104">dotnet-add reference</span></span>

## <a name="name"></a><span data-ttu-id="dae8d-105">Nom</span><span class="sxs-lookup"><span data-stu-id="dae8d-105">Name</span></span>

<span data-ttu-id="dae8d-106">`dotnet-add reference` : ajoute des références entre projets (P2P).</span><span class="sxs-lookup"><span data-stu-id="dae8d-106">`dotnet-add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dae8d-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="dae8d-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="dae8d-108">Description</span><span class="sxs-lookup"><span data-stu-id="dae8d-108">Description</span></span>

<span data-ttu-id="dae8d-109">La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet.</span><span class="sxs-lookup"><span data-stu-id="dae8d-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="dae8d-110">Une fois que vous avez exécuté la commande, les éléments [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) sont ajoutés au fichier projet.</span><span class="sxs-lookup"><span data-stu-id="dae8d-110">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="dae8d-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="dae8d-111">Arguments</span></span>

`PROJECT`

<span data-ttu-id="dae8d-112">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="dae8d-112">Specifies the project file.</span></span> <span data-ttu-id="dae8d-113">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="dae8d-113">If not specified, the command will search the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="dae8d-114">Références entre projets (P2P) à ajouter.</span><span class="sxs-lookup"><span data-stu-id="dae8d-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="dae8d-115">Spécifiez un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="dae8d-115">Specify one or more projects.</span></span> <span data-ttu-id="dae8d-116">Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les systèmes Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="dae8d-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="dae8d-117">Options</span><span class="sxs-lookup"><span data-stu-id="dae8d-117">Options</span></span>

`-h|--help`

<span data-ttu-id="dae8d-118">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="dae8d-118">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="dae8d-119">Ajoute des références de projet uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="dae8d-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="dae8d-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="dae8d-120">Examples</span></span>

<span data-ttu-id="dae8d-121">Ajouter une référence de projet :</span><span class="sxs-lookup"><span data-stu-id="dae8d-121">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="dae8d-122">Ajouter plusieurs références de projet :</span><span class="sxs-lookup"><span data-stu-id="dae8d-122">Add multiple project references:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="dae8d-123">Ajouter plusieurs références de projet à l’aide du modèle d’utilisation des caractères génériques (globbing) sur Linux/Unix :</span><span class="sxs-lookup"><span data-stu-id="dae8d-123">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`

