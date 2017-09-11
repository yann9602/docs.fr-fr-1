---
title: Commande dotnet-nuget-locals - Interface CLI .NET Core
description: "La commande dotnet-nuget-locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur."
keywords: dotnet-nuget-locals, CLI, commande CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2c9ea7b3b7c61b347cb7c56254773290f04a0cd6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-nuget-locals"></a><span data-ttu-id="33dce-104">dotnet-nuget locals</span><span class="sxs-lookup"><span data-stu-id="33dce-104">dotnet-nuget locals</span></span>

## <a name="name"></a><span data-ttu-id="33dce-105">Nom</span><span class="sxs-lookup"><span data-stu-id="33dce-105">Name</span></span>

<span data-ttu-id="33dce-106">`dotnet-nuget locals` - Efface ou liste les ressources NuGet locales.</span><span class="sxs-lookup"><span data-stu-id="33dce-106">`dotnet-nuget locals` - Clears or lists local NuGet resources.</span></span> 

## <a name="synopsis"></a><span data-ttu-id="33dce-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="33dce-107">Synopsis</span></span>

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="33dce-108">Description</span><span class="sxs-lookup"><span data-stu-id="33dce-108">Description</span></span>

<span data-ttu-id="33dce-109">La commande `dotnet nuget locals` efface ou liste les ressources NuGet locales dans le cache de requête HTTP, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="33dce-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="33dce-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="33dce-110">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="33dce-111">Une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="33dce-111">One of the following values:</span></span>

`all`

<span data-ttu-id="33dce-112">Indique que l’opération spécifiée est appliquée à tous les types de cache : le cache de requête HTTP, le cache des packages globaux et le cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="33dce-112">Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>

`http-cache`

<span data-ttu-id="33dce-113">Indique que l’opération spécifiée est appliquée uniquement au cache de requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="33dce-113">Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="33dce-114">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="33dce-114">The other cache locations are not affected.</span></span>

`global-packages`

<span data-ttu-id="33dce-115">Indique que l’opération spécifiée est appliquée uniquement au cache des packages globaux.</span><span class="sxs-lookup"><span data-stu-id="33dce-115">Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="33dce-116">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="33dce-116">The other cache locations are not affected.</span></span>

`temp`

<span data-ttu-id="33dce-117">Indique que l’opération spécifiée est appliquée uniquement au cache temporaire.</span><span class="sxs-lookup"><span data-stu-id="33dce-117">Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="33dce-118">Les autres emplacements de cache ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="33dce-118">The other cache locations are not affected.</span></span>

## <a name="options"></a><span data-ttu-id="33dce-119">Options</span><span class="sxs-lookup"><span data-stu-id="33dce-119">Options</span></span>

`-h|--help`

<span data-ttu-id="33dce-120">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="33dce-120">Prints out a short help for the command.</span></span>  

`-c|--clear`

<span data-ttu-id="33dce-121">L’option clear effectue une opération d’effacement sur le type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="33dce-121">The clear option performs a clear operation on the specified cache type.</span></span> <span data-ttu-id="33dce-122">Le contenu des répertoires de cache est supprimé de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="33dce-122">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="33dce-123">Le groupe ou l’utilisateur qui effectue l’opération doit disposer de droits sur les fichiers des répertoires de cache.</span><span class="sxs-lookup"><span data-stu-id="33dce-123">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="33dce-124">Sinon, une erreur s’affiche, indiquant les fichiers ou dossiers qui n’ont pas été effacés.</span><span class="sxs-lookup"><span data-stu-id="33dce-124">If not, an error is displayed indicating the files/folders which were not cleared.</span></span>

`-l|--list`

<span data-ttu-id="33dce-125">L’option list est utilisée pour afficher l’emplacement du type de cache spécifié.</span><span class="sxs-lookup"><span data-stu-id="33dce-125">The list option is used to display the location of the specified cache type.</span></span> 

`--force-english-output`

<span data-ttu-id="33dce-126">Oblige la sortie de la ligne de commande à être en anglais.</span><span class="sxs-lookup"><span data-stu-id="33dce-126">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="33dce-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="33dce-127">Examples</span></span>

<span data-ttu-id="33dce-128">Afficher les chemins d’accès de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="33dce-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="33dce-129">Affiche le chemin du répertoire du cache http local :</span><span class="sxs-lookup"><span data-stu-id="33dce-129">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="33dce-130">Effacer tous les fichiers de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :</span><span class="sxs-lookup"><span data-stu-id="33dce-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="33dce-131">Effacer tous les fichiers du répertoire du cache des packages globaux local :</span><span class="sxs-lookup"><span data-stu-id="33dce-131">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="33dce-132">Effacer tous les fichiers du répertoire du cache temporaire local :</span><span class="sxs-lookup"><span data-stu-id="33dce-132">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="33dce-133">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="33dce-133">Troubleshooting</span></span>

<span data-ttu-id="33dce-134">Pour plus d’informations sur les problèmes et erreurs courants liés à l’utilisation de la commande `dotnet nuget locals`, consultez la page [Gestion du cache NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="33dce-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>

