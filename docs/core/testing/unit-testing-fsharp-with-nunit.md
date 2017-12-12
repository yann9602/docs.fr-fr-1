---
title: "Effectuer des tests unitaires des bibliothèques F# dans .NET Core à l’aide de dotnet test et de NUnit"
description: "Apprenez les concepts des tests unitaires pour F# dans .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de NUnit."
author: rprouse
ms.date: 12/01/2017
ms.topic: article
dev_langs: fsharp
ms.prod: .net-core
ms.openlocfilehash: 27a7bb889fd736294252da39b1839b2197b8df03
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="35b20-103">Effectuer des tests unitaires des bibliothèques F# dans .NET Core à l’aide de dotnet test et de NUnit</span><span class="sxs-lookup"><span data-stu-id="35b20-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="35b20-104">Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="35b20-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="35b20-105">Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-nunit/) avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="35b20-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="35b20-106">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="35b20-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="35b20-107">Création du projet source</span><span class="sxs-lookup"><span data-stu-id="35b20-107">Creating the source project</span></span>

<span data-ttu-id="35b20-108">Ouvrez une fenêtre d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="35b20-108">Open a shell window.</span></span> <span data-ttu-id="35b20-109">Créez un répertoire appelé *unit-testing-with-fsharp* qui contiendra la solution.</span><span class="sxs-lookup"><span data-stu-id="35b20-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="35b20-110">Dans ce nouveau répertoire, exécutez [`dotnet new sln`](../tools/dotnet-new.md) pour créer une solution.</span><span class="sxs-lookup"><span data-stu-id="35b20-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="35b20-111">Ceci permet de simplifier la gestion de la bibliothèque de classes et du projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="35b20-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="35b20-112">Dans le répertoire de la solution, créez un répertoire *MathService*.</span><span class="sxs-lookup"><span data-stu-id="35b20-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="35b20-113">La structure du répertoire et des fichiers jusqu’ici est indiquée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="35b20-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="35b20-114">Accédez au répertoire *MathService* et exécutez [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) pour créer le projet source.</span><span class="sxs-lookup"><span data-stu-id="35b20-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="35b20-115">Pour utiliser le développement piloté par les tests (TDD), vous devez créer une implémentation défaillante du service Math :</span><span class="sxs-lookup"><span data-stu-id="35b20-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let sumOfSquares xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="35b20-116">Accédez de nouveau au répertoire *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="35b20-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="35b20-117">Exécutez [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) pour ajouter le projet de la bibliothèque de classes à la solution.</span><span class="sxs-lookup"><span data-stu-id="35b20-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="35b20-118">Installer le modèle de projet NUnit</span><span class="sxs-lookup"><span data-stu-id="35b20-118">Install the NUnit project template</span></span>

<span data-ttu-id="35b20-119">Les modèles de projet de test NUnit doivent être installés avant de créer un projet de test.</span><span class="sxs-lookup"><span data-stu-id="35b20-119">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="35b20-120">Cette opération ne doit être effectuée qu’une fois sur chaque ordinateur de développeur où vous allez créer des projets NUnit.</span><span class="sxs-lookup"><span data-stu-id="35b20-120">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="35b20-121">Exécutez [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) pour installer les modèles NUnit.</span><span class="sxs-lookup"><span data-stu-id="35b20-121">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="35b20-122">Création du projet de test</span><span class="sxs-lookup"><span data-stu-id="35b20-122">Creating the test project</span></span>

