---
title: "Réduction des dépendances de package avec project.json"
description: "Réduisez les dépendances de package dans le cadre de la création de bibliothèques project.json."
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 916251e3-87f9-4eee-81ec-94076215e6fa
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 23d83f0402e35bc4bed31ef59a6fff0e28e01d35
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="22f2d-104">Réduction des dépendances de package avec project.json</span><span class="sxs-lookup"><span data-stu-id="22f2d-104">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="22f2d-105">Cet article décrit ce que vous devez savoir sur la réduction de vos dépendances de package lors de la création de bibliothèques `project.json`.</span><span class="sxs-lookup"><span data-stu-id="22f2d-105">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="22f2d-106">À la fin de cet article, vous saurez comment composer votre bibliothèque de sorte qu’elle utilise seulement les dépendances dont elle a besoin.</span><span class="sxs-lookup"><span data-stu-id="22f2d-106">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="22f2d-107">Pourquoi c’est important</span><span class="sxs-lookup"><span data-stu-id="22f2d-107">Why it's Important</span></span>

<span data-ttu-id="22f2d-108">.NET Core est un produit composé de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="22f2d-108">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="22f2d-109">Parmi les packages essentiels figure le [métapackage .NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), un package NuGet composé d’autres packages.</span><span class="sxs-lookup"><span data-stu-id="22f2d-109">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="22f2d-110">Il vous fournit l’ensemble des packages dont le fonctionnement est garanti sur plusieurs implémentations de .NET, comme le .NET Framework, .NET Core et Xamarin/Mono.</span><span class="sxs-lookup"><span data-stu-id="22f2d-110">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="22f2d-111">Cependant, il est probable que votre bibliothèque n’utilise pas chaque package individuel qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="22f2d-111">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="22f2d-112">Lors de la création d’une bibliothèque et de sa distribution sur NuGet, il est conseillé de « réduire » vos dépendances aux seuls packages que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="22f2d-112">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="22f2d-113">Ceci aboutit à un encombrement global inférieur pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="22f2d-113">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="22f2d-114">Comment faire</span><span class="sxs-lookup"><span data-stu-id="22f2d-114">How to do it</span></span>

<span data-ttu-id="22f2d-115">Il n’existe actuellement aucune commande `dotnet` officielle qui réduit les références de package.</span><span class="sxs-lookup"><span data-stu-id="22f2d-115">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="22f2d-116">Vous devez donc le faire manuellement.</span><span class="sxs-lookup"><span data-stu-id="22f2d-116">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="22f2d-117">Le processus général se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="22f2d-117">The general process looks like the following:</span></span>

1. <span data-ttu-id="22f2d-118">Faites référence à `NETStandard.Library` version `1.6.0` dans une section `dependencies` de votre fichier `project.json`.</span><span class="sxs-lookup"><span data-stu-id="22f2d-118">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="22f2d-119">Restaurer les packages avec `dotnet restore` à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="22f2d-119">Restore packages with `dotnet restore` from the command line.</span></span>
3. <span data-ttu-id="22f2d-120">Parcourez le fichier `project.lock.json` et recherchez la section `NETSTandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="22f2d-120">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="22f2d-121">Elle est au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="22f2d-121">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="22f2d-122">Copiez tous les packages répertoriés sous `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="22f2d-122">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="22f2d-123">Supprimez la référence à `.NETStandard.Library` et remplacez-la par les packages copiés.</span><span class="sxs-lookup"><span data-stu-id="22f2d-123">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="22f2d-124">Supprimez les références aux packages dont vous n’avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="22f2d-124">Remove references to packages you don't need.</span></span>

<span data-ttu-id="22f2d-125">Vous pouvez déterminer les packages dont vous n’avez pas besoin de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="22f2d-125">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="22f2d-126">Essai et erreur.</span><span class="sxs-lookup"><span data-stu-id="22f2d-126">Trial and error.</span></span>  <span data-ttu-id="22f2d-127">Ceci implique de supprimer un package, de le restaurer, de déterminer si votre bibliothèque se compile encore et de répéter ce processus.</span><span class="sxs-lookup"><span data-stu-id="22f2d-127">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="22f2d-128">L’utilisation d’un outil comme [ILSpy](http://ilspy.net) ou [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) permet d’examiner les références pour voir ce que votre code utilise réellement.</span><span class="sxs-lookup"><span data-stu-id="22f2d-128">Using a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="22f2d-129">Vous pouvez ensuite supprimer les packages qui ne correspondent pas aux types que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="22f2d-129">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="22f2d-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="22f2d-130">Example</span></span> 

<span data-ttu-id="22f2d-131">Imaginez que vous avez écrit une bibliothèque qui fournit des fonctionnalités supplémentaires pour les types de collections génériques.</span><span class="sxs-lookup"><span data-stu-id="22f2d-131">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="22f2d-132">Ce type de bibliothèque doit dépendre de packages comme `System.Collections`, mais peut ne pas du tout dépendre de packages comme `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="22f2d-132">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="22f2d-133">Par conséquent, il serait judicieux de réduire les dépendances des packages aux seuls packages dont cette bibliothèque a besoin !</span><span class="sxs-lookup"><span data-stu-id="22f2d-133">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="22f2d-134">Pour réduire cette bibliothèque, vous commencez par le fichier `project.json` et vous ajoutez une référence à `NETStandard.Library` version `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="22f2d-134">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="22f2d-135">Ensuite, vous restaurez les packages avec `dotnet restore`, vous examinez le fichier `project.lock.json` et vous recherchez tous les packages restaurés pour `NETSTandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="22f2d-135">Next, you restore packages with `dotnet restore`, inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="22f2d-136">Voici à quoi ressemble la section appropriée du fichier `project.lock.json` quand vous ciblez `netstandard1.0` :</span><span class="sxs-lookup"><span data-stu-id="22f2d-136">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

<span data-ttu-id="22f2d-137">Ensuite, copiez les références de package dans la section `dependencies` du fichier `project.json` de la bibliothèque, en remplaçant la référence `NETStandard.Library` :</span><span class="sxs-lookup"><span data-stu-id="22f2d-137">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

<span data-ttu-id="22f2d-138">Ceci représente beaucoup de packages, dont un grand nombre ne sont certainement pas nécessaires pour étendre les types de collections.</span><span class="sxs-lookup"><span data-stu-id="22f2d-138">That's quite a lot of packages, many of which which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="22f2d-139">Vous pouvez supprimer manuellement les packages ou utiliser un outil comme [ILSpy](http://ilspy.net) ou [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) pour identifier les packages utilisés par votre code.</span><span class="sxs-lookup"><span data-stu-id="22f2d-139">You can either remove packages manually or use a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="22f2d-140">Voici ce à quoi un package réduit peut ressembler :</span><span class="sxs-lookup"><span data-stu-id="22f2d-140">Here's what a trimmed package could look like:</span></span>

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="22f2d-141">Il a maintenant un encombrement moindre que s’il dépendait du métapackage `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="22f2d-141">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

