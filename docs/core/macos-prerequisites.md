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

# <a name="prerequisites-for-net-core-on-mac"></a>Configuration requise pour .NET Core sur Mac

Cet article vous présente les versions macOS et les dépendances .NET Core prises en charge nécessaires pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS. Les versions de système d’exploitation et dépendances prises en charge suivantes s’appliquent aux trois méthodes de développement des applications .NET Core sur un Mac : via la [ligne de commande de votre éditeur favori](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/) et [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Versions macOS prises en charge

.NET Core est pris en charge par les versions suivantes de macOS :

* macOS 10.12 "Sierra"
* macOS 10.11 « El Capitan » (.NET Core 1.x uniquement)

Consultez la page [Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions) pour obtenir la liste complète des systèmes d’exploitation pris en charge.

## <a name="net-core-dependencies"></a>Dépendances .NET Core

**.NET Core 1.x**

.NET Core 1.x nécessite OpenSSL lors d’une exécution sous macOS. Un moyen simple d’obtenir OpenSSL consiste à utiliser le gestionnaire de package [Homebrew (« brew »)](https://brew.sh/) pour macOS. Après avoir installé *brew*, installez OpenSSL en exécutant les commandes suivantes dans une invite de Terminal (commande) :

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Téléchargez et installez le kit SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core). Si vous rencontrez des problèmes d’installation sur macOS, consultez les rubriques [Problèmes connus 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) et [Problèmes connus 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).

**.NET Core 2.x**

Téléchargez et installez le kit SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core). Si vous rencontrez des problèmes d’installation sur macOS, consultez la rubrique [Problèmes connus](https://github.com/dotnet/core/tree/master/release-notes/2.0) associée à la version installée.

## <a name="visual-studio-for-mac"></a>Visual Studio pour Mac

Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core. Toutefois, si vous voulez développer des applications .NET Core sous Mac dans un environnement de développement intégré, vous pouvez utiliser [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/). 

Le développement .NET Core sur macOS avec Visual Studio pour Mac nécessite :

* Une version prise en charge du système d’exploitation macOS
* OpenSSL (.NET Core 1.x uniquement ; .NET Core 2.x utilise les services de sécurité disponibles en mode natif dans macOS)
* .NET Core SDK pour Mac
* [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

