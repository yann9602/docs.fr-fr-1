---
title: Commande dotnet-remove package - Interface CLI .NET Core
description: "La commande dotnet-remove package est une option pratique pour supprimer une référence de package NuGet d’un projet."
keywords: dotnet-remove, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2fcc8d37-16b3-4581-8038-832160e72d36
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a3fef846d5850e2c2a158ccd1f30a84e8f23f793
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-remove-package"></a><span data-ttu-id="5a451-104">dotnet-remove package</span><span class="sxs-lookup"><span data-stu-id="5a451-104">dotnet-remove package</span></span>

## <a name="name"></a><span data-ttu-id="5a451-105">Nom</span><span class="sxs-lookup"><span data-stu-id="5a451-105">Name</span></span>

<span data-ttu-id="5a451-106">`dotnet-remove package` : Supprime une référence de package d’un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="5a451-106">`dotnet-remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5a451-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="5a451-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="5a451-108">Description</span><span class="sxs-lookup"><span data-stu-id="5a451-108">Description</span></span>

<span data-ttu-id="5a451-109">La commande `dotnet remove package` est une option pratique pour supprimer une référence de package NuGet d’un projet.</span><span class="sxs-lookup"><span data-stu-id="5a451-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="5a451-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="5a451-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="5a451-111">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="5a451-111">Specifies the project file.</span></span> <span data-ttu-id="5a451-112">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="5a451-112">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5a451-113">Référence de package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="5a451-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="5a451-114">Options</span><span class="sxs-lookup"><span data-stu-id="5a451-114">Options</span></span>

`-h|--help`

<span data-ttu-id="5a451-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5a451-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5a451-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="5a451-116">Examples</span></span>

<span data-ttu-id="5a451-117">Supprime le package NuGet `Newtonsoft.Json` d’un projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="5a451-117">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`

