---
title: Commande dotnet-list reference - Interface CLI .NET Core
description: "La commande dotnet-list reference est une option pratique pour répertorier des références entre projets."
keywords: dotnet-list, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8f954a0c-03f8-4fbc-a529-b313ab12c623
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 701345e4db51d26b9eefe8f02b6c0526934de5c9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-list-reference"></a><span data-ttu-id="5102e-104">dotnet-list reference</span><span class="sxs-lookup"><span data-stu-id="5102e-104">dotnet-list reference</span></span>

## <a name="name"></a><span data-ttu-id="5102e-105">Nom</span><span class="sxs-lookup"><span data-stu-id="5102e-105">Name</span></span>

<span data-ttu-id="5102e-106">`dotnet-list reference` : Répertorie des références entre projets.</span><span class="sxs-lookup"><span data-stu-id="5102e-106">`dotnet-list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5102e-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="5102e-107">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="5102e-108">Description</span><span class="sxs-lookup"><span data-stu-id="5102e-108">Description</span></span>

<span data-ttu-id="5102e-109">La commande `dotnet list reference` est une option pratique pour répertorier des références de projet pour un projet donné.</span><span class="sxs-lookup"><span data-stu-id="5102e-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="5102e-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="5102e-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="5102e-111">Spécifie le fichier projet à utiliser pour répertorier les références.</span><span class="sxs-lookup"><span data-stu-id="5102e-111">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="5102e-112">Si aucun fichier n’est spécifié, la commande recherche un fichier projet dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="5102e-112">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="5102e-113">Options</span><span class="sxs-lookup"><span data-stu-id="5102e-113">Options</span></span>

`-h|--help`

<span data-ttu-id="5102e-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5102e-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5102e-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="5102e-115">Examples</span></span>

<span data-ttu-id="5102e-116">Lister les références de projet pour le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="5102e-116">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="5102e-117">Lister les références de projet du projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="5102e-117">List the project references for the project in the current directory:</span></span>

`dotnet list reference`

