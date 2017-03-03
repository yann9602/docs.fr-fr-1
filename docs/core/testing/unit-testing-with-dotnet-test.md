---
title: "Effectuer des tests unitaires dans .NET Core à l’aide de dotnet test"
description: "Effectuer des tests unitaires dans .NET Core à l’aide de dotnet test"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdcdb812-6f13-4f20-9e90-0c0977937142
translationtype: Human Translation
ms.sourcegitcommit: 5687fc7ded899a478d1972ffea10a1e37d40124b
ms.openlocfilehash: f1f08f550d7484869e67fe705dc789ca5dae8e2f
ms.lasthandoff: 01/18/2017

---

# <a name="unit-testing-in-net-core-using-dotnet-test"></a>Effectuer des tests unitaires dans .NET Core à l’aide de dotnet test

Article rédigé par [Steve Smith](http://ardalis.com) et [Bill Wagner](https://github.com/BillWagner)

[Afficher ou télécharger l’exemple de code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test)

> [!NOTE]
> Cette rubrique s'applique à .NET Core 1.0.

## <a name="creating-the-projects"></a>Création des projets

L’article relatif à l’[écriture de bibliothèques avec des outils multiplateformes](../tutorials/libraries.md) donne des indications sur l’organisation de solutions multiprojets pour la source et les tests. Cet article suit ces conventions. La structure de projet finale se présentera comme suit :

```
/unit-testing-using-dotnet-test
|__global.json
|__/src
   |__/PrimeService
      |__Source Files
      |__project.json
|__/test
   |__/PrimeService.Tests
      |__Test Files
      |__project.json
```

Dans le répertoire racine, vous devez créer un fichier `global.json` qui contienne le nom de vos répertoires `src` et `test` :

```json
{
    "projects": [
        "src",
        "test"
    ]
}
```

### <a name="creating-the-source-project"></a>Création du projet source

Ensuite, dans le répertoire `src`, créez le répertoire `PrimeService`.
À l’aide de la commande CD, accédez à ce répertoire, puis exécutez `dotnet new -t lib` pour créer le projet source.


Renommez `Library.cs` `PrimeService.cs`. Pour utiliser le développement piloté par les tests (TDD), vous devez créer une implémentation défaillante de la classe `PrimeService` :

```cs
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

Ensuite, à l’aide de la commande CD, accédez au répertoire « test », puis créez le répertoire `PrimeServices.Tests`.
Toujours à l’aide de la commande CD, accédez au répertoire `PrimeServices.Tests`, puis créez un projet à l’aide de `dotnet new -t xunittest`. `dotnet new -t xunittest` crée un projet de test qui utilise xunit comme bibliothèque de test. 

Le modèle généré a configuré Test Runner à la racine de `project.json` :

```json
{
  "version": "1.0.0-*",
  "testRunner": "xunit",
  // ...
}
```

Le modèle définit aussi le nœud frameworks pour utiliser `netcoreapp1.0` et comprend les importations nécessaires pour permettre à xUnit.net de fonctionner avec la version finale de .NET Core :

```json
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dotnet54",
        "portable-net45+win8" 
      ]
    }
  }
```

Le projet de test a besoin d’autres packages pour créer et exécuter des tests unitaires.
`dotnet new` a ajouté xunit et le runner xunit. Vous devez ajouter au projet le package PrimeService comme autre dépendance :

```json
"dependencies": {
  "xunit":"2.1.0",
  "dotnet-test-xunit": "1.0.0-rc2-192208-24",
  "PrimeService": {
    "target": "project"
  }
}
```

Notez que le projet `PrimeService` ne contient pas d’informations de chemin de répertoire. Comme vous avez créé la structure de projet en fonction de l’organisation attendue de `src` et `test`, et que le fichier `global.json` indique cela, le système de build trouve l’emplacement correct du projet. Vous ajoutez l’élément `"target": "project"` pour informer NuGet qu’il doit regarder dans les répertoires du projet, et non dans le flux NuGet. Sans cette clé, vous risquez de télécharger un package ayant le même nom que votre bibliothèque interne.

Vous pouvez consulter le fichier dans son intégralité dans le [dépôt d’exemples](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/project.json) sur GitHub.

Vous pouvez écrire votre premier test dès lors que cette structure initiale est en place.
Une fois que vous avez vérifié ce premier test unitaire, tout est configuré et doit s’exécuter correctement à mesure que vous ajoutez des fonctionnalités et des tests.

## <a name="creating-the-first-test"></a>Création du premier test

L’approche TDD impose d’écrire un test défaillant, de le corriger pour qu’il réussisse, puis de répéter le processus. Par conséquent, écrivons ce test défaillant. Supprimez `program.cs` du répertoire `PrimeService.Tests`, puis créez un fichier C# avec le contenu suivant :

```cs
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

