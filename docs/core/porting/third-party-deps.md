---
title: "Portage sur .NET Core - Analyse de vos dépendances tierces"
description: "Portage sur .NET Core - Analyse de vos dépendances tierces"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a><span data-ttu-id="18b80-104">Portage sur .NET Core - Analyse de vos dépendances tierces</span><span class="sxs-lookup"><span data-stu-id="18b80-104">Porting to .NET Core - Analyzing your Third-Party Party Dependencies</span></span>

<span data-ttu-id="18b80-105">La première étape du processus de portage est de comprendre vos dépendances tierces.</span><span class="sxs-lookup"><span data-stu-id="18b80-105">The first step in the porting process is to understand your third party dependencies.</span></span>  <span data-ttu-id="18b80-106">Vous devez déterminer ceux d’entre eux (s’il y en a) qui ne s’exécutent pas encore sur .NET Core et développer un plan d’urgence pour ceux qui ne s’exécutent pas sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18b80-106">You need to figure out which of them, if any, don't yet run on .NET Core, and develop a contingency plan for those which don't run on .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18b80-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="18b80-107">Prerequisites</span></span>

<span data-ttu-id="18b80-108">Cet article suppose que vous utilisez Windows et Visual Studio, et que vous disposez d’un code qui s’exécute aujourd’hui sur le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18b80-108">This article will assume you are using Windows and Visual Studio, and that you have code which runs on the .NET Framework today.</span></span>

## <a name="analyzing-nuget-packages"></a><span data-ttu-id="18b80-109">Analyse des packages NuGet</span><span class="sxs-lookup"><span data-stu-id="18b80-109">Analyzing NuGet Packages</span></span>

<span data-ttu-id="18b80-110">L’analyse des packages NuGet pour la portabilité est très facile.</span><span class="sxs-lookup"><span data-stu-id="18b80-110">Analyzing NuGet packages for portability is very easy.</span></span>  <span data-ttu-id="18b80-111">Un package NuGet étant lui-même un ensemble de dossiers qui contiennent des assemblys spécifiques à une plateforme, il vous suffit de vérifier s’il existe un dossier qui contient un assembly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18b80-111">Because a NuGet package is itself a set of folders which contain platform-specific assemblies, all you have to do is check to see if there is a folder which contains a .NET Core assembly.</span></span>

<span data-ttu-id="18b80-112">L’examen des dossiers d’un package NuGet est plus facile avec l’outil [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer).</span><span class="sxs-lookup"><span data-stu-id="18b80-112">Inspecting NuGet Package folders is easiest with the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span>  <span data-ttu-id="18b80-113">Voici comment faire.</span><span class="sxs-lookup"><span data-stu-id="18b80-113">Here's how to do it.</span></span>

