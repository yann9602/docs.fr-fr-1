---
title: "Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac"
description: "Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core."
keywords: .NET, .NET Core, MacOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8902e849-dd17-42c0-8264-cc7ae3927a0c
ms.openlocfilehash: 893999f9abcc299da4fb0923fe47c371079f695c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac

Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core. Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core.

> [!NOTE]
> Vos commentaires sont extrêmement précieux. Il existe deux méthodes pour transmettre vos commentaires à l’équipe de développement Visual Studio pour Mac :
> * Dans Visual Studio pour Mac, sélectionnez **Aide** > **Signaler un problème** dans le menu ou **Signaler un problème** sur l’écran d’accueil, ce qui ouvre une fenêtre permettant de soumettre un rapport de bogue. Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Pour soumettre une suggestion, sélectionnez **Aide** > **Émettre une suggestion** dans le menu ou **Émettre une suggestion** sur l’écran d’accueil, ce qui vous amène à la [page Web UserVoice de Visual Studio pour Mac](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Prérequis

Consultez la rubrique [Prérequis de .NET Core sur Mac](../../core/macos-prerequisites.md).

## <a name="getting-started"></a>Bien démarrer

Si vous avez déjà installé les composants requis et Visual Studio pour Mac, ignorez cette section et passez à la [création d’un projet](#creating-a-project). Suivez ces étapes pour installer les composants requis et Visual Studio pour Mac :

Téléchargez le [programme d’installation de Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/). Exécutez le programme d’installation. Lisez et acceptez le contrat de licence. Lors de l’installation, vous avez la possibilité d’installer Xamarin, une technologie de développement d’application mobile multiplateforme. L’installation de Xamarin et de ses composants associés est facultative pour le développement .NET Core. Pour obtenir une vue d’ensemble du processus d’installation de Visual Studio pour Mac, consultez [Présentation de Visual Studio pour Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Une fois l’installation terminée, démarrez l’IDE Visual Studio pour Mac.

## <a name="creating-a-project"></a>Création d'un projet

1. Sélectionnez **Nouveau projet** sur l’écran d’accueil.

   ![Bouton Nouveau projet sur l’écran d’accueil Visual Studio pour Mac](./media/using-on-mac-vs/vsmac1.png)

1. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **App** dans le nœud **.NET Core**. Sélectionnez le modèle **Application console** puis **Suivant**.

   ![Liste des modèles Nouveau projet](./media/using-on-mac-vs/vsmac2.png)

1. Tapez « HelloWorld » comme **nom de projet**. Sélectionnez **Créer**.

   ![Boîte de dialogue de configuration de votre nouvelle application console](./media/using-on-mac-vs/vsmac3.png)

1. Attendez la restauration des dépendances du projet. Le projet comporte un seul fichier C#, *Program.cs*, contenant une classe `Program` avec une méthode `Main`. L’instruction `Console.WriteLine` affichera « Hello World! » dans la console lorsque l’application est exécutée.

   ![Fenêtre principale avec le fichier Program.cs ouvert](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a>Exécuter l'application

Exécutez l’application en mode débogage à l’aide de <kbd>F5</kbd> ou en mode release avec <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![Le volet de sortie de l’application affiche Hello World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a>Étape suivante

La rubrique [Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac](using-on-mac-vs-full-solution.md) vous montre comment créer une solution complète .NET Core qui inclut une bibliothèque réutilisable et un test unitaire.
