---
title: 'Mise en route avec F # dans le Code de Visual Studio avec Ionide'
description: "Découvrez comment utiliser F # avec Code Visual Studio et la suite de plug-in Ionide."
keywords: 'Visual f #, f #, fonctionnelle de programmation, .NET, Visual Studio Code, vscode, Ionide'
author: cartermp
ms.author: phcart
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 336316eaf474f4c10d63657f178ce4a336ad7a54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-f-in-visual-studio-code-with-ionide"></a><span data-ttu-id="2c958-104">Mise en route avec F # dans le Code de Visual Studio avec Ionide</span><span class="sxs-lookup"><span data-stu-id="2c958-104">Getting Started with F# in Visual Studio Code with Ionide</span></span>

<span data-ttu-id="2c958-105">Vous pouvez écrire F # dans [Visual Studio Code](https://code.visualstudio.com) avec la [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), afin d’obtenir une expérience d’IDE inter-plateformes et léger optimale avec IntelliSense et refactorisations du code de base.</span><span class="sxs-lookup"><span data-stu-id="2c958-105">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight IDE experience with IntelliSense and basic code refactorings.</span></span>  <span data-ttu-id="2c958-106">Visitez [Ionide.io](http://ionide.io) pour en savoir plus sur la suite de plug-in.</span><span class="sxs-lookup"><span data-stu-id="2c958-106">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2c958-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2c958-107">Prerequisites</span></span>

<span data-ttu-id="2c958-108">F # 4.0 ou version ultérieure doit être installé sur votre ordinateur pour Ionide.</span><span class="sxs-lookup"><span data-stu-id="2c958-108">F# 4.0 or higher must be installed on your machine to use Ionide.</span></span>

