---
title: Configuration requise pour .NET Core sur Mac | Microsoft Docs
description: "Versions macOS et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS."
keywords: .NET, .NET Core, MacOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: Human Translation
ms.sourcegitcommit: 83200e452bccc20bfa82d94899514019e9d05a23
ms.openlocfilehash: 2aa685751fae9fa9771fa1cd86d211f742e06932
ms.contentlocale: fr-fr
ms.lasthandoff: 07/05/2017

---

<a id="prerequisites-for-net-core-on-mac" class="xliff"></a>

# Configuration requise pour .NET Core sur Mac

Cet article vous présente les versions macOS et les dépendances .NET Core prises en charge nécessaires pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS. Les versions de système d’exploitation et dépendances prises en charge suivantes s’appliquent aux trois méthodes de développement des applications .NET Core sur un Mac : via la [ligne de commande de votre éditeur favori](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/) et [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/).

<a id="supported-macos-versions" class="xliff"></a>

## Versions macOS prises en charge

.NET Core est pris en charge par les versions suivantes de macOS :

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Consultez les [notes de publication de .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge.

<a id="net-core-dependencies" class="xliff"></a>

## Dépendances .NET Core

**.NET Core 1.x**

.NET Core 1.x nécessite OpenSSL lors d’une exécution sous macOS. Un moyen simple d’obtenir OpenSSL consiste à utiliser le gestionnaire de package [Homebrew (« brew »)](https://brew.sh/) pour macOS. Après avoir installé *brew*, installez OpenSSL en exécutant les commandes suivantes dans une invite de Terminal (commande) :

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Téléchargez et installez le kit SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core). Si vous rencontrez des problèmes d’installation sur macOS, consultez [Problèmes connus et solutions de contournement](https://github.com/dotnet/core/blob/master/cli/known-issues.md).

**.NET Core 2.x**

Téléchargez et installez le kit SDK .NET Core à partir de [Téléchargements .NET](https://www.microsoft.com/net/download/core). Si vous rencontrez des problèmes d’installation sur macOS, consultez [Problèmes connus et solutions de contournement](https://github.com/dotnet/core/blob/master/cli/known-issues.md).

<a id="visual-studio-for-mac" class="xliff"></a>

## Visual Studio pour Mac

Le développement .NET Core sur macOS avec Visual Studio pour Mac nécessite :

* Une version prise en charge du système d’exploitation macOS
* OpenSSL (.NET Core 1.x uniquement ; .NET Core 2.x utilise les services de sécurité disponibles en mode natif dans macOS)
* .NET Core SDK pour Mac
* [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

