---
title: "Générer .NET Core à partir de la source"
description: "Découvrez comment générer .NET Core et le .NET Core CLI à partir du code source."
keywords: ".NET, .NET Core, source, générer"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8b49079c-6ede-429a-92d7-ecd2fda1ab0e
ms.workload: dotnetcore
ms.openlocfilehash: 6aa5abd071355b1c1a367b35e9521e6b1af9c945
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="31a85-104">Générer .NET Core à partir de la source</span><span class="sxs-lookup"><span data-stu-id="31a85-104">Build .NET Core from source</span></span>

<span data-ttu-id="31a85-105">La capacité de générer .NET Core à partir de son code source est importante à plusieurs titres : elle facilite le portage de .NET Core vers de nouvelles plateformes, elle permet les contributions et les correctifs pour le produit, et elle permet la création de versions personnalisées de .NET.</span><span class="sxs-lookup"><span data-stu-id="31a85-105">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="31a85-106">Cet article fournit de l’aide aux développeurs qui veulent créer et distribuer leurs propres versions de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="31a85-106">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="31a85-107">Générer le CLR à partir de la source</span><span class="sxs-lookup"><span data-stu-id="31a85-107">Build the CLR from source</span></span>

<span data-ttu-id="31a85-108">Vous trouverez le code source de .NET CLRCore dans [le dépôt `dotnet/coreclr` sur GitHub](https://github.com/dotnet/coreclr/).</span><span class="sxs-lookup"><span data-stu-id="31a85-108">The source code for the .NET CoreCLR can be found in [the `dotnet/coreclr` repository on GitHub](https://github.com/dotnet/coreclr/).</span></span>

<span data-ttu-id="31a85-109">La génération dépend actuellement des prérequis suivants :</span><span class="sxs-lookup"><span data-stu-id="31a85-109">The build currently depends on the following prerequisites:</span></span>
* [<span data-ttu-id="31a85-110">Git</span><span class="sxs-lookup"><span data-stu-id="31a85-110">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="31a85-111">CMake</span><span class="sxs-lookup"><span data-stu-id="31a85-111">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="31a85-112">Python</span><span class="sxs-lookup"><span data-stu-id="31a85-112">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="31a85-113">Un compilateur C++.</span><span class="sxs-lookup"><span data-stu-id="31a85-113">a C++ compiler.</span></span>

<span data-ttu-id="31a85-114">Une fois ces prérequis installés, vous pouvez générer le CLR en appelant le script de génération (`build.cmd` sur Windows, ou `build.sh` sur Linux et macOS) à la base du [dépôt CoreCLR](https://github.com/dotnet/coreclr/).</span><span class="sxs-lookup"><span data-stu-id="31a85-114">After you've installed these prerequisites are installed, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of [the CoreCLR repository](https://github.com/dotnet/coreclr/).</span></span>

<span data-ttu-id="31a85-115">L’installation des composants diffère selon le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="31a85-115">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="31a85-116">Consultez les instructions de génération pour votre système d’exploitation spécifique :</span><span class="sxs-lookup"><span data-stu-id="31a85-116">See the build instructions for your specific OS:</span></span>

 * [<span data-ttu-id="31a85-117">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="31a85-117">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [<span data-ttu-id="31a85-118">Linux</span><span class="sxs-lookup"><span data-stu-id="31a85-118">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [<span data-ttu-id="31a85-119">macOS</span><span class="sxs-lookup"><span data-stu-id="31a85-119">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [<span data-ttu-id="31a85-120">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="31a85-120">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [<span data-ttu-id="31a85-121">NetBSD</span><span class="sxs-lookup"><span data-stu-id="31a85-121">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="31a85-122">La génération croisée entre systèmes d’exploitation n’est pas possible (sauf pour ARM, qui est basé sur X64).</span><span class="sxs-lookup"><span data-stu-id="31a85-122">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="31a85-123">Vous devez être sur la plateforme spécifique pour générer cette plateforme.</span><span class="sxs-lookup"><span data-stu-id="31a85-123">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="31a85-124">La build a deux `buildTypes` principaux :</span><span class="sxs-lookup"><span data-stu-id="31a85-124">The build has two main `buildTypes`:</span></span>

 * <span data-ttu-id="31a85-125">Debug (par défaut) : compile le runtime avec des optimisations minimales et des vérifications (assertions) supplémentaires à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="31a85-125">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="31a85-126">Cette réduction du niveau d’optimisation et les vérifications supplémentaires ralentissent l’exécution du runtime, mais sont utiles pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="31a85-126">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="31a85-127">Il s’agit du paramètre recommandé pour les environnements de développement et de test.</span><span class="sxs-lookup"><span data-stu-id="31a85-127">This is the recommended setting for development and testing environments.</span></span>
 * <span data-ttu-id="31a85-128">Release : compile le runtime avec des optimisations complètes et sans les vérifications supplémentaires à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="31a85-128">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="31a85-129">Vous obtenez des performances d’exécution plus rapides, mais la génération peut prendre plus de temps et être difficile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="31a85-129">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="31a85-130">Passez `release` au script de compilation pour sélectionner ce type de build.</span><span class="sxs-lookup"><span data-stu-id="31a85-130">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="31a85-131">Par défaut, la génération crée non seulement les exécutables du runtime, mais elle produit également tous les tests.</span><span class="sxs-lookup"><span data-stu-id="31a85-131">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="31a85-132">Il existe un bon nombre de tests qui prennent un temps considérable alors qu’ils ne sont pas nécessaires si vous voulez faire des essais avec des modifications.</span><span class="sxs-lookup"><span data-stu-id="31a85-132">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="31a85-133">Vous pouvez ignorer les builds de tests en ajoutant l’argument `skiptests` au script de génération, comme dans l’exemple suivant (remplacez `.\build` par `./build.sh` sur les machines Unix) :</span><span class="sxs-lookup"><span data-stu-id="31a85-133">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests 
```

<span data-ttu-id="31a85-134">L’exemple précédent a montré comment générer la version `Debug`, avec les vérifications (assertions) au moment du développement activées et les optimisations désactivées.</span><span class="sxs-lookup"><span data-stu-id="31a85-134">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="31a85-135">Pour générer la version Release (celle qui s’exécute à pleine vitesse), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="31a85-135">To build the release (full speed) flavor, do the following:</span></span>

```bat 
    .\build release skiptests
```

<span data-ttu-id="31a85-136">Vous trouverez plus d’options de génération de la build en utilisant le qualificateur -?</span><span class="sxs-lookup"><span data-stu-id="31a85-136">You can find more build options with build by using the -?</span></span> <span data-ttu-id="31a85-137">ou - help.</span><span class="sxs-lookup"><span data-stu-id="31a85-137">or -help qualifier.</span></span>   

### <a name="using-your-build"></a><span data-ttu-id="31a85-138">Utilisation de votre build</span><span class="sxs-lookup"><span data-stu-id="31a85-138">Using Your Build</span></span>

<span data-ttu-id="31a85-139">La build place tous les fichiers générés sous le répertoire `bin` à la base du dépôt.</span><span class="sxs-lookup"><span data-stu-id="31a85-139">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="31a85-140">Il existe un répertoire *bin\Log* qui contient les fichiers journaux générés pendant la génération (utiles principalement en cas d’échec de la build).</span><span class="sxs-lookup"><span data-stu-id="31a85-140">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="31a85-141">Le résultat est placé dans un répertoire *bin\Product\[plateforme].[Architecture d’UC].[type de build]*, comme *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="31a85-141">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="31a85-142">Si la sortie « brute » de la build est parfois utile, vous n’êtes normalement intéressé que par les packages NuGet, qui sont placés dans le sous-répertoire `.nuget\pkg` du répertoire de sortie précédent.</span><span class="sxs-lookup"><span data-stu-id="31a85-142">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="31a85-143">Vous pouvez utiliser votre nouveau runtime selon deux techniques de base :</span><span class="sxs-lookup"><span data-stu-id="31a85-143">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="31a85-144">**Utiliser dotnet.exe et NuGet pour composer une application**.</span><span class="sxs-lookup"><span data-stu-id="31a85-144">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="31a85-145">Consultez [Utilisation de votre build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) pour obtenir des instructions sur la création d’un programme qui utilise votre nouveau runtime avec les packages NuGet que vous venez de créer et l’interface de ligne de commande (CLI) « dotnet ».</span><span class="sxs-lookup"><span data-stu-id="31a85-145">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="31a85-146">Cette technique est celle que les développeurs « non-runtime » vont probablement utiliser pour consommer votre nouveau runtime.</span><span class="sxs-lookup"><span data-stu-id="31a85-146">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>    

 2. <span data-ttu-id="31a85-147">**Utiliser corerun.exe pour exécuter une application avec des DLL non packagées**.</span><span class="sxs-lookup"><span data-stu-id="31a85-147">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="31a85-148">Ce dépôt définit également un hôte simple appelé corerun.exe, qui n’accepte AUCUNE dépendance de NuGet.</span><span class="sxs-lookup"><span data-stu-id="31a85-148">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="31a85-149">Vous devez indiquer à l’hôte où obtenir les DLL nécessaires que vous utilisez, puis vous devez les rassembler manuellement.</span><span class="sxs-lookup"><span data-stu-id="31a85-149">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="31a85-150">Cette technique est utilisée par tous les tests du [dépôt CLRCore](https://github.com/dotnet/coreclr) et est utile pour le cycle local rapide « Édition-Compilation-Débogage », comme les tests unitaires préliminaires.</span><span class="sxs-lookup"><span data-stu-id="31a85-150">This technique is used by all the tests in [the CoreCLR repo](https://github.com/dotnet/coreclr), and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="31a85-151">Pour plus d’informations sur l’utilisation de cette technique, consultez [Exécution d’applications .NET Core avec CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md).</span><span class="sxs-lookup"><span data-stu-id="31a85-151">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="31a85-152">Générer l’interface CLI à partir de la source</span><span class="sxs-lookup"><span data-stu-id="31a85-152">Build the CLI from source</span></span>

<span data-ttu-id="31a85-153">Vous trouverez le code source pour l’interface CLI de .NET Core dans [le dépôt `dotnet/cli` sur GitHub](https://github.com/dotnet/cli/).</span><span class="sxs-lookup"><span data-stu-id="31a85-153">The source code for the .NET Core CLI can be found in [the `dotnet/cli` repository on GitHub](https://github.com/dotnet/cli/).</span></span>

<span data-ttu-id="31a85-154">Pour générer l’interface CLI de .NET Core, les éléments suivants doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31a85-154">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="31a85-155">Windows et Linux :</span><span class="sxs-lookup"><span data-stu-id="31a85-155">Windows & Linux:</span></span>
    - <span data-ttu-id="31a85-156">git sur la variable PATH</span><span class="sxs-lookup"><span data-stu-id="31a85-156">git on the PATH</span></span>
* <span data-ttu-id="31a85-157">macOS :</span><span class="sxs-lookup"><span data-stu-id="31a85-157">macOS:</span></span>
    - <span data-ttu-id="31a85-158">git sur la variable PATH</span><span class="sxs-lookup"><span data-stu-id="31a85-158">git on the PATH</span></span>
    - <span data-ttu-id="31a85-159">Xcode</span><span class="sxs-lookup"><span data-stu-id="31a85-159">Xcode</span></span>
    - <span data-ttu-id="31a85-160">Openssl</span><span class="sxs-lookup"><span data-stu-id="31a85-160">OpenSSL</span></span>

<span data-ttu-id="31a85-161">Pour générer, exécutez `build.cmd` sur Windows, ou `build.sh` sur Linux et macOS à partir de la racine.</span><span class="sxs-lookup"><span data-stu-id="31a85-161">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="31a85-162">Si vous ne voulez pas exécuter les tests, exécutez `build.cmd /t:Compile` ou `./build.sh /t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="31a85-162">If you don't want to execute tests, run `build.cmd /t:Compile` or `./build.sh /t:Compile`.</span></span> <span data-ttu-id="31a85-163">Pour générer l’interface CLI dans macOS Sierra, vous devez définir la variable d’environnement DOTNET_RUNTIME_ID en exécutant `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="31a85-163">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="31a85-164">Utilisation de votre build</span><span class="sxs-lookup"><span data-stu-id="31a85-164">Using your build</span></span>

<span data-ttu-id="31a85-165">Utilisez l’exécutable `dotnet` à partir de *artifacts/{os}-{arch}/stage2* pour essayer l’interface CLI nouvellement générée.</span><span class="sxs-lookup"><span data-stu-id="31a85-165">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="31a85-166">Si vous voulez utiliser la sortie de la génération lors de l’appel de `dotnet` à partir de la console active, vous pouvez également ajouter *artifacts/{os}-{arch}/stage2* à la variable PATH.</span><span class="sxs-lookup"><span data-stu-id="31a85-166">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="31a85-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31a85-167">See also</span></span>

* [<span data-ttu-id="31a85-168">Common Language Runtime .NET Core (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="31a85-168">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="31a85-169">Guide du développeur de l’interface CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="31a85-169">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="31a85-170">Empaquetage de la distribution de .NET Core</span><span class="sxs-lookup"><span data-stu-id="31a85-170">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
