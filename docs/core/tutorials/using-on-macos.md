---
title: "Bien démarrer avec .NET Core sur macOS"
description: "Bien démarrer avec .NET Core sur macOS à l’aide du code Visual Studio"
keywords: .NET, .NET Core
author: bleroy
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
translationtype: Human Translation
ms.sourcegitcommit: 2339be6aef7e2ff942f1f1999a12f48ee4a77ee8
ms.openlocfilehash: 12b7bed380db53aad04f0615c6efa6152b3035b7

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-code"></a>Bien démarrer avec .NET Core sur macOS à l’aide du code Visual Studio

par [Bertrand Le Roy](https://github.com/bleroy), [Phillip Carter](https://github.com/cartermp), [Bill Wagner](https://github.com/billwagner)

Contributions de [Marco Solarin-Sodara](https://github.com/tsolarin)

Ce document présente les étapes et les flux de travail permettant de créer une solution .NET Core à l’aide de [Visual Studio Code](http://code.visualstudio.com).
Vous allez apprendre à créer des projets, à créer des tests unitaires, à utiliser les outils de débogage et à incorporer des bibliothèques tierces à l’aide de [NuGet](http://nuget.org).

Cet article utilise Visual Studio Code sur Mac OS. En cas de divergence, il signale les différences correspondant à la plateforme Windows.

## <a name="prerequisites"></a>Prérequis

Avant de commencer, vous devez installer le [SDK .NET Core](https://www.microsoft.com/net/core), actuellement en préversion. Ce SDK .NET Core inclut la dernière version du framework et du runtime .NET Core.

Vous devez également installer [Visual Studio Code](http://code.visualstudio.com).
Au cours de cet article, vous allez également installer des extensions permettant d’améliorer l’expérience de développement de .NET Core.

Des liens vers tous ces éléments sont disponibles dans la [page d’accueil .NET](http://dot.net).

## <a name="getting-started"></a>Commencer

La source de ce didacticiel est disponible sur [GitHub](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden).

Démarrez Visual Studio Code. Appuyez sur Ctrl+' \` ' (caractère guillemet inversé) pour ouvrir un terminal incorporé dans VS Code. (Vous pouvez également utiliser une fenêtre de terminal distincte, si vous le souhaitez).

Quand nous aurons terminé, vous aurez créé trois projets : un projet de bibliothèque, des tests pour ce projet de bibliothèque et une application console qui utilise la bibliothèque. Vous allez suivre une structure de dossier standard pour les trois projets. L’application de cette structure de dossier standard signifie que les outils du SDK .NET Core comprennent la relation entre vos projets de code de production et vos projets de code de test. Cela améliore votre expérience de développement.

Commençons par créer ces dossiers. Dans le terminal, créez un répertoire 'golden'. Sous ce répertoire, créez les répertoires `src` et `test`. Sous `src`, créez les répertoires `app` et `library`. Dans `test`, créez un répertoire `test-library`. Vous pouvez effectuer ces opérations à l’aide du terminal dans VS Code, ou en cliquant sur le dossier parent dans VS Code puis en sélectionnant l’icône « Nouveau dossier ».

Dans VS Code, ouvrez le répertoire 'golden'. Ce répertoire est la racine de votre solution.

Ensuite, créez un fichier `global.json` dans le répertoire racine de votre solution.
Le contenu de `global.json` est le suivant :

```json
{
    "projects": [
        "src",
        "test"
    ]
}
```

À ce stade, votre arborescence de répertoires doit ressembler à ceci :


```
/golden
|__global.json
|__/src
   |__/app
   |__/library
|__/test
   |__/test-library
```

### <a name="writing-the-library"></a>Écriture de la bibliothèque

La tâche suivante consiste à créer la bibliothèque. Dans la fenêtre du terminal (le terminal incorporé dans VS Code ou un autre terminal), accédez au répertoire `golden/src/library`, puis tapez la commande `dotnet new -t lib`.
Cette opération crée un projet de bibliothèque comportant deux fichiers : `project.json` et `Library.cs`.

`project.json` contient les informations suivantes :

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {},
  "frameworks": {
    "netstandard1.6": {
      "dependencies": {
        "NETStandard.Library": "1.6.0"
      }
    }
  }
}
```


Ce projet de bibliothèque utilise la représentation JSON des objets. Vous allez donc devoir ajouter une référence au package NuGet `Newtonsoft.Json`. Dans `project.json`, ajoutez la dernière préversion du package comme dépendance :

```json
"dependencies": {
    "Newtonsoft.Json": "9.0.1-beta1"
},
```

Une fois l’ajout de ces dépendances terminé, vous devez installer ces packages dans l’espace de travail. Exécutez la commande `dotnet restore` pour mettre à jour toutes les dépendances, puis écrivez un fichier `project.lock.json` dans le répertoire du projet. Ce fichier contient l’arborescence complète de toutes les dépendances dans votre projet. Vous n’avez pas besoin de lire ce fichier. Il est utilisé par les outils du SDK .NET Core.

À présent, mettons à jour le code C#. Créons une classe `Thing` contenant une méthode publique. Cette méthode retourne la somme de deux nombres, mais elle effectue cette opération en convertissant ce nombre en chaîne JSON, puis en la désérialisant. Renommer le fichier `Library.cs` en `Thing.cs`. Ensuite, remplacez le code existant (pour la Class1 générée à partir d’un modèle) par ce qui suit :

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

Ce code utilise un certain nombre de fonctionnalités C# modernes, telles que les instructions Using statiques, des membres expression-bodied et des chaînes interpolées, que vous pouvez découvrir dans la section [Découvrir C#](../../csharp/index.md).

Maintenant que vous avez mis à jour le code, vous pouvez créer la bibliothèque à l’aide de `dotnet build`.

Vous avez maintenant un fichier `library.dll` sous `golden/src/library/bin/Debug/netstandard1.6`.

### <a name="writing-the-test-project"></a>Écriture du projet de test

Créons un projet de test pour cette bibliothèque que vous avez générée. Accédez au répertoire `test/test-library`. Exécutez `dotnet new -t xunittest` pour créer un projet de test unitaire. 

Vous devez ajouter un nœud de dépendance pour la bibliothèque que vous avez écrite dans la procédure ci-dessus. Ouvrez `project.json`, puis mettez à jour la section 'dependencies' avec le code suivant (dont le nœud `library`, qui est le dernier nœud ci-dessous) :

```json
"dependencies": {
  "System.Runtime.Serialization.Primitives": "4.1.1",
  "xunit": "2.1.0",
  "dotnet-test-xunit": "1.0.0-rc2-192208-24",
  "library": {
    "target": "project"
  }
}
```

Le nœud `library` spécifie que cette dépendance doit être résolue en un projet dans l’espace de travail actuel. Si cela n’est pas spécifié explicitement, le projet de test risque de reposer sur un package NuGet du même nom.

Maintenant que les dépendances ont été correctement configurées, nous allons créer les tests pour votre bibliothèque. Ouvrez `Tests.cs`, puis remplacez son contenu par le code suivant :

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.Equal(42, new Thing().Get(19, 23));
        }
    }
}
```

À présent, exécutez `dotnet restore`, `dotnet build` et `dotnet test`.
L’exécuteur de tests de la console xUnit exécute le seul test, puis indique s’il a réussi. 

### <a name="writing-the-console-app"></a>Écriture de l’application console

Dans votre terminal, accédez au répertoire `golden/src/app`. Exécutez `dotnet new` pour créer une application console.

Votre application console dépend de la bibliothèque que vous avez créée et testée lors des étapes précédentes. Vous devez l’indiquer en modifiant `project.json` pour ajouter cette dépendance.  Dans le nœud `dependencies`, ajoutez le nœud `library` comme suit :

```json
"dependencies": {
  "library": {
    "target": "project"
  }
}
```

Le nœud `project` est important ici, car il figurait dans la bibliothèque de tests. Il indique qu’il s’agit d’un projet dans la solution actuelle, et non d’un package NuGet.

Exécutez `dotnet restore` pour restaurer toutes les dépendances. Ouvrez `program.cs`, puis remplacez le contenu de la méthode `Main` par la ligne suivante :

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Vous devez ajouter deux directives `using` en haut du fichier :

```csharp
using static System.Console;
using Library;
```

Ensuite, exécutez `dotnet build`. Cette opération crée les assemblys. Vous pouvez taper `dotnet run` pour exécuter l’exécutable.

### <a name="debugging-your-application"></a>Débogage de votre application

Vous pouvez déboguer votre code dans VS Code à l’aide de l’extension C#.
Pour installer cette extension, appuyez sur `F1` afin d’ouvrir la palette VS Code. Tapez `ext install` pour afficher la liste des extensions. Sélectionnez l’extension C#. (Des informations plus détaillées sont disponibles dans la page de [documentation relative à l’extension C# Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).)

Quand vous avez terminé d’installer l’extension, VS Code vous demande de redémarrer l’application pour charger la nouvelle extension. Une fois l’extension installée, vous pouvez ouvrir l’onglet du débogueur (voir la figure).

![Débogueur VS Code](./media/using-on-macos/vscodedebugger.png)


Quand vous démarrez le débogueur, VS Code vous demande de le configurer. Il crée alors un répertoire `.vscode` comportant deux fichiers : `tasks.json` et `launch.json`. Ces deux fichiers contrôlent la configuration du débogueur. Dans la plupart des projets, ce répertoire n’est pas inclus dans le contrôle de code source.
Il est inclus dans l’exemple associé à cette procédure pas à pas pour vous permettre de voir les modifications à apporter.

Votre solution contient plusieurs projets. Vous devrez donc modifier chacun de ces fichiers pour exécuter les commandes appropriées. Tout d’abord, ouvrez `tasks.json`. La tâche de génération par défaut exécute `dotnet build` dans le répertoire source de l’espace de travail. Au lieu de cela, vous voulez l’exécuter dans le répertoire `src/app`. Vous devez ajouter un nœud `options` pour définir comme répertoire de travail actif le suivant :

```json
"options": {
    "cwd": "${workspaceRoot}/src/app"
}
```

Ensuite, vous devez ouvrir `launch.json` et mettre à jour le chemin du programme. Un nœud décrivant le programme s’affiche sous « configurations ». Vous devez voir ceci :

```json
"program": "${workspaceRoot}/bin/Debug/<target-framework>/<project-name.dll>",
```

Vous devez le remplacer par ceci :

```json
"program": "${workspaceRoot}/src/app/bin/Debug/netcoreapp1.0/app.dll",
```

Si vous exécutez Windows, vous devez mettre à jour le fichier `project.json` de l’application (dans le répertoire `src/app`) pour générer des fichiers PDB portables (cette opération s’effectue par défaut sur Mac OSX et Linux).
Ajoutez le nœud `debugType` dans `buildOptions`. Vous devez ajouter le nœud `debugType` dans `project.json` pour les deux dossiers `src/app` et `src/library`.

```json
  "buildOptions": {
    "debugType": "portable"
  },
```

Définissez un point d’arrêt au niveau de l’instruction `WriteLine``Main`. Pour cela, appuyez sur la touche `F9` ou cliquez dans la marge gauche de la ligne sur laquelle vous voulez placer le point d’arrêt. Ouvrez le débogueur en appuyant sur l’icône de débogage à gauche dans l’écran VS Code (voir la figure). Appuyez ensuite sur le bouton de lecture pour démarrer l’application sous le débogueur.

Vous devez atteindre le point d’arrêt. Exécutez pas à pas la méthode `Get`, puis vérifiez que vous avez passé les arguments appropriés. Vérifiez que la réponse est bien 42.



<!--HONumber=Nov16_HO1-->