L’attribut `[Fact]` désigne une méthode en tant que test unique. 

Enregistrez ce fichier, puis exécutez `dotnet build` pour générer le projet de test.
Si vous n’avez pas déjà généré le projet `PrimeService`, le système de génération le détecte et le génère, car il s’agit d’une dépendance du projet de test.

À présent, exécutez `dotnet test` pour exécuter les tests à partir de la console.
Le Test Runner xunit dispose du point d’entrée de programme pour exécuter vos tests à partir de la console. `dotnet test` démarre Test Runner et lui transmet un argument de ligne de commande désignant l’assembly qui contient vos tests.

Votre test échoue. Vous n’avez pas encore créé l’implémentation.
Écrivez le code le plus simple pour faire en sorte que ce test réussisse :

```cs
public bool IsPrime(int candidate) 
{
    if(candidate == 1) 
    { 
        return false;
    } 
    throw new NotImplementedException("Please create a test first");
} 
```

### <a name="adding-more-features"></a>Ajout de fonctionnalités supplémentaires

Maintenant que vous avez fait réussir un test, le moment est venu d’écrire plus de code.
Il existe quelques autres cas simples pour des nombres premiers : 0, -1. Vous pouvez les ajouter en tant que nouveaux tests, avec l’attribut `[Fact]`, mais cela devient vite fastidieux. D’autres attributs xunit vous permettent d’écrire une suite de tests similaires.  L’attribut `Theory` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.
Vous pouvez utiliser l’attribut `[InlineData]` pour spécifier des valeurs pour ces entrées. 
 
 Au lieu de créer de nouveaux tests, servez-vous de ces deux attributs pour créer une théorie unique qui teste des valeurs inférieures à 2, qui est le nombre premier le plus petit :

```cs
[Theory]
[InlineData(-1)]
[InlineData(0)]
[InlineData(1)]
public void ReturnFalseGivenValuesLessThan2(int value)
{
    var result = _primeService.IsPrime(value);

    Assert.False(result, $"{value} should not be prime");
}
```

Si vous exécutez `dotnet test`, vous constaterez que deux de ces tests échouent.
Vous pouvez les faire réussir en changeant de service. Vous devez modifier la clause `if` au début de la méthode :

```cs
if(candidate < 2)
```

À présent, ces tests réussissent tous.

Poursuivez l’itération en ajoutant plus de tests, plus de théories et plus de code dans la bibliothèque principale. Vous parviendrez rapidement à la [version finale des tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/PrimeServie_IsPrimeShould.cs) et à l’[implémentation complète de la bibliothèque](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/src/PrimeService/PrimeService.cs).

Vous avez créé une petite bibliothèque et un ensemble de tests unitaires pour cette bibliothèque.
Vous avez structuré cette solution de façon à simplifier l’ajout de nouveaux packages et tests, et vous pouvez vous concentrer sur le problème en cours. Les outils s’exécuteront automatiquement.
   
   > [!TIP]
   > Sur la plateforme Windows, vous pouvez utiliser MSTest. Pour en savoir plus, consultez le document sur l’[utilisation de MSTest sur Windows](./using-mstest-on-windows.md).

