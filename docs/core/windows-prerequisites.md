---
title: Configuration requise pour .NET Core sur Windows | Microsoft Docs
description: "Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core."
keywords: ".NET core, Windows, configuration requise, dépendances, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 01/05/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: a8019c9fc25ef458aa555743e61cd83a3beb11ed
ms.openlocfilehash: b5c088da7d1155414a08995ae0d72154af891190
ms.lasthandoff: 01/24/2017

---

# <a name="prerequisites-for-net-core-on-windows"></a>Configuration requise pour .NET Core sur Windows

Cet article détaille les dépendances nécessaires pour déployer et exécuter des applications .NET Core sur des machines Windows, et développer avec Visual Studio.

## <a name="supported-windows-versions"></a>Versions prises en charge de Windows

.NET Core est pris en charge par les versions suivantes de Windows :

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (version complète ou Server Core)
* Windows Server 2012 SP1 (version complète ou Server Core)
* Windows Server 2012 R2 SP1 (version complète ou Server Core)
* Windows Server 2016 (version complète, Server Core ou Nano Server)

Tous les [systèmes d’exploitation pris en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md#rtm-platform-support) sont répertoriés dans les [notes de publication de .NET Core 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md).

## <a name="net-core-dependencies"></a>Dépendances .NET Core

.NET Core nécessite le package redistribuable Visual C++ lors de l’exécution sur des versions de Windows antérieures à Windows 10 et Windows Server 2016. Cette dépendance est installée automatiquement pour vous si vous utilisez le programme d’installation de .NET Core. Toutefois, vous devez installer manuellement le [Package redistribuable Visual C++ pour Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145) si vous installez .NET Core via le [script d’installation](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/dotnet-install-script) ou si vous déployez une application .NET Core autonome.

> [!NOTE]
> <em>Pour les machines Windows 7 et Windows Server 2008 uniquement :</em><br>
> Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2533623](https://support.microsoft.com/en-us/kb/2533623) installé via Windows Update.

## <a name="prerequisites-with-visual-studio"></a>Configuration requise pour Visual Studio

Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du kit de développement logiciel (SDK) .NET Core. Toutefois, si vous souhaitez développer des applications .NET Core sur Windows avec Visual Studio, il existe deux versions que vous pouvez utiliser :

* [Visual Studio 2015](#visual-studio-2015)
* [Visual Studio 2017 RC](#visual-studio-2017-rc)

Les projets créés avec Visual Studio 2015 seront basés sur project.json par défaut alors que les projets créés avec Visual Studio 2017 RC seront toujours basés sur MSBuild. Pour plus d’informations sur les changements de format, consultez la page [Vue d’ensemble de haut niveau des modifications](./preview3/tools/layering.md).

### <a name="visual-studio-2015"></a>Visual Studio 2015

Si vous souhaitez utiliser Visual Studio 2015 pour développer des applications .NET Core, vous aurez besoin de ce qui suit :

* Visual Studio 2015 Update 3.3 ou version ultérieure.

   Il existe différentes [éditions](https://www.visualstudio.com/vs/compare) de Visual Studio 2015. Vous pouvez télécharger [Visual Studio Community 2015](https://www.visualstudio.com/downloads/) gratuitement pour commencer. 

   Pour vérifier que vous exécutez bien [Visual Studio 2015 Update 3.3](https://msdn.microsoft.com/library/mt752379.aspx), effectuez ce qui suit :

   * Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.
   * La boîte de dialogue **À propos de Microsoft Visual Studio** doit indiquer le numéro de version 14.0.25424.00 ou supérieur, ainsi que « Update 3 ».
   * Si vous n’avez pas Update 3, vous devez au préalable télécharger et installer [Visual Studio 2015 Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).
   * Si vous avez Update 3, mais que le numéro de version est inférieur à 14.0.25424.00, vous devez télécharger et installer [Visual Studio 2015 Update 3.3](https://msdn.microsoft.com/library/mt752379.aspx).

   Vous trouverez des informations complémentaires sur les modifications apportées à Update 3 dans les [notes de publication](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).

* L’extension du Gestionnaire de packages NuGet pour Visual Studio

   NuGet est le gestionnaire de packages pour la plateforme de développement Microsoft constituée notamment de .NET Core. Vous avez besoin de [NuGet 3.5.0-beta](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) ou d’une version ultérieure pour générer des applications .NET Core.

* .NET Core Tooling Preview 2

   Téléchargez et installez [.NET Core 1.0.1 - VS 2015 Tooling Preview 2][sdk]. 

   Le package d’outils .NET Core installe .NET Core, des modèles de projet et d’autres outils pour Visual Studio 2015.

   > [!NOTE]
   > Pour l’heure, vous ne pouvez pas télécharger de programme d’installation en mode hors connexion pour [.NET Core 1.0.1 - VS 2015 Tooling Preview 2][sdk]. Vous devez en effet télécharger le [programme d’amorçage normal][sdk] et l’exécuter avec une option de ligne de commande (p.ex., `/layout c:\path`) pour obtenir une configuration hors connexion. Après quoi, il peut être utilisé comme un programme d’installation en mode hors connexion : il suffit d’exécuter le fichier exécutable à partir du chemin local. S’agissant d’une configuration complète, notez que cette procédure télécharge l’ensemble des packages pour tous les langages pris en charge, ce qui représente une taille d’environ 1 Go.

### <a name="visual-studio-2017-rc"></a>Visual Studio 2017 RC

Si vous souhaitez utiliser Visual Studio 2017 RC pour développer des applications .NET Core, vous devez disposer de la dernière version de Visual Studio RC installée avec la charge de travail « .NET Core et Docker (préversion) » sélectionnée. 

Il existe différentes éditions de Visual Studio 2017 RC. Vous pouvez télécharger gratuitement [Visual Studio Community 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/#downloadvs) pour commencer.  Pour en savoir plus sur le processus d'installation de Visual Studio, consultez [Installation de Visual Studio](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio) 2017 REC.

Pour vérifier que vous exécutez la dernière version de Visual Studio 2017 RC, procédez comme suit :

* Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.
* La boîte de dialogue **À propos de Microsoft Visual Studio** doit indiquer le numéro de version 15.0.26020.0 ou supérieur.

Vous trouverez des informations complémentaires sur les modifications apportées à Visual Studio 2017 RC dans les [notes de publication](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes).

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546