<span data-ttu-id="35b20-123">Ensuite, créez le répertoire *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="35b20-123">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="35b20-124">La structure du répertoire est illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="35b20-124">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="35b20-125">Accédez au répertoire *MathService.Tests* et créez un projet à l’aide de [`dotnet new nunit -lang F#`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="35b20-125">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="35b20-126">Vous obtenez un projet de test qui utilise NUnit comme framework de test.</span><span class="sxs-lookup"><span data-stu-id="35b20-126">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="35b20-127">Le modèle généré configure le Test Runner dans *MathServiceTests.fsproj* :</span><span class="sxs-lookup"><span data-stu-id="35b20-127">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="35b20-128">Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="35b20-128">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="35b20-129">`dotnet new` dans l’étape précédente a ajouté NUnit et l’adaptateur de test NUnit.</span><span class="sxs-lookup"><span data-stu-id="35b20-129">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="35b20-130">Maintenant, ajoutez la bibliothèque de classes `MathService` en tant qu’une autre dépendance au projet.</span><span class="sxs-lookup"><span data-stu-id="35b20-130">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="35b20-131">Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="35b20-131">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="35b20-132">Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="35b20-132">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="35b20-133">La solution finale se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="35b20-133">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="35b20-134">Exécutez [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) dans le répertoire *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="35b20-134">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="35b20-135">Création du premier test</span><span class="sxs-lookup"><span data-stu-id="35b20-135">Creating the first test</span></span>

<span data-ttu-id="35b20-136">L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus.</span><span class="sxs-lookup"><span data-stu-id="35b20-136">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="35b20-137">Ouvrez *Tests.fs* et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="35b20-137">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="35b20-138">L’attribut `[<TestFixture>]` désigne une classe qui contient des tests.</span><span class="sxs-lookup"><span data-stu-id="35b20-138">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="35b20-139">L’attribut `[<Test>]` désigne une méthode de test qui est exécutée par le Test Runner.</span><span class="sxs-lookup"><span data-stu-id="35b20-139">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="35b20-140">À partir du répertoire *unit-testing-with-fsharp*, exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="35b20-140">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="35b20-141">Le Test Runner NUnit contient le point d’entrée de programme qui permet d’exécuter vos tests.</span><span class="sxs-lookup"><span data-stu-id="35b20-141">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="35b20-142">`dotnet test` démarre le Test Runner à l’aide du projet de test unitaire que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="35b20-142">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="35b20-143">Ces deux tests illustrent les tests de réussite et d’échec les plus basiques.</span><span class="sxs-lookup"><span data-stu-id="35b20-143">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="35b20-144">`My test` réussit et `Fail every time` échoue.</span><span class="sxs-lookup"><span data-stu-id="35b20-144">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="35b20-145">À présent, créez un test pour la méthode `sumOfSquares`.</span><span class="sxs-lookup"><span data-stu-id="35b20-145">Now, create a test for the `sumOfSquares` method.</span></span> <span data-ttu-id="35b20-146">La méthode `sumOfSquares` retourne la somme des carrés de toutes les valeurs de nombre entier impair qui font partie de la séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="35b20-146">The `sumOfSquares` method returns the sum of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="35b20-147">Au lieu d’essayer d’écrire toutes ces fonctions simultanément, vous pouvez créer de manière itérative des tests qui valident les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="35b20-147">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="35b20-148">La réussite de chaque test correspond à la création de la fonctionnalité nécessaire pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="35b20-148">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="35b20-149">Le test le plus simple que nous pouvons écrire consiste à appeler `sumOfSquares` avec tous les nombres pairs, où le résultat doit être une séquence vide de nombres entiers.</span><span class="sxs-lookup"><span data-stu-id="35b20-149">The simplest test we can write is to call `sumOfSquares` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="35b20-150">Voici ce test :</span><span class="sxs-lookup"><span data-stu-id="35b20-150">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.sumOfSquares [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="35b20-151">Notez que la séquence `expected` a été convertie en liste.</span><span class="sxs-lookup"><span data-stu-id="35b20-151">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="35b20-152">Le framework NUnit s’appuie sur de nombreux types .NET standard.</span><span class="sxs-lookup"><span data-stu-id="35b20-152">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="35b20-153">Cette dépendance signifie que votre interface publique et les résultats attendus prennent en charge <xref:System.Collections.ICollection> plutôt que <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="35b20-153">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="35b20-154">Lorsque vous exécutez le test, vous constatez que votre test échoue.</span><span class="sxs-lookup"><span data-stu-id="35b20-154">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="35b20-155">Vous n’avez pas encore créé l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="35b20-155">You haven't created the implementation yet.</span></span> <span data-ttu-id="35b20-156">Effectuez ce test en écrivant le code le plus simple dans la classe `Mathservice` qui fonctionne :</span><span class="sxs-lookup"><span data-stu-id="35b20-156">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let sumOfSquares xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="35b20-157">Dans le répertoire *unit-testing-with-fsharp*, réexécutez `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="35b20-157">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="35b20-158">La commande `dotnet test` exécute une build pour le projet `MathService` puis pour le projet `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="35b20-158">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="35b20-159">Après la création des deux projets, il exécute ce test unique.</span><span class="sxs-lookup"><span data-stu-id="35b20-159">After building both projects, it runs this single test.</span></span> <span data-ttu-id="35b20-160">Le test réussit.</span><span class="sxs-lookup"><span data-stu-id="35b20-160">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="35b20-161">Finalisation des spécifications</span><span class="sxs-lookup"><span data-stu-id="35b20-161">Completing the requirements</span></span>

<span data-ttu-id="35b20-162">Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.</span><span class="sxs-lookup"><span data-stu-id="35b20-162">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="35b20-163">Le cas simple suivant fonctionne avec une séquence dont le seul nombre impair est `1`.</span><span class="sxs-lookup"><span data-stu-id="35b20-163">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="35b20-164">Le nombre 1 est plus facile, car le carré de 1 est 1.</span><span class="sxs-lookup"><span data-stu-id="35b20-164">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="35b20-165">Voici ce test suivant :</span><span class="sxs-lookup"><span data-stu-id="35b20-165">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.SumOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.sumOfSquares [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="35b20-166">L’exécution de `dotnet test` fait échouer le nouveau test.</span><span class="sxs-lookup"><span data-stu-id="35b20-166">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="35b20-167">Vous devez mettre à jour la méthode `sumOfSquares` pour gérer ce nouveau test.</span><span class="sxs-lookup"><span data-stu-id="35b20-167">You must update the `sumOfSquares` method to handle this new test.</span></span> <span data-ttu-id="35b20-168">Vous devez filtrer tous les nombres pairs hors de la séquence pour que ce test réussisse.</span><span class="sxs-lookup"><span data-stu-id="35b20-168">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="35b20-169">Pour ce faire, vous pouvez écrire une petite fonction de filtre et utiliser `Seq.filter` :</span><span class="sxs-lookup"><span data-stu-id="35b20-169">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
    |> Seq.toList
```

<span data-ttu-id="35b20-170">Notez l’appel à `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="35b20-170">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="35b20-171">Ceci crée une liste qui implémente l’interface <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="35b20-171">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="35b20-172">Encore une étape : calculer le carré de chaque nombre impair.</span><span class="sxs-lookup"><span data-stu-id="35b20-172">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="35b20-173">Commencez par écrire un nouveau test :</span><span class="sxs-lookup"><span data-stu-id="35b20-173">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.sumOfSquares [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="35b20-174">Vous pouvez corriger le test en redirigeant la séquence filtrée via une opération de mappage pour calculer le carré de chaque nombre impair :</span><span class="sxs-lookup"><span data-stu-id="35b20-174">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="35b20-175">Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="35b20-175">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="35b20-176">Vous avez structuré la solution afin que l’ajout de nouveaux packages et tests fasse partie du flux de travail normal.</span><span class="sxs-lookup"><span data-stu-id="35b20-176">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="35b20-177">Vous avez concentré la plupart de votre temps et de vos efforts sur la résolution des objectifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="35b20-177">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
