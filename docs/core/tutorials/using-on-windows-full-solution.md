---
title: "Génération d’une solution .NET Core complète sur Windows à l’aide de Visual Studio 2017"
description: "Découvrez comment générer une solution .NET Core complète dans Visual Studio 2017 sous Windows."
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ba7e082c-a7c8-431e-a342-f67734b660f6
ms.openlocfilehash: 694201c1a2a2c373f62b0e0d8e3c1d8aa7e6e881
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="dc178-104">Génération d’une solution .NET Core complète sur Windows à l’aide de Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dc178-104">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="dc178-105">Visual Studio 2017 fournit un environnement de développement complet pour le développement d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc178-105">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="dc178-106">Les procédures décrites dans ce document expliquent comment créer une solution .NET Core classique qui inclut des bibliothèques réutilisables, des tests et utilise des bibliothèques tierces.</span><span class="sxs-lookup"><span data-stu-id="dc178-106">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="dc178-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="dc178-107">Prerequisites</span></span>

<span data-ttu-id="dc178-108">Suivez les instructions stipulées dans [notre page de prérequis](../windows-prerequisites.md) pour mettre à jour votre environnement.</span><span class="sxs-lookup"><span data-stu-id="dc178-108">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="dc178-109">Une solution utilisant uniquement des projets .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc178-109">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="dc178-110">Écriture de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="dc178-110">Writing the library</span></span>

1. <span data-ttu-id="dc178-111">Dans Visual Studio, choisissez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="dc178-111">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="dc178-112">Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** nœud et choisissez la **.NET Standard** nœud, puis choisissez **bibliothèque de classes (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="dc178-112">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="dc178-113">Nommez le projet « Library » et la solution « Golden ».</span><span class="sxs-lookup"><span data-stu-id="dc178-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="dc178-114">Laissez l’option **Créer le répertoire pour la solution** activée.</span><span class="sxs-lookup"><span data-stu-id="dc178-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="dc178-115">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dc178-115">Click **OK**.</span></span>

3. <span data-ttu-id="dc178-116">Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud **Dépendances**, puis choisissez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="dc178-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="dc178-117">Choisissez « nuget.org » comme **Source de package**, puis choisissez l’onglet **Parcourir**. Recherchez **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="dc178-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="dc178-118">Cliquez sur **Installer** et acceptez le contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="dc178-118">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="dc178-119">Le package doit maintenant apparaître sous **Dependencies/NuGet** (Dépendances/NuGet) et être automatiquement restauré.</span><span class="sxs-lookup"><span data-stu-id="dc178-119">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="dc178-120">Renommer le fichier `Class1.cs` en `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="dc178-120">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="dc178-121">Acceptez le renommage de la classe.</span><span class="sxs-lookup"><span data-stu-id="dc178-121">Accept the rename of the class.</span></span> <span data-ttu-id="dc178-122">Ajouter une méthode : `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="dc178-122">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="dc178-123">Dans le menu **Générer** , choisissez **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="dc178-123">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="dc178-124">La solution doit se générer sans erreur.</span><span class="sxs-lookup"><span data-stu-id="dc178-124">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="dc178-125">Écriture du projet de test</span><span class="sxs-lookup"><span data-stu-id="dc178-125">Writing the test project</span></span>

1. <span data-ttu-id="dc178-126">Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud **Solution** et sélectionnez **Ajouter**, **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="dc178-126">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="dc178-127">Dans la boîte de dialogue **Nouveau projet**, sous **Visual C#**, choisissez **Projet de test unitaire (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="dc178-127">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="dc178-128">Nommez-le « TestLibrary » et cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="dc178-128">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="dc178-129">Dans le projet **TestLibrary**, ouvrez le menu contextuel du nœud **Dépendances**, puis choisissez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="dc178-129">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="dc178-130">Cliquez sur **Projets**, puis enregistrez le projet de bibliothèque et cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="dc178-130">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="dc178-131">Cette opération ajoute une référence à votre bibliothèque à partir du projet de test.</span><span class="sxs-lookup"><span data-stu-id="dc178-131">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="dc178-132">Renommez le fichier `UnitTest1.cs` en `LibraryTests.cs` et acceptez le changement de nom de classe.</span><span class="sxs-lookup"><span data-stu-id="dc178-132">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="dc178-133">Ajoutez `using Library;` au début du fichier et remplacez la méthode `TestMethod1` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="dc178-133">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="dc178-134">Vous devez maintenant être en mesure de générer la solution.</span><span class="sxs-lookup"><span data-stu-id="dc178-134">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="dc178-135">Dans le menu **Test**, choisissez **Windows**, **Explorateur de tests** afin d’intégrer la fenêtre Explorateur de tests à votre espace de travail.</span><span class="sxs-lookup"><span data-stu-id="dc178-135">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="dc178-136">Après quelques secondes, le test `ThingGetsObjectValFromNumber` doit s’afficher dans l’Explorateur de tests.</span><span class="sxs-lookup"><span data-stu-id="dc178-136">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="dc178-137">Choisissez **Exécuter tout**.</span><span class="sxs-lookup"><span data-stu-id="dc178-137">Choose **Run All**.</span></span>
   
   <span data-ttu-id="dc178-138">Le test doit réussir.</span><span class="sxs-lookup"><span data-stu-id="dc178-138">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="dc178-139">Écriture de l’application console</span><span class="sxs-lookup"><span data-stu-id="dc178-139">Writing the console app</span></span>

1. <span data-ttu-id="dc178-140">Dans l’Explorateur de solutions, ouvrez le menu contextuel de la solution et ajoutez un nouveau projet **Application console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="dc178-140">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="dc178-141">Nommez-le « Application ».</span><span class="sxs-lookup"><span data-stu-id="dc178-141">Name it "App".</span></span>

2. <span data-ttu-id="dc178-142">Dans le projet **App**, ouvrez le menu contextuel du nœud **Dépendances**, puis choisissez **Ajouter**, **Référence**.</span><span class="sxs-lookup"><span data-stu-id="dc178-142">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="dc178-143">Dans la boîte de dialogue **Gestionnaire de références**, cochez **Bibliothèque** sous le nœud **Projets**, **Solution**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dc178-143">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="dc178-144">Ouvrez le menu contextuel du nœud **App**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="dc178-144">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="dc178-145">Ainsi, il est possible d’appuyer sur F5 ou Ctrl+F5 pour démarrer l’application console.</span><span class="sxs-lookup"><span data-stu-id="dc178-145">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="dc178-146">Ouvrez le fichier `Program.cs`, ajoutez une directive `using Library;` en haut du fichier, puis ajoutez `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` à la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="dc178-146">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="dc178-147">Définissez un point d’arrêt après la ligne que vous venez d’ajouter.</span><span class="sxs-lookup"><span data-stu-id="dc178-147">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="dc178-148">Appuyez sur F5 pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="dc178-148">Press F5 to run the application..</span></span>

   <span data-ttu-id="dc178-149">L’application doit se générer sans erreur et atteindre le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="dc178-149">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="dc178-150">Vous pouvez également vérifier que la sortie de l’application est « The answer is 42. ».</span><span class="sxs-lookup"><span data-stu-id="dc178-150">You should also be able to check that the application output "The answer is 42.".</span></span>
