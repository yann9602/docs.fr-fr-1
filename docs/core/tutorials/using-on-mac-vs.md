---
title: "Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac | Microsoft Docs"
description: "Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core."
keywords: .NET, .NET Core, MacOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8902e849-dd17-42c0-8264-cc7ae3927a0c
ms.translationtype: Human Translation
ms.sourcegitcommit: 83200e452bccc20bfa82d94899514019e9d05a23
ms.openlocfilehash: c377d0669efed9abb50965652d286ceb6fad3299
ms.contentlocale: fr-fr
ms.lasthandoff: 07/05/2017

---

<a id="getting-started-with-net-core-on-macos-using-visual-studio-for-mac" class="xliff"></a>

# Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac

Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core. Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core.

> [!NOTE]
> Visual Studio pour Mac est un logiciel en version préliminaire. Comme avec toutes les versions préliminaires des produits Microsoft, vos commentaires sont très appréciés. Il existe deux méthodes pour transmettre vos commentaires à l’équipe de développement Visual Studio pour Mac :
> * Dans Visual Studio pour Mac, sélectionnez **Aide > Signaler un problème** dans le menu ou **Signaler un problème** dans l’écran d’accueil, qui ouvre une fenêtre vous permettant de remplir un rapport de bogue.
> * Pour soumettre une suggestion, sélectionnez **Aide > Fournir une suggestion** dans le menu ou **Four une suggestion** dans l’écran d’accueil, ce qui vous amène à la page Web [UserVoice Visual Studio pour Mac](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

<a id="prerequisites" class="xliff"></a>

## Prérequis

Pour plus d’informations sur la configuration requise, consultez la [configuration requise de .NET Core sur Mac](../../core/macos-prerequisites.md).

<a id="getting-started" class="xliff"></a>

## Bien démarrer

Si vous avez déjà installé les composants requis et Visual Studio pour Mac, ignorez cette section et passez à la [création d’un projet](#creating-a-project). Suivez ces étapes pour installer les composants requis et Visual Studio pour Mac :

Téléchargez le [programme d’installation de Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/). Exécutez le programme d’installation. Lisez et acceptez le contrat de licence. Lors de l’installation, vous avez la possibilité d’installer Xamarin, une technologie de développement d’application mobile multiplateforme. L’installation de Xamarin et de ses composants associés est facultative pour le développement .NET Core. Pour obtenir une vue d’ensemble du processus d’installation de Visual Studio pour Mac, consultez [Présentation de Visual Studio pour Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Une fois l’installation terminée, démarrez l’IDE Visual Studio pour Mac.

<a id="creating-a-project" class="xliff"></a>

## Création d'un projet

1. Sélectionnez **Nouveau projet** sur l’écran d’accueil.

   ![Bouton Nouveau projet sur l’écran d’accueil Visual Studio pour Mac](./media/using-on-mac-vs/vsmac1.png)

1. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **App** dans le nœud **.NET Core**. Sélectionnez le modèle **Application console** puis **Suivant**.

   ![Liste des modèles Nouveau projet](./media/using-on-mac-vs/vsmac2.png)

1. Tapez « HelloWorld » comme **nom de projet**. Sélectionnez **Créer**.

   ![Boîte de dialogue de configuration de votre nouvelle application console](./media/using-on-mac-vs/vsmac3.png)

1. Attendez la restauration des dépendances du projet. Le projet comporte un seul fichier C#, *Program.cs*, contenant une classe `Program` avec une méthode `Main`. L’instruction `Console.WriteLine` affichera « Hello World! » dans la console lorsque l’application est exécutée.

   ![Fenêtre principale avec le fichier Program.cs ouvert](./media/using-on-mac-vs/vsmac4.png)

<a id="run-the-application" class="xliff"></a>

## Exécuter l'application

Exécutez l’application en mode débogage à l’aide de <kbd>F5</kbd> ou en mode release avec <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![Le volet de sortie de l’application affiche Hello World!](./media/using-on-mac-vs/vsmac5.png)

<a id="next-step" class="xliff"></a>

## Étape suivante

La rubrique [Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac](using-on-mac-vs-full-solution.md) vous montre comment créer une solution complète .NET Core qui inclut une bibliothèque réutilisable et un test unitaire.

