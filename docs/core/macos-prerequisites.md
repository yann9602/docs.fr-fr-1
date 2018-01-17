---
title: Configuration requise pour .NET Core sur Mac
description: "Versions macOS et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS."
keywords: .NET, .NET Core, MacOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: 5aac7566f532312c890bad07c901929ae826ece3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="bbf77-104">Configuration requise pour .NET Core sur macOS</span><span class="sxs-lookup"><span data-stu-id="bbf77-104">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="bbf77-105">Cet article vous présente les versions macOS et les dépendances .NET Core prises en charge nécessaires pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS.</span><span class="sxs-lookup"><span data-stu-id="bbf77-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="bbf77-106">Les versions de système d’exploitation et dépendances prises en charge suivantes s’appliquent aux trois méthodes de développement des applications .NET Core sur un Mac : via la [ligne de commande de votre éditeur favori](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/) et [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="bbf77-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="bbf77-107">Versions macOS prises en charge</span><span class="sxs-lookup"><span data-stu-id="bbf77-107">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbf77-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbf77-108">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bbf77-109">.NET Core 2.x est pris en charge par les versions suivantes de macOS :</span><span class="sxs-lookup"><span data-stu-id="bbf77-109">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="bbf77-110">macOS 10.12 « Sierra » et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bbf77-110">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="bbf77-111">Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="bbf77-111">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbf77-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbf77-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bbf77-113">.NET Core 1.x est pris en charge par les versions suivantes de macOS :</span><span class="sxs-lookup"><span data-stu-id="bbf77-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="bbf77-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="bbf77-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="bbf77-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="bbf77-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="bbf77-116">Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="bbf77-116">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="bbf77-117">Dépendances .NET Core</span><span class="sxs-lookup"><span data-stu-id="bbf77-117">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbf77-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbf77-118">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bbf77-119">Téléchargez et installez le kit SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="bbf77-119">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="bbf77-120">Si vous rencontrez des problèmes d’installation sur macOS, consultez la rubrique [Problèmes connus](https://github.com/dotnet/core/tree/master/release-notes/2.0) associée à la version installée.</span><span class="sxs-lookup"><span data-stu-id="bbf77-120">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbf77-121">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbf77-121">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bbf77-122">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="bbf77-122">**.NET Core 1.x**</span></span>

<span data-ttu-id="bbf77-123">.NET Core 1.x nécessite OpenSSL lors d’une exécution sous macOS.</span><span class="sxs-lookup"><span data-stu-id="bbf77-123">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="bbf77-124">Un moyen simple d’obtenir OpenSSL consiste à utiliser le gestionnaire de package [Homebrew (« brew »)](https://brew.sh/) pour macOS.</span><span class="sxs-lookup"><span data-stu-id="bbf77-124">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="bbf77-125">Après avoir installé *brew*, installez OpenSSL en exécutant les commandes suivantes dans une invite de Terminal (commande) :</span><span class="sxs-lookup"><span data-stu-id="bbf77-125">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="bbf77-126">Téléchargez et installez le kit SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="bbf77-126">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="bbf77-127">Si vous rencontrez des problèmes d’installation sur macOS, consultez les rubriques [Problèmes connus 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) et [Problèmes connus 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="bbf77-127">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit"></a><span data-ttu-id="bbf77-128">Augmenter la limite maximale d’ouverture de fichier</span><span class="sxs-lookup"><span data-stu-id="bbf77-128">Increase the maximum open file limit</span></span>

<span data-ttu-id="bbf77-129">La limite d’ouverture de fichier par défaut sur macOS peut ne pas suffire pour certaines charges de travail .NET Core, telles que la restauration de projets ou l’exécution de tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="bbf77-129">The default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="bbf77-130">Vous pouvez augmenter cette limite en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bbf77-130">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="bbf77-131">À l’aide d’un éditeur de texte, créez un fichier _/Library/LaunchDaemons/limit.maxfiles.plist_ et enregistrez le fichier avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="bbf77-131">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. <span data-ttu-id="bbf77-132">Dans une fenêtre de terminal, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="bbf77-132">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="bbf77-133">Redémarrez votre Mac pour appliquer ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="bbf77-133">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="bbf77-134">Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="bbf77-134">Visual Studio for Mac</span></span>

<span data-ttu-id="bbf77-135">Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbf77-135">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="bbf77-136">Toutefois, si vous voulez développer des applications .NET Core sous Mac dans un environnement de développement intégré, vous pouvez utiliser [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="bbf77-136">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="bbf77-137">Le développement .NET Core sur macOS avec Visual Studio pour Mac nécessite :</span><span class="sxs-lookup"><span data-stu-id="bbf77-137">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="bbf77-138">Une version prise en charge du système d’exploitation macOS</span><span class="sxs-lookup"><span data-stu-id="bbf77-138">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="bbf77-139">OpenSSL (.NET Core 1.x uniquement ; .NET Core 2.x utilise les services de sécurité disponibles en mode natif dans macOS)</span><span class="sxs-lookup"><span data-stu-id="bbf77-139">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="bbf77-140">.NET Core SDK pour Mac</span><span class="sxs-lookup"><span data-stu-id="bbf77-140">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="bbf77-141">Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="bbf77-141">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)
