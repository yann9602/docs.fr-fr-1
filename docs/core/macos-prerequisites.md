---
title: Configuration requise pour .NET Core sur Mac
description: "Versions macOS et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS."
keywords: .NET, .NET Core, MacOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 07/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8feaee2cbfa55e23bd49c0ab76d995f15be343b4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="prerequisites-for-net-core-on-mac"></a><span data-ttu-id="c40d2-104">Configuration requise pour .NET Core sur Mac</span><span class="sxs-lookup"><span data-stu-id="c40d2-104">Prerequisites for .NET Core on Mac</span></span>

<span data-ttu-id="c40d2-105">Cet article vous présente les versions macOS et les dépendances .NET Core prises en charge nécessaires pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS.</span><span class="sxs-lookup"><span data-stu-id="c40d2-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="c40d2-106">Les versions de système d’exploitation et dépendances prises en charge suivantes s’appliquent aux trois méthodes de développement des applications .NET Core sur un Mac : via la [ligne de commande de votre éditeur favori](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/) et [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="c40d2-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="c40d2-107">Versions macOS prises en charge</span><span class="sxs-lookup"><span data-stu-id="c40d2-107">Supported macOS versions</span></span>

<span data-ttu-id="c40d2-108">.NET Core est pris en charge par les versions suivantes de macOS :</span><span class="sxs-lookup"><span data-stu-id="c40d2-108">.NET Core is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="c40d2-109">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="c40d2-109">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="c40d2-110">macOS 10.11 « El Capitan » (.NET Core 1.x uniquement)</span><span class="sxs-lookup"><span data-stu-id="c40d2-110">macOS 10.11 "El Capitan" (.NET Core 1.x only)</span></span>

<span data-ttu-id="c40d2-111">Consultez la page [Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions) pour obtenir la liste complète des systèmes d’exploitation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c40d2-111">See [Supported OS Versions](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions) for the complete list of supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="c40d2-112">Dépendances .NET Core</span><span class="sxs-lookup"><span data-stu-id="c40d2-112">.NET Core dependencies</span></span>

<span data-ttu-id="c40d2-113">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="c40d2-113">**.NET Core 1.x**</span></span>

<span data-ttu-id="c40d2-114">.NET Core 1.x nécessite OpenSSL lors d’une exécution sous macOS.</span><span class="sxs-lookup"><span data-stu-id="c40d2-114">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="c40d2-115">Un moyen simple d’obtenir OpenSSL consiste à utiliser le gestionnaire de package [Homebrew (« brew »)](https://brew.sh/) pour macOS.</span><span class="sxs-lookup"><span data-stu-id="c40d2-115">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="c40d2-116">Après avoir installé *brew*, installez OpenSSL en exécutant les commandes suivantes dans une invite de Terminal (commande) :</span><span class="sxs-lookup"><span data-stu-id="c40d2-116">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="c40d2-117">Téléchargez et installez le kit SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="c40d2-117">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="c40d2-118">Si vous rencontrez des problèmes d’installation sur macOS, consultez les rubriques [Problèmes connus 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) et [Problèmes connus 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="c40d2-118">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

<span data-ttu-id="c40d2-119">**.NET Core 2.x**</span><span class="sxs-lookup"><span data-stu-id="c40d2-119">**.NET Core 2.x**</span></span>

<span data-ttu-id="c40d2-120">Téléchargez et installez le kit SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="c40d2-120">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="c40d2-121">Si vous rencontrez des problèmes d’installation sur macOS, consultez la rubrique [Problèmes connus](https://github.com/dotnet/core/tree/master/release-notes/2.0) associée à la version installée.</span><span class="sxs-lookup"><span data-stu-id="c40d2-121">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="c40d2-122">Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="c40d2-122">Visual Studio for Mac</span></span>

<span data-ttu-id="c40d2-123">Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c40d2-123">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="c40d2-124">Toutefois, si vous voulez développer des applications .NET Core sous Mac dans un environnement de développement intégré, vous pouvez utiliser [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="c40d2-124">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="c40d2-125">Le développement .NET Core sur macOS avec Visual Studio pour Mac nécessite :</span><span class="sxs-lookup"><span data-stu-id="c40d2-125">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="c40d2-126">Une version prise en charge du système d’exploitation macOS</span><span class="sxs-lookup"><span data-stu-id="c40d2-126">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="c40d2-127">OpenSSL (.NET Core 1.x uniquement ; .NET Core 2.x utilise les services de sécurité disponibles en mode natif dans macOS)</span><span class="sxs-lookup"><span data-stu-id="c40d2-127">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="c40d2-128">.NET Core SDK pour Mac</span><span class="sxs-lookup"><span data-stu-id="c40d2-128">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="c40d2-129">Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="c40d2-129">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

