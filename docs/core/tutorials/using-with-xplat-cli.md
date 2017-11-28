---
title: "Bien démarrer avec .NET Core à l’aide de l’interface CLI"
description: "Didacticiel pas à pas montrant comment démarrer avec .NET Core sur Windows, Linux ou Mac OS à l’aide de l’interface de ligne de commande (CLI) .NET Core."
keywords: ".NET Core, CLI"
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 41632e63-d5c6-4427-a09e-51dc1116d45f
ms.openlocfilehash: 19622cca1dd28d4d2248d69f1b4081c352a0c4f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Bien démarrer avec .NET Core sur Windows/Linux/macOS à l’aide de la ligne de commande

Cette rubrique décrit comment commencer à développer des applications multiplateformes sur votre ordinateur à l’aide des outils CLI .NET Core.

Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/index.md).

## <a name="prerequisites"></a>Prérequis

- [.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).
- Un éditeur de texte ou un éditeur de code de votre choix.

## <a name="hello-console-app"></a>Application console Hello

Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild) à partir du dépôt GitHub dotnet/docs. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Ouvrez une invite de commandes et créez un dossier nommé *Hello*. Accédez au dossier créé et tapez ce qui suit :

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

Suivons une procédure pas à pas rapide :

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) crée un fichier projet `Hello.csproj` à jour avec les dépendances nécessaires pour générer une application console.  Il crée également `Program.cs`, un fichier de base contenant le point d’entrée pour l’application.
   
   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.

   * La balise `OutputType` spécifie que nous générons un fichier exécutable, autrement dit une application console.
   * La balise `TargetFramework` spécifie l’implémentation .NET que nous ciblons. Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération. Dans ce didacticiel, nous nous en tiendrons à une génération limitée à .NET Core 1.0.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ». L’espace de noms `System` inclut des constructions de base, telles que `string`, ou des types numériques.

   Ensuite, nous définissons un espace de noms appelé `Hello`. Vous pouvez le modifier à votre gré. Une classe nommée `Program` est définie dans cet espace de noms avec une méthode `Main` qui accepte un tableau de chaînes comme argument. Ce tableau contient la liste des arguments passés quand le programme compilé est appelé. Tel quel, ce tableau n’est pas utilisé : le programme se limite à écrire « Hello World! » dans la console. Plus tard, nous apporterons des modifications au code qui utilisent cet argument.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) appelle [NuGet](https://www.nuget.org/) (gestionnaire de package .NET) pour restaurer l’arborescence de dépendances. NuGet analyse le fichier *Hello.csproj*, télécharge les dépendances indiquées dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier *obj/project.assets.json*.  Le fichier *project.assets.json* est nécessaire pour pouvoir effectuer la compilation et l’exécution.
   
   Le fichier *project.assets.json* est un ensemble persistant et complet du graphique de dépendances NuGet et d’autres informations qui décrivent une application.  Ce fichier est lu par d’autres outils, comme [`dotnet build`](../tools/dotnet-build.md) et [`dotnet run`](../tools/dotnet-run.md), ce qui leur permet de traiter le code source avec un ensemble approprié de dépendances NuGet et de résolutions de liaison.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) appelle [`dotnet build`](../tools/dotnet-build.md) pour garantir que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.
   
    ```
    $ dotnet run
    Hello World!
    ```

    Si vous préférez, vous pouvez exécuter [`dotnet build`](../tools/dotnet-build.md) pour compiler le code sans exécuter les applications console de la build. Il en résulte une application compilée sous forme de fichier DLL qui peut être exécutée avec `dotnet bin\Debug\netcoreapp1.0\Hello.dll` sur Windows (utilisez `/` sur les autres systèmes). Vous pouvez également spécifier des arguments pour l’application, comme nous le verrons par la suite dans la rubrique.

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    Dans le cadre d’un scénario avancé, vous pouvez générer l’application comme un ensemble autonome de fichiers spécifiques à la plateforme qui peuvent être déployés et exécutés sur un ordinateur sur lequel .NET Core n’est pas nécessairement installé. Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

### <a name="augmenting-the-program"></a>Augmentation du programme

Modifions un peu le programme. Les nombres de Fibonacci sont amusants, nous allons donc les ajouter en plus de l’argument pour accueillir la personne qui exécute l’application.

1. Remplacez le contenu du fichier *Program.cs* par le code suivant :

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. Exécutez [`dotnet build`](../tools/dotnet-build.md) pour compiler les modifications.

3. Exécutez le programme en passant un paramètre à l’application :

   ```
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

Et voilà !  Vous pouvez augmenter `Program.cs` comme vous le souhaitez.

## <a name="working-with-multiple-files"></a>Utilisation de plusieurs fichiers

Les fichiers uniques conviennent à des programmes simples et ponctuels, mais si vous créez une application plus complexe, vous avez probablement plusieurs fichiers sources dans votre projet. Reprenons l’exemple précédent de Fibonacci en mettant en cache certaines valeurs de Fibonacci et en ajoutant des fonctionnalités récursives. 

1. Ajoutez un nouveau fichier nommé *FibonacciGenerator.cs* dans le répertoire *Hello* avec le code suivant :

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. Modifiez la méthode `Main` dans votre fichier *Program.cs* pour instancier la nouvelle classe et appelez sa méthode comme dans l’exemple suivant :

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Exécutez [`dotnet build`](../tools/dotnet-build.md) pour compiler les modifications.

4. Exécutez votre application en exécutant [`dotnet run`](../tools/dotnet-run.md). Voici la sortie du programme :

   ```
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

Et voilà ! À présent, vous pouvez commencer à utiliser les concepts de base que vous avez appris ici pour créer vos propres programmes.

Notez que les commandes et les étapes indiquées dans ce didacticiel pour exécuter votre application sont utilisées uniquement au moment du développement. Une fois que vous êtes prêt à déployer votre application, consultez les différentes [stratégies de déploiement](../deploying/index.md) pour les applications .NET Core et la commande [`dotnet publish`](../tools/dotnet-publish.md).

## <a name="see-also"></a>Voir aussi

[Organisation et test de projets avec les outils CLI .NET Core](testing-with-cli.md)
