---
title: Commande dotnet msbuild - Interface CLI .NET Core
description: "La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 96e4eac528abad2b336a979a98c9be2bee5d17ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="b6775-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b6775-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b6775-104">Nom</span><span class="sxs-lookup"><span data-stu-id="b6775-104">Name</span></span>

<span data-ttu-id="b6775-105">`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="b6775-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b6775-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="b6775-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="b6775-107">Description</span><span class="sxs-lookup"><span data-stu-id="b6775-107">Description</span></span>

<span data-ttu-id="b6775-108">La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="b6775-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="b6775-109">La commande a les mêmes fonctionnalités que le client de ligne de commande MSBuild existant.</span><span class="sxs-lookup"><span data-stu-id="b6775-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="b6775-110">Les options sont identiques.</span><span class="sxs-lookup"><span data-stu-id="b6775-110">The options are all the same.</span></span> <span data-ttu-id="b6775-111">Utilisez les [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) pour obtenir des informations sur les options disponibles.</span><span class="sxs-lookup"><span data-stu-id="b6775-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="b6775-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="b6775-112">Examples</span></span>

<span data-ttu-id="b6775-113">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="b6775-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="b6775-114">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="b6775-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="b6775-115">Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :</span><span class="sxs-lookup"><span data-stu-id="b6775-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="b6775-116">Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :</span><span class="sxs-lookup"><span data-stu-id="b6775-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
