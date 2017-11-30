---
title: "Bien démarrer avec .NET Core sur macOS"
description: "Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core à l’aide de Visual Studio Code."
keywords: .NET, .NET Core, Mac, macOS, Visual Studio Code
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
ms.openlocfilehash: b172e5fc4fcf9dd5c1e6f268f3c046e77592ebd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-macos"></a>Bien démarrer avec .NET Core sur macOS

Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core pour macOS. Découvrez comment créer des projets et des tests unitaires, utiliser les outils de débogage et incorporer des bibliothèques tierces à l’aide de [NuGet](https://www.nuget.org/).

> [!NOTE]
> Cet article utilise [Visual Studio Code](http://code.visualstudio.com) sur macOS.

## <a name="prerequisites"></a>Prérequis

Installez le [SDK .NET Core](https://www.microsoft.com/net/core). Ce SDK .NET Core inclut la dernière version du framework et du runtime .NET Core.

Installez [Visual Studio Code](http://code.visualstudio.com). Au cours de cet article, vous allez également installer des extensions Visual Studio Code pour améliorer l’expérience de développement de .NET Core.

Installez l’extension C# de Visual Studio Code en ouvrant Visual Studio Code et en appuyant sur <kbd>F1</kbd> pour ouvrir la palette Visual Studio Code. Tapez **ext install** pour afficher la liste des extensions. Sélectionnez l’extension C#. Redémarrez Visual Studio Code pour activer l’extension. Pour plus d’informations, consultez la [documentation sur l’extension C# pour Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="getting-started"></a>Bien démarrer

Dans ce didacticiel, vous créez trois projets : un projet de bibliothèque, des tests pour ce projet de bibliothèque et une application console qui utilise la bibliothèque. Vous pouvez [afficher ou télécharger la source](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) pour cette rubrique dans le dépôt dotnet/docs sur GitHub. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Démarrez Visual Studio Code. Appuyez sur <kbd>Ctrl</kbd>+<kbd>\`</kbd> (accent grave) ou sélectionnez **Affichage > Terminal intégré** dans le menu pour ouvrir un terminal incorporé dans Visual Studio Code. Vous pouvez également ouvrir un interpréteur de commandes externe à l’aide de la commande **Ouvrir dans l’invite de commandes** de l’Explorateur (**Ouvrir dans Terminal** sur Mac ou Linux) si vous préférez travailler en dehors de Visual Studio Code.

Commencez par créer un fichier de solution qui servira de conteneur pour un ou plusieurs projets .NET Core. Dans le terminal, créez un dossier *golden* et ouvrez le dossier. Ce dossier est la racine de votre solution. Exécutez la commande [`dotnet new`](../tools/dotnet-new.md) pour créer une solution, *golden.sln* :

```console
dotnet new sln
```

À partir du dossier *golden*, exécutez la commande suivante pour créer un projet de bibliothèque qui génère deux fichiers,*library.csproj* et *Class1.cs*, dans le dossier *library* :

```console
dotnet new classlib -o library
```

Exécutez la commande [`dotnet sln`](../tools/dotnet-sln.md) pour ajouter le projet *library.csproj* que vous venez de créer à la solution :

```console
dotnet sln add library/library.csproj
```

Le fichier *library.csproj* contient les informations suivantes :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

Les méthodes de la bibliothèque sérialisent et désérialisent les objets au format JSON. Pour prendre en charge la sérialisation et la désérialisation JSON, ajoutez une référence au package NuGet `Newtonsoft.Json`. La commande `dotnet add` ajoute de nouveaux éléments à un projet. Pour ajouter une référence à un package NuGet, utilisez la commande [`dotnet add package`](../tools/dotnet-add-package.md) et spécifiez le nom du package :

```console
dotnet add library package Newtonsoft.Json
```

Cette opération ajoute `Newtonsoft.Json` et ses dépendances au projet de bibliothèque. Vous pouvez aussi modifier manuellement le fichier *library.csproj* et ajouter le nœud suivant :

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

Exécuter [ `dotnet restore` ](../tools/dotnet-restore.md), ([voir la Remarque](#dotnet-restore-note)) qui restaure les dépendances et crée un *obj* dossier *bibliothèque* avec trois fichiers, y compris un *project.assets.json* fichier :

```console
dotnet restore
```

Dans le dossier *library*, renommez le fichier *Class1.cs* en *Thing.cs*. Remplacez le code par ce qui suit :

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

La classe `Thing` contient une méthode publique, `Get`, qui retourne la somme de deux nombres. Pour cela, elle convertit la somme en chaîne, puis la désérialise en entier. Ce code utilise un certain nombre de fonctionnalités C# modernes, telles que des [`using static`directives](../../csharp/language-reference/keywords/using-static.md), des [membres expression-bodied](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members) et des [chaînes interpolées](../../csharp/language-reference/keywords/interpolated-strings.md).

Générez la bibliothèque à l’aide de la commande [ `dotnet build` ](../tools/dotnet-build.md). Un fichier *library.dll* est généré sous *golden/library/bin/Debug/netstandard1.4* :

```console
dotnet build
```

## <a name="create-the-test-project"></a>Créer le projet de test

Créez un projet de test pour la bibliothèque. À partir du dossier *golden*, créez un projet de test :

```console
dotnet new xunit -o test-library
```

Ajoutez le projet de test à la solution :

```console
dotnet sln add test-library/test-library.csproj
```

Ajoutez une référence de projet à la bibliothèque créée à la section précédente pour que le compilateur puisse trouver et utiliser le projet de bibliothèque. Utilisez la commande [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Vous pouvez aussi modifier manuellement le fichier *test-library.csproj* et ajouter le nœud suivant :

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Maintenant que les dépendances ont été correctement configurées, créez les tests pour votre bibliothèque. Ouvrez *UnitTest1.cs* et remplacez son contenu par le code suivant :

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Le fait de déclarer la valeur 42 n’est pas égal à 19+23 (ou 42) quand vous créez initialement le test unitaire (`Assert.NotEqual`), qui échoue. Lors de la création d’un test unitaire, une étape importante consiste à le faire échouer une fois pour confirmer sa logique.

À partir du dossier *golden*, exécutez les commandes suivantes :

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Ces commandes trouvent de manière récursive tous les projets pour restaurer les dépendances, les générer et activer le Test Runner xUnit pour exécuter les tests. Le test unique échoue comme prévu.

Modifiez le fichier *UnitTest1.cs* et remplacez l’assertion `Assert.NotEqual` par `Assert.Equal`. Exécutez la commande suivante à partir du dossier *golden* pour réexécuter le test, qui réussit cette fois-ci :

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Créer l’application console

L’application console que vous allez créer dans les étapes suivantes est dépendante du projet de bibliothèque créé précédemment et appelle sa méthode de bibliothèque durant l’exécution. Ce modèle de développement vous permet de voir comment créer des bibliothèques réutilisables pour plusieurs projets.

Créez une application console à partir du dossier *golden* :

```console
dotnet new console -o app
```

Ajoutez le projet d’application console à la solution :

```console
dotnet sln add app/app.csproj
```

Créez la dépendance à la bibliothèque en exécutant la commande `dotnet add reference` :

```console
dotnet add app/app.csproj reference library/library.csproj
```

Exécutez `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) pour restaurer les dépendances de ces trois projets dans la solution. Ouvrez *program.cs* et remplacez le contenu de la méthode `Main` par la ligne suivante :

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Ajoutez deux directives `using` en haut du fichier *Program.cs* :

```csharp
using static System.Console;
using Library;
```

Lancez la commande suivante `dotnet run` pour exécuter l’exécutable, où l’option `-p` après `dotnet run` spécifie le projet de l’application principale. L’application génère la chaîne « The answer is 42 ».

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Déboguer l’application

Définissez un point d’arrêt au niveau de l’instruction `WriteLine` dans la méthode `Main`. Pour ce faire, appuyez sur la touche <kbd>F9</kbd> quand le curseur se trouve sur la ligne `WriteLine` ou cliquez dans la marge gauche de la ligne où vous souhaitez définir le point d’arrêt. Un cercle rouge apparaît dans la marge à côté de la ligne de code. Quand le point d’arrêt est atteint, l’exécution du code s’arrête *avant* l’exécution de la ligne de point d’arrêt.

Ouvrez l’onglet du débogueur. Pour cela, sélectionnez l’icône de débogage dans la barre d’outils de Visual Studio Code, puis **Affichage > Déboguer** à partir de la barre de menus, ou utilisez le raccourci clavier <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd> :

![Débogueur Visual Studio Code](./media/using-on-macos/vscodedebugger.png)

Appuyez sur le bouton de lecture pour démarrer l’application sous le débogueur. L’application s’exécute jusqu’au point d’arrêt. Exécutez pas à pas la méthode `Get`, puis vérifiez que vous avez passé les arguments appropriés. Vérifiez que la réponse est 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]