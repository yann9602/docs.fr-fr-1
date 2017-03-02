---
title: "Vue d’ensemble du SDK .NET Core"
description: "Vue d’ensemble du SDK .NET Core"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 41093464c0dc2631217d89e2e715d05b78051284
ms.lasthandoff: 03/02/2017

---

# <a name="net-core-sdk-overview"></a>Vue d’ensemble du SDK .NET Core 

## <a name="introduction"></a>Introduction
Le Kit de développement logiciel (SDK) .NET Core est un ensemble de bibliothèques et d’outils qui permettent aux développeurs de créer des applications et des bibliothèques .NET Core. Il s’agit du package que les développeurs voudront très probablement se procurer. 

Il comprend les composants suivants :

1. Outils en ligne de commande .NET Core servant à générer des applications.
2. Bibliothèques et runtime .NET Core permettant de générer et d’exécuter des applications.
3. Pilote `dotnet` permettant d’exécuter les [commandes CLI](tools/index.md), ainsi que les applications en cours d’exécution.


## <a name="acquiring-the-net-core-sdk"></a>Obtention du SDK .NET Core
Comme pour n’importe quel ensemble d’outils, la première étape consiste à se procurer les outils sur l’ordinateur. Selon le cas, vous pouvez utiliser les programmes d’installation natifs pour installer le SDK ou utiliser le script de l’interpréteur de commandes d’installation.

Les programmes d’installation natifs s’adressent principalement aux ordinateurs des développeurs. Le SDK est distribué selon le mécanisme d’installation natif de chaque plateforme prise en charge, par exemple des packages DEB sur Ubuntu ou des ensemble MSI sur Windows. Ces programmes d’installation installent et configurent l’environnement comme il se doit pour permettre à l’utilisateur d’exploiter le SDK de suite après l’installation. Cependant, ils nécessitent aussi de disposer de privilèges d’administration sur l’ordinateur. Vous pouvez consulter les instructions d’installation dans la [page de prise en main de .NET Core](https://aka.ms/dotnetcoregs).

Les scripts d’installation, quant à eux, ne nécessitent pas de privilèges d’administration. En revanche, ils n’installent pas les prérequis sur l’ordinateur ; vous devez tous les installer manuellement. Les scripts visent principalement à configurer les serveurs de builds et permettent d’installer les outils sans privilèges d’administration (notez les mises en garde concernant les prérequis répertoriés ci-dessus). Vous trouverez des informations complémentaires dans la [rubrique de référence sur les scripts d’installation](tools/dotnet-install-script.md). Si vous voulez savoir comment configurer le SDK sur votre serveur de builds CI, vous pouvez consulter le document qui traite de l’utilisation du [SDK avec les serveurs CI](tools/using-ci-with-cli.md). 

Par défaut, le SDK s’installe « côte à côte » (SxS). Cela signifie que plusieurs versions des outils CLI peuvent coexister à un moment donné sur un même ordinateur. La façon dont la version appropriée est utilisée est expliquée plus en détail dans la [section Pilote](tools/index.md#driver) de la rubrique Outils en ligne de commande .NET Core.