1. <span data-ttu-id="18b80-114">Téléchargez et ouvrez NuGet Package Explorer.</span><span class="sxs-lookup"><span data-stu-id="18b80-114">Download and open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="18b80-115">Cliquez sur « Open package from online feed ».</span><span class="sxs-lookup"><span data-stu-id="18b80-115">Click "Open package from online feed".</span></span>
3. <span data-ttu-id="18b80-116">Recherchez le nom du package.</span><span class="sxs-lookup"><span data-stu-id="18b80-116">Search for the name of the package.</span></span>
4. <span data-ttu-id="18b80-117">Développez le dossier « lib » du côté droit et examinez les noms de dossier.</span><span class="sxs-lookup"><span data-stu-id="18b80-117">Expand the "lib" folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="18b80-118">Vous pouvez également voir ce qu’un package prend en charge sur [nuget.org](https://www.nuget.org/) sous la section **Dependencies** de la page pour ce package.</span><span class="sxs-lookup"><span data-stu-id="18b80-118">You can also see what a package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the page for that package.</span></span>

<span data-ttu-id="18b80-119">Dans les deux cas, vous devez rechercher un dossier ou une entrée [nuget.org](https://www.nuget.org/) avec un des noms suivants :</span><span class="sxs-lookup"><span data-stu-id="18b80-119">In either case, you'll need to look for a folder or entry on [nuget.org](https://www.nuget.org/) with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="18b80-120">Voici les monikers de la version cible de .NET Framework qui correspondent aux versions de [.NET Standard](../../standard/net-standard.md) et des profils traditionnels de bibliothèques de classes portables compatibles avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18b80-120">These are the Target Framework Monikers (TFM) which map to versions of the [.NET Standard](../../standard/net-standard.md) and traditional Portable Class Library (PCL) profiles which are compatible with .NET Core.</span></span>  <span data-ttu-id="18b80-121">Notez que `netcoreapp1.0`, bien que compatible, est destiné aux applications et non pas aux bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="18b80-121">Note that `netcoreapp1.0`, while compatible, is for applications and not libraries.</span></span>  <span data-ttu-id="18b80-122">Bien que ce ne soit pas un problème d’utiliser une bibliothèque basée sur `netcoreapp1.0`, il est possible que cette bibliothèque ne soit pas destinée à *autre chose* qu’à la consommation par d’autres applications `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="18b80-122">Although there's nothing wrong with using a library which is `netcoreapp1.0`-based, that library may not be intended for anything *other* than consumption by other `netcoreapp1.0` applications.</span></span>

<span data-ttu-id="18b80-123">Il existe également certains monikers du Framework cible hérités utilisés dans des préversions de .NET Core qui peuvent également être compatibles :</span><span class="sxs-lookup"><span data-stu-id="18b80-123">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="18b80-124">**Bien que ceux-ci puissent probablement fonctionner avec votre code, il n’existe aucune garantie de compatibilité**.</span><span class="sxs-lookup"><span data-stu-id="18b80-124">**While these will likely work with your code, there is no guarantee of compatibility**.</span></span>  <span data-ttu-id="18b80-125">Les packages avec ces monikers du Framework cible ont été créés avec des packages .NET Core en préversion.</span><span class="sxs-lookup"><span data-stu-id="18b80-125">Packages with these TFMs were built with pre-release .NET Core packages.</span></span>  <span data-ttu-id="18b80-126">Notez quand (ou si) des packages comme ceci sont mis à jour pour être basés sur `netstandard`.</span><span class="sxs-lookup"><span data-stu-id="18b80-126">Take note of when (or if) packages like this are updated to be `netstandard`-based.</span></span>

> [!NOTE]
> <span data-ttu-id="18b80-127">Pour utiliser un package ciblant une bibliothèque de classes portable traditionnelle ou une cible de .NET Core en préversion, vous devez utiliser la directive `imports` dans votre fichier `project.json`.</span><span class="sxs-lookup"><span data-stu-id="18b80-127">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `imports` directive in your `project.json` file.</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="18b80-128">Ce qu’il faut faire quand votre dépendance de package NuGet ne s’exécute pas sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="18b80-128">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="18b80-129">Voici quelques actions possibles si un package NuGet dont vous dépendez ne s’exécute pas sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18b80-129">There are a few things you can do if a NuGet package you depend on won't run on .NET Core.</span></span>

1. <span data-ttu-id="18b80-130">Si le projet est open source et hébergé à un endroit comme GitHub, vous pouvez demander aux développeurs de le modifier.</span><span class="sxs-lookup"><span data-stu-id="18b80-130">If the project is open source and hosted somewhere like GitHub, you can engage the developer(s) directly.</span></span>
2. <span data-ttu-id="18b80-131">Vous pouvez contacter l’auteur directement sur [nuget.org](https://www.nuget.org/) en recherchant le package et en cliquant sur « Contact Owners » sur le côté gauche de la page du package.</span><span class="sxs-lookup"><span data-stu-id="18b80-131">You can contact the author directly on [nuget.org](https://www.nuget.org/) by searching for the package and clicking "Contact Owners" on the left hand side of the package's page.</span></span>
3. <span data-ttu-id="18b80-132">Vous pouvez rechercher un autre package qui s’exécute sur .NET Core et qui réalise la même tâche que le package que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="18b80-132">You can look for another package that runs on .NET Core which accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="18b80-133">Vous pouvez essayer d’écrire vous-même le code qui était exécuté par le package.</span><span class="sxs-lookup"><span data-stu-id="18b80-133">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="18b80-134">Vous pouvez éliminer la dépendance du package en modifiant les fonctionnalités de votre application, au moins jusqu’à ce qu’une version compatible du package soit disponible.</span><span class="sxs-lookup"><span data-stu-id="18b80-134">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="18b80-135">N’oubliez pas que les personnes qui maintiennent les projets open source et celles qui publient des packages NuGet sont souvent des bénévoles qui apportent leur contribution car elles s’intéressent à un domaine donné, le font gratuitement et ont souvent un autre travail au quotidien.</span><span class="sxs-lookup"><span data-stu-id="18b80-135">Please remember that open source project maintainers and NuGet package publishers are often volunteers who contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="18b80-136">Si vous les contactez, il peut être convenable d’émettre d’abord un avis positif sur la bibliothèque avant de parler d’une prise en charge de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18b80-136">If you do reach out, you might start with a positive statement about the library before asking about .NET Core support.</span></span>

<span data-ttu-id="18b80-137">Si vous ne parvenez pas à résoudre votre problème via une des actions ci-dessus, il peut être nécessaire de porter sur .NET Core à une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="18b80-137">If you're unable to resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="18b80-138">L’équipe .NET aimerait savoir quelles sont les prochaines bibliothèques les plus importantes à prendre en charge avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18b80-138">The .NET Team would like to know which libraries are the most important to support next with .NET Core.</span></span> <span data-ttu-id="18b80-139">Vous pouvez également nous envoyer un e-mail à l’adresse dotnet@microsoft.com sur les bibliothèques que vous voudriez utiliser.</span><span class="sxs-lookup"><span data-stu-id="18b80-139">You can also send us mail at dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a><span data-ttu-id="18b80-140">Analyse des dépendances qui ne sont pas des packages NuGet</span><span class="sxs-lookup"><span data-stu-id="18b80-140">Analyzing Dependencies which aren't NuGet Packages</span></span>

<span data-ttu-id="18b80-141">Vous pouvez avoir une dépendance qui n’est pas un package NuGet, comme une DLL dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="18b80-141">You may have a dependency that isn't a NuGet package, such as a DLL in the filesystem.</span></span>  <span data-ttu-id="18b80-142">La seule façon de déterminer la portabilité de cette dépendance est d’exécuter l’[outil ApiPort](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span><span class="sxs-lookup"><span data-stu-id="18b80-142">The only way to determine the portability of that dependency is to run the [ApiPort tool](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="18b80-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="18b80-143">Next steps</span></span>

<span data-ttu-id="18b80-144">Si vous portez une bibliothèque, consultez [Portage de vos bibliothèques](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="18b80-144">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
