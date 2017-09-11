---
title: "Bien démarrer avec C# et Visual Studio Code - Guide C# | Microsoft Docs"
description: "Découvrez comment créer et déboguer votre première application .NET Core en C# à l’aide de Visual Studio Code."
keywords: "C#, bien démarrer, acquisition, installer, Visual Studio Code, multiplateforme"
author: kendrahavens
ms.author: mairaw
ms.date: 8/01/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.translationtype: HT
ms.sourcegitcommit: 3bd8800e7410ae4a3b89f5962af957789edd48b0
ms.openlocfilehash: a10fda5663f0a49069388ee8ee7a9ebb575cd549
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---

# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="4672d-104">Bien démarrer avec C# et Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4672d-104">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="4672d-105">.NET Core vous offre une plateforme rapide et évolutive pour la création d’applications qui s’exécutent sur Windows, Linux et Mac OS.</span><span class="sxs-lookup"><span data-stu-id="4672d-105">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="4672d-106">Utilisez Visual Studio Code avec l’extension de langage C# pour une expérience d’édition puissante avec prise en charge complète de C# IntelliSense (saisie semi-automatique intelligente de code).</span><span class="sxs-lookup"><span data-stu-id="4672d-106">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4672d-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4672d-107">Prerequisites</span></span>

1. <span data-ttu-id="4672d-108">Installez [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="4672d-108">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="4672d-109">Installez le [SDK .NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="4672d-109">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="4672d-110">Installez [l’extension C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) à partir de la Place de marché Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4672d-110">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) from the Visual Studio Code Marketplace.</span></span>

## <a name="hello-world"></a><span data-ttu-id="4672d-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="4672d-111">Hello World</span></span>

<span data-ttu-id="4672d-112">Commençons par un programme « Hello World » simple sur .NET Core :</span><span class="sxs-lookup"><span data-stu-id="4672d-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="4672d-113">Ouvrez un projet :</span><span class="sxs-lookup"><span data-stu-id="4672d-113">Open a project:</span></span>

    * <span data-ttu-id="4672d-114">Ouvrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4672d-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="4672d-115">Cliquez sur l’icône Explorer dans le menu de gauche, puis sur **Ouvrir le dossier**.</span><span class="sxs-lookup"><span data-stu-id="4672d-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="4672d-116">Sélectionnez le dossier dans lequel vous souhaitez que votre projet C# se trouve et cliquez sur **Sélectionner le dossier**.</span><span class="sxs-lookup"><span data-stu-id="4672d-116">Select the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="4672d-117">Dans notre exemple, nous allons créer un dossier pour notre projet nommé « HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="4672d-117">For our example, we'll create a folder for our project named 'HelloWorld'.</span></span> 

  ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

    * <span data-ttu-id="4672d-119">Vous pouvez également sélectionner **Fichier** > **Ouvrir le dossier** dans le menu principal pour ouvrir le dossier de votre projet.</span><span class="sxs-lookup"><span data-stu-id="4672d-119">Alternatively, you can select **File** > **Open Folder** from the main menu to open your project folder.</span></span>

2. <span data-ttu-id="4672d-120">Initialiser un projet C# :</span><span class="sxs-lookup"><span data-stu-id="4672d-120">Initialize a C# project:</span></span>
    * <span data-ttu-id="4672d-121">Ouvrez le terminal intégré à partir de Visual Studio Code en tapant sur <kbd>CTRL</kbd>+<kbd>\\`</kbd> (accent grave).</span><span class="sxs-lookup"><span data-stu-id="4672d-121">Open the Integrated Terminal from Visual Studio Code by typing <kbd>CTRL</kbd>+<kbd>\\`</kbd> (backtick).</span></span> <span data-ttu-id="4672d-122">Vous pouvez également sélectionner **Affichage** > **Terminal intégré** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="4672d-122">Alternatively, you can select **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="4672d-123">Dans la fenêtre de Terminal, tapez `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="4672d-123">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="4672d-124">Cela crée un fichier `Program.cs` dans votre dossier avec un programme simple « Hello World » déjà écrit, ainsi qu’un fichier de projet C# nommé `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="4672d-124">This creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

  ![La nouvelle commande dotnet](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="4672d-126">Résolution des ressources de génération :</span><span class="sxs-lookup"><span data-stu-id="4672d-126">Resolve the build assets:</span></span>

    * <span data-ttu-id="4672d-127">Pour **.NET Core 1.1**, tapez `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="4672d-127">For **.NET Core 1.1**, type `dotnet restore`.</span></span> <span data-ttu-id="4672d-128">Exécuter `dotnet restore` vous donne accès aux packages .NET Core qui sont nécessaires pour générer votre projet.</span><span class="sxs-lookup"><span data-stu-id="4672d-128">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

   ![La commande dotnet restore](media/with-visual-studio-code/dotnetrestore.png)

    * <span data-ttu-id="4672d-130">Pour **.NET Core 2.0**, cette étape est facultative.</span><span class="sxs-lookup"><span data-stu-id="4672d-130">For **.NET Core 2.0**, this step is optional.</span></span> <span data-ttu-id="4672d-131">La commande `dotnet restore` s’exécute automatiquement lorsqu’un nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="4672d-131">The `dotnet restore` command executes automatically when a new project is created.</span></span>

4. <span data-ttu-id="4672d-132">Exécutez le programme Hello World :</span><span class="sxs-lookup"><span data-stu-id="4672d-132">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="4672d-133">Tapez `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="4672d-133">Type `dotnet run`.</span></span> 

  ![La commande dotnet run](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="4672d-135">Vous pouvez également regarder un court didacticiel vidéo pour plus d’informations sur la configuration sur [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="4672d-135">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="4672d-136">Débogage</span><span class="sxs-lookup"><span data-stu-id="4672d-136">Debug</span></span>
1. <span data-ttu-id="4672d-137">Ouvrez *Program.cs* en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="4672d-137">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="4672d-138">La première fois que vous ouvrez un fichier C# dans Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) se charge dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="4672d-138">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) will load in the editor.</span></span>

  ![Ouvrez le fichier Program.cs](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="4672d-140">Visual Studio Code vous invite à ajouter les ressources manquantes pour générer et déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="4672d-140">Visual Studio Code will prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="4672d-141">Sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="4672d-141">Select **Yes**.</span></span> 

  ![Invite pour les fichiers manquants](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="4672d-143">Pour ouvrir la vue de débogage, cliquez sur l’icône de débogage dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="4672d-143">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

  ![Ouvrez l'onglet Déboguer](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="4672d-145">Cherchez la flèche verte en haut du volet.</span><span class="sxs-lookup"><span data-stu-id="4672d-145">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="4672d-146">Assurez-vous que `.NET Core Launch (console)` est sélectionné dans la liste déroulante à côté du volet.</span><span class="sxs-lookup"><span data-stu-id="4672d-146">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

  ![Sélection de .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="4672d-148">Ajoutez un point d’arrêt à votre projet en cliquant sur la **Marge de l’éditeur** (l’espace à gauche des numéros de ligne dans l’éditeur) à côté de la ligne 9.</span><span class="sxs-lookup"><span data-stu-id="4672d-148">Add a breakpoint to your project by clicking on the **editor margin** (the space on the left of the line numbers in the editor) next to line 9.</span></span>

  ![Définition d'un point d'arrêt](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="4672d-150">Sélectionnez <kbd>F5</kbd> ou sur la flèche verte pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="4672d-150">Select <kbd>F5</kbd> or the green arrow to start debugging.</span></span> <span data-ttu-id="4672d-151">Le débogueur arrête l’exécution de votre programme lorsqu’il atteint le point d’arrêt que vous avez défini à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="4672d-151">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="4672d-152">Pendant le débogage, vous pouvez afficher vos variables locales dans le volet supérieur gauche ou utiliser la console de débogage.</span><span class="sxs-lookup"><span data-stu-id="4672d-152">While debugging you can view your local variables in the top left pane or use the debug console.</span></span>

  ![Exécuter et déboguer](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="4672d-154">Cliquez sur la flèche verte en haut pour continuer le débogage, ou sélectionnez le carré rouge en haut pour arrêter.</span><span class="sxs-lookup"><span data-stu-id="4672d-154">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="4672d-155">Pour obtenir plus d’informations et de conseils de dépannage sur le débogage de .NET Core avec OmniSharp dans Visual Studio Code, consultez [Instructions de configuration du débogueur .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="4672d-155">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4672d-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4672d-156">See also</span></span>
<span data-ttu-id="4672d-157">[Configuration de Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="4672d-157">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="4672d-158">Débogage dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4672d-158">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)

