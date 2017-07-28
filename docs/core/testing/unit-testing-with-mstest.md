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

# <a name="unit-testing-with-mstest-and-net-core"></a>Tests unitaires avec MSTest et .NET Core

Ce didacticiel vous guide pas à pas dans la création d’un exemple de solution pour apprendre les concepts des tests unitaires. Si vous préférez suivre le didacticiel à l’aide d’une solution prédéfinie, [affichez ou téléchargez l’exemple de code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) avant de commencer. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="creating-the-source-project"></a>Création du projet source

Ouvrez une fenêtre d’interpréteur de commandes. Créez un répertoire appelé *unit-testing-using-dotnet-test* qui contiendra la solution. Dans ce nouveau répertoire, créez un répertoire *PrimeService*. La structure de répertoires jusqu’ici est indiquée ci-dessous :

```
/unit-testing-using-mstest
    /PrimeService
```

Accédez au répertoire *PrimeService* et exécutez [`dotnet new classlib`](../tools/dotnet-new.md) pour créer le projet source. Renommez *Class1.cs* en *PrimeService.cs*. Pour utiliser le développement piloté par les tests (TDD), vous devez créer une implémentation défaillante de la classe `PrimeService` :

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

### <a name="creating-the-test-project"></a>Création du projet de test

Revenez au répertoire *unit-testing-using-mstest* et créez le répertoire *PrimeService.Tests*. La structure de répertoires est indiquée ci-dessous :

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Accédez au répertoire *PrimeService.Tests* et créez un projet à l’aide de [`dotnet new mstest`](../tools/dotnet-new.md). Vous obtenez un projet de test qui utilise MSTest comme bibliothèque de test. Le modèle généré configure Test Runner dans le fichier *PrimeServiceTests.csproj* :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.11" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11" />
</ItemGroup>
```

Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires. À l’étape précédente, `dotnet new` a ajouté le SDK MSTest, le framework de test MSTest et le Test Runner MSTest. Maintenant, ajoutez la bibliothèque de classes `PrimeService` en tant qu’une autre dépendance au projet. Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Vous pouvez également modifier le fichier *PrimeService.Tests.csproj*. Directement sous le premier nœud `<ItemGroup>`, ajoutez un autre nœud `<ItemGroup>` avec une référence au projet de bibliothèque :

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) sur GitHub.

La disposition de la solution finale est présentée ci-dessous :

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a>Création du premier test

Avant de générer la bibliothèque ou les tests, exécutez [ `dotnet restore` ](../tools/dotnet-restore.md) dans le répertoire *PrimeService.Tests*. Cette commande restaure tous les packages NuGet nécessaires pour chaque projet.

L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus. Supprimez *UnitTest1.cs* du répertoire *PrimeService.Tests* et créez un fichier C# nommé *PrimeService_IsPrimeShould.cs* avec le contenu suivant :

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

L’attribut `[TestClass]` désigne une classe qui contient des tests unitaires. L’attribut `[TestMethod]` désigne une méthode en tant que test unique. 

Enregistrez ce fichier et exécutez [`dotnet test`](../tools/dotnet-test.md) pour générer les tests et la bibliothèque de classes, puis exécutez les tests. Le Test Runner MSTest contient le point d’entrée de programme qui permet d’exécuter vos tests. `dotnet test` démarre Test Runner et lui transmet un argument de ligne de commande désignant l’assembly qui contient vos tests.

Votre test échoue. Vous n’avez pas encore créé l’implémentation. Écrivez le code le plus simple dans la classe `PrimeService` pour faire en sorte que ce test réussisse :

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

Dans le répertoire *PrimeService.Tests*, réexécutez `dotnet test`. La commande `dotnet test` exécute une build pour le projet `PrimeService` puis pour le projet `PrimeService.Tests`. Après la création des deux projets, il exécute ce test unique. Le test réussit.

## <a name="adding-more-features"></a>Ajout de fonctionnalités supplémentaires

Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code. Il existe quelques autres cas simples pour des nombres premiers : 0, -1. Vous pouvez les ajouter en tant que nouveaux tests, avec l’attribut `[TestMethod]`, mais cela devient vite fastidieux. D’autres attributs MSTest vous permettent d’écrire une suite de tests similaires.  L’attribut `[DataTestMethod]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents. Vous pouvez utiliser l’attribut `[DataRow]` pour spécifier des valeurs pour ces entrées. 
 
Au lieu de créer d’autres tests, servez-vous de ces deux attributs pour créer une méthode de test de données unique testant plusieurs valeurs inférieures à 2, qui est le nombre premier le plus petit :

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Exécutez `dotnet test`, et deux de ces tests échouent. Pour que tous les tests réussissent, modifiez la clause `if` au début de la méthode :

```csharp
if (candidate < 2)
```

Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale. Vous parviendrez à la [version finale des tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et à l’[implémentation complète de la bibliothèque](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).

Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque. Vous avez structuré la solution afin de faciliter l’ajout de nouveaux packages et tests, et vous pouvez concentrer vos efforts sur les objectifs de l’application.