<span data-ttu-id="2c958-109">Vous devez également disposer [git installé](https://git-scm.com/download) et disponible sur votre chemin d’accès permettent d’utiliser des modèles de projet Ionide.</span><span class="sxs-lookup"><span data-stu-id="2c958-109">You must also have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span>  <span data-ttu-id="2c958-110">Vous pouvez vérifier qu’il est correctement installé en tapant `git` à une pression de prompt.and commande **entrée**.</span><span class="sxs-lookup"><span data-stu-id="2c958-110">You can verify that it is installed correctly by typing `git` at a command prompt.and pressing **Enter**.</span></span>

### <a name="windows"></a><span data-ttu-id="2c958-111">Windows</span><span class="sxs-lookup"><span data-stu-id="2c958-111">Windows</span></span>

<span data-ttu-id="2c958-112">Si vous êtes sous Windows, vous avez deux options pour l’installation de F #.</span><span class="sxs-lookup"><span data-stu-id="2c958-112">If you're on Windows, you have two options for installing F#.</span></span>

<span data-ttu-id="2c958-113">Si vous avez déjà installé Visual Studio et que vous n’avez pas F #, vous pouvez [installer les outils Visual F #](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="2c958-113">If you've already installed Visual Studio and don't have F#, you can [Install the Visual F# Tools](get-started-visual-studio.md#installing-f).</span></span>  <span data-ttu-id="2c958-114">Cela installe tous les composants nécessaires pour écrire, compiler et exécuter du code F #.</span><span class="sxs-lookup"><span data-stu-id="2c958-114">This will install all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="2c958-115">Si vous préférez ne pas installer Visual Studio, utilisez les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c958-115">If you prefer not to install Visual Studio, use the following instructions:</span></span>

1. <span data-ttu-id="2c958-116">Installer [.NET Framework 4.5 ou version ultérieure](https://www.microsoft.com/en-US/download/details.aspx?id=30653) si vous utilisez Windows 7.</span><span class="sxs-lookup"><span data-stu-id="2c958-116">Install [.NET Framework 4.5 or higher](https://www.microsoft.com/en-US/download/details.aspx?id=30653) if you're running Windows 7.</span></span>  <span data-ttu-id="2c958-117">Si vous utilisez Windows 8 ou une version ultérieure, vous n’avez pas besoin pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="2c958-117">If you're using Windows 8 or higher, you do not need to do this.</span></span>

2. <span data-ttu-id="2c958-118">Installer le Kit de développement logiciel Windows pour votre système d’exploitation :</span><span class="sxs-lookup"><span data-stu-id="2c958-118">Install the Windows SDK for your OS:</span></span>

    * [<span data-ttu-id="2c958-119">Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="2c958-119">Windows 10 SDK</span></span>](https://dev.windows.com/en-US/downloads/windows-10-sdk)
    * [<span data-ttu-id="2c958-120">Windows 8.1 SDK</span><span class="sxs-lookup"><span data-stu-id="2c958-120">Windows 8.1 SDK</span></span>](http://msdn.microsoft.com/windows/desktop/bg162891)
    * [<span data-ttu-id="2c958-121">Windows 8 SDK</span><span class="sxs-lookup"><span data-stu-id="2c958-121">Windows 8 SDK</span></span>](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)
    * [<span data-ttu-id="2c958-122">Windows 7 SDK</span><span class="sxs-lookup"><span data-stu-id="2c958-122">Windows 7 SDK</span></span>](http://www.microsoft.com/download/details.aspx?id=8279)

3. <span data-ttu-id="2c958-123">Installer le [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span><span class="sxs-lookup"><span data-stu-id="2c958-123">Install the [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span></span>  <span data-ttu-id="2c958-124">Vous devez également installer [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span><span class="sxs-lookup"><span data-stu-id="2c958-124">You may also need to install [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span></span>

4. <span data-ttu-id="2c958-125">Installer le [outils Visual F #](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span><span class="sxs-lookup"><span data-stu-id="2c958-125">Install the [Visual F# Tools](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span></span>

<span data-ttu-id="2c958-126">Sur Windows 64 bits, le compilateur et les outils se trouvent ici :</span><span class="sxs-lookup"><span data-stu-id="2c958-126">On 64-bit Windows, the compiler and tools are located here:</span></span>

```
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="2c958-127">Sur Windows 32 bits, les outils du compilateur se trouvent ici :</span><span class="sxs-lookup"><span data-stu-id="2c958-127">On 32-bit Windows, the compiler tools are located here:</span></span>

```
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="2c958-128">Ionide détecte automatiquement le compilateur et les outils, mais si elle n’est pas pour une raison quelconque (par exemple, les outils Visual F # a été installés dans un répertoire différent), vous pouvez ajouter manuellement le dossier qui contient (`...\Microsoft SDKs\F#\4.0`) à votre chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="2c958-128">Ionide automatically detects the compiler and tools, but if it doesn't for some reason (for example, the Visual F# Tools were installed to a different directory), you can manually add the containing folder (`...\Microsoft SDKs\F#\4.0`) to your PATH.</span></span>

### <a name="macos"></a><span data-ttu-id="2c958-129">MacOS</span><span class="sxs-lookup"><span data-stu-id="2c958-129">macOS</span></span>

<span data-ttu-id="2c958-130">Sur Mac OS, utilise Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="2c958-130">On macOS, Ionide uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="2c958-131">Le moyen le plus simple pour installer Mono sur macOS est via Homebrew.</span><span class="sxs-lookup"><span data-stu-id="2c958-131">The easiest way to install Mono on macOS is via Homebrew.</span></span>  <span data-ttu-id="2c958-132">Tapez simplement la commande suivante dans votre terminal :</span><span class="sxs-lookup"><span data-stu-id="2c958-132">Simply type the following into your terminal:</span></span>

```
brew install mono
```

### <a name="linux"></a><span data-ttu-id="2c958-133">Linux</span><span class="sxs-lookup"><span data-stu-id="2c958-133">Linux</span></span>

<span data-ttu-id="2c958-134">Sur Linux, Ionide utilise également [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="2c958-134">On Linux, Ionide also uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="2c958-135">Si vous êtes sur Debian ou Ubuntu, vous pouvez utiliser les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2c958-135">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="2c958-136">L’installation de Visual Studio Code et le plug-in Ionide</span><span class="sxs-lookup"><span data-stu-id="2c958-136">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="2c958-137">Vous pouvez installer Visual Studio Code, à partir de la [code.visualstudio.com](https://code.visualstudio.com) site Web.</span><span class="sxs-lookup"><span data-stu-id="2c958-137">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>  <span data-ttu-id="2c958-138">Après cela, il existe deux façons de trouver le plug-in Ionide :</span><span class="sxs-lookup"><span data-stu-id="2c958-138">After that, there are two ways to find the Ionide plugin:</span></span>

1. <span data-ttu-id="2c958-139">Utilisez la Palette de commandes (Ctrl + Maj + P sur Windows, ⌘ + MAJ + P sur macOS, Ctrl + Maj + P sur Linux) et tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="2c958-139">Use the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

    ```
    >ext install Ionide
    ```

2. <span data-ttu-id="2c958-140">Cliquez sur l’icône des Extensions et recherchez « Ionide » :</span><span class="sxs-lookup"><span data-stu-id="2c958-140">Click the Extensions icon and search for "Ionide":</span></span>

    ![](media/getting-started-vscode/vscode-ext.png)

<span data-ttu-id="2c958-141">Le plug-in uniquement requis pour la prise en charge F # dans Visual Studio Code est [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="2c958-141">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>  <span data-ttu-id="2c958-142">Toutefois, vous pouvez également installer [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) et pour obtenir [faux](http://fsharp.github.io/FAKE/) prennent en charge et [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pour obtenir [Paket](https://fsprojects.github.io/Paket/) prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="2c958-142">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) and to get [FAKE](http://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span>  <span data-ttu-id="2c958-143">FAUX et Paket sont des outils de communauté supplémentaires F # pour générer des projets et la gestion des dépendances, respectivement.</span><span class="sxs-lookup"><span data-stu-id="2c958-143">FAKE and Paket are additonal F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="2c958-144">Créer votre premier projet avec Ionide</span><span class="sxs-lookup"><span data-stu-id="2c958-144">Creating your first project with Ionide</span></span>

<span data-ttu-id="2c958-145">Pour créer un projet F #, ouvrez Visual Studio Code dans un nouveau dossier (vous pouvez appeler comme vous le souhaitez).</span><span class="sxs-lookup"><span data-stu-id="2c958-145">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

![](media/getting-started-vscode/vscode-open-dir.png)

<span data-ttu-id="2c958-146">Ensuite, ouvrez la Palette de commandes (Ctrl + Maj + P sur Windows, ⌘ + MAJ + P sur macOS, Ctrl + Maj + P sur Linux) et tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="2c958-146">Next, open the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

```
>f#: New Project
```

<span data-ttu-id="2c958-147">Il est alimenté par le [FORGE](https://github.com/fsharp-editing/Forge) projet.</span><span class="sxs-lookup"><span data-stu-id="2c958-147">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>  <span data-ttu-id="2c958-148">Vous devez voir quelque chose de similaire à :</span><span class="sxs-lookup"><span data-stu-id="2c958-148">You should see something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
<span data-ttu-id="2c958-149">Si vous ne voyez pas la commande ci-dessus, essayez d’actualiser les modèles en exécutant la commande suivante dans la Palette de commandes : `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="2c958-149">If you don't see the above, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="2c958-150">Sélectionnez « F #: nouveau projet » en appuyant sur **entrée**, s’affiche alors à cette étape :</span><span class="sxs-lookup"><span data-stu-id="2c958-150">Select "F#: New Project" by hitting **Enter**, which will take you to this step:</span></span>

![](media/getting-started-vscode/vscode-proj-type.png)

<span data-ttu-id="2c958-151">Il sélectionne un modèle pour un type de projet spécifique.</span><span class="sxs-lookup"><span data-stu-id="2c958-151">This will select a template for a specific type of project.</span></span>  <span data-ttu-id="2c958-152">Régi par de nombreuses options sont, par exemple un [FsLab](http://fslab.org) modèle pour la science des données ou [Suave](https://suave.io) modèle de programmation du Web.</span><span class="sxs-lookup"><span data-stu-id="2c958-152">There are quite a few options here, such as an [FsLab](http://fslab.org) template for Data Science or [Suave](https://suave.io) template for Web Programming.</span></span>  <span data-ttu-id="2c958-153">Cet article utilise la `classlib` modèle, par conséquent, mettez en surbrillance qui et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="2c958-153">This article uses the `classlib` template, so highlight that and hit **Enter**.</span></span>  <span data-ttu-id="2c958-154">Vous allez ensuite atteindre l’étape suivante :</span><span class="sxs-lookup"><span data-stu-id="2c958-154">You will then reach the following step:</span></span>

![](media/getting-started-vscode/vscode-new-dir.png)

<span data-ttu-id="2c958-155">Cela vous permet de créer le projet dans un répertoire différent, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="2c958-155">This lets you create the project in a different directory, if you like.</span></span>  <span data-ttu-id="2c958-156">Laissez ce champ vide pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="2c958-156">Leave it blank for now.</span></span>  <span data-ttu-id="2c958-157">Il créera le projet dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="2c958-157">It will create the project in the current directory.</span></span>  <span data-ttu-id="2c958-158">Une fois que vous appuyez sur **entrée**, vous allez atteindre l’étape suivante :</span><span class="sxs-lookup"><span data-stu-id="2c958-158">Once you press **Enter**, you will reach the following step:</span></span>

![](media/getting-started-vscode/vscode-proj-name.png)

<span data-ttu-id="2c958-159">Cela vous permet de nommer votre projet.</span><span class="sxs-lookup"><span data-stu-id="2c958-159">This lets you name your project.</span></span>  <span data-ttu-id="2c958-160">F # utilise [casse Pascal](http://c2.com/cgi/wiki?PascalCase) pour les noms de projet.</span><span class="sxs-lookup"><span data-stu-id="2c958-160">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span>  <span data-ttu-id="2c958-161">Cet article utilise `ClassLibraryDemo` comme nom.</span><span class="sxs-lookup"><span data-stu-id="2c958-161">This article uses `ClassLibraryDemo` as the name.</span></span>  <span data-ttu-id="2c958-162">Une fois que vous avez entré le nom souhaité pour votre projet, appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="2c958-162">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="2c958-163">Si vous avez suivi les étapes précédentes, vous devez obtenir Visual Studio Code espace de travail sur le côté gauche pour ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="2c958-163">If you followed the previous step steps, you should get the Visual Studio Code Workspace on the left-hand side to look something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

<span data-ttu-id="2c958-164">Ce modèle génère quelques éléments qui que vous seront utiles :</span><span class="sxs-lookup"><span data-stu-id="2c958-164">This template generates a few things you'll find useful:</span></span>

1. <span data-ttu-id="2c958-165">F # de projet, sous la `ClassLibraryDemo` dossier.</span><span class="sxs-lookup"><span data-stu-id="2c958-165">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="2c958-166">La structure de répertoire correct pour l’ajout de packages via [ `Paket` ](http://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="2c958-166">The correct directory structure for adding packages via [`Paket`](http://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="2c958-167">Un inter-plateformes générer le script avec [ `FAKE` ](http://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="2c958-167">A cross-platform build script with [`FAKE`](http://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="2c958-168">Le `paket.exe` exécutable qui peut récupérer des packages et résoudre les dépendances pour vous.</span><span class="sxs-lookup"><span data-stu-id="2c958-168">The `paket.exe` executable which can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="2c958-169">A `.gitignore` fichier si vous souhaitez ajouter ce projet au contrôle de code source basée sur Git.</span><span class="sxs-lookup"><span data-stu-id="2c958-169">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="2c958-170">Écrire du code</span><span class="sxs-lookup"><span data-stu-id="2c958-170">Writing some code</span></span>

<span data-ttu-id="2c958-171">Ouvrez le *ClassLibraryDemo* dossier.</span><span class="sxs-lookup"><span data-stu-id="2c958-171">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="2c958-172">Vous devez voir les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="2c958-172">You should see the following files:</span></span>

1. <span data-ttu-id="2c958-173">`ClassLibraryDemo.fs`, un fichier d’implémentation F # avec une classe définie.</span><span class="sxs-lookup"><span data-stu-id="2c958-173">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="2c958-174">`CassLibraryDemo.fsproj`, un fichier de projet F # est utilisé pour générer ce projet.</span><span class="sxs-lookup"><span data-stu-id="2c958-174">`CassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="2c958-175">`Script.fsx`, un fichier de script F # qui charge le fichier source.</span><span class="sxs-lookup"><span data-stu-id="2c958-175">`Script.fsx`, an F# script file which loads the source file.</span></span>
4. <span data-ttu-id="2c958-176">`paket.references`, un fichier Paket qui spécifie les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="2c958-176">`paket.references`, a Paket file which specifies the project dependencies.</span></span>

<span data-ttu-id="2c958-177">Ouvrez `Script.fsx`et ajoutez le code suivant à la fin de celle-ci :</span><span class="sxs-lookup"><span data-stu-id="2c958-177">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="2c958-178">Cette fonction convertit un mot à un formulaire de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="2c958-178">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span>  <span data-ttu-id="2c958-179">L’étape suivante consiste à évaluer à l’aide de F # Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="2c958-179">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="2c958-180">Mettez en surbrillance de la fonction entière (il doit être 11 lignes).</span><span class="sxs-lookup"><span data-stu-id="2c958-180">Highlight the entire function (it should be 11 lines long).</span></span>  <span data-ttu-id="2c958-181">Une fois qu’il est mis en surbrillance, maintenez la **Alt** clé, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="2c958-181">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span>  <span data-ttu-id="2c958-182">Vous remarquerez une fenêtre contextuelle ci-dessous, et il doit afficher quelque chose comme ceci :</span><span class="sxs-lookup"><span data-stu-id="2c958-182">You'll notice a window pop up below, and it should show something like this:</span></span>

![](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="2c958-183">Cela a trois opérations :</span><span class="sxs-lookup"><span data-stu-id="2c958-183">This did three things:</span></span>

1. <span data-ttu-id="2c958-184">Il a démarré le processus FSI.</span><span class="sxs-lookup"><span data-stu-id="2c958-184">It started the FSI process.</span></span>
2. <span data-ttu-id="2c958-185">Il envoyé le code que vous avez sélectionnée sur le processus FSI.</span><span class="sxs-lookup"><span data-stu-id="2c958-185">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="2c958-186">Le processus FSI évaluer le code que vous avez envoyé via.</span><span class="sxs-lookup"><span data-stu-id="2c958-186">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="2c958-187">Étant donné que ce que vous avez envoyé via a été un [fonction](../language-reference/functions/index.md), vous pouvez maintenant appeler cette fonction avec FSI !</span><span class="sxs-lookup"><span data-stu-id="2c958-187">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span>  <span data-ttu-id="2c958-188">Dans la fenêtre interactive, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2c958-188">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="2c958-189">Vous devez voir le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="2c958-189">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="2c958-190">Maintenant, essayons avec une voyelle en tant que la première lettre.</span><span class="sxs-lookup"><span data-stu-id="2c958-190">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="2c958-191">Entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c958-191">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="2c958-192">Vous devez voir le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="2c958-192">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="2c958-193">La fonction semble fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="2c958-193">The function appears to be working as expected.</span></span>  <span data-ttu-id="2c958-194">Félicitations, vous venez d’écriture de votre première fonction) (F # dans Visual Studio Code et il évaluée avec FSI.</span><span class="sxs-lookup"><span data-stu-id="2c958-194">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="2c958-195">Comme vous l’avez peut-être remarqué, les lignes de FSI sont terminent par `;;`.</span><span class="sxs-lookup"><span data-stu-id="2c958-195">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span>  <span data-ttu-id="2c958-196">Il s’agit, car FSI vous permet d’entrer plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="2c958-196">This is because FSI allows you to enter multiple lines.</span></span>  <span data-ttu-id="2c958-197">Le `;;` à la fin informe FSI lorsque le code est terminé.</span><span class="sxs-lookup"><span data-stu-id="2c958-197">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="2c958-198">Explique le code</span><span class="sxs-lookup"><span data-stu-id="2c958-198">Explaining the code</span></span>

<span data-ttu-id="2c958-199">Si vous n’êtes pas sûr de ce que le code est en fait, Voici un pas à pas.</span><span class="sxs-lookup"><span data-stu-id="2c958-199">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="2c958-200">Comme vous pouvez le voir, `toPigLatin` est une fonction qui prend un mot en entrée et la convertit en une représentation sous forme de Pig-Latin de ce mot.</span><span class="sxs-lookup"><span data-stu-id="2c958-200">As you can see, `toPigLatin` is a function which takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span>  <span data-ttu-id="2c958-201">Les règles pour ce sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c958-201">The rules for this are as follows:</span></span>

<span data-ttu-id="2c958-202">Si le premier caractère dans un mot commence par une voyelle, ajoutez « hourra » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="2c958-202">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span>  <span data-ttu-id="2c958-203">Si elle ne commence pas par une voyelle, déplacez le premier caractère à la fin du mot et ajoutez-y « ay ».</span><span class="sxs-lookup"><span data-stu-id="2c958-203">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="2c958-204">Vous avez peut-être remarqué les éléments suivants dans FSI :</span><span class="sxs-lookup"><span data-stu-id="2c958-204">You may have noticed the following in FSI:</span></span>

```
val toPigLatin : word:string -> string
```

<span data-ttu-id="2c958-205">Cela indique que `toPigLatin` est une fonction qui accepte un `string` en tant qu’entrée (appelé `word`), ainsi qu’un autre `string`.</span><span class="sxs-lookup"><span data-stu-id="2c958-205">This states that `toPigLatin` is a function which takes in a `string` as input (called `word`), and returns another `string`.</span></span>  <span data-ttu-id="2c958-206">Il s’agit du [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un élément fondamental de F #, qui est la clé pour comprendre le code F #.</span><span class="sxs-lookup"><span data-stu-id="2c958-206">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span>  <span data-ttu-id="2c958-207">Vous pouvez également constater si vous pointez sur la fonction dans le Code de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c958-207">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="2c958-208">Dans le corps de la fonction, vous pouvez remarquer que les deux parties distinctes :</span><span class="sxs-lookup"><span data-stu-id="2c958-208">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="2c958-209">Une fonction interne, appelée `isVowel`, qui détermine si un caractère donné (`c`) est une voyelle en vérifiant si elle correspond à un des modèles fournis via [recherche de correspondance](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="2c958-209">An inner function, called `isVowel`, which determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="2c958-210">Un [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) qui vérifie si le premier caractère est une voyelle et construit une valeur de retour de caractères d’entrée selon que le premier caractère de l’expression était une voyelle ou non :</span><span class="sxs-lookup"><span data-stu-id="2c958-210">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression which checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="2c958-211">Le flux de `toPigLatin` est donc :</span><span class="sxs-lookup"><span data-stu-id="2c958-211">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="2c958-212">Vérifiez si le premier caractère du mot d’entrée est une voyelle.</span><span class="sxs-lookup"><span data-stu-id="2c958-212">Check if the first character of the input word is a vowel.</span></span>  <span data-ttu-id="2c958-213">S’il s’agit, attachez « hourra » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="2c958-213">If it is, attach "yay" to the end of the word.</span></span>  <span data-ttu-id="2c958-214">Sinon, déplacez le premier caractère à la fin du mot et « ay » lui ajouter.</span><span class="sxs-lookup"><span data-stu-id="2c958-214">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="2c958-215">Il existe une dernière chose à noter à ce sujet : il n’existe aucune instruction explicite à retourner à partir de la fonction, contrairement à nombreux autres langages très utiles.</span><span class="sxs-lookup"><span data-stu-id="2c958-215">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span>  <span data-ttu-id="2c958-216">Cela est que F # est basé sur une Expression, et la dernière expression dans le corps d’une fonction est la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="2c958-216">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span>  <span data-ttu-id="2c958-217">Car `if..then..else` lui-même est une expression, le corps de la `then` bloc ou le corps de la `else` bloc s’affichera en fonction de la valeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2c958-217">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="2c958-218">Déplacement de votre code de script dans le fichier d’implémentation</span><span class="sxs-lookup"><span data-stu-id="2c958-218">Moving your script code into the implementation file</span></span>

<span data-ttu-id="2c958-219">Les sections précédentes de cet article présenté une première étape dans l’écriture de code F # courants : écrire une fonction initiale et l’exécuter interactivement avec FSI.</span><span class="sxs-lookup"><span data-stu-id="2c958-219">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span>  <span data-ttu-id="2c958-220">Il s’agit en tant que le développement piloté par les REPL, où REPL représente « Boucle en lecture-évaluation-impression ».</span><span class="sxs-lookup"><span data-stu-id="2c958-220">This is known as REPL-driven development, where REPL stands for "Read-Evaluate-Print Loop".</span></span>  <span data-ttu-id="2c958-221">Il s’agit d’un excellent moyen de faire des essais avec des fonctionnalités jusqu'à ce que vous ayez un élément de travail.</span><span class="sxs-lookup"><span data-stu-id="2c958-221">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="2c958-222">L’étape suivante de développement piloté par REPL consiste à déplacer de code opérationnel dans un fichier d’implémentation F #.</span><span class="sxs-lookup"><span data-stu-id="2c958-222">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span>  <span data-ttu-id="2c958-223">Il peut ensuite être compilé par le compilateur F # dans un assembly qui peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="2c958-223">It can then be compiled by the F# compiler into an assembly which can be executed.</span></span>

<span data-ttu-id="2c958-224">Pour commencer, ouvrez `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="2c958-224">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="2c958-225">Vous remarquerez que du code existe déjà dans.</span><span class="sxs-lookup"><span data-stu-id="2c958-225">You'll notice that some code is already in there.</span></span>  <span data-ttu-id="2c958-226">Continuer et supprimer la définition de classe, mais veillez à laisser le [ `namespace` ](../language-reference/namespaces.md) déclaration en haut.</span><span class="sxs-lookup"><span data-stu-id="2c958-226">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="2c958-227">Ensuite, créez un nouveau [ `module` ](../language-reference/modules.md) appelé `PigLatin` et copiez le `toPigLatin` fonction en tant que tel dans celui-ci :</span><span class="sxs-lookup"><span data-stu-id="2c958-227">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="2c958-228">Il s’agit d’une des nombreuses méthodes que vous pouvez organiser les fonctions dans le code F # et une approche courante si vous souhaitez également appeler votre code à partir de c# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2c958-228">This is one of the many ways you can organize functions in F# code, and a common approach if you also want to call your code from C# or Visual Basic projects.</span></span>

<span data-ttu-id="2c958-229">Ensuite, ouvrez le `Script.fsx` à nouveau de fichiers et supprimez la totalité de `toPigLatin` de fonctionner, mais veillez à conserver les deux lignes suivantes dans le fichier :</span><span class="sxs-lookup"><span data-stu-id="2c958-229">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="2c958-230">La première ligne est nécessaire pour écrire un script pour charger de FSI `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="2c958-230">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="2c958-231">La deuxième ligne est une commodité : omettant est facultative, mais vous devez taper `open ClassLibraryDemo` dans une fenêtre FSI si vous souhaitez mettre le `ToPigLatin` module dans la portée.</span><span class="sxs-lookup"><span data-stu-id="2c958-231">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="2c958-232">Ensuite, dans la fenêtre FSI, appelez la fonction avec le `PigLatin` module que vous avez défini précédemment :</span><span class="sxs-lookup"><span data-stu-id="2c958-232">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="2c958-233">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="2c958-233">Success!</span></span>  <span data-ttu-id="2c958-234">Vous obtenez les mêmes résultats qu’avant, mais maintenant chargé à partir d’un fichier d’implémentation F #.</span><span class="sxs-lookup"><span data-stu-id="2c958-234">You get the same results as before, but now loaded from an F# implementation file.</span></span>  <span data-ttu-id="2c958-235">La principale différence ici est que les fichiers de code source F # sont compilés dans des assemblys qui peuvent être exécutées n’importe où, pas seulement dans FSI.</span><span class="sxs-lookup"><span data-stu-id="2c958-235">The major difference here is that F# source files are compiled into assemblies which can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="2c958-236">Résumé</span><span class="sxs-lookup"><span data-stu-id="2c958-236">Summary</span></span>

<span data-ttu-id="2c958-237">Dans cet article, vous avez appris :</span><span class="sxs-lookup"><span data-stu-id="2c958-237">In this article, you've learned:</span></span>

1. <span data-ttu-id="2c958-238">Comment configurer le Code de Visual Studio avec Ionide.</span><span class="sxs-lookup"><span data-stu-id="2c958-238">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="2c958-239">Comment créer votre premier projet F # avec Ionide.</span><span class="sxs-lookup"><span data-stu-id="2c958-239">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="2c958-240">Comment utiliser F # script pour écrire votre première fonction) (F # dans Ionide puis l’exécuter dans FSI.</span><span class="sxs-lookup"><span data-stu-id="2c958-240">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="2c958-241">Comment migrer votre code de script pour le code source F #, puis appelez ce code à partir de FSI.</span><span class="sxs-lookup"><span data-stu-id="2c958-241">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="2c958-242">Vous êtes désormais équipés pour écrire du code F # beaucoup plus à l’aide de Code Visual Studio et Ionide.</span><span class="sxs-lookup"><span data-stu-id="2c958-242">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="2c958-243">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="2c958-243">Troubleshooting</span></span>

<span data-ttu-id="2c958-244">Voici quelques manières que vous pouvez résoudre certains problèmes que vous pouvez rencontrer :</span><span class="sxs-lookup"><span data-stu-id="2c958-244">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="2c958-245">Pour obtenir les fonctionnalités de Ionide de modification du code, vos fichiers F # doivent être enregistrés sur disque et à l’intérieur d’un dossier qui est ouvert dans l’espace de travail de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2c958-245">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="2c958-246">Si vous avez apporté des modifications à votre système ou installé des composants requis de Ionide avec Code Visual Studio ouvert, redémarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2c958-246">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="2c958-247">Vérifiez que vous pouvez utiliser le compilateur F # et F # interactive à partir de la ligne de commande sans un chemin d’accès qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="2c958-247">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span>  <span data-ttu-id="2c958-248">Vous pouvez le faire en tapant `fsc` dans une ligne de commande pour le compilateur F #, et `fsi` ou `fsharpi` pour Visual F # outils sur Windows et Mono sur Mac/Linux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="2c958-248">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="2c958-249">Si vous avez des caractères non valides dans les répertoires de votre projet, Ionide peut ne pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="2c958-249">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="2c958-250">Renommer les répertoires de votre projet si c’est le cas.</span><span class="sxs-lookup"><span data-stu-id="2c958-250">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="2c958-251">Si aucun des commandes Ionide ne fonctionnent pas, vérifiez votre [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) pour voir si vous les remplacez par inadvertance.</span><span class="sxs-lookup"><span data-stu-id="2c958-251">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="2c958-252">Si Ionide est rompue sur votre ordinateur et qu’aucun d'entre eux a résolu votre problème, essayez de supprimer le `ionide-fsharp` répertoire sur votre ordinateur et réinstallez la suite de plug-in.</span><span class="sxs-lookup"><span data-stu-id="2c958-252">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="2c958-253">Ionide est un projet open source créé et géré par les membres de la Communauté F #.</span><span class="sxs-lookup"><span data-stu-id="2c958-253">Ionide is an open source project built and maintained by members of the F# community.</span></span>  <span data-ttu-id="2c958-254">Veuillez signaler des problèmes et n’hésitez pas à contribuer à la [Ionide-VSCode : référentiel GitHub de FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="2c958-254">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="2c958-255">Si vous avez un problème de rapport, veuillez suivre [les instructions pour l’obtention de journaux à utiliser lors de la déclaration d’un problème](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="2c958-255">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="2c958-256">Vous pouvez également demander à pour plus d’informations à partir de la Ionide développeurs et de F # dans le [Ionide Gitter canal](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="2c958-256">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2c958-257">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2c958-257">Next steps</span></span>

<span data-ttu-id="2c958-258">Pour en savoir plus sur F # et les fonctionnalités du langage, consultez [visite guidée de F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="2c958-258">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c958-259">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c958-259">See also</span></span>

[<span data-ttu-id="2c958-260">Présentation de F#</span><span class="sxs-lookup"><span data-stu-id="2c958-260">Tour of F#</span></span>](../tour.md)

[<span data-ttu-id="2c958-261">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="2c958-261">F# Language Reference</span></span>](../language-reference/index.md)

[<span data-ttu-id="2c958-262">Fonctions</span><span class="sxs-lookup"><span data-stu-id="2c958-262">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="2c958-263">Modules</span><span class="sxs-lookup"><span data-stu-id="2c958-263">Modules</span></span>](../language-reference/modules.md)

[<span data-ttu-id="2c958-264">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="2c958-264">Namespaces</span></span>](../language-reference/namespaces.md)

[<span data-ttu-id="2c958-265">Ionide-VSCode : FSharp</span><span class="sxs-lookup"><span data-stu-id="2c958-265">Ionide-VSCode: FSharp</span></span>](https://github.com/ionide/ionide-vscode-fsharp)
