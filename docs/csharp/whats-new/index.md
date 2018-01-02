---
title: "Nouveautés de C# | Guide C#"
description: "Évolution du langage C#"
keywords: "C#, dernières fonctionnalités, nouveautés, Roslyn"
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 719fbe826b0b115b19067dbaf0d04f14e6534890
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="whats-new-in-c"></a><span data-ttu-id="2fbe1-104">Nouveautés de C#</span><span class="sxs-lookup"><span data-stu-id="2fbe1-104">What's new in C#</span></span> #

<span data-ttu-id="2fbe1-105">Cette page fournit un Guide des nouvelles fonctionnalités de chaque version majeure du langage c#.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="2fbe1-106">Les liens suivants fournissent des informations détaillées sur les principales fonctionnalités ajoutées dans chaque version.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-106">The following links provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2fbe1-107">Le langage c# s’appuie sur des types et des méthodes présents dans une *bibliothèque standard* pour certaines des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="2fbe1-108">Par exemple, le traitement des exceptions.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-108">One example is exception processing.</span></span> <span data-ttu-id="2fbe1-109">Chaque instruction ou expression`throw` est vérifiée pour s’assurer de l’objet levé est dérivé de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="2fbe1-110">De même, chaque `catch` est vérifié pour assurer que le type intercepté est dérivé de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="2fbe1-111">Chaque version peut ajouter de nouvelles spécifications.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-111">Each version may add new requirements.</span></span> <span data-ttu-id="2fbe1-112">Pour utiliser les dernières fonctionnalités de langage dans les environnements plus anciens, vous devrez peut-être installer des bibliothèques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="2fbe1-113">Ces dépendances sont décrites dans la page pour chaque version spécifique.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-113">These dependencies are documented in the page for each specific version.</span></span> <span data-ttu-id="2fbe1-114">Pour en savoir plus, consultez les [relations entre le langage et la bibliothèque](relationships-between-language-and-library.md) pour l’arrière-plan sur cette dépendance.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 


* <span data-ttu-id="2fbe1-115">[C# 7.2](csharp-7-2.md) :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-115">[C# 7.2](csharp-7-2.md):</span></span>
    - <span data-ttu-id="2fbe1-116">Cette page décrit les dernières fonctionnalités du langage C#.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="2fbe1-117">C# 7.2 est actuellement disponible dans [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/) et dans le kit [SDK .NET Core 2.0](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="2fbe1-117">C# 7.2 is currently available in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="2fbe1-118">[C# 7.1](csharp-7-1.md):</span><span class="sxs-lookup"><span data-stu-id="2fbe1-118">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="2fbe1-119">Cette page décrit les fonctionnalités dans C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-119">This page describes the features in C# 7.1.</span></span> <span data-ttu-id="2fbe1-120">Ces fonctionnalités ont été ajoutées dans [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/) et dans le kit [SDK .NET Core 2.0](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="2fbe1-120">These features were added in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="2fbe1-121">[C# 7](csharp-7.md) :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-121">[C# 7](csharp-7.md):</span></span>
    - <span data-ttu-id="2fbe1-122">Cette page décrit les fonctionnalités ajoutées dans C# 7.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-122">This page describes the features added in C# 7.</span></span> <span data-ttu-id="2fbe1-123">Ces fonctionnalités ont été ajoutées dans [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) et [.NET Core 1.0](../../core/whats-new/index.md) et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="2fbe1-123">These features were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="2fbe1-124">[C# 6](csharp-6.md) :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-124">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="2fbe1-125">Cette page décrit les nouvelles fonctionnalités de C# 6.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-125">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="2fbe1-126">Ces fonctionnalités sont disponibles dans Visual Studio 2015 pour les développeurs Windows, et dans .NET Core 1.0 pour les développeurs s’intéressant à C# sur Mac OS et Linux.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-126">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="2fbe1-127">[Prise en charge multiplateforme](../../core/index.md) :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-127">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="2fbe1-128">Grâce à sa prise en charge de .NET Core, C# s’exécute sur plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-128">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="2fbe1-129">Si vous voulez essayer C# sur macOS ou sur une des nombreuses distributions Linux prises en charge, découvrez plus d’informations sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-129">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="2fbe1-130">Versions antérieures</span><span class="sxs-lookup"><span data-stu-id="2fbe1-130">Previous Versions</span></span>
<span data-ttu-id="2fbe1-131">Les fonctionnalités clés répertoriées ci-dessous ont été introduites dans des versions antérieures du langage C# et de Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-131">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="2fbe1-132">Visual Studio .NET 2013 :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-132">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="2fbe1-133">Cette version de Visual Studio incluait des correctifs de bogues, des améliorations des performances ainsi que des préversions de la plateforme de compilation .NET (« Roslyn »), aujourd’hui connue sous le nom de .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-133">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="2fbe1-134">C# 5, Visual Studio .NET 2012 :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-134">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="2fbe1-135">`Async` / `await`, et attributs des [informations sur l’appelant](../programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="2fbe1-135">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="2fbe1-136">C# 4, Visual Studio .NET 2010 :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-136">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="2fbe1-137">`Dynamic`, [arguments nommés](../programming-guide/classes-and-structs/named-and-optional-arguments.md), paramètres facultatifs, et [covariance et contravariance](../programming-guide/concepts/covariance-contravariance/index.md) génériques.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-137">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="2fbe1-138">C# 3, Visual Studio .NET 2008 :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-138">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="2fbe1-139">Initialiseurs d’objet et de collection, expressions lambda, méthodes d’extension, types anonymes, propriétés automatiques, inférence de type `var` locale, et [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="2fbe1-139">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="2fbe1-140">C# 2, Visual Studio .NET 2005 :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-140">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="2fbe1-141">Méthodes anonymes, génériques, types Nullable, itérateurs/yield, classes `static`, variance et contravariance pour les délégués.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-141">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="2fbe1-142">C# 1.1, Visual Studio .NET 2003 :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-142">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="2fbe1-143">Pragma `#line` et commentaires de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="2fbe1-143">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="2fbe1-144">C# 1, Visual Studio .NET 2002 :</span><span class="sxs-lookup"><span data-stu-id="2fbe1-144">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="2fbe1-145">Première version de [C#](../csharp.md).</span><span class="sxs-lookup"><span data-stu-id="2fbe1-145">The first release of [C#](../csharp.md).</span></span>   
