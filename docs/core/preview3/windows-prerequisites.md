---
title: "Prérequis pour .NET Core (outils Preview 3)"
description: "Prérequis pour .NET Core (outils Preview 3)"
keywords: .NET, .NET Core
author: billwagner
ms.author: wiwagn
ms.date: 09/15/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: 07b62bd7163193eff8dc8f61fda7a45a924bba2b
ms.openlocfilehash: ee4ccba7c06f0a7f67e3fe59c885febf895235fd

---

# <a name="prerequisites-for-windows-development-preview-3-tooling"></a>Prérequis pour le développement Windows (outils Preview 3)

Le développement .NET Core sur Windows avec Visual Studio nécessite :

* Une version prise en charge du client ou du système d’exploitation Windows
* Visual Studio 2017 RC ou version ultérieure
* Outils .NET Core Preview 3

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

Vous pouvez développer des applications .NET Core avec n’importe quel éditeur à l’aide des outils en ligne de commande .NET Core, mais si vous souhaitez utiliser Visual Studio et la version Preview 3 des outils .NET Core, vous avez besoin de Visual Studio 2017 RC ou version ultérieure. Vous pouvez télécharger gratuitement [Visual Studio Community 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/). 

Vérifiez que vous exécutez bien Visual Studio 2017 RC :

* Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.
* La boîte de dialogue **À propos de Microsoft Visual Studio** doit indiquer le numéro de version 15.0.25831.1 ou supérieur.

Vous trouverez des informations complémentaires sur les modifications apportées à Visual Studio 2017 RC dans les [notes de publication](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes).

Vérifiez que vous avez installé la charge de travail « .NET Core et Docker (préversion) » pendant l’installation. Si vous ne l’avez pas fait, vous pouvez réexécuter le programme d’installation et la sélectionner.



<!--HONumber=Nov16_HO3-->


