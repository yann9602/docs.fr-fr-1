---
title: Commande dotnet remove reference - Interface CLI .NET Core
description: "La commande dotnet remove reference est une option pratique pour supprimer des références entre projets."
keywords: dotnet-remove, CLI, commande CLI, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 691fd77c7605b6476adc764f20e59b51abd7d914
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="2c657-104">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="2c657-104">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2c657-105">Name</span><span class="sxs-lookup"><span data-stu-id="2c657-105">Name</span></span>

<span data-ttu-id="2c657-106">`dotnet remove reference` - Supprime des références entre projets.</span><span class="sxs-lookup"><span data-stu-id="2c657-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2c657-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="2c657-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="2c657-108">Description</span><span class="sxs-lookup"><span data-stu-id="2c657-108">Description</span></span>

<span data-ttu-id="2c657-109">La commande `dotnet remove reference` est une option pratique pour supprimer des références de projet d’un projet.</span><span class="sxs-lookup"><span data-stu-id="2c657-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="2c657-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="2c657-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="2c657-111">Fichier projet cible.</span><span class="sxs-lookup"><span data-stu-id="2c657-111">Target project file.</span></span> <span data-ttu-id="2c657-112">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="2c657-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="2c657-113">Références entre projets (P2P) à supprimer.</span><span class="sxs-lookup"><span data-stu-id="2c657-113">Project to project (P2P references to remove.</span></span> <span data-ttu-id="2c657-114">Vous pouvez spécifier un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="2c657-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="2c657-115">Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="2c657-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="2c657-116">Options</span><span class="sxs-lookup"><span data-stu-id="2c657-116">Options</span></span>

`-h|--help`

<span data-ttu-id="2c657-117">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="2c657-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2c657-118">Ne supprime une référence que quand [framework](../../standard/frameworks.md) spécifique est ciblé.</span><span class="sxs-lookup"><span data-stu-id="2c657-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="2c657-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="2c657-119">Examples</span></span>

<span data-ttu-id="2c657-120">Supprimer une référence de projet du projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="2c657-120">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="2c657-121">Supprimer plusieurs références de projet du projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="2c657-121">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="2c657-122">Supprimer plusieurs références de projet à l’aide du modèle Glob sous Unix/Linux :</span><span class="sxs-lookup"><span data-stu-id="2c657-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
