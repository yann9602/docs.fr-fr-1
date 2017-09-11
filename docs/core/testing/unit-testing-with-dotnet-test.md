---
title: "Effectuer des tests unitaires dans .NET Core à l’aide de dotnet test et de xUnit"
description: "Apprenez les concepts des tests unitaires dans .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de xUnit."
author: ardalis
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.translationtype: HT
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: d989ee731d7ffd0439bac69afe1458e2aa10733a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/17/2017

---
# <a name="unit-testing-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="fa279-103">Effectuer des tests unitaires dans .NET Core à l’aide de dotnet test et de xUnit</span><span class="sxs-lookup"><span data-stu-id="fa279-103">Unit testing in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="fa279-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="fa279-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="fa279-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="fa279-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="fa279-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="fa279-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="fa279-107">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="fa279-107">Creating the source project</span></span>

<span data-ttu-id="fa279-108">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="fa279-108">Open a shell window.</span></span> <span data-ttu-id="fa279-109">Créez un répertoire appelé *unit-testing-using-dotnet-test* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="fa279-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="fa279-110">Dans ce nouveau répertoire, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="fa279-110">Inside this new directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="fa279-111">La structure de répertoires jusqu’ici est indiquée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="fa279-111">The directory structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    /PrimeService
```

<span data-ttu-id="fa279-112">Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="fa279-112">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="fa279-113">Renommez *Class1.cs* en *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="fa279-113">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="fa279-114">Pour utiliser le développement piloté par les tests (TDD), vous devez créer une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="fa279-114">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

## <a name="creating-the-test-project"></a><span data-ttu-id="fa279-115">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="fa279-115">Creating the test project</span></span>

<span data-ttu-id="fa279-116">Revenez au répertoire *unit-testing-using-dotnet-test* et créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="fa279-116">Change the directory back to the *unit-testing-using-dotnet-test* directory and create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="fa279-117">La structure de répertoires est indiquée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="fa279-117">The directory structure is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="fa279-118">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new xunit`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="fa279-118">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="fa279-119">Ceci crée un projet de test qui utilise xUnit comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="fa279-119">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="fa279-120">Le modèle généré configure Test Runner dans *PrimeServiceTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="fa279-120">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="fa279-121">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="fa279-121">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="fa279-122">`dotnet new` a ajouté xUnit et le Test Runner xUnit à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="fa279-122">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="fa279-123">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="fa279-123">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="fa279-124">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="fa279-124">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="fa279-125">Vous pouvez également modifier le fichier *PrimeService.Tests.csproj*.</span><span class="sxs-lookup"><span data-stu-id="fa279-125">Another option is to edit the *PrimeService.Tests.csproj* file.</span></span> <span data-ttu-id="fa279-126">Directement sous le premier nœud `<ItemGroup>`, ajoutez un autre nœud `<ItemGroup>` avec une référence au projet de bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="fa279-126">Directly under the first `<ItemGroup>` node, add another `<ItemGroup>` node with a reference to the library project:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

<span data-ttu-id="fa279-127">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="fa279-127">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="fa279-128">La disposition de la solution finale est présentée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="fa279-128">The final solution layout is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="fa279-129">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="fa279-129">Creating the first test</span></span>

<span data-ttu-id="fa279-130">Avant de générer la bibliothèque ou les tests, exécutez [ `dotnet restore` ](../tools/dotnet-restore.md) dans le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="fa279-130">Before building the library or the tests, execute [`dotnet restore`](../tools/dotnet-restore.md) in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="fa279-131">Cette commande restaure tous les packages NuGet nécessaires pour chaque projet.</span><span class="sxs-lookup"><span data-stu-id="fa279-131">This command restores all the necessary NuGet packages for each project.</span></span>

<span data-ttu-id="fa279-132">L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="fa279-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="fa279-133">Supprimez *UnitTest1.cs* du répertoire *PrimeService.Tests* et créez un fichier C# nommé *PrimeService_IsPrimeShould.cs* avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="fa279-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, $"1 should not be prime");
        }
    }
}
```

<span data-ttu-id="fa279-134">L’attribut `[Fact]` désigne une méthode en tant que test unique.</span><span class="sxs-lookup"><span data-stu-id="fa279-134">The `[Fact]` attribute denotes a method as a single test.</span></span> <span data-ttu-id="fa279-135">Exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="fa279-135">Execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="fa279-136">Le Test Runner xUnit contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="fa279-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="fa279-137">`dotnet test` démarre Test Runner et lui transmet un argument de ligne de commande désignant l’assembly qui contient vos tests.</span><span class="sxs-lookup"><span data-stu-id="fa279-137">`dotnet test` starts the test runner and provides a command-line argument to the test runner indicating the assembly that contains your tests.</span></span>

<span data-ttu-id="fa279-138">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="fa279-138">Your test fails.</span></span> <span data-ttu-id="fa279-139">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="fa279-139">You haven't created the implementation yet.</span></span> <span data-ttu-id="fa279-140">Écrivez le code le plus simple dans la classe `PrimeService` pour faire en sorte que ce test réussisse :</span><span class="sxs-lookup"><span data-stu-id="fa279-140">Write the simplest code in the `PrimeService` class to make this test pass:</span></span>

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

<span data-ttu-id="fa279-141">Dans le répertoire *PrimeService.Tests*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="fa279-141">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="fa279-142">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="fa279-142">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="fa279-143">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="fa279-143">After building both projects, it runs this single test.</span></span> <span data-ttu-id="fa279-144">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="fa279-144">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="fa279-145">Ajout de fonctionnalités supplémentaires</span><span class="sxs-lookup"><span data-stu-id="fa279-145">Adding more features</span></span>

<span data-ttu-id="fa279-146">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="fa279-146">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="fa279-147">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="fa279-147">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="fa279-148">Vous pouvez les ajouter en tant que nouveaux tests, avec l’attribut `[Fact]`, mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="fa279-148">You could add those as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="fa279-149">D’autres attributs xUnit vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="fa279-149">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="fa279-150">L’attribut `[Theory]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="fa279-150">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="fa279-151">Vous pouvez utiliser l’attribut `[InlineData]` pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="fa279-151">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span> 
 
<span data-ttu-id="fa279-152">Au lieu de créer de nouveaux tests, servez-vous de ces deux attributs pour créer une théorie unique qui teste plusieurs valeurs inférieures à 2, qui est le nombre premier le plus petit :</span><span class="sxs-lookup"><span data-stu-id="fa279-152">Instead of creating new tests, leverage these two attributes to create a single theory that tests several values less than two, which is the lowest prime number:</span></span>

<span data-ttu-id="fa279-153">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span><span class="sxs-lookup"><span data-stu-id="fa279-153">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span></span>

<span data-ttu-id="fa279-154">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="fa279-154">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="fa279-155">Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :</span><span class="sxs-lookup"><span data-stu-id="fa279-155">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="fa279-156">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="fa279-156">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="fa279-157">Vous parviendrez à la [version finale des tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et à l’[implémentation complète de la bibliothèque](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="fa279-157">You'll end up with the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="fa279-158">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="fa279-158">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="fa279-159">Vous avez structuré la solution afin de faciliter l’ajout de nouveaux packages et tests, et vous pouvez concentrer vos efforts sur les objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="fa279-159">You've structured the solution so that adding new packages and tests is seamless, and you can concentrate most of your time and effort on solving the goals of the applicaiton.</span></span>

