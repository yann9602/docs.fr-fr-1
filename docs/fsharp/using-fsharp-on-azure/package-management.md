---
title: "À l’aide de la gestion des packages avec F # pour Azure"
description: "Permet de gérer les dépendances de F # Azure Paket ou Nuget"
keywords: 'Visual f #, f #, fonctionnelle de programmation, .NET, .NET Core, Azure'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: 22dc94ea69e0dfb95e22da4bc64ce915398190d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="51f17-104">Gestion des packages pour les dépendances F# Azure</span><span class="sxs-lookup"><span data-stu-id="51f17-104">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="51f17-105">Il est facile d’obtention de packages pour le développement Azure lorsque vous utilisez un gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="51f17-105">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="51f17-106">Les deux options sont [Paket](https://fsprojects.github.io/Paket/) et [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="51f17-106">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="51f17-107">À l’aide de Paket</span><span class="sxs-lookup"><span data-stu-id="51f17-107">Using Paket</span></span>

<span data-ttu-id="51f17-108">Si vous utilisez [Paket](https://fsprojects.github.io/Paket/) comme gestionnaire de dépendance, vous pouvez utiliser la `paket.exe` outil pour ajouter des dépendances Azure.</span><span class="sxs-lookup"><span data-stu-id="51f17-108">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="51f17-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="51f17-109">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="51f17-110">Ou, si vous utilisez [Mono](http://www.mono-project.com/) pour le développement d’inter-plateformes .NET :</span><span class="sxs-lookup"><span data-stu-id="51f17-110">Or, if you're using [Mono](http://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="51f17-111">Cela ajoutera `WindowsAzure.Storage` à votre jeu de dépendances de package pour le projet dans le répertoire actif, vous devez modifier le `paket.dependencies` de fichiers et de télécharger le package.</span><span class="sxs-lookup"><span data-stu-id="51f17-111">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="51f17-112">Si vous avez configuré précédemment des dépendances, ou que vous travaillez avec un projet où les dépendances ont été définis par un autre développeur, vous pouvez résoudre et installer des dépendances localement comme suit :</span><span class="sxs-lookup"><span data-stu-id="51f17-112">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="51f17-113">Ou, pour le développement Mono :</span><span class="sxs-lookup"><span data-stu-id="51f17-113">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="51f17-114">Vous pouvez mettre à jour toutes les dépendances de votre package vers la dernière version à ceci :</span><span class="sxs-lookup"><span data-stu-id="51f17-114">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="51f17-115">Ou, pour le développement Mono :</span><span class="sxs-lookup"><span data-stu-id="51f17-115">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="51f17-116">À l’aide de Nuget</span><span class="sxs-lookup"><span data-stu-id="51f17-116">Using Nuget</span></span>

<span data-ttu-id="51f17-117">Si vous utilisez [NuGet](https://www.nuget.org/) comme gestionnaire de dépendance, vous pouvez utiliser la `nuget.exe` outil pour ajouter des dépendances Azure.</span><span class="sxs-lookup"><span data-stu-id="51f17-117">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="51f17-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="51f17-118">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="51f17-119">Ou, pour le développement Mono :</span><span class="sxs-lookup"><span data-stu-id="51f17-119">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="51f17-120">Cela ajoutera `WindowsAzure.Storage` à votre jeu de dépendances de package pour le projet dans le répertoire actif et téléchargez le package.</span><span class="sxs-lookup"><span data-stu-id="51f17-120">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="51f17-121">Si vous avez configuré précédemment des dépendances, ou que vous travaillez avec un projet où les dépendances ont été définis par un autre développeur, vous pouvez résoudre et installer des dépendances localement comme suit :</span><span class="sxs-lookup"><span data-stu-id="51f17-121">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="51f17-122">Ou, pour le développement Mono :</span><span class="sxs-lookup"><span data-stu-id="51f17-122">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="51f17-123">Vous pouvez mettre à jour toutes les dépendances de votre package vers la dernière version à ceci :</span><span class="sxs-lookup"><span data-stu-id="51f17-123">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="51f17-124">Ou, pour le développement Mono :</span><span class="sxs-lookup"><span data-stu-id="51f17-124">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="51f17-125">Référencement d'assemblys</span><span class="sxs-lookup"><span data-stu-id="51f17-125">Referencing Assemblies</span></span>

<span data-ttu-id="51f17-126">Pour utiliser vos packages dans votre script F #, vous devez référencer les assemblys inclus dans les packages à l’aide un `#r` la directive.</span><span class="sxs-lookup"><span data-stu-id="51f17-126">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="51f17-127">Exemple :</span><span class="sxs-lookup"><span data-stu-id="51f17-127">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="51f17-128">Comme vous pouvez le voir, vous devez spécifier le chemin d’accès relatif à la DLL et le nom complet de la DLL, qui peut ne pas être exactement le même que le nom du package.</span><span class="sxs-lookup"><span data-stu-id="51f17-128">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="51f17-129">Le chemin d’accès inclut une version du framework et éventuellement un numéro de version du package.</span><span class="sxs-lookup"><span data-stu-id="51f17-129">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="51f17-130">Pour rechercher tous les assemblys installés, vous pouvez utiliser quelque chose comme ceci sur une ligne de commande de Windows :</span><span class="sxs-lookup"><span data-stu-id="51f17-130">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="51f17-131">Ou dans un interpréteur de commandes Unix, quelque chose comme ceci :</span><span class="sxs-lookup"><span data-stu-id="51f17-131">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="51f17-132">Cela vous donne les chemins d’accès vers les assemblys installés.</span><span class="sxs-lookup"><span data-stu-id="51f17-132">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="51f17-133">À partir de là, vous pouvez sélectionner le chemin d’accès approprié pour votre version de framework.</span><span class="sxs-lookup"><span data-stu-id="51f17-133">From there, you can select the correct path for your framework version.</span></span>
