---
title: "Nouveautés de C# | Guide C#"
description: "Évolution du langage C#"
keywords: "C#, dernières fonctionnalités, nouveautés, Roslyn"
author: BillWagner
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.translationtype: HT
ms.sourcegitcommit: df0438dd742db802bb0f935d840006236d5d9bf9
ms.openlocfilehash: 0a328f62a02aea223340fcc00e839e841041a7d6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/29/2017

---

# <a name="whats-new-in-c"></a><span data-ttu-id="ae668-104">Nouveautés de C#</span><span class="sxs-lookup"><span data-stu-id="ae668-104">What's new in C#</span></span> #

<span data-ttu-id="ae668-105">Cette page fournit un Guide des nouvelles fonctionnalités de chaque version majeure du langage c#.</span><span class="sxs-lookup"><span data-stu-id="ae668-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="ae668-106">Les liens suivants fournissent des informations détaillées sur les principales fonctionnalités ajoutées dans chaque version.</span><span class="sxs-lookup"><span data-stu-id="ae668-106">The links below provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae668-107">Le langage c# s’appuie sur des types et des méthodes présents dans une *bibliothèque standard* pour certaines des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="ae668-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="ae668-108">Par exemple, le traitement des exceptions.</span><span class="sxs-lookup"><span data-stu-id="ae668-108">One example is exception processing.</span></span> <span data-ttu-id="ae668-109">Chaque instruction ou expression`throw` est vérifiée pour s’assurer de l’objet levé est dérivé de @System.Exception.</span><span class="sxs-lookup"><span data-stu-id="ae668-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from @System.Exception.</span></span> <span data-ttu-id="ae668-110">De même, chaque `catch` est vérifié pour assurer que le type intercepté est dérivé de @System.Exception.</span><span class="sxs-lookup"><span data-stu-id="ae668-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from @System.Exception.</span></span> <span data-ttu-id="ae668-111">Chaque version peut ajouter de nouvelles spécifications.</span><span class="sxs-lookup"><span data-stu-id="ae668-111">Each version may add new requirements.</span></span> <span data-ttu-id="ae668-112">Pour utiliser les dernières fonctionnalités de langage dans les environnements plus anciens, vous devrez peut-être installer des bibliothèques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ae668-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="ae668-113">Celles-ci sont décrits dans la page pour chaque version spécifique.</span><span class="sxs-lookup"><span data-stu-id="ae668-113">These are documented in the page for each specific version.</span></span> <span data-ttu-id="ae668-114">Pour en savoir plus, consultez les [relations entre le langage et la bibliothèque](relationships-between-language-and-library.md) pour l’arrière-plan sur cette dépendance.</span><span class="sxs-lookup"><span data-stu-id="ae668-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 

* <span data-ttu-id="ae668-115">[C# 7.1](csharp-7-1.md):</span><span class="sxs-lookup"><span data-stu-id="ae668-115">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="ae668-116">Cette page décrit les dernières fonctionnalités du langage C#.</span><span class="sxs-lookup"><span data-stu-id="ae668-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="ae668-117">Cela concerne C# 7.1, actuellement disponible dans [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/) et dans le kit [SDK .NET Core 2.0](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae668-117">This covers C# 7.1, currently available in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="ae668-118">[C# 7](csharp-7.md) :</span><span class="sxs-lookup"><span data-stu-id="ae668-118">[C# 7](csharp-7.md):</span></span>
    - <span data-ttu-id="ae668-119">Cette page décrit les fonctionnalités ajoutées dans C# 7.</span><span class="sxs-lookup"><span data-stu-id="ae668-119">This page describes the features added in C# 7.</span></span> <span data-ttu-id="ae668-120">Elles ont été ajoutées dans [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) et [.NET Core 1.0](../../core/whats-new/index.md) et ultérieur</span><span class="sxs-lookup"><span data-stu-id="ae668-120">Theses were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="ae668-121">[C# 6](csharp-6.md) :</span><span class="sxs-lookup"><span data-stu-id="ae668-121">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="ae668-122">Cette page décrit les nouvelles fonctionnalités de C# 6.</span><span class="sxs-lookup"><span data-stu-id="ae668-122">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="ae668-123">Ces fonctionnalités sont disponibles dans Visual Studio 2015 pour les développeurs Windows, et dans .NET Core 1.0 pour les développeurs s’intéressant à C# sur Mac OS et Linux.</span><span class="sxs-lookup"><span data-stu-id="ae668-123">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="ae668-124">[Prise en charge multiplateforme](../../core/index.md) :</span><span class="sxs-lookup"><span data-stu-id="ae668-124">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="ae668-125">Grâce à sa prise en charge de .NET Core, C# s’exécute sur plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="ae668-125">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="ae668-126">Si vous voulez essayer C# sur macOS ou sur une des nombreuses distributions Linux prises en charge, découvrez plus d’informations sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae668-126">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="ae668-127">Versions antérieures</span><span class="sxs-lookup"><span data-stu-id="ae668-127">Previous Versions</span></span>
<span data-ttu-id="ae668-128">Les fonctionnalités clés répertoriées ci-dessous ont été introduites dans des versions antérieures du langage C# et de Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="ae668-128">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="ae668-129">Visual Studio .NET 2013 :</span><span class="sxs-lookup"><span data-stu-id="ae668-129">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="ae668-130">Cette version de Visual Studio incluait des correctifs de bogues, des améliorations des performances ainsi que des préversions de la plateforme de compilation .NET (« Roslyn »), aujourd’hui connue sous le nom de .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span><span class="sxs-lookup"><span data-stu-id="ae668-130">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="ae668-131">C# 5, Visual Studio .NET 2012 :</span><span class="sxs-lookup"><span data-stu-id="ae668-131">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="ae668-132">`Async` / `await`, et attributs des [informations sur l’appelant](../programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="ae668-132">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="ae668-133">C# 4, Visual Studio .NET 2010 :</span><span class="sxs-lookup"><span data-stu-id="ae668-133">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="ae668-134">`Dynamic`, [arguments nommés](../programming-guide/classes-and-structs/named-and-optional-arguments.md), paramètres facultatifs, et [covariance et contravariance](../programming-guide/concepts/covariance-contravariance/index.md) génériques.</span><span class="sxs-lookup"><span data-stu-id="ae668-134">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="ae668-135">C# 3, Visual Studio .NET 2008 :</span><span class="sxs-lookup"><span data-stu-id="ae668-135">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="ae668-136">Initialiseurs d’objet et de collection, expressions lambda, méthodes d’extension, types anonymes, propriétés automatiques, inférence de type `var` locale, et [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae668-136">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="ae668-137">C# 2, Visual Studio .NET 2005 :</span><span class="sxs-lookup"><span data-stu-id="ae668-137">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="ae668-138">Méthodes anonymes, génériques, types Nullable, itérateurs/yield, classes `static`, variance et contravariance pour les délégués.</span><span class="sxs-lookup"><span data-stu-id="ae668-138">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="ae668-139">C# 1.1, Visual Studio .NET 2003 :</span><span class="sxs-lookup"><span data-stu-id="ae668-139">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="ae668-140">Pragma `#line` et commentaires de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="ae668-140">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="ae668-141">C# 1, Visual Studio .NET 2002 :</span><span class="sxs-lookup"><span data-stu-id="ae668-141">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="ae668-142">Première version de [C#](../csharp.md).</span><span class="sxs-lookup"><span data-stu-id="ae668-142">The first release of [C#](../csharp.md).</span></span>   

