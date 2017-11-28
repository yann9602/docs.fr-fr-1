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
ms.openlocfilehash: 62c81bf070a435f6105c313ae95340a5504233df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Organiser et tester des projets avec la ligne de commande .NET Core

Ce didacticiel, qui fait suite à la rubrique [Bien démarrer avec .NET Core sur Windows/Linux/macOS à l’aide de la ligne de commande](using-with-xplat-cli.md), montre comment aller au-delà de la création d’une application console simple pour développer des applications avancées et bien organisées. Après une présentation des dossiers disponibles pour organiser votre code, ce didacticiel vous montre comment étendre une application console avec le framework de tests [xUnit](https://xunit.github.io/).

## <a name="using-folders-to-organize-code"></a>Utilisation de dossiers pour organiser le code

Si vous souhaitez introduire de nouveaux types dans une application console, ajoutez des fichiers contenant les types à l’application. Par exemple, si vous ajoutez des fichiers contenant les types `AccountInformation` et `MonthlyReportRecords` à votre projet, la structure du fichier projet est plate et facile à parcourir :

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Toutefois, cela ne fonctionne bien que si la taille de votre projet est relativement petite. Imaginez ce qui se passerait si vous ajoutiez 20 types au projet : avec autant de fichiers alourdissant le répertoire racine du projet, la navigation et la maintenance seraient particulièrement difficiles.

Pour organiser le projet, créez un dossier et nommez-le *Models* pour stocker les fichiers de types. Placez les fichiers de types dans le dossier *Models* :

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Les projets qui regroupent logiquement les fichiers dans des dossiers simplifient la navigation et la gestion. Dans la section suivante, vous allez créer un exemple plus complexe avec des dossiers et des tests unitaires.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Organisation et test du code à l’aide de l’exemple NewTypes Pets

### <a name="building-the-sample"></a>Génération de l’exemple

Pour les étapes suivantes, vous pouvez soit suivre [l’exemple NewTypes Pets](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild), soit créer vos propres fichiers et dossiers. Les types et les tests sont logiquement organisés dans une structure de dossiers qui autorise l’ajout d’autres types et tests par la suite.

L’exemple contient deux types, `Dog` et `Cat`, qui implémentent une interface commune `IPet`. Pour le projet `NewTypes`, votre objectif est d’organiser les types liés aux animaux domestiques dans un dossier *Pets*. Si un autre jeu de types est ajouté par la suite, *WildAnimals* par exemple, il est placé dans le dossier *NewTypes* aux côtés du dossier *Pets*. Le dossier *WildAnimals* peut contenir des types pour des animaux non domestiques, par exemple `Squirrel` et `Rabbit`. De cette façon, à mesure que vous ajoutez des types, le projet reste bien organisé. 

Créez la structure de dossiers suivante avec le contenu de fichier indiqué :

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

*IPet.cs* :

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

*Dog.cs* :

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

*Cat.cs* :

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

*Program.cs* :

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj* :

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

Exécutez les commandes suivantes :

```console
dotnet run
```

Observez la sortie suivante :

```console
Woof!
Meow!
```

Exercice facultatif : Vous pouvez ajouter un nouveau type d’animal domestique, par exemple `Bird`, en étendant ce projet. Faites en sorte que la méthode `TalkToOwner` du type Bird envoie un `Tweet!` au propriétaire. Réexécutez l’application. La sortie inclut `Tweet!`

### <a name="testing-the-sample"></a>Test de l’exemple

Le projet `NewTypes` est en place et vous l’avez organisé en conservant les types liés aux animaux domestiques dans un dossier. Créez à présent votre projet de test et commencez à écrire des tests à l’aide du framework de tests [xUnit](https://xunit.github.io/). Les tests unitaires vous permettent de vérifier automatiquement le comportement de vos types d’animaux domestiques et de confirmer qu’ils fonctionnent correctement.

Créez un dossier*test* et un sous-dossier *NewTypesTests*. À une invite de commandes à partir du dossier *NewTypesTests*, exécutez `dotnet new xunit`. Deux fichiers sont générés : *NewTypesTests.csproj* et *UnitTest1.cs*.

Le projet de test ne peut pas actuellement tester les types dans `NewTypes` et nécessite une référence de projet au projet `NewTypes`. Pour ajouter une référence de projet, utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Vous pouvez également ajouter manuellement la référence de projet en ajoutant un nœud `<ItemGroup>` au fichier *NewTypesTests.csproj* :

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj* :

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

Le fichier *NewTypesTests.csproj* contient les éléments suivants :

* Référence de package à `Microsoft.NET.Test.Sdk` (infrastructure de tests .NET)
* Référence de package à `xunit` (framework de tests xUnit)
* Référence de package à `xunit.runner.visualstudio` (Test Runner)
* Référence de projet à `NewTypes` (code à tester)

Renommez *UnitTest1.cs* en *PetTests.cs* et remplacez le code dans le fichier par le suivant :

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

Exercice facultatif : Si vous avez précédemment ajouté un type `Bird` qui envoie un `Tweet!` au propriétaire, ajoutez une méthode de test au fichier *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, pour vérifier que la méthode `TalkToOwner` fonctionne correctement pour le type `Bird`.

> [!NOTE]
> Bien que l’on s’attende à ce que les valeurs `expected` et `actual` soient identiques, les assertions initiales avec les vérifications `Assert.NotEqual` spécifient qu’elles *ne sont pas égales*. Commencez toujours par créer vos tests en les faisant échouer une fois pour vérifier leur logique. Il s’agit d’une étape importante de la méthodologie de conception conduite par les tests. Après avoir confirmé l’échec des tests, ajustez les assertions pour leur permettre de réussir.

Le code suivant montre la structure complète du projet :

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

Démarrez dans le répertoire *test/NewTypesTests*. Restaurez le projet de test avec la commande [`dotnet restore`](../tools/dotnet-restore.md). Exécutez les tests avec la commande [`dotnet test`](../tools/dotnet-test.md). Cette commande démarre le Test Runner spécifié dans le fichier projet.

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
Comme prévu, les tests échouent et la console affiche la sortie suivante :
 
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

Remplacez les assertions de vos tests `Assert.NotEqual` par `Assert.Equal` :

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

Réexécutez les tests avec la commande `dotnet test` et observez la sortie suivante :

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

Les tests réussissent. Les méthodes des types d’animaux domestiques retournent des valeurs correctes quand elles communiquent avec le propriétaire.

Vous avez appris les techniques permettant d’organiser et de tester des projets à l’aide de xUnit. Vous pouvez maintenant les mettre en pratique dans vos propres projets. *Bon développement !*

