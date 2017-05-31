---
title: Configuration requise pour .NET Core sur Mac | Microsoft Docs
description: "Versions macOS et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS."
keywords: .NET, .NET Core, MacOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 03/16/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: Human Translation
ms.sourcegitcommit: d97a1501ad25b683cbb5d7fbd8bd1b137f7f4046
ms.openlocfilehash: 9574d76564b34f500674662f2b2bb8f4d50976f5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/10/2017

---

# <a name="prerequisites-for-net-core-on-mac"></a>Configuration requise pour .NET Core sur Mac

Cet article vous présente les versions macOS et les dépendances .NET Core prises en charge nécessaires pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS. Les versions de système d’exploitation et dépendances prises en charge suivantes s’appliquent aux trois méthodes de développement des applications .NET Core sur un Mac : via la [ligne de commande de votre éditeur favori](tutorials/using-with-xplat-cli.md), [Visual Studio Code (VS Code)](https://code.visualstudio.com/) et [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Versions macOS prises en charge

.NET Core est pris en charge par les versions suivantes de macOS :

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Consultez les [notes de publication de .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge.

## <a name="net-core-dependencies"></a>Dépendances .NET Core

.NET Core nécessite OpenSSL lors d’une exécution sous macOS. Un moyen simple d’obtenir OpenSSL consiste à utiliser le gestionnaire de package [Homebrew (« brew »)](https://brew.sh/) pour macOS. Après avoir installé *brew*, installez OpenSSL en exécutant les commandes suivantes dans une invite de Terminal (commande) :

```Terminal
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Après l’installation d’OpenSSL, téléchargez et installez le SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core). Si vous rencontrez des problèmes d’installation sur macOS, consultez [Problèmes connus et solutions de contournement](https://github.com/dotnet/core/blob/master/cli/known-issues.md).

## <a name="visual-studio-for-mac"></a>Visual Studio pour Mac

Le développement .NET Core sur macOS avec Visual Studio pour Mac nécessite :

* Une version prise en charge du système d’exploitation macOS
* Openssl
* .NET Core SDK pour Mac
* [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

