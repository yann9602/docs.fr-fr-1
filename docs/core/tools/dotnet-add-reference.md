---
title: Commande dotnet-add reference - Interface CLI .NET Core
description: "La commande dotnet add reference est une option pratique pour ajouter des références entre projets."
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 9a79468168979a7c89efe48e11175f926e39cf4f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="a7bfb-103">dotnet-add reference</span><span class="sxs-lookup"><span data-stu-id="a7bfb-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a7bfb-104">Name</span><span class="sxs-lookup"><span data-stu-id="a7bfb-104">Name</span></span>

<span data-ttu-id="a7bfb-105">`dotnet add reference` : ajoute des références entre projets (P2P).</span><span class="sxs-lookup"><span data-stu-id="a7bfb-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7bfb-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="a7bfb-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="a7bfb-107">Description</span><span class="sxs-lookup"><span data-stu-id="a7bfb-107">Description</span></span>

<span data-ttu-id="a7bfb-108">La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="a7bfb-109">Une fois que vous avez exécuté la commande, les éléments [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) sont ajoutés au fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="a7bfb-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="a7bfb-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a7bfb-111">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-111">Specifies the project file.</span></span> <span data-ttu-id="a7bfb-112">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="a7bfb-113">Références entre projets (P2P) à ajouter.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="a7bfb-114">Spécifiez un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-114">Specify one or more projects.</span></span> <span data-ttu-id="a7bfb-115">Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les systèmes Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="a7bfb-116">Options</span><span class="sxs-lookup"><span data-stu-id="a7bfb-116">Options</span></span>

`-h|--help`

<span data-ttu-id="a7bfb-117">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a7bfb-118">Ajoute des références de projet uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="a7bfb-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="a7bfb-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="a7bfb-119">Examples</span></span>

<span data-ttu-id="a7bfb-120">Ajouter une référence de projet :</span><span class="sxs-lookup"><span data-stu-id="a7bfb-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="a7bfb-121">Ajouter plusieurs références de projet au projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="a7bfb-121">Add multiple project references to the project in the current directory:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="a7bfb-122">Ajouter plusieurs références de projet à l’aide du modèle d’utilisation des caractères génériques (globbing) sur Linux/Unix :</span><span class="sxs-lookup"><span data-stu-id="a7bfb-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`
