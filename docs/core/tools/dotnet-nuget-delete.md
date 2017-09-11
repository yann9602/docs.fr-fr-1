---
title: Commande dotnet-nuget-delete - Interface CLI .NET Core
description: La commande nuget-dotnet-delete supprime ou retire un package du serveur.
keywords: dotnet-nuget-delete, CLI, commande CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ce6886f2f4cc8cc633cfc61215fe17550f746c91
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-nuget-delete"></a><span data-ttu-id="e1a66-104">dotnet-nuget delete</span><span class="sxs-lookup"><span data-stu-id="e1a66-104">dotnet-nuget delete</span></span>

## <a name="name"></a><span data-ttu-id="e1a66-105">Nom</span><span class="sxs-lookup"><span data-stu-id="e1a66-105">Name</span></span>

<span data-ttu-id="e1a66-106">`dotnet-nuget-delete` -Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="e1a66-106">`dotnet-nuget-delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e1a66-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="e1a66-107">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="e1a66-108">Description</span><span class="sxs-lookup"><span data-stu-id="e1a66-108">Description</span></span>

<span data-ttu-id="e1a66-109">La commande `dotnet nuget delete` supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="e1a66-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="e1a66-110">Pour [nuget.org](https://www.nuget.org/), l’action consiste à supprimer le package de la liste.</span><span class="sxs-lookup"><span data-stu-id="e1a66-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="e1a66-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="e1a66-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="e1a66-112">Package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="e1a66-112">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="e1a66-113">Version du package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="e1a66-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="e1a66-114">Options</span><span class="sxs-lookup"><span data-stu-id="e1a66-114">Options</span></span>

`-h|--help`

<span data-ttu-id="e1a66-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="e1a66-115">Prints out a short help for the command.</span></span>  

`-s|--source <SOURCE>`

<span data-ttu-id="e1a66-116">Spécifie l’URL du serveur.</span><span class="sxs-lookup"><span data-stu-id="e1a66-116">Specifies the server URL.</span></span> <span data-ttu-id="e1a66-117">Les URL prises en charge pour nuget.org incluent `http://www.nuget.org`, `http://www.nuget.org/api/v3` et `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="e1a66-117">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="e1a66-118">Pour les flux privés, remplacez le nom d’hôte (par exemple, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="e1a66-118">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="e1a66-119">Ne demande pas de saisie ou de confirmation de la part de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e1a66-119">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="e1a66-120">Clé d’API pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="e1a66-120">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="e1a66-121">Oblige la sortie de la ligne de commande à être en anglais.</span><span class="sxs-lookup"><span data-stu-id="e1a66-121">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="e1a66-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="e1a66-122">Examples</span></span>

<span data-ttu-id="e1a66-123">Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` :</span><span class="sxs-lookup"><span data-stu-id="e1a66-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="e1a66-124">Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` sans inviter l’utilisateur à fournir ses informations d’identification ou d’autres données :</span><span class="sxs-lookup"><span data-stu-id="e1a66-124">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`

