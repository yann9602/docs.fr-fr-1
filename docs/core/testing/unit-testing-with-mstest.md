---
title: Tests unitaires avec MSTest et .NET Core
description: Comment utiliser MSTest avec .NET Core
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d1cb9f6667e1317e74d246988ef1257d0712c431
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="unit-testing-with-mstest-and-net-core"></a><span data-ttu-id="03997-104">Tests unitaires avec MSTest et .NET Core</span><span class="sxs-lookup"><span data-stu-id="03997-104">Unit testing with MSTest and .NET Core</span></span>

<span data-ttu-id="03997-105">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="03997-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="03997-106">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="03997-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="03997-107">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="03997-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="03997-108">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="03997-108">Creating the source project</span></span>

<span data-ttu-id="03997-109">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="03997-109">Open a shell window.</span></span> <span data-ttu-id="03997-110">Créez un répertoire appelé *unit-testing-using-dotnet-test* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="03997-110">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="03997-111">Dans ce nouveau répertoire, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="03997-111">Inside this new directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="03997-112">La structure de répertoires jusqu’ici est indiquée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="03997-112">The directory structure thus far is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
```

<span data-ttu-id="03997-113">Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="03997-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="03997-114">Renommez *Class1.cs* en *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="03997-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="03997-115">Pour utiliser le développement piloté par les tests (TDD), vous devez créer une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="03997-115">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

### <a name="creating-the-test-project"></a><span data-ttu-id="03997-116">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="03997-116">Creating the test project</span></span>

<span data-ttu-id="03997-117">Revenez au répertoire *unit-testing-using-mstest* et créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="03997-117">Change the directory back to the *unit-testing-using-mstest* directory and create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="03997-118">La structure de répertoires est indiquée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="03997-118">The directory structure is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="03997-119">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new mstest`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="03997-119">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="03997-120">Vous obtenez un projet de test qui utilise MSTest comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="03997-120">This creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="03997-121">Le modèle généré configure Test Runner dans le fichier *PrimeServiceTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="03997-121">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.11" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11" />
</ItemGroup>
```

<span data-ttu-id="03997-122">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="03997-122">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="03997-123">À l’étape précédente, `dotnet new` a ajouté le SDK MSTest, le framework de test MSTest et le Test Runner MSTest.</span><span class="sxs-lookup"><span data-stu-id="03997-123">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="03997-124">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="03997-124">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="03997-125">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="03997-125">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="03997-126">Vous pouvez également modifier le fichier *PrimeService.Tests.csproj*.</span><span class="sxs-lookup"><span data-stu-id="03997-126">Another option is to edit the *PrimeService.Tests.csproj* file.</span></span> <span data-ttu-id="03997-127">Directement sous le premier nœud `<ItemGroup>`, ajoutez un autre nœud `<ItemGroup>` avec une référence au projet de bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="03997-127">Directly under the first `<ItemGroup>` node, add another `<ItemGroup>` node with a reference to the library project:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

<span data-ttu-id="03997-128">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="03997-128">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="03997-129">La disposition de la solution finale est présentée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="03997-129">The final solution layout is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="03997-130">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="03997-130">Creating the first test</span></span>

<span data-ttu-id="03997-131">Avant de générer la bibliothèque ou les tests, exécutez [ `dotnet restore` ](../tools/dotnet-restore.md) dans le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="03997-131">Before building the library or the tests, execute [`dotnet restore`](../tools/dotnet-restore.md) in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="03997-132">Cette commande restaure tous les packages NuGet nécessaires pour chaque projet.</span><span class="sxs-lookup"><span data-stu-id="03997-132">This command restores all the necessary NuGet packages for each project.</span></span>

<span data-ttu-id="03997-133">L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="03997-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="03997-134">Supprimez *UnitTest1.cs* du répertoire *PrimeService.Tests* et créez un fichier C# nommé *PrimeService_IsPrimeShould.cs* avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="03997-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

            Assert.IsFalse(result, $"1 should not be prime");
        }
    }
}
```

<span data-ttu-id="03997-135">L’attribut `[TestClass]` désigne une classe qui contient des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="03997-135">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="03997-136">L’attribut `[TestMethod]` désigne une méthode en tant que test unique.</span><span class="sxs-lookup"><span data-stu-id="03997-136">The `[TestMethod]` attribute denotes a method as a single test.</span></span> 

<span data-ttu-id="03997-137">Enregistrez ce fichier et exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="03997-137">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="03997-138">Le Test Runner MSTest contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="03997-138">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="03997-139">`dotnet test` démarre Test Runner et lui transmet un argument de ligne de commande désignant l’assembly qui contient vos tests.</span><span class="sxs-lookup"><span data-stu-id="03997-139">`dotnet test` starts the test runner and provides a command-line argument to the test runner indicating the assembly that contains your tests.</span></span>

<span data-ttu-id="03997-140">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="03997-140">Your test fails.</span></span> <span data-ttu-id="03997-141">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="03997-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="03997-142">Écrivez le code le plus simple dans la classe `PrimeService` pour faire en sorte que ce test réussisse :</span><span class="sxs-lookup"><span data-stu-id="03997-142">Write the simplest code in the `PrimeService` class to make this test pass:</span></span>

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

<span data-ttu-id="03997-143">Dans le répertoire *PrimeService.Tests*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="03997-143">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="03997-144">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="03997-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="03997-145">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="03997-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="03997-146">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="03997-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="03997-147">Ajout de fonctionnalités supplémentaires</span><span class="sxs-lookup"><span data-stu-id="03997-147">Adding more features</span></span>

<span data-ttu-id="03997-148">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="03997-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="03997-149">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="03997-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="03997-150">Vous pouvez les ajouter en tant que nouveaux tests, avec l’attribut `[TestMethod]`, mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="03997-150">You could add those as new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="03997-151">D’autres attributs MSTest vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="03997-151">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="03997-152">L’attribut `[DataTestMethod]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="03997-152">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="03997-153">Vous pouvez utiliser l’attribut `[DataRow]` pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="03997-153">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span> 
 
<span data-ttu-id="03997-154">Au lieu de créer d’autres tests, servez-vous de ces deux attributs pour créer une méthode de test de données unique testant plusieurs valeurs inférieures à 2, qui est le nombre premier le plus petit :</span><span class="sxs-lookup"><span data-stu-id="03997-154">Instead of creating new tests, leverage these two attributes to create a single data test method that tests several values less than two, which is the lowest prime number:</span></span>

<span data-ttu-id="03997-155">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span><span class="sxs-lookup"><span data-stu-id="03997-155">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span></span>

<span data-ttu-id="03997-156">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="03997-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="03997-157">Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :</span><span class="sxs-lookup"><span data-stu-id="03997-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="03997-158">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="03997-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="03997-159">Vous parviendrez à la [version finale des tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et à l’[implémentation complète de la bibliothèque](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="03997-159">You'll end up with the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="03997-160">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="03997-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="03997-161">Vous avez structuré la solution afin de faciliter l’ajout de nouveaux packages et tests, et vous pouvez concentrer vos efforts sur les objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="03997-161">You've structured the solution so that adding new packages and tests is seamless, and you can concentrate most of your time and effort on solving the goals of the applicaiton.</span></span>

