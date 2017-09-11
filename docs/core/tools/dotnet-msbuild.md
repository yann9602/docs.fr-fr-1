---
title: Commande dotnet-msbuild - Interface CLI .NET Core
description: "La commande dotnet-msbuild fournit l’accès à la ligne de commande MSbuild."
keywords: dotnet-msmsbuild, CLI, commande CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 05/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1f02dcd779b9ed249ebd2fedb973383b1dcd8963
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-msbuild"></a><span data-ttu-id="79b37-104">dotnet-msbuild</span><span class="sxs-lookup"><span data-stu-id="79b37-104">dotnet-msbuild</span></span>

## <a name="name"></a><span data-ttu-id="79b37-105">Nom</span><span class="sxs-lookup"><span data-stu-id="79b37-105">Name</span></span>

<span data-ttu-id="79b37-106">`dotnet-msbuild` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="79b37-106">`dotnet-msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="79b37-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="79b37-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="79b37-108">Description</span><span class="sxs-lookup"><span data-stu-id="79b37-108">Description</span></span>

<span data-ttu-id="79b37-109">La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="79b37-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="79b37-110">La commande a les mêmes fonctionnalités que le client de ligne de commande MSBuild existant.</span><span class="sxs-lookup"><span data-stu-id="79b37-110">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="79b37-111">Les options sont identiques.</span><span class="sxs-lookup"><span data-stu-id="79b37-111">The options are all the same.</span></span> <span data-ttu-id="79b37-112">Utilisez les [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) pour obtenir des informations sur les options disponibles.</span><span class="sxs-lookup"><span data-stu-id="79b37-112">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="79b37-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="79b37-113">Examples</span></span>

<span data-ttu-id="79b37-114">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="79b37-114">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="79b37-115">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="79b37-115">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="79b37-116">Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :</span><span class="sxs-lookup"><span data-stu-id="79b37-116">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="79b37-117">Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :</span><span class="sxs-lookup"><span data-stu-id="79b37-117">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`

