---
title: Organiser et tester des projets avec la ligne de commande .NET Core
description: "Ce didacticiel explique comment organiser et tester des projets .NET Core à partir de la ligne de commande."
keywords: .NET, .NET Core, tests unitaires, interface CLI .NET Core, xUnit
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
ms.workload: dotnetcore
ms.openlocfilehash: 4b8728a175d67cc532866d4de41d412e459f0291
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="67021-104">Organiser et tester des projets avec la ligne de commande .NET Core</span><span class="sxs-lookup"><span data-stu-id="67021-104">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="67021-105">Ce didacticiel, qui fait suite à la rubrique [Bien démarrer avec .NET Core sur Windows/Linux/macOS à l’aide de la ligne de commande](using-with-xplat-cli.md), montre comment aller au-delà de la création d’une application console simple pour développer des applications avancées et bien organisées.</span><span class="sxs-lookup"><span data-stu-id="67021-105">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="67021-106">Après une présentation des dossiers disponibles pour organiser votre code, ce didacticiel vous montre comment étendre une application console avec le framework de tests [xUnit](https://xunit.github.io/).</span><span class="sxs-lookup"><span data-stu-id="67021-106">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="67021-107">Utilisation de dossiers pour organiser le code</span><span class="sxs-lookup"><span data-stu-id="67021-107">Using folders to organize code</span></span>

<span data-ttu-id="67021-108">Si vous souhaitez introduire de nouveaux types dans une application console, ajoutez des fichiers contenant les types à l’application.</span><span class="sxs-lookup"><span data-stu-id="67021-108">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="67021-109">Par exemple, si vous ajoutez des fichiers contenant les types `AccountInformation` et `MonthlyReportRecords` à votre projet, la structure du fichier projet est plate et facile à parcourir :</span><span class="sxs-lookup"><span data-stu-id="67021-109">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="67021-110">Toutefois, cela ne fonctionne bien que si la taille de votre projet est relativement petite.</span><span class="sxs-lookup"><span data-stu-id="67021-110">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="67021-111">Imaginez ce qui se passerait si vous ajoutiez 20 types au projet :</span><span class="sxs-lookup"><span data-stu-id="67021-111">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="67021-112">avec autant de fichiers alourdissant le répertoire racine du projet, la navigation et la maintenance seraient particulièrement difficiles.</span><span class="sxs-lookup"><span data-stu-id="67021-112">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="67021-113">Pour organiser le projet, créez un dossier et nommez-le *Models* pour stocker les fichiers de types.</span><span class="sxs-lookup"><span data-stu-id="67021-113">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="67021-114">Placez les fichiers de types dans le dossier *Models* :</span><span class="sxs-lookup"><span data-stu-id="67021-114">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="67021-115">Les projets qui regroupent logiquement les fichiers dans des dossiers simplifient la navigation et la gestion.</span><span class="sxs-lookup"><span data-stu-id="67021-115">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="67021-116">Dans la section suivante, vous allez créer un exemple plus complexe avec des dossiers et des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="67021-116">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="67021-117">Organisation et test du code à l’aide de l’exemple NewTypes Pets</span><span class="sxs-lookup"><span data-stu-id="67021-117">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="67021-118">Génération de l’exemple</span><span class="sxs-lookup"><span data-stu-id="67021-118">Building the sample</span></span>

<span data-ttu-id="67021-119">Pour les étapes suivantes, vous pouvez soit suivre [l’exemple NewTypes Pets](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild), soit créer vos propres fichiers et dossiers.</span><span class="sxs-lookup"><span data-stu-id="67021-119">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="67021-120">Les types et les tests sont logiquement organisés dans une structure de dossiers qui autorise l’ajout d’autres types et tests par la suite.</span><span class="sxs-lookup"><span data-stu-id="67021-120">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="67021-121">L’exemple contient deux types, `Dog` et `Cat`, qui implémentent une interface commune `IPet`.</span><span class="sxs-lookup"><span data-stu-id="67021-121">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="67021-122">Pour le projet `NewTypes`, votre objectif est d’organiser les types liés aux animaux domestiques dans un dossier *Pets*.</span><span class="sxs-lookup"><span data-stu-id="67021-122">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="67021-123">Si un autre jeu de types est ajouté par la suite, *WildAnimals* par exemple, il est placé dans le dossier *NewTypes* aux côtés du dossier *Pets*.</span><span class="sxs-lookup"><span data-stu-id="67021-123">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="67021-124">Le dossier *WildAnimals* peut contenir des types pour des animaux non domestiques, par exemple `Squirrel` et `Rabbit`.</span><span class="sxs-lookup"><span data-stu-id="67021-124">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="67021-125">De cette façon, à mesure que vous ajoutez des types, le projet reste bien organisé.</span><span class="sxs-lookup"><span data-stu-id="67021-125">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="67021-126">Créez la structure de dossiers suivante avec le contenu de fichier indiqué :</span><span class="sxs-lookup"><span data-stu-id="67021-126">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="67021-127">*IPet.cs* :</span><span class="sxs-lookup"><span data-stu-id="67021-127">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="67021-128">*Dog.cs* :</span><span class="sxs-lookup"><span data-stu-id="67021-128">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="67021-129">*Cat.cs* :</span><span class="sxs-lookup"><span data-stu-id="67021-129">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="67021-130">*Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="67021-130">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="67021-131">*NewTypes.csproj* :</span><span class="sxs-lookup"><span data-stu-id="67021-131">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="67021-132">Exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="67021-132">Execute the following commands:</span></span>

```console
dotnet run
```

<span data-ttu-id="67021-133">Observez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="67021-133">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="67021-134">Exercice facultatif : Vous pouvez ajouter un nouveau type d’animal domestique, par exemple `Bird`, en étendant ce projet.</span><span class="sxs-lookup"><span data-stu-id="67021-134">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="67021-135">Faites en sorte que la méthode `TalkToOwner` du type Bird envoie un `Tweet!` au propriétaire.</span><span class="sxs-lookup"><span data-stu-id="67021-135">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="67021-136">Réexécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="67021-136">Run the app again.</span></span> <span data-ttu-id="67021-137">La sortie inclut `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="67021-137">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="67021-138">Test de l’exemple</span><span class="sxs-lookup"><span data-stu-id="67021-138">Testing the sample</span></span>

<span data-ttu-id="67021-139">Le projet `NewTypes` est en place et vous l’avez organisé en conservant les types liés aux animaux domestiques dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="67021-139">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="67021-140">Créez à présent votre projet de test et commencez à écrire des tests à l’aide du framework de tests [xUnit](https://xunit.github.io/).</span><span class="sxs-lookup"><span data-stu-id="67021-140">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="67021-141">Les tests unitaires vous permettent de vérifier automatiquement le comportement de vos types d’animaux domestiques et de confirmer qu’ils fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="67021-141">Unit testing allows you to automatically check the bevahior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="67021-142">Créez un dossier*test* et un sous-dossier *NewTypesTests*.</span><span class="sxs-lookup"><span data-stu-id="67021-142">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="67021-143">À une invite de commandes à partir du dossier *NewTypesTests*, exécutez `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="67021-143">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="67021-144">Deux fichiers sont générés : *NewTypesTests.csproj* et *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="67021-144">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="67021-145">Le projet de test ne peut pas actuellement tester les types dans `NewTypes` et nécessite une référence de projet au projet `NewTypes`.</span><span class="sxs-lookup"><span data-stu-id="67021-145">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="67021-146">Pour ajouter une référence de projet, utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="67021-146">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="67021-147">Vous pouvez également ajouter manuellement la référence de projet en ajoutant un nœud `<ItemGroup>` au fichier *NewTypesTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="67021-147">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="67021-148">*NewTypesTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="67021-148">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="67021-149">Le fichier *NewTypesTests.csproj* contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="67021-149">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="67021-150">Référence de package à `Microsoft.NET.Test.Sdk` (infrastructure de tests .NET)</span><span class="sxs-lookup"><span data-stu-id="67021-150">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="67021-151">Référence de package à `xunit` (framework de tests xUnit)</span><span class="sxs-lookup"><span data-stu-id="67021-151">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="67021-152">Référence de package à `xunit.runner.visualstudio` (Test Runner)</span><span class="sxs-lookup"><span data-stu-id="67021-152">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="67021-153">Référence de projet à `NewTypes` (code à tester)</span><span class="sxs-lookup"><span data-stu-id="67021-153">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="67021-154">Renommez *UnitTest1.cs* en *PetTests.cs* et remplacez le code dans le fichier par le suivant :</span><span class="sxs-lookup"><span data-stu-id="67021-154">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="67021-155">Exercice facultatif : Si vous avez précédemment ajouté un type `Bird` qui envoie un `Tweet!` au propriétaire, ajoutez une méthode de test au fichier *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, pour vérifier que la méthode `TalkToOwner` fonctionne correctement pour le type `Bird`.</span><span class="sxs-lookup"><span data-stu-id="67021-155">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="67021-156">Bien que l’on s’attende à ce que les valeurs `expected` et `actual` soient identiques, les assertions initiales avec les vérifications `Assert.NotEqual` spécifient qu’elles *ne sont pas égales*.</span><span class="sxs-lookup"><span data-stu-id="67021-156">Although you expect that the `expected` and `actual` values are equal, the initial assertions with the `Assert.NotEqual` checks specify that they are *not equal*.</span></span> <span data-ttu-id="67021-157">Commencez toujours par créer vos tests en les faisant échouer une fois pour vérifier leur logique.</span><span class="sxs-lookup"><span data-stu-id="67021-157">Always initially create your tests to fail once in order to check the logic of the tests.</span></span> <span data-ttu-id="67021-158">Il s’agit d’une étape importante de la méthodologie de conception conduite par les tests.</span><span class="sxs-lookup"><span data-stu-id="67021-158">This is an important step in test-driven design (TDD) methodology.</span></span> <span data-ttu-id="67021-159">Après avoir confirmé l’échec des tests, ajustez les assertions pour leur permettre de réussir.</span><span class="sxs-lookup"><span data-stu-id="67021-159">After you confirm the tests fail, you adjust the assertions to allow them to pass.</span></span>

<span data-ttu-id="67021-160">Le code suivant montre la structure complète du projet :</span><span class="sxs-lookup"><span data-stu-id="67021-160">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="67021-161">Démarrez dans le répertoire *test/NewTypesTests*.</span><span class="sxs-lookup"><span data-stu-id="67021-161">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="67021-162">Restaurez le projet de test avec la commande [`dotnet restore`](../tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="67021-162">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="67021-163">Exécutez les tests avec la commande [`dotnet test`](../tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="67021-163">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="67021-164">Cette commande démarre le Test Runner spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="67021-164">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="67021-165">Comme prévu, les tests échouent et la console affiche la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="67021-165">As expected, testing fails, and the console displays the following output:</span></span>
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

<span data-ttu-id="67021-166">Remplacez les assertions de vos tests `Assert.NotEqual` par `Assert.Equal` :</span><span class="sxs-lookup"><span data-stu-id="67021-166">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="67021-167">Réexécutez les tests avec la commande `dotnet test` et observez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="67021-167">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

<span data-ttu-id="67021-168">Les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="67021-168">Testing passes.</span></span> <span data-ttu-id="67021-169">Les méthodes des types d’animaux domestiques retournent des valeurs correctes quand elles communiquent avec le propriétaire.</span><span class="sxs-lookup"><span data-stu-id="67021-169">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="67021-170">Vous avez appris les techniques permettant d’organiser et de tester des projets à l’aide de xUnit.</span><span class="sxs-lookup"><span data-stu-id="67021-170">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="67021-171">Vous pouvez maintenant les mettre en pratique dans vos propres projets.</span><span class="sxs-lookup"><span data-stu-id="67021-171">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="67021-172">*Bon développement !*</span><span class="sxs-lookup"><span data-stu-id="67021-172">*Happy coding!*</span></span>

