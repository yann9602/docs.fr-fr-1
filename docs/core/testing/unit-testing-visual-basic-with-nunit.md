---
title: "Effectuer des tests unitaires sur Visual Basic dans .NET Core à l’aide de dotnet test et de NUnit"
description: "Apprenez les concepts des tests unitaires dans .NET Core de manière interactive en créant un exemple de solution Visual Basic pas à pas à l’aide de NUnit."
author: rprouse
ms.date: 12/01/2017
ms.topic: article
dev_langs: vb
ms.prod: .net-core
ms.openlocfilehash: 2166da36fe9d0297f03e7c38249135d281b9a5d6
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="08d1a-103">Effectuer des tests unitaires sur les bibliothèques .NET Core Visual Basic à l’aide de dotnet test et de NUnit</span><span class="sxs-lookup"><span data-stu-id="08d1a-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="08d1a-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="08d1a-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="08d1a-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-vb-nunit/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="08d1a-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="08d1a-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="08d1a-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="08d1a-107">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="08d1a-107">Creating the source project</span></span>

<span data-ttu-id="08d1a-108">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="08d1a-108">Open a shell window.</span></span> <span data-ttu-id="08d1a-109">Créez un répertoire appelé *unit-testing-vb-nunit* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="08d1a-109">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="08d1a-110">Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer une solution.</span><span class="sxs-lookup"><span data-stu-id="08d1a-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="08d1a-111">Cette méthode permet de simplifier la gestion de la bibliothèque de classes et du projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="08d1a-111">This practice makes it easier to manage both the class library and the unit test project.</span></span> <span data-ttu-id="08d1a-112">Dans le répertoire de la solution, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="08d1a-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="08d1a-113">Vous disposez de la structure du répertoire et des fichiers suivante :</span><span class="sxs-lookup"><span data-stu-id="08d1a-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="08d1a-114">Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="08d1a-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="08d1a-115">Renommez *Class1.VB* en *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="08d1a-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="08d1a-116">Pour utiliser le développement piloté par les tests (TDD), vous créez une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="08d1a-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="08d1a-117">Accédez de nouveau au répertoire *unit-testing-vb-using-stest*.</span><span class="sxs-lookup"><span data-stu-id="08d1a-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="08d1a-118">Exécutez [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.</span><span class="sxs-lookup"><span data-stu-id="08d1a-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="08d1a-119">Installer le modèle de projet NUnit</span><span class="sxs-lookup"><span data-stu-id="08d1a-119">Install the NUnit project template</span></span>

<span data-ttu-id="08d1a-120">Les modèles de projet de test NUnit doivent être installés avant de créer un projet de test.</span><span class="sxs-lookup"><span data-stu-id="08d1a-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="08d1a-121">Cette opération ne doit être effectuée qu’une fois sur chaque ordinateur de développeur où vous allez créer des projets NUnit.</span><span class="sxs-lookup"><span data-stu-id="08d1a-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="08d1a-122">Exécutez [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) pour installer les modèles NUnit.</span><span class="sxs-lookup"><span data-stu-id="08d1a-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="08d1a-123">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="08d1a-123">Creating the test project</span></span>

<span data-ttu-id="08d1a-124">Ensuite, créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="08d1a-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="08d1a-125">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="08d1a-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="08d1a-126">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="08d1a-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="08d1a-127">Cette commande crée un projet de test qui utilise NUnit comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="08d1a-127">This command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="08d1a-128">Le modèle généré configure le Test Runner dans *PrimeServiceTests.vbproj* :</span><span class="sxs-lookup"><span data-stu-id="08d1a-128">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="08d1a-129">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="08d1a-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="08d1a-130">`dotnet new` dans l’étape précédente a ajouté NUnit et l’adaptateur de test NUnit.</span><span class="sxs-lookup"><span data-stu-id="08d1a-130">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="08d1a-131">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="08d1a-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="08d1a-132">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="08d1a-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="08d1a-133">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="08d1a-133">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="08d1a-134">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="08d1a-134">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="08d1a-135">Exécutez [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-vb-nunit*.</span><span class="sxs-lookup"><span data-stu-id="08d1a-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-nunit* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="08d1a-136">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="08d1a-136">Creating the first test</span></span>

<span data-ttu-id="08d1a-137">L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="08d1a-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="08d1a-138">Supprimez *UnitTest1.vb* du répertoire *PrimeService.Tests* et créez un fichier Visual Basic nommé *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="08d1a-138">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="08d1a-139">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="08d1a-139">Add the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="08d1a-140">L’attribut `<TestFixture>` désigne une classe qui contient des tests.</span><span class="sxs-lookup"><span data-stu-id="08d1a-140">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="08d1a-141">L’attribut `<Test>` désigne une méthode qui est exécutée par le Test Runner.</span><span class="sxs-lookup"><span data-stu-id="08d1a-141">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="08d1a-142">À partir de *unit-testing-vb-nunit*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="08d1a-142">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="08d1a-143">Le Test Runner NUnit contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="08d1a-143">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="08d1a-144">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="08d1a-144">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="08d1a-145">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="08d1a-145">Your test fails.</span></span> <span data-ttu-id="08d1a-146">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="08d1a-146">You haven't created the implementation yet.</span></span> <span data-ttu-id="08d1a-147">Effectuez ce test en écrivant le code le plus simple dans la classe `PrimeService` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="08d1a-147">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="08d1a-148">Dans le répertoire *unit-testing-vb-nunit*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="08d1a-148">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="08d1a-149">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="08d1a-149">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="08d1a-150">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="08d1a-150">After building both projects, it runs this single test.</span></span> <span data-ttu-id="08d1a-151">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="08d1a-151">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="08d1a-152">Ajout de fonctionnalités supplémentaires</span><span class="sxs-lookup"><span data-stu-id="08d1a-152">Adding more features</span></span>

<span data-ttu-id="08d1a-153">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="08d1a-153">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="08d1a-154">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="08d1a-154">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="08d1a-155">Vous pouvez ajouter ces cas en tant que nouveaux tests, avec l’attribut `<Test>`, mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="08d1a-155">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="08d1a-156">D’autres attributs xUnit vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="08d1a-156">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="08d1a-157">L’attribut `<TestCase>` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="08d1a-157">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="08d1a-158">Vous pouvez utiliser l’attribut `<TestCase>` pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="08d1a-158">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="08d1a-159">Au lieu de créer des tests, appliquez ces deux attributs pour créer une série de tests qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :</span><span class="sxs-lookup"><span data-stu-id="08d1a-159">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="08d1a-160">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="08d1a-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="08d1a-161">Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :</span><span class="sxs-lookup"><span data-stu-id="08d1a-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="08d1a-162">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="08d1a-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="08d1a-163">Vous disposez de la [version finale des tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="08d1a-163">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="08d1a-164">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="08d1a-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="08d1a-165">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="08d1a-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="08d1a-166">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="08d1a-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
