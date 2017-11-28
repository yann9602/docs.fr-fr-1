---
title: Effectuer des tests unitaires de C# avec MSTest et .NET Core
description: "Apprenez les concepts des tests unitaires dans C# et .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de MSTest."
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
ms.openlocfilehash: 2915c2f4b18b9e9d03915c2f17cfc96d4f401c09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="f50ac-104">Effectuer des tests unitaires de C# avec MSTest et .NET Core</span><span class="sxs-lookup"><span data-stu-id="f50ac-104">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="f50ac-105">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="f50ac-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="f50ac-106">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="f50ac-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="f50ac-107">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f50ac-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="f50ac-108">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="f50ac-108">Creating the source project</span></span>

<span data-ttu-id="f50ac-109">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="f50ac-109">Open a shell window.</span></span> <span data-ttu-id="f50ac-110">Créez un répertoire appelé *unit-testing-using-dotnet-test* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="f50ac-110">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="f50ac-111">Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer un fichier de solution pour la bibliothèque de classes et le projet de test.</span><span class="sxs-lookup"><span data-stu-id="f50ac-111">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="f50ac-112">Ensuite, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="f50ac-112">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="f50ac-113">Vous disposez de la structure de répertoire et de fichiers suivante :</span><span class="sxs-lookup"><span data-stu-id="f50ac-113">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="f50ac-114">Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="f50ac-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="f50ac-115">Renommez *Class1.cs* en *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="f50ac-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="f50ac-116">Pour utiliser le développement piloté par les tests (TDD), vous créez une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="f50ac-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate) 
        {
            throw new NotImplementedException("Please create a test first");
        } 
    }
}
```

<span data-ttu-id="f50ac-117">Accédez de nouveau au répertoire *unit-testing-using-mstest*.</span><span class="sxs-lookup"><span data-stu-id="f50ac-117">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="f50ac-118">Exécutez [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.</span><span class="sxs-lookup"><span data-stu-id="f50ac-118">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="f50ac-119">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="f50ac-119">Creating the test project</span></span>

<span data-ttu-id="f50ac-120">Ensuite, créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="f50ac-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="f50ac-121">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="f50ac-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="f50ac-122">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new mstest`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="f50ac-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="f50ac-123">La commande dotnet new crée un projet de test qui utilise MSTest comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="f50ac-123">The dotnet new command creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="f50ac-124">Le modèle généré configure Test Runner dans le fichier *PrimeServiceTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="f50ac-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="f50ac-125">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="f50ac-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="f50ac-126">À l’étape précédente, `dotnet new` a ajouté le SDK MSTest, le framework de test MSTest et le Test Runner MSTest.</span><span class="sxs-lookup"><span data-stu-id="f50ac-126">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="f50ac-127">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="f50ac-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="f50ac-128">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="f50ac-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="f50ac-129">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="f50ac-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="f50ac-130">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="f50ac-130">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="f50ac-131">Exécutez [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="f50ac-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="f50ac-132">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="f50ac-132">Creating the first test</span></span>

<span data-ttu-id="f50ac-133">L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="f50ac-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="f50ac-134">Supprimez *UnitTest1.cs* du répertoire *PrimeService.Tests* et créez un fichier C# nommé *PrimeService_IsPrimeShould.cs* avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="f50ac-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="f50ac-135">L’attribut `[TestClass]` désigne une classe qui contient des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="f50ac-135">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="f50ac-136">L’attribut `[TestMethod]` indique une méthode qui est une méthode de test.</span><span class="sxs-lookup"><span data-stu-id="f50ac-136">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="f50ac-137">Enregistrez ce fichier et exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="f50ac-137">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="f50ac-138">Le Test Runner MSTest contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="f50ac-138">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="f50ac-139">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="f50ac-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="f50ac-140">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="f50ac-140">Your test fails.</span></span> <span data-ttu-id="f50ac-141">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="f50ac-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="f50ac-142">Pour que ce test réussisse, écrivez le code le plus simple dans la classe `PrimeService` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="f50ac-142">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

<span data-ttu-id="f50ac-143">Dans le répertoire *unit-testing-using-mstest*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="f50ac-143">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="f50ac-144">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="f50ac-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="f50ac-145">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="f50ac-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="f50ac-146">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="f50ac-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="f50ac-147">Ajout de fonctionnalités supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f50ac-147">Adding more features</span></span>

<span data-ttu-id="f50ac-148">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="f50ac-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="f50ac-149">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="f50ac-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="f50ac-150">Vous pouvez ajouter de nouveaux tests avec l’attribut `[TestMethod]`, mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="f50ac-150">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="f50ac-151">D’autres attributs MSTest vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="f50ac-151">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="f50ac-152">L’attribut `[DataTestMethod]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="f50ac-152">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="f50ac-153">Vous pouvez utiliser l’attribut `[DataRow]` pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="f50ac-153">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="f50ac-154">Au lieu de créer de nouveaux tests, appliquez ces deux attributs pour créer un test unique piloté par les données.</span><span class="sxs-lookup"><span data-stu-id="f50ac-154">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="f50ac-155">Le test piloté par les données est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :</span><span class="sxs-lookup"><span data-stu-id="f50ac-155">The data driven test is a method that tests several values less than two, which is the lowest prime number: :</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="f50ac-156">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="f50ac-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="f50ac-157">Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :</span><span class="sxs-lookup"><span data-stu-id="f50ac-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="f50ac-158">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="f50ac-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="f50ac-159">Vous disposez de la [version finale des tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="f50ac-159">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="f50ac-160">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f50ac-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="f50ac-161">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="f50ac-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="f50ac-162">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="f50ac-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
