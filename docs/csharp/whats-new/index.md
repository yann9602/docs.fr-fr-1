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
ms.sourcegitcommit: 195b2206eec0a8f070454aed1ddefe56ee92adc9
ms.openlocfilehash: 7b7cb235e2ba5bc3c9a21603058eb20475766ea7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/15/2017

---

# <a name="whats-new-in-c"></a><span data-ttu-id="ab777-104">Nouveautés de C#</span><span class="sxs-lookup"><span data-stu-id="ab777-104">What's new in C#</span></span> #

<span data-ttu-id="ab777-105">Cette page fournit un Guide des nouvelles fonctionnalités de chaque version majeure du langage c#.</span><span class="sxs-lookup"><span data-stu-id="ab777-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="ab777-106">Les liens suivants fournissent des informations détaillées sur les principales fonctionnalités ajoutées dans chaque version.</span><span class="sxs-lookup"><span data-stu-id="ab777-106">The links below provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab777-107">Le langage c# s’appuie sur des types et des méthodes présents dans une *bibliothèque standard* pour certaines des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="ab777-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="ab777-108">Par exemple, le traitement des exceptions.</span><span class="sxs-lookup"><span data-stu-id="ab777-108">One example is exception processing.</span></span> <span data-ttu-id="ab777-109">Chaque instruction ou expression`throw` est vérifiée pour s’assurer de l’objet levé est dérivé de @System.Exception.</span><span class="sxs-lookup"><span data-stu-id="ab777-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from @System.Exception.</span></span> <span data-ttu-id="ab777-110">De même, chaque `catch` est vérifié pour assurer que le type intercepté est dérivé de @System.Exception.</span><span class="sxs-lookup"><span data-stu-id="ab777-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from @System.Exception.</span></span> <span data-ttu-id="ab777-111">Chaque version peut ajouter de nouvelles spécifications.</span><span class="sxs-lookup"><span data-stu-id="ab777-111">Each version may add new requirements.</span></span> <span data-ttu-id="ab777-112">Pour utiliser les dernières fonctionnalités de langage dans les environnements plus anciens, vous devrez peut-être installer des bibliothèques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ab777-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="ab777-113">Celles-ci sont décrits dans la page pour chaque version spécifique.</span><span class="sxs-lookup"><span data-stu-id="ab777-113">These are documented in the page for each specific version.</span></span> <span data-ttu-id="ab777-114">Pour en savoir plus, consultez les [relations entre le langage et la bibliothèque](relationships-between-language-and-library.md) pour l’arrière-plan sur cette dépendance.</span><span class="sxs-lookup"><span data-stu-id="ab777-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 

* <span data-ttu-id="ab777-115">[C# 7](csharp-7.md) :</span><span class="sxs-lookup"><span data-stu-id="ab777-115">[C# 7](csharp-7.md):</span></span>
    - <span data-ttu-id="ab777-116">Cette page décrit les dernières fonctionnalités du langage C#.</span><span class="sxs-lookup"><span data-stu-id="ab777-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="ab777-117">Cela concerne C# 7, actuellement disponible dans [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/).</span><span class="sxs-lookup"><span data-stu-id="ab777-117">This covers C# 7, currently available in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/).</span></span>

* <span data-ttu-id="ab777-118">[C# 6](csharp-6.md) :</span><span class="sxs-lookup"><span data-stu-id="ab777-118">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="ab777-119">Cette page décrit les nouvelles fonctionnalités de C# 6.</span><span class="sxs-lookup"><span data-stu-id="ab777-119">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="ab777-120">Ces fonctionnalités sont disponibles dans Visual Studio 2015 pour les développeurs Windows, et dans .NET Core 1.0 pour les développeurs s’intéressant à C# sur Mac OS et Linux.</span><span class="sxs-lookup"><span data-stu-id="ab777-120">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="ab777-121">[Prise en charge multiplateforme](../../core/index.md) :</span><span class="sxs-lookup"><span data-stu-id="ab777-121">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="ab777-122">Grâce à sa prise en charge de .NET Core, C# s’exécute sur plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="ab777-122">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="ab777-123">Si vous voulez essayer C# sur macOS ou sur une des nombreuses distributions Linux prises en charge, découvrez plus d’informations sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab777-123">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="ab777-124">Versions antérieures</span><span class="sxs-lookup"><span data-stu-id="ab777-124">Previous Versions</span></span>
<span data-ttu-id="ab777-125">Les fonctionnalités clés répertoriées ci-dessous ont été introduites dans des versions antérieures du langage C# et de Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="ab777-125">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="ab777-126">Visual Studio .NET 2013 :</span><span class="sxs-lookup"><span data-stu-id="ab777-126">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="ab777-127">Cette version de Visual Studio incluait des correctifs de bogues, des améliorations des performances ainsi que des préversions de la plateforme de compilation .NET (« Roslyn »), aujourd’hui connue sous le nom de .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span><span class="sxs-lookup"><span data-stu-id="ab777-127">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="ab777-128">C# 5, Visual Studio .NET 2012 :</span><span class="sxs-lookup"><span data-stu-id="ab777-128">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="ab777-129">`Async` / `await`, et attributs des [informations sur l’appelant](../programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="ab777-129">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="ab777-130">C# 4, Visual Studio .NET 2010 :</span><span class="sxs-lookup"><span data-stu-id="ab777-130">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="ab777-131">`Dynamic`, [arguments nommés](../programming-guide/classes-and-structs/named-and-optional-arguments.md), paramètres facultatifs, et [covariance et contravariance](../programming-guide/concepts/covariance-contravariance/index.md) génériques.</span><span class="sxs-lookup"><span data-stu-id="ab777-131">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="ab777-132">C# 3, Visual Studio .NET 2008 :</span><span class="sxs-lookup"><span data-stu-id="ab777-132">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="ab777-133">Initialiseurs d’objet et de collection, expressions lambda, méthodes d’extension, types anonymes, propriétés automatiques, inférence de type `var` locale, et [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab777-133">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="ab777-134">C# 2, Visual Studio .NET 2005 :</span><span class="sxs-lookup"><span data-stu-id="ab777-134">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="ab777-135">Méthodes anonymes, génériques, types Nullable, itérateurs/yield, classes `static`, variance et contravariance pour les délégués.</span><span class="sxs-lookup"><span data-stu-id="ab777-135">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="ab777-136">C# 1.1, Visual Studio .NET 2003 :</span><span class="sxs-lookup"><span data-stu-id="ab777-136">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="ab777-137">Pragma `#line` et commentaires de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="ab777-137">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="ab777-138">C# 1, Visual Studio .NET 2002 :</span><span class="sxs-lookup"><span data-stu-id="ab777-138">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="ab777-139">Première version de [C#](../csharp.md).</span><span class="sxs-lookup"><span data-stu-id="ab777-139">The first release of [C#](../csharp.md).</span></span>   

