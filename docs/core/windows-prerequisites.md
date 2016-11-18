---
title: "Prérequis pour .NET Core"
description: "Prérequis pour .NET Core"
keywords: .NET, .NET Core
author: billwagner
manager: wpickett
ms.date: 09/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: 130b94a745b0e3222e205d8af26194239130ec9c
ms.openlocfilehash: 2e6483b3f1b8b9e1f36a0f4f7377319871fd5674

---

# <a name="prerequisites-for-windows-development"></a>Prérequis pour le développement Windows

Le développement .NET Core sur Windows avec Visual Studio nécessite :

* Une version prise en charge du client ou du système d’exploitation Windows
* Visual Studio 2015 Update 3.3 ou version ultérieure
* L’extension du Gestionnaire de packages NuGet pour Visual Studio
* .NET Core Tooling Preview 2

## <a name="supported-windows-versions"></a>Versions prises en charge de Windows

.NET Core est pris en charge par les versions suivantes de Windows :

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (version complète ou Server Core)
* Windows Server 2012 SP1 (version complète ou Server Core)
* Windows Server 2012 R2 SP1 (version complète ou Server Core)
* Windows Server 2016 (version complète, Server Core ou Nano Server)

Tous les [systèmes d’exploitation pris en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md#rtm-platform-support) sont répertoriés dans les [notes de publication de .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md).

## <a name="net-core-dependencies"></a>Dépendances .NET Core

.NET Core nécessite le package Redistribuable VC++ pour une exécution sur Windows. Il est installé automatiquement par le programme d’installation de .NET Core. Vous devez installer manuellement le package Redistribuable Visual C++ si vous installez .NET Core via le script du programme d’installation (`dotnet-install.ps1`). 

La version du package Redistribuable Visual C++ varie en fonction de la version de Windows.

* Windows 10
    * [Package Redistribuable Visual C++ pour Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
* Windows 7+ (pas Windows 10)
    * Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2533623](https://support.microsoft.com/en-us/kb/2533623) installé via Windows Update.
    * [Mise à jour de Universal CRT](https://www.microsoft.com/en-us/download/details.aspx?id=48234) (vous trouverez des informations plus détaillées sur Universal CRT dans [ce billet de blog](https://blogs.msdn.microsoft.com/vcblog/2015/03/03/introducing-the-universal-crt/))

## <a name="visual-studio"></a>Visual Studio

Vous avez besoin de Visual Studio 2015 pour développer des applications .NET Core. Vous pouvez télécharger [Visual Studio Community 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs) gratuitement. 

Vérifiez que vous exécutez bien [Visual Studio 2015 Update 3.3](https://msdn.microsoft.com/library/mt752379.aspx) :

* Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.
* La boîte de dialogue **À propos de Microsoft Visual Studio** doit indiquer le numéro de version 14.0.25424.00 ou supérieur, ainsi que « Update 3 ».
* Si vous n’avez pas Update 3, vous devez au préalable télécharger et installer [Visual Studio 2015 Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).
* Si vous avez Update 3, mais que le numéro de version est inférieur à 14.0.25424.00, vous devez télécharger et installer [Visual Studio 2015 Update 3.3](https://msdn.microsoft.com/library/mt752379.aspx).

Vous trouverez des informations complémentaires sur les modifications apportées à Update 3 dans les [notes de publication](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).

## <a name="nuget-manager-extension-for-visual-studio"></a>L’extension du Gestionnaire de packages NuGet pour Visual Studio

NuGet est le gestionnaire de packages pour la plateforme de développement Microsoft constituée notamment de .NET Core. Vous avez besoin de [NuGet 3.5.0](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) ou d’une version ultérieure pour générer des applications .NET Core.

## <a name="net-core-tools-for-visual-studio-2015"></a>Outils .NET Core pour Visual Studio 2015

Téléchargez et installez [.NET Core 1.0.1 - VS 2015 Tooling Preview 2][sdk]. 

Le package d’outils .NET Core installe .NET Core, des modèles de projet et d’autres outils pour Visual Studio 2015.

> [!NOTE]
Pour l’heure, vous ne pouvez pas télécharger de programme d’installation en mode hors connexion pour [.NET Core 1.0.1 - VS 2015 Tooling Preview 2][sdk]. Vous devez en effet télécharger le [programme d’amorçage normal][sdk] et l’exécuter avec une option de ligne de commande (p.ex., `/layout c:\path`) pour obtenir une configuration hors connexion. Après quoi, il peut être utilisé comme un programme d’installation en mode hors connexion : il suffit d’exécuter le fichier exécutable à partir du chemin local. S’agissant d’une configuration complète, notez que cette procédure télécharge l’ensemble des packages pour tous les langages pris en charge, ce qui représente une taille d’environ 1 Go.

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546



<!--HONumber=Nov16_HO3-->


