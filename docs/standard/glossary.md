---
title: Glossaire .NET
description: "Découvrez la signification de certains termes utilisés dans la documentation .NET."
keywords: glossaire .NET, dictionnaire .NET, terminologie .NET, plateforme .NET, .NET Framework, runtime .NET
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.translationtype: HT
ms.sourcegitcommit: 33b22ab80f9b4d42975f2c41c880543c615a3e01
ms.openlocfilehash: c66f1b2b85d377c84712c0ad73682cdeeb7249fd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/31/2017

---

# <a name="net-glossary"></a><span data-ttu-id="e2e9c-104">Glossaire .NET</span><span class="sxs-lookup"><span data-stu-id="e2e9c-104">.NET Glossary</span></span>

<span data-ttu-id="e2e9c-105">L’objectif principal de ce glossaire est de préciser la signification de certains termes et acronymes qui apparaissent fréquemment dans la documentation .NET sans y être définis.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-105">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="e2e9c-106">AOT</span><span class="sxs-lookup"><span data-stu-id="e2e9c-106">AOT</span></span>

<span data-ttu-id="e2e9c-107">Compilateur Ahead Of Time.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-107">Ahead-of-time compiler.</span></span>

<span data-ttu-id="e2e9c-108">Semblable au compilateur [JIT](#jit), ce compilateur convertit également le langage [IL](#il) en code machine.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-108">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="e2e9c-109">Contrairement à la compilation JIT, la compilation AOT se produit avant que l’application ne soit exécutée et est généralement effectuée sur une autre machine.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-109">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="e2e9c-110">Étant donné que les chaînes d’outil AOT ne se compilent pas au moment de l’exécution, elles n’ont pas besoin de réduire le temps consacré à la compilation.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-110">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="e2e9c-111">Ainsi, elles peuvent dédier plus de temps à l’optimisation.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-111">That means they can spend more time optimizing.</span></span> <span data-ttu-id="e2e9c-112">Étant donné que le contexte d’AOT est l’ensemble de l’application, le compilateur AOT effectue également une liaison entre modules et une analyse de la totalité du programme, ce qui signifie que toutes les références sont suivies et qu’un seul exécutable est produit.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-112">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="e2e9c-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e2e9c-113">ASP.NET</span></span> 

<span data-ttu-id="e2e9c-114">Implémentation ASP.NET d’origine fournie avec .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="e2e9c-115">ASP.NET est parfois un terme général qui désigne les deux implémentations d’ASP.NET, y compris ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="e2e9c-116">C’est le contexte qui détermine la signification véhiculée par le terme.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-116">The meaning that the term carries in any given instance is determined by context.</span></span> 

<span data-ttu-id="e2e9c-117">Consultez [ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-117">See [ASP.NET](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="e2e9c-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e2e9c-118">ASP.NET Core</span></span>

<span data-ttu-id="e2e9c-119">Implémentation multiplateforme, hautes performances et open source d’ASP.NET basée sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-119">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="e2e9c-120">Consultez [ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-120">See [ASP.NET Core](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="e2e9c-121">assembly</span><span class="sxs-lookup"><span data-stu-id="e2e9c-121">assembly</span></span>

<span data-ttu-id="e2e9c-122">Fichier *.dll* qui contient une collection d’API pouvant être appelées par les applications ou d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-122">A *.dll* file that contains a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="e2e9c-123">Un assembly .NET est une collection de types.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-123">A .NET assembly is a collection of types.</span></span> <span data-ttu-id="e2e9c-124">Un assembly inclut des interfaces, des classes, des structures, des énumérations et des délégués.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-124">An assembly includes interfaces, classes, structures, enumerations, and delegates.</span></span>  <span data-ttu-id="e2e9c-125">Les assemblys qui se trouvent dans le dossier *bin* d’un projet sont parfois appelés *binaires*.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="e2e9c-126">Voir aussi [bibliothèque](#library).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="e2e9c-127">CLR</span><span class="sxs-lookup"><span data-stu-id="e2e9c-127">CLR</span></span>

<span data-ttu-id="e2e9c-128">Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-128">Common Language Runtime.</span></span>

<span data-ttu-id="e2e9c-129">La signification exacte dépend du contexte, mais ce terme fait généralement référence au runtime de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-129">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="e2e9c-130">Le CLR gère l’allocation et la gestion de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="e2e9c-131">Le CLR est également une machine virtuelle qui non seulement exécute des applications, mais aussi génère et compile du code à la volée à l’aide d’un compilateur JIT.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="e2e9c-132">L’implémentation CLR Microsoft actuelle est Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="e2e9c-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="e2e9c-133">CoreCLR</span></span>

<span data-ttu-id="e2e9c-134">.NET Core Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="e2e9c-135">Ce CLR repose sur la même base de code que le CLR.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="e2e9c-136">À l’origine, CoreCLR était le runtime de Silverlight et était conçu pour s’exécuter sur plusieurs plateformes, notamment Windows et OS X. CoreCLR fait désormais partie de .NET Core et représente une version simplifiée du CLR.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="e2e9c-137">C’est toujours un runtime multiplateforme, qui prend désormais en charge de nombreuses distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-137">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="e2e9c-138">CoreCLR est également une machine virtuelle avec des capacités JIT et d’exécution de code.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="e2e9c-139">CoreFX</span><span class="sxs-lookup"><span data-stu-id="e2e9c-139">CoreFX</span></span>

<span data-ttu-id="e2e9c-140">Bibliothèque de classes de base .NET Core</span><span class="sxs-lookup"><span data-stu-id="e2e9c-140">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="e2e9c-141">Ensemble de bibliothèques qui comprend les espaces de noms System.* (et, dans une certaine mesure, Microsoft.*).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-141">A set of libraries that comprise the System.* (and to a limited extent  Microsoft.*) namespaces.</span></span> <span data-ttu-id="e2e9c-142">La bibliothèque de classes de base est un framework de niveau inférieur à usage général sur lequel reposent les frameworks d’applications de niveau supérieur, tels qu’ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-142">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="e2e9c-143">Le code source de la bibliothèque de classes de base .NET Core se trouve dans le [dépôt CoreFX](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-143">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="e2e9c-144">Toutefois, la plupart des API .NET Core étant également disponibles dans .NET Framework, vous pouvez considérer CoreFX comme une duplication (fork) de la bibliothèque de classes de base .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-144">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="e2e9c-145">CoreRT</span><span class="sxs-lookup"><span data-stu-id="e2e9c-145">CoreRT</span></span>

<span data-ttu-id="e2e9c-146">Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-146">.NET Core runtime.</span></span>

<span data-ttu-id="e2e9c-147">Contrairement à CLR/CoreCLR, CoreRT n’est pas une machine virtuelle, ce qui signifie qu’il n’inclut pas les fonctionnalités de génération et d’exécution de code à la volée en raison de l’absence d’un compilateur [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-147">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="e2e9c-148">Toutefois, il inclut le [GC](#gc) et les fonctionnalités RTTI (identification du type au moment de l’exécution) et de réflexion.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-148">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="e2e9c-149">Toutefois, son système de type est conçu pour que les métadonnées de réflexion ne soient pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-149">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="e2e9c-150">Cela permet d’avoir une chaîne d’outils [AOT](#aot) qui peut écarter les métadonnées superflues et (surtout) identifier le code que l’application n’utilise pas.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-150">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="e2e9c-151">CoreRT est en cours de développement.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-151">CoreRT is in development.</span></span>

<span data-ttu-id="e2e9c-152">Consultez [Présentation de .NET Native et CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-152">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="e2e9c-153">écosystème</span><span class="sxs-lookup"><span data-stu-id="e2e9c-153">ecosystem</span></span>

<span data-ttu-id="e2e9c-154">Tous les logiciels d’exécution, outils de développement et ressources de communautés qui permettent de générer et d’exécuter des applications pour une technologie donnée.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-154">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="e2e9c-155">Le terme « écosystème .NET » diffère des termes tels que « pile .NET » en ce sens qu’il inclut les bibliothèques et les applications tierces.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-155">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="e2e9c-156">Voici un exemple dans une phrase :</span><span class="sxs-lookup"><span data-stu-id="e2e9c-156">Here's an example in a sentence:</span></span>

- <span data-ttu-id="e2e9c-157">« L’objectif de [.NET Standard](#net-standard) est d’établir une meilleure uniformité dans l’écosystème .NET. »</span><span class="sxs-lookup"><span data-stu-id="e2e9c-157">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="e2e9c-158">framework</span><span class="sxs-lookup"><span data-stu-id="e2e9c-158">framework</span></span>

<span data-ttu-id="e2e9c-159">En général, ensemble complet d’API qui facilite le développement et le déploiement d’applications basées sur une technologie particulière.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-159">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="e2e9c-160">Selon ce sens général, ASP.NET Core et Windows Forms sont des exemples de frameworks d’application.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-160">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="e2e9c-161">Voir aussi [bibliothèque](#library).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-161">See also [library](#library).</span></span>

<span data-ttu-id="e2e9c-162">Le mot « framework » a une signification technique plus spécifique dans les termes suivants :</span><span class="sxs-lookup"><span data-stu-id="e2e9c-162">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="e2e9c-163">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2e9c-163">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="e2e9c-164">framework cible</span><span class="sxs-lookup"><span data-stu-id="e2e9c-164">target framework</span></span>](#target-framework)
* [<span data-ttu-id="e2e9c-165">TFM (moniker de la version cible de .Net Framework)</span><span class="sxs-lookup"><span data-stu-id="e2e9c-165">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="e2e9c-166">Dans la documentation existante, « framework » fait parfois référence à une [implémentation de .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-166">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="e2e9c-167">Par exemple, un article peut appeler .NET Core un framework.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-167">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="e2e9c-168">Nous envisageons d’éliminer de la documentation cet usage qui prête à confusion.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-168">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="e2e9c-169">GC</span><span class="sxs-lookup"><span data-stu-id="e2e9c-169">GC</span></span>

<span data-ttu-id="e2e9c-170">Garbage collector.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-170">Garbage collector.</span></span>

<span data-ttu-id="e2e9c-171">Le garbage collector est une implémentation de la gestion automatique de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-171">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="e2e9c-172">Le GC libère la mémoire occupée par les objets qui ne sont plus en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-172">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="e2e9c-173">Consultez [Nettoyage de la mémoire](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-173">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="e2e9c-174">IL</span><span class="sxs-lookup"><span data-stu-id="e2e9c-174">IL</span></span>

<span data-ttu-id="e2e9c-175">Langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-175">Intermediate language.</span></span>

<span data-ttu-id="e2e9c-176">Les langages .NET de haut niveau, tels que C#, se compilent en un jeu d’instructions indépendant du matériel, qui est appelé Langage intermédiaire (IL).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-176">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="e2e9c-177">IL est parfois appelé MSIL (Microsoft IL) ou CIL (Common IL).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-177">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="e2e9c-178">JIT</span><span class="sxs-lookup"><span data-stu-id="e2e9c-178">JIT</span></span>

<span data-ttu-id="e2e9c-179">Compilateur juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-179">Just-in-time compiler.</span></span>

<span data-ttu-id="e2e9c-180">Semblable au compilateur [AOT](#aot), ce compilateur convertit le langage [IL](#il) en code machine que le processeur comprend.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-180">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="e2e9c-181">Contrairement à la compilation AOT, la compilation JIT se produit à la demande et est effectuée sur la machine sur laquelle le code doit s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-181">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="e2e9c-182">Étant donné que la compilation JIT se produit pendant l’exécution de l’application, la compilation fait partie du temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-182">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="e2e9c-183">Ainsi, les compilateurs JIT doivent trouver un équilibre entre le temps consacré à l’optimisation du code et les économies pouvant découler du code résultant.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-183">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="e2e9c-184">Toutefois, un compilateur JIT connaît le matériel réel et peut éviter aux développeurs d’avoir à transmettre différentes implémentations.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-184">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="e2e9c-185">implémentation de .NET</span><span class="sxs-lookup"><span data-stu-id="e2e9c-185">implementation of .NET</span></span>

<span data-ttu-id="e2e9c-186">Une implémentation de .NET inclut les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="e2e9c-186">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="e2e9c-187">Un ou plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-187">One or more runtimes.</span></span> <span data-ttu-id="e2e9c-188">Exemples : CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-188">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="e2e9c-189">Une bibliothèque de classes qui implémente une version de .NET Standard et qui peut inclure des API supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-189">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="e2e9c-190">Exemples : bibliothèque de classes de base .NET Framework, bibliothèque de classes de base .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-190">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="e2e9c-191">Le cas échéant, un ou plusieurs frameworks d’application.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-191">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="e2e9c-192">Exemples : ASP.NET, Windows Forms et WPF) sont inclus dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-192">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="e2e9c-193">Le cas échéant, des outils de développement.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-193">Optionally, development tools.</span></span> <span data-ttu-id="e2e9c-194">Certains outils de développement sont partagés entre plusieurs implémentations.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-194">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="e2e9c-195">Exemples d’implémentations de .NET :</span><span class="sxs-lookup"><span data-stu-id="e2e9c-195">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="e2e9c-196">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2e9c-196">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="e2e9c-197">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e2e9c-197">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="e2e9c-198">Plateforme Windows universelle (UWP)</span><span class="sxs-lookup"><span data-stu-id="e2e9c-198">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="e2e9c-199">bibliothèque</span><span class="sxs-lookup"><span data-stu-id="e2e9c-199">library</span></span>

<span data-ttu-id="e2e9c-200">Ensemble d’API que peuvent appeler les applications ou d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-200">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="e2e9c-201">Une bibliothèque .NET est composée d’un ou plusieurs [assemblys](#assembly).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-201">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="e2e9c-202">Les mots bibliothèque et [framework](#framework) sont souvent utilisés indifféremment.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-202">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="e2e9c-203">métapackage</span><span class="sxs-lookup"><span data-stu-id="e2e9c-203">metapackage</span></span>

<span data-ttu-id="e2e9c-204">Package NuGet ne disposant pas de sa propre bibliothèque, mais qui est simplement une liste de dépendances.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-204">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="e2e9c-205">Les packages inclus peuvent éventuellement établir l’API pour un framework cible.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-205">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="e2e9c-206">Consultez [Packages, métapackages et frameworks](../core/packages.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-206">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="e2e9c-207">Mono</span><span class="sxs-lookup"><span data-stu-id="e2e9c-207">Mono</span></span>

<span data-ttu-id="e2e9c-208">Mono est une implémentation de .NET qui est principalement utilisée quand un runtime réduit est requis.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-208">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="e2e9c-209">Ce runtime, qui alimente les applications Xamarin sur Android, Mac, iOS, tvOS et watchOS, est avant tout axé sur les applications qui requièrent un faible encombrement.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-209">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="e2e9c-210">Il prend en charge toutes les versions de .NET Standard publiées.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-210">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="e2e9c-211">Historiquement, Mono implémentait l’API plus volumineuse de .NET Framework et émulait certaines des fonctionnalités les plus populaires sur Unix.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-211">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="e2e9c-212">Il est parfois utilisé pour exécuter des applications .NET qui s’appuient sur ces fonctionnalités sous Unix.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-212">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="e2e9c-213">Mono est généralement utilisé avec un compilateur juste-à-temps, mais il comporte également un compilateur statique complet (compilation Ahead Of Time) qui est utilisé sur des plateformes comme iOS.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-213">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="e2e9c-214">Pour en savoir plus sur Mono, consultez la [documentation Mono](http://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-214">To learn more about Mono, see the [Mono documentation](http://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="e2e9c-215">.NET</span><span class="sxs-lookup"><span data-stu-id="e2e9c-215">.NET</span></span>

<span data-ttu-id="e2e9c-216">Terme générique désignant [.NET Standard](#net-standard), ainsi que toutes les charges de travail et les [implémentations de .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-216">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="e2e9c-217">Toujours en majuscules, jamais « .Net ».</span><span class="sxs-lookup"><span data-stu-id="e2e9c-217">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="e2e9c-218">Consultez le [Guide de .NET](index.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-218">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="e2e9c-219">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e2e9c-219">.NET Core</span></span> 

<span data-ttu-id="e2e9c-220">Implémentation multiplateforme, hautes performances et open source de .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-220">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="e2e9c-221">Inclut CoreCLR (Core Common Language Runtime), CoreRT (Core AOT Runtime, en cours de développement), la bibliothèque de classes de base et le SDK Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-221">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="e2e9c-222">Consultez [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-222">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="e2e9c-223">CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="e2e9c-223">.NET Core CLI</span></span>

<span data-ttu-id="e2e9c-224">Chaîne d’outils multiplateforme pour développer des applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-224">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="e2e9c-225">Consultez [Outils de l’interface de ligne de commande (CLI) de .NET Core](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-225">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="e2e9c-226">SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="e2e9c-226">.NET Core SDK</span></span>

<span data-ttu-id="e2e9c-227">Ensemble de bibliothèques et d’outils qui permettent aux développeurs de créer des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-227">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="e2e9c-228">Inclut la [CLI .NET Core](#net-core-cli) pour la génération d’applications, les bibliothèques .NET Core et le runtime pour la génération et l’exécution d’applications et l’exécutable dotnet (*dotnet.exe*) qui exécute les commandes CLI et les applications.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-228">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="e2e9c-229">Consultez [Vue d’ensemble du SDK .NET Core](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-229">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="e2e9c-230">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2e9c-230">.NET Framework</span></span>

<span data-ttu-id="e2e9c-231">Implémentation de .NET qui s’exécute uniquement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-231">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="e2e9c-232">Inclut le Common Language Runtime (CLR), la bibliothèque de classes de base et des bibliothèques de framework d’application telles qu’ASP.NET, Windows Forms et WPF.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-232">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="e2e9c-233">Consultez [Guide du .NET Framework](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-233">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="e2e9c-234">.NET Native</span><span class="sxs-lookup"><span data-stu-id="e2e9c-234">.NET Native</span></span>

<span data-ttu-id="e2e9c-235">Chaîne d’outils de compilateur qui génère du code natif Ahead Of Time (AOT), par opposition à juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-235">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="e2e9c-236">La compilation se produit sur la machine du développeur, à l’image du fonctionnement d’un éditeur de liens et d’un compilateur C++.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-236">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="e2e9c-237">Elle supprime le code inutilisé et consacre plus de temps à l’optimisation du code.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-237">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="e2e9c-238">Elle extrait le code des bibliothèques et le fusionne dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-238">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="e2e9c-239">Le résultat est un module unique qui représente l’application entière.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-239">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="e2e9c-240">UWP fut le premier framework d’application pris en charge par .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-240">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="e2e9c-241">De nos jours, nous prenons en charge la génération d’applications console natives pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-241">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="e2e9c-242">Consultez [Présentation de .NET Native et CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-242">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="e2e9c-243">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e2e9c-243">.NET Standard</span></span>

<span data-ttu-id="e2e9c-244">Spécification formelle des API .NET disponibles dans chaque implémentation de .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-244">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="e2e9c-245">La spécification .NET Standard est parfois appelée bibliothèque dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-245">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="e2e9c-246">Comme une bibliothèque inclut des implémentations d’API, outre des spécifications (interfaces), il est trompeur d’appeler .NET Standard une « bibliothèque ».</span><span class="sxs-lookup"><span data-stu-id="e2e9c-246">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="e2e9c-247">Nous prévoyons de supprimer cette utilisation de la documentation, sauf en référence au nom du métapackage .NET Standard (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-247">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="e2e9c-248">Consultez [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-248">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="e2e9c-249">NGEN</span><span class="sxs-lookup"><span data-stu-id="e2e9c-249">NGEN</span></span>

<span data-ttu-id="e2e9c-250">Génération (d’images) native</span><span class="sxs-lookup"><span data-stu-id="e2e9c-250">Native (image) generation.</span></span>

<span data-ttu-id="e2e9c-251">Vous pouvez considérer cette technologie comme un compilateur JIT persistant.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-251">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="e2e9c-252">Elle compile généralement le code sur la machine où le code est exécuté, mais la compilation se produit en règle générale au moment de l’installation.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-252">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="e2e9c-253">package</span><span class="sxs-lookup"><span data-stu-id="e2e9c-253">package</span></span>

<span data-ttu-id="e2e9c-254">Un package NuGet &mdash; ou simplement un package &mdash; est un fichier *.zip* qui comporte un ou plusieurs assemblys portant le même nom, ainsi que des métadonnées supplémentaires, telles que le nom de l’auteur.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-254">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="e2e9c-255">Le fichier *.zip* porte l’extension *.nupkg* et peut contenir des composants, tels que des fichiers *.dll* et des fichiers *.xml*, à utiliser avec plusieurs frameworks et versions.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-255">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple frameworks and versions.</span></span> <span data-ttu-id="e2e9c-256">Quand ils sont installés dans une application ou une bibliothèque, les composants appropriés sont sélectionnés en fonction du framework cible spécifié par l’application ou la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-256">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="e2e9c-257">Les composants qui définissent l’interface se trouvent dans le dossier *ref*, tandis que les ressources qui définissent l’implémentation se trouvent dans le dossier *lib*.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-257">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="e2e9c-258">platform</span><span class="sxs-lookup"><span data-stu-id="e2e9c-258">platform</span></span>

<span data-ttu-id="e2e9c-259">Système d’exploitation et le matériel sur lequel il s’exécute, tel que Windows, macOS, Linux, iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-259">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="e2e9c-260">Voici quelques exemples d’utilisation dans des phrases :</span><span class="sxs-lookup"><span data-stu-id="e2e9c-260">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="e2e9c-261">« .NET Core est une implémentation multiplateforme de .NET ».</span><span class="sxs-lookup"><span data-stu-id="e2e9c-261">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="e2e9c-262">« Les profils de bibliothèque de classes portable représentent les plateformes Microsoft, alors que .NET Standard est indépendant de la plateforme. »</span><span class="sxs-lookup"><span data-stu-id="e2e9c-262">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="e2e9c-263">La documentation .NET utilise fréquemment « plateforme .NET » pour désigner soit une implémentation de .NET, soit la pile .NET y compris toutes les implémentations.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-263">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="e2e9c-264">Ces deux utilisations ayant tendance à être confondues avec la signification principale (système d’exploitation/matériel), nous envisageons de les supprimer de la documentation.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-264">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="e2e9c-265">runtime</span><span class="sxs-lookup"><span data-stu-id="e2e9c-265">runtime</span></span>

<span data-ttu-id="e2e9c-266">Environnement d’exécution d’un programme managé.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-266">The execution environment for a managed program.</span></span>

<span data-ttu-id="e2e9c-267">Le système d’exploitation fait partie de l’environnement d’exécution, mais pas du runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-267">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="e2e9c-268">Voici quelques exemples de runtimes .NET :</span><span class="sxs-lookup"><span data-stu-id="e2e9c-268">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="e2e9c-269">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="e2e9c-269">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="e2e9c-270">Core Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="e2e9c-270">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="e2e9c-271">.NET Native (pour la plateforme Windows universelle)</span><span class="sxs-lookup"><span data-stu-id="e2e9c-271">.NET Native (for UWP)</span></span>
- <span data-ttu-id="e2e9c-272">Runtime Mono</span><span class="sxs-lookup"><span data-stu-id="e2e9c-272">Mono runtime</span></span>

<span data-ttu-id="e2e9c-273">Parfois, la documentation de .NET utilise « runtime » pour désigner une implémentation de .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-273">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="e2e9c-274">Par exemple, dans les phrases suivantes, « runtime » doit être remplacé par « implémentation » :</span><span class="sxs-lookup"><span data-stu-id="e2e9c-274">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="e2e9c-275">« Les différents runtimes .NET implémentent des versions spécifiques de .NET Standard. »</span><span class="sxs-lookup"><span data-stu-id="e2e9c-275">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="e2e9c-276">« Les bibliothèques destinées à s’exécuter sur plusieurs runtimes doivent cibler ce framework. »</span><span class="sxs-lookup"><span data-stu-id="e2e9c-276">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="e2e9c-277">(s’applique à .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="e2e9c-277">(referring to .NET Standard)</span></span>
- <span data-ttu-id="e2e9c-278">« Les différents runtimes .NET implémentent des versions spécifiques de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-278">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="e2e9c-279">…</span><span class="sxs-lookup"><span data-stu-id="e2e9c-279">…</span></span> <span data-ttu-id="e2e9c-280">Chaque version du runtime .NET publie la version .NET Standard la plus élevée qu’elle prend en charge... »</span><span class="sxs-lookup"><span data-stu-id="e2e9c-280">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="e2e9c-281">Nous envisageons de supprimer cette utilisation incohérente.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-281">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="e2e9c-282">pile</span><span class="sxs-lookup"><span data-stu-id="e2e9c-282">stack</span></span>

<span data-ttu-id="e2e9c-283">Ensemble de technologies de programmation qui sont utilisées conjointement pour générer et exécuter des applications.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-283">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="e2e9c-284">L’expression « la pile .NET » fait référence à .NET Standard et à toutes les implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-284">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="e2e9c-285">L’expression « une pile .NET » peut faire référence à une implémentation de .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-285">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="e2e9c-286">version cible de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2e9c-286">target framework</span></span>

<span data-ttu-id="e2e9c-287">Ensemble d’API sur lequel repose une bibliothèque ou une application .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-287">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="e2e9c-288">Une application ou une bibliothèque peut cibler une version de .NET Standard (par exemple, .NET Standard 2.0), qui est la spécification d’un ensemble standard d’API parmi toutes les implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-288">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="e2e9c-289">Une application ou une bibliothèque peut également cibler une version d’une implémentation spécifique de .NET ; dans ce cas, elle a accès aux API spécifiques à l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-289">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="e2e9c-290">Par exemple, une application qui cible Xamarin.iOS accède aux wrappers d’API iOS fournis par Xamarin.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-290">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="e2e9c-291">Pour certains frameworks cibles (par exemple, .NET Framework), les API disponibles sont définies par les assemblys qu’une implémentation de .NET installe sur un système. Les API peuvent inclure des API de framework d’application (par exemple, ASP.NET ou WinForms).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-291">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="e2e9c-292">Pour les frameworks cibles basés sur le package (par exemple, .NET Standard et .NET Core), les API de framework sont définies par les packages installés dans l’application ou la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-292">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="e2e9c-293">Dans ce cas, le framework cible spécifie implicitement un métapackage qui référence tous les packages constituant le framework.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-293">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="e2e9c-294">Consultez [Versions cibles de .NET Framework](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-294">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="e2e9c-295">TFM</span><span class="sxs-lookup"><span data-stu-id="e2e9c-295">TFM</span></span>

<span data-ttu-id="e2e9c-296">Moniker de la version cible de .Net Framework.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-296">Target framework moniker.</span></span>

<span data-ttu-id="e2e9c-297">Format de jeton standardisé pour la spécification du framework cible d’une bibliothèque ou d’une application .NET.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-297">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="e2e9c-298">Les frameworks cibles sont en général référencés par un nom court, tel que `net462`.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-298">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="e2e9c-299">Les TFM de forme longue (par exemple, .NETFramework,Version=4.6.2) existent, mais ne sont généralement pas utilisés pour spécifier un framework cible.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-299">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="e2e9c-300">Consultez [Versions cibles de .NET Framework](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-300">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="e2e9c-301">UWP</span><span class="sxs-lookup"><span data-stu-id="e2e9c-301">UWP</span></span>

<span data-ttu-id="e2e9c-302">Plateforme Windows universelle.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-302">Universal Windows Platform.</span></span>

<span data-ttu-id="e2e9c-303">Implémentation de .NET qui sert à générer des logiciels et des applications Windows tactiles modernes pour l’Internet des objets (IoT).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-303">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="e2e9c-304">Elle vise à unifier les différents types d’appareils que vous pouvez cibler, y compris les PC, les tablettes, les phablettes, les téléphones et même la Xbox.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-304">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="e2e9c-305">UWP fournit de nombreux services, comme un magasin d’applications centralisé, un environnement d’exécution (AppContainer) et un ensemble d’API Windows à utiliser à la place de Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="e2e9c-305">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="e2e9c-306">Les applications peuvent être écrites en C++, C#, VB.NET et JavaScript.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-306">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="e2e9c-307">Quand vous utilisez C# et VB.NET, les API .NET sont fournies par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2e9c-307">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2e9c-308">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2e9c-308">See also</span></span>

[<span data-ttu-id="e2e9c-309">Guide de .NET</span><span class="sxs-lookup"><span data-stu-id="e2e9c-309">.NET Guide</span></span>](index.md)  
[<span data-ttu-id="e2e9c-310">Guide du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2e9c-310">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="e2e9c-311">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e2e9c-311">.NET Core</span></span>](../core/index.md)  
<span data-ttu-id="e2e9c-312">[ASP.NET Overview](/aspnet/index#pivot=aspnet) (Vue d’ensemble d’ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="e2e9c-312">[ASP.NET Overview](/aspnet/index#pivot=aspnet)</span></span>  
<span data-ttu-id="e2e9c-313">[ASP.NET Core Overview](/aspnet/index#pivot=core) (Vue d’ensemble d’ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="e2e9c-313">[ASP.NET Core Overview](/aspnet/index#pivot=core)</span></span>  


