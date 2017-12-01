---
title: Configuration requise pour .NET Core sur Windows
description: "Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core."
author: JRAlexander
ms.author: johalex
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 16a72edde39e4857dbdfb400f195deb9975f993c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-windows"></a>Configuration requise pour .NET Core sur Windows

Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Windows. Les versions de système d’exploitation et les dépendances prises en charge ci-après s’appliquent aux trois façons de développer des applications .NET Core sur Windows :

* [Ligne de commande](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://www.visualstudio.com/downloads/)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>Versions Windows prises en charge par .NET Core

.NET Core est pris en charge par les versions suivantes de :

* Windows 7 SP1
* Windows 8.1
* Windows 10, Mise à jour anniversaire Windows 10 (version 1607) ou versions ultérieures
* Windows Server 2008 R2 SP1 (version complète ou Server Core)
* Windows Server 2012 SP1 (version complète ou Server Core)
* Windows Server 2012 R2 (version complète ou Server Core)
* Windows Server 2016 (version complète, Server Core ou Nano Server)

Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x.

Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x.

## <a name="net-core-dependencies"></a>Dépendances .NET Core

.NET core 1.1 et antérieur requiert le package redistribuable Visual C++ lors de l’exécution sur les versions de Windows antérieures à Windows 10 et Windows Server 2016. Cette dépendance est installée automatiquement par le programme d’installation de .NET Core.

Vous devez installer [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) manuellement quand :

   * vous installez .NET Core avec le [script du programme d’installation](./tools/dotnet-install-script.md) ;
   * vous déployez une application .NET Core autonome.

> [!NOTE]
> <em>Pour les machines Windows 7 et Windows Server 2008 uniquement :</em><br>
> Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2533623](https://support.microsoft.com/help/2533623) installé via Windows Update.

## <a name="prerequisites-with-visual-studio-2017"></a>Prérequis pour Visual Studio 2017

Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core.  [Visual Studio 2017](#visual-studio-2017) fournit un environnement de développement intégré pour les applications .NET Core sur Windows.

Vous trouverez plus d’informations sur les modifications apportées à Visual Studio 2017 dans les [notes de publication](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).
# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Pour développer des applications .NET Core 2.x dans Visual Studio 2017 :

 1. [Téléchargez et installez Visual Studio 2017 version 15.3.0 ou version ultérieure](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).
![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-15-3-workloads.jpg)

Une fois installé l’ensemble d’outils **Développement multiplateforme .NET Core**, Visual Studio 2017 utilise .NET Core 1.x par défaut. Installez le SDK .NET Core 2.x pour obtenir la prise en charge de .NET Core 2.x dans Visual Studio 2017.

 2. Installez le [SDK .NET Core 2.x](https://www.microsoft.com/net/download/core).
 3. Reciblez les projets .NET Core 1.x existants ou nouveaux sur .NET Core 2.x en suivant les instructions suivantes :
    * Dans le menu **Projet**, choisissez **Propriétés**. 
    * Dans le menu de sélection **framework cible**, choisissez **.NET Core 2.0**.

![Capture d’écran de la propriété de projet Application Visual Studio 2017 avec définition de l’élément de menu framework cible sur « .NET Core 2.0 »](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Une fois installé le SDK .NET Core 2.x, Visual Studio 2017 l’utilise par défaut et prend en charge les actions suivantes :

  * Ouvrir, générer et exécuter les projets .NET Core 1.x existants.
  * Recibler les projets .NET Core 1.x vers .NET Core 2.x, les générer et les exécuter.
  * Créer des projets .NET Core 2.x.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
Pur développer des applications .NET Core 1.x dans Visual Studio, [téléchargez et installez Visual Studio 2017 RTM (version 15.0.26228.4) ou version ultérieure](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).
![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs_workloads.jpg)
> [!IMPORTANT]
> Bien que vous puissiez utiliser Visual Studio 2015 pour le développement .NET Core 1.x, nous vous le déconseillons pour les raisons suivantes :
  > * Les outils .NET Core sont une préversion, qui n’est pas prise en charge.
  > * Les projets sont basés sur project.json, configuration qui est dépréciée.
>
> Pour plus d’informations sur les changements de format de projet, consultez la page [Vue d’ensemble des modifications](./tools/cli-msbuild-architecture.md).
---

>[!TIP]
  > Pour vérifier votre version de Visual Studio 2017 :
>
     > * Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.
     > * Dans la boîte de dialogue **À propos de Microsoft Visual Studio**, vérifiez le numéro de version.
>     * Pour les applications .NET Core 2.x, Visual Studio 2017 version 15.3 (26730.01) ou une version ultérieure.
>     * Pour les applications .NET Core 1.x, Visual Studio 2017 version 15.0 (26228.04) ou une version ultérieure.
