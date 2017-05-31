---
title: Configuration requise pour .NET Core sur Windows | Microsoft Docs
description: "Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core."
keywords: ".NET core, Windows, configuration requise, dépendances, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: Human Translation
ms.sourcegitcommit: d97a1501ad25b683cbb5d7fbd8bd1b137f7f4046
ms.openlocfilehash: 582b7d7f00b939493cea6d8cb4055b6779118c14
ms.contentlocale: fr-fr
ms.lasthandoff: 04/10/2017

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

Consultez les [ notes de publication .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) pour plus d’informations sur tous les systèmes d’exploitation pris en charge.

## <a name="net-core-dependencies"></a>Dépendances .NET Core

.NET Core nécessite le package redistribuable Visual C++ lors de l’exécution sur des versions de Windows antérieures à Windows 10 et Windows Server 2016. Cette dépendance est installée automatiquement pour vous si vous utilisez le programme d’installation de .NET Core. Toutefois, vous devez installer manuellement [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=53840) si vous installez .NET Core par le biais du [script d’installation](./tools/dotnet-install-script.md) ou si vous déployez une application .NET Core autonome.

> [!NOTE]
> <em>Pour les machines Windows 7 et Windows Server 2008 uniquement :</em><br>
> Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2533623](https://support.microsoft.com/help/2533623) installé via Windows Update.

## <a name="prerequisites-with-visual-studio-2017"></a>Prérequis pour Visual Studio 2017

Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du kit de développement logiciel (SDK) .NET Core. Toutefois, si vous voulez développer des applications .NET Core sur Windows dans un environnement de développement intégré, vous pouvez utiliser [Visual Studio 2017](#visual-studio-2017).

> [!IMPORTANT]
> Même s’il est possible d’utiliser Visual Studio 2015 avec une version préliminaire des outils .NET Core, ces projets s’appuieront sur le fichier *project.json*, ce qui est maintenant déconseillé. Visual Studio 2017 utilise des fichiers de projet basés sur MSBuild. Pour plus d’informations sur les changements de format, consultez la page [Vue d’ensemble de haut niveau des modifications](./tools/cli-msbuild-architecture.md).

Pour utiliser Visual Studio 2017 afin de développer des applications .NET Core, vous devez installer la dernière version de Visual Studio en sélectionnant l’ensemble d’outils **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).
![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs_workloads.jpg)

Il existe différentes éditions de Visual Studio 2017. Vous pouvez télécharger [Visual Studio Community 2017](https://www.visualstudio.com/downloads/) gratuitement pour commencer.  Pour en savoir plus sur le processus d'installation de Visual Studio, consultez [Installation de Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio).

Pour vérifier que vous exécutez la dernière version de Visual Studio 2017, effectuez les étapes suivantes :

 * Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.
 * La boîte de dialogue **À propos de Microsoft Visual Studio** doit indiquer le numéro de version 15.0.26228.4 ou ultérieur.

Vous trouverez plus d’informations sur les modifications apportées à Visual Studio 2017 dans les [notes de publication](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).
