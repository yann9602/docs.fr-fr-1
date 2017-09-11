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
ms.translationtype: HT
ms.sourcegitcommit: fd165e8745e78c76dc233540575fac841eda37aa
ms.openlocfilehash: 893999f9abcc299da4fb0923fe47c371079f695c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/24/2017

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="86a90-104">Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="86a90-104">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="86a90-105">Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86a90-105">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="86a90-106">Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86a90-106">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="86a90-107">Vos commentaires sont extrêmement précieux.</span><span class="sxs-lookup"><span data-stu-id="86a90-107">Your feedback is highly valued.</span></span> <span data-ttu-id="86a90-108">Il existe deux méthodes pour transmettre vos commentaires à l’équipe de développement Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="86a90-108">There are a two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="86a90-109">Dans Visual Studio pour Mac, sélectionnez **Aide** > **Signaler un problème** dans le menu ou **Signaler un problème** sur l’écran d’accueil, ce qui ouvre une fenêtre permettant de soumettre un rapport de bogue.</span><span class="sxs-lookup"><span data-stu-id="86a90-109">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="86a90-110">Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="86a90-110">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="86a90-111">Pour soumettre une suggestion, sélectionnez **Aide** > **Émettre une suggestion** dans le menu ou **Émettre une suggestion** sur l’écran d’accueil, ce qui vous amène à la [page Web UserVoice de Visual Studio pour Mac](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="86a90-111">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="86a90-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="86a90-112">Prerequisites</span></span>

<span data-ttu-id="86a90-113">Consultez la rubrique [Prérequis de .NET Core sur Mac](../../core/macos-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="86a90-113">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="86a90-114">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="86a90-114">Getting started</span></span>

<span data-ttu-id="86a90-115">Si vous avez déjà installé les composants requis et Visual Studio pour Mac, ignorez cette section et passez à la [création d’un projet](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="86a90-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="86a90-116">Suivez ces étapes pour installer les composants requis et Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="86a90-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="86a90-117">Téléchargez le [programme d’installation de Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="86a90-117">Download the [Visual Studio for Mac installer](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="86a90-118">Exécutez le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="86a90-118">Run the installer.</span></span> <span data-ttu-id="86a90-119">Lisez et acceptez le contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="86a90-119">Read and accept the license agreement.</span></span> <span data-ttu-id="86a90-120">Lors de l’installation, vous avez la possibilité d’installer Xamarin, une technologie de développement d’application mobile multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="86a90-120">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="86a90-121">L’installation de Xamarin et de ses composants associés est facultative pour le développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86a90-121">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="86a90-122">Pour obtenir une vue d’ensemble du processus d’installation de Visual Studio pour Mac, consultez [Présentation de Visual Studio pour Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="86a90-122">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="86a90-123">Une fois l’installation terminée, démarrez l’IDE Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="86a90-123">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="86a90-124">Création d'un projet</span><span class="sxs-lookup"><span data-stu-id="86a90-124">Creating a project</span></span>

1. <span data-ttu-id="86a90-125">Sélectionnez **Nouveau projet** sur l’écran d’accueil.</span><span class="sxs-lookup"><span data-stu-id="86a90-125">Select **New Project** on the Welcome screen.</span></span>

   ![Bouton Nouveau projet sur l’écran d’accueil Visual Studio pour Mac](./media/using-on-mac-vs/vsmac1.png)

1. <span data-ttu-id="86a90-127">Dans la boîte de dialogue **Nouveau projet**, sélectionnez **App** dans le nœud **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="86a90-127">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="86a90-128">Sélectionnez le modèle **Application console** puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="86a90-128">Select the **Console Application** template followed by **Next**.</span></span>

   ![Liste des modèles Nouveau projet](./media/using-on-mac-vs/vsmac2.png)

1. <span data-ttu-id="86a90-130">Tapez « HelloWorld » comme **nom de projet**.</span><span class="sxs-lookup"><span data-stu-id="86a90-130">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="86a90-131">Sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="86a90-131">Select **Create**.</span></span>

   ![Boîte de dialogue de configuration de votre nouvelle application console](./media/using-on-mac-vs/vsmac3.png)

1. <span data-ttu-id="86a90-133">Attendez la restauration des dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="86a90-133">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="86a90-134">Le projet comporte un seul fichier C#, *Program.cs*, contenant une classe `Program` avec une méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="86a90-134">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="86a90-135">L’instruction `Console.WriteLine` affichera « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="86a90-135">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="86a90-136">dans la console lorsque l’application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="86a90-136">to the console when the app is run.</span></span>

   ![Fenêtre principale avec le fichier Program.cs ouvert](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a><span data-ttu-id="86a90-138">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="86a90-138">Run the application</span></span>

<span data-ttu-id="86a90-139">Exécutez l’application en mode débogage à l’aide de <kbd>F5</kbd> ou en mode release avec <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="86a90-139">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![Le volet de sortie de l’application affiche Hello World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a><span data-ttu-id="86a90-141">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="86a90-141">Next step</span></span>

<span data-ttu-id="86a90-142">La rubrique [Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac](using-on-mac-vs-full-solution.md) vous montre comment créer une solution complète .NET Core qui inclut une bibliothèque réutilisable et un test unitaire.</span><span class="sxs-lookup"><span data-stu-id="86a90-142">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>

