---
title: "Guide pratique pour gérer les versions de dépendances de package pour .NET Core 1.0"
description: "Découvrez plus en détails la gestion de version des dépendances de package pour les applications et bibliothèques .NET Core."
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
ms.workload: dotnetcore
ms.openlocfilehash: 2bb55f3bcd6678a127f099afbb9461cafe1a9c94
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="def78-104">Guide pratique pour gérer les versions de dépendances de package pour .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="def78-104">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="def78-105">Cet article décrit ce que vous devez savoir sur les versions de package de vos applications et bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="def78-105">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="def78-106">Glossaire</span><span class="sxs-lookup"><span data-stu-id="def78-106">Glossary</span></span>

<span data-ttu-id="def78-107">**Fixer** : Fixer des dépendances consiste à utiliser la même « famille » de packages publiés sur NuGet pour .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="def78-107">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="def78-108">**Métapackage** : Package NuGet représentant un ensemble de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="def78-108">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="def78-109">**Suppression** : Opération consistant à supprimer d’un métapackage les packages dont vous ne dépendez pas.</span><span class="sxs-lookup"><span data-stu-id="def78-109">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="def78-110">Elle concerne les auteurs de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="def78-110">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="def78-111">Pour plus d’informations, consultez [Réduction des dépendances de package avec project.json](../deploying/reducing-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="def78-111">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="def78-112">Fixer vos dépendances sur .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="def78-112">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="def78-113">Pour restaurer des packages et écrire du code de manière fiable, il est important de fixer les dépendances aux versions de package fournies avec .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="def78-113">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="def78-114">Cela signifie que chaque package doit avoir une seule version sans aucun qualificateur supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="def78-114">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="def78-115">**Exemples de packages fixés sur 1.0**</span><span class="sxs-lookup"><span data-stu-id="def78-115">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="def78-116">**Exemples de packages NON fixés sur 1.0**</span><span class="sxs-lookup"><span data-stu-id="def78-116">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="def78-117">Pourquoi est-ce important ?</span><span class="sxs-lookup"><span data-stu-id="def78-117">Why does this matter?</span></span>

<span data-ttu-id="def78-118">Nous garantissons que, si vous fixez vos dépendances sur celles fournies avec .NET Core 1.0, ces packages fonctionneront ensemble.</span><span class="sxs-lookup"><span data-stu-id="def78-118">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="def78-119">Par contre, nous ne garantissons rien si vous utilisez des packages qui ne sont pas fixés de cette façon.</span><span class="sxs-lookup"><span data-stu-id="def78-119">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="def78-120">Scénarios</span><span class="sxs-lookup"><span data-stu-id="def78-120">Scenarios</span></span>

<span data-ttu-id="def78-121">Bien qu’il existe une longue liste de tous les packages et de leurs versions publiées avec .NET Core 1.0, vous n’avez pas à la parcourir si votre code correspond à certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="def78-121">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="def78-122">**Dépendez-vous uniquement de** `NETStandard.Library`**?**</span><span class="sxs-lookup"><span data-stu-id="def78-122">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="def78-123">Si c’est le cas, vous devez fixer votre package `NETStandard.Library` sur la version `1.6`.</span><span class="sxs-lookup"><span data-stu-id="def78-123">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="def78-124">Comme il s’agit d’un métapackage organisé, sa fermeture de package est également fixée sur 1.0.</span><span class="sxs-lookup"><span data-stu-id="def78-124">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="def78-125">**Dépendez-vous uniquement de** `Microsoft.NETCore.App`**?**</span><span class="sxs-lookup"><span data-stu-id="def78-125">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="def78-126">Si c’est le cas, vous devez fixer votre package `Microsoft.NETCore.App` sur la version `1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="def78-126">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="def78-127">Comme il s’agit d’un métapackage organisé, sa fermeture de package est également fixée sur 1.0.</span><span class="sxs-lookup"><span data-stu-id="def78-127">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="def78-128">**[Supprimez](../deploying/reducing-dependencies.md)-vous vos dépendances de métapackage** `NETStandard.Library` **ou** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="def78-128">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="def78-129">Si c’est le cas, vous devez vérifier que le métapackage avec lequel vous commencez est fixé sur 1.0.</span><span class="sxs-lookup"><span data-stu-id="def78-129">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="def78-130">Les packages individuels desquels vous dépendez après la suppression sont également fixés sur 1.0.</span><span class="sxs-lookup"><span data-stu-id="def78-130">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="def78-131">**Dépendez-vous de packages hors des métapackages** `NETStandard.Library` **ou** `Microsoft.NETCore.App`**?**</span><span class="sxs-lookup"><span data-stu-id="def78-131">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="def78-132">Si c’est le cas, vous devez fixer vos autres dépendances sur 1.0.</span><span class="sxs-lookup"><span data-stu-id="def78-132">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="def78-133">Consultez les versions de package et les numéros de build appropriés à la fin de cet article.</span><span class="sxs-lookup"><span data-stu-id="def78-133">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="def78-134">Remarque sur l’utilisation d’une chaîne se terminant par un astérisque (\\*) lors de la gestion de version</span><span class="sxs-lookup"><span data-stu-id="def78-134">A note on using a splat string (\\*) when versioning</span></span>

<span data-ttu-id="def78-135">Vous avez peut-être adopté un modèle de gestion de version qui utilise une chaîne se terminant par un astérisque (\*) comme la suivante : `"System.Collections":"4.0.11-*"`.</span><span class="sxs-lookup"><span data-stu-id="def78-135">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="def78-136">**Vous ne devez pas procéder ainsi**.</span><span class="sxs-lookup"><span data-stu-id="def78-136">**You should not do this**.</span></span>  <span data-ttu-id="def78-137">L’utilisation de la chaîne se terminant par un astérisque peut entraîner la restauration de packages de différentes builds, dont certaines peuvent être plus avancées que .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="def78-137">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="def78-138">Cela pourrait alors entraîner l’incompatibilité de certains packages.</span><span class="sxs-lookup"><span data-stu-id="def78-138">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="def78-139">Packages et numéros de version organisés par métapackage</span><span class="sxs-lookup"><span data-stu-id="def78-139">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="def78-140">[Liste de tous les packages .NET Standard et de leurs versions pour 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="def78-140">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="def78-141">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt)(Liste de tous les packages d’exécution et leurs versions pour 1.0).</span><span class="sxs-lookup"><span data-stu-id="def78-141">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="def78-142">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt) (Liste de tous les packages d’application .NET Core et leurs versions pour 1.0).</span><span class="sxs-lookup"><span data-stu-id="def78-142">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>
