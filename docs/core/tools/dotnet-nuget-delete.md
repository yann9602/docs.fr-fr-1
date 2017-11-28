---
title: Commande dotnet nuget delete - Interface CLI .NET Core
description: La commande nuget-dotnet-delete supprime ou retire un package du serveur.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 65fe52f07ed823b4f7518c5b1f2da1f7a61b0371
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="c8b06-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="c8b06-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c8b06-104">Nom</span><span class="sxs-lookup"><span data-stu-id="c8b06-104">Name</span></span>

<span data-ttu-id="c8b06-105">`dotnet nuget delete` -Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="c8b06-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8b06-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="c8b06-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="c8b06-107">Description</span><span class="sxs-lookup"><span data-stu-id="c8b06-107">Description</span></span>

<span data-ttu-id="c8b06-108">La commande `dotnet nuget delete` supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="c8b06-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="c8b06-109">Pour [nuget.org](https://www.nuget.org/), l’action consiste à supprimer le package de la liste.</span><span class="sxs-lookup"><span data-stu-id="c8b06-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="c8b06-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="c8b06-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="c8b06-111">Package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c8b06-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="c8b06-112">Version du package à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c8b06-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="c8b06-113">Options</span><span class="sxs-lookup"><span data-stu-id="c8b06-113">Options</span></span>

`-h|--help`

<span data-ttu-id="c8b06-114">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="c8b06-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="c8b06-115">Spécifie l’URL du serveur.</span><span class="sxs-lookup"><span data-stu-id="c8b06-115">Specifies the server URL.</span></span> <span data-ttu-id="c8b06-116">Les URL prises en charge pour nuget.org incluent `http://www.nuget.org`, `http://www.nuget.org/api/v3` et `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="c8b06-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="c8b06-117">Pour les flux privés, remplacez le nom d’hôte (par exemple, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="c8b06-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="c8b06-118">Ne demande pas de saisie ou de confirmation de la part de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c8b06-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="c8b06-119">Clé d’API pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="c8b06-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="c8b06-120">Oblige la sortie de la ligne de commande à être en anglais.</span><span class="sxs-lookup"><span data-stu-id="c8b06-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="c8b06-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="c8b06-121">Examples</span></span>

<span data-ttu-id="c8b06-122">Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` :</span><span class="sxs-lookup"><span data-stu-id="c8b06-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="c8b06-123">Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` sans inviter l’utilisateur à fournir ses informations d’identification ou d’autres données :</span><span class="sxs-lookup"><span data-stu-id="c8b06-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`