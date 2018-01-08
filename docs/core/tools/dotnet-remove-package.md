---
title: Commande dotnet remove package - Interface CLI .NET Core
description: "La commande dotnet remove package est une option pratique pour supprimer une référence de package NuGet d’un projet."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1bc8d9cdc4db1f103b73116b43e630185a2c35de
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="dc79f-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="dc79f-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="dc79f-104">Name</span><span class="sxs-lookup"><span data-stu-id="dc79f-104">Name</span></span>

<span data-ttu-id="dc79f-105">`dotnet remove package` : Supprime une référence de package d’un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="dc79f-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dc79f-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="dc79f-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="dc79f-107">Description</span><span class="sxs-lookup"><span data-stu-id="dc79f-107">Description</span></span>

<span data-ttu-id="dc79f-108">La commande `dotnet remove package` est une option pratique pour supprimer une référence de package NuGet d’un projet.</span><span class="sxs-lookup"><span data-stu-id="dc79f-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="dc79f-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="dc79f-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="dc79f-110">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="dc79f-110">Specifies the project file.</span></span> <span data-ttu-id="dc79f-111">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="dc79f-111">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="dc79f-112">Référence de package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="dc79f-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="dc79f-113">Options</span><span class="sxs-lookup"><span data-stu-id="dc79f-113">Options</span></span>

`-h|--help`

<span data-ttu-id="dc79f-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="dc79f-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="dc79f-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="dc79f-115">Examples</span></span>

<span data-ttu-id="dc79f-116">Supprime le package NuGet `Newtonsoft.Json` d’un projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="dc79f-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
