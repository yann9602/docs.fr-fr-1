---
title: "Effectuer des tests unitaires du code C# dans .NET Core à l’aide de dotnet test et de xUnit"
description: "Apprenez les concepts des tests unitaires dans C# et .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de xUnit."
author: ardalis
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6e986e89d47ba4de9b8563f1a95cb1ae89accc89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="1460e-103">Effectuer des tests unitaires de C# dans .NET Core à l’aide de dotnet test et de xUnit</span><span class="sxs-lookup"><span data-stu-id="1460e-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="1460e-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="1460e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="1460e-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="1460e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="1460e-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="1460e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="1460e-107">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="1460e-107">Creating the source project</span></span>

<span data-ttu-id="1460e-108">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="1460e-108">Open a shell window.</span></span> <span data-ttu-id="1460e-109">Créez un répertoire appelé *unit-testing-using-dotnet-test* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="1460e-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="1460e-110">Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer une solution.</span><span class="sxs-lookup"><span data-stu-id="1460e-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="1460e-111">Ceci permet de simplifier la gestion de la bibliothèque de classes et du projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="1460e-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="1460e-112">Dans le répertoire de la solution, créez un répertoire *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="1460e-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="1460e-113">La structure du répertoire et des fichiers jusqu’ici est indiquée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="1460e-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="1460e-114">Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="1460e-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="1460e-115">Renommez *Class1.cs* en *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="1460e-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="1460e-116">Pour utiliser le développement piloté par les tests (TDD), vous devez créer une implémentation défaillante de la classe `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="1460e-116">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="1460e-117">Accédez de nouveau au répertoire *unit-testing-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="1460e-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span> <span data-ttu-id="1460e-118">Exécutez [`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.</span><span class="sxs-lookup"><span data-stu-id="1460e-118">Run [`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="1460e-119">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="1460e-119">Creating the test project</span></span>

<span data-ttu-id="1460e-120">Ensuite, créez le répertoire *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="1460e-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="1460e-121">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="1460e-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="1460e-122">Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new xunit`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="1460e-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="1460e-123">Ceci crée un projet de test qui utilise xUnit comme bibliothèque de test.</span><span class="sxs-lookup"><span data-stu-id="1460e-123">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="1460e-124">Le modèle généré configure Test Runner dans *PrimeServiceTests.csproj* :</span><span class="sxs-lookup"><span data-stu-id="1460e-124">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="1460e-125">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="1460e-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="1460e-126">`dotnet new` a ajouté xUnit et le Test Runner xUnit à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="1460e-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="1460e-127">Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="1460e-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="1460e-128">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="1460e-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="1460e-129">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="1460e-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="1460e-130">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="1460e-130">The following shows the final solution layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="1460e-131">Exécutez [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="1460e-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="1460e-132">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="1460e-132">Creating the first test</span></span>

<span data-ttu-id="1460e-133">L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="1460e-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="1460e-134">Supprimez *UnitTest1.cs* du répertoire *PrimeService.Tests* et créez un fichier C# nommé *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="1460e-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="1460e-135">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1460e-135">Add the following code:</span></span>

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

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="1460e-136">L’attribut `[Fact]` désigne une méthode de test qui est exécutée par le Test Runner.</span><span class="sxs-lookup"><span data-stu-id="1460e-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="1460e-137">À partir de *unit-testing-using-dotnet-test*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="1460e-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="1460e-138">Le Test Runner xUnit contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="1460e-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="1460e-139">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="1460e-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="1460e-140">Votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="1460e-140">Your test fails.</span></span> <span data-ttu-id="1460e-141">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="1460e-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="1460e-142">Effectuez ce test en écrivant le code le plus simple dans la classe `PrimeService` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="1460e-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="1460e-143">Dans le répertoire *unit-testing-using-dotnet-test*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="1460e-143">In the *unit-testing-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="1460e-144">La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="1460e-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="1460e-145">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="1460e-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="1460e-146">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="1460e-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="1460e-147">Ajout de fonctionnalités supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1460e-147">Adding more features</span></span>

<span data-ttu-id="1460e-148">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="1460e-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="1460e-149">Il existe quelques autres cas simples pour des nombres premiers : 0, -1.</span><span class="sxs-lookup"><span data-stu-id="1460e-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="1460e-150">Vous pouvez ajouter ces cas en tant que nouveaux tests, avec l’attribut `[Fact]`, mais cela devient vite fastidieux.</span><span class="sxs-lookup"><span data-stu-id="1460e-150">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="1460e-151">D’autres attributs xUnit vous permettent d’écrire une suite de tests similaires.</span><span class="sxs-lookup"><span data-stu-id="1460e-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="1460e-152">L’attribut `[Theory]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.</span><span class="sxs-lookup"><span data-stu-id="1460e-152">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="1460e-153">Vous pouvez utiliser l’attribut `[InlineData]` pour spécifier des valeurs pour ces entrées.</span><span class="sxs-lookup"><span data-stu-id="1460e-153">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="1460e-154">Au lieu de créer de nouveaux tests, appliquez ces deux attributs pour créer une théorie unique.</span><span class="sxs-lookup"><span data-stu-id="1460e-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="1460e-155">La théorie est une méthode qui teste plusieurs valeurs inférieures à deux, qui est le plus petit nombre premier :</span><span class="sxs-lookup"><span data-stu-id="1460e-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="1460e-156">Exécutez `dotnet test`, et deux de ces tests échouent.</span><span class="sxs-lookup"><span data-stu-id="1460e-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="1460e-157">Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :</span><span class="sxs-lookup"><span data-stu-id="1460e-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="1460e-158">Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="1460e-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="1460e-159">Vous disposez de la [version finale des tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et de [l’implémentation complète de la bibliothèque](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="1460e-159">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1460e-160">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1460e-160">Additional resources</span></span>

[<span data-ttu-id="1460e-161">Pour tester la logique de contrôleur dans ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1460e-161">Testing controller logic in ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)
