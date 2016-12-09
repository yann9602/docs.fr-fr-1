---
title: "Bien démarrer avec .NET Core sur Windows/Linux/macOS à l’aide de la ligne de commande"
description: "Bien démarrer avec .NET Core sur Windows, Linux ou macOS à l’aide de l’interface de ligne de commande (CLI)"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: be988f09-7349-43b0-97fb-3a703d4587ce
translationtype: Human Translation
ms.sourcegitcommit: 37e14d5cdf1593f6a8b1ecee9d9828647b023548
ms.openlocfilehash: 5493ccb77e62d20d5101728ef8ab1744ea697fb8

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Bien démarrer avec .NET Core sur Windows/Linux/macOS à l’aide de la ligne de commande

Ce guide indique comment utiliser les outils d’interface de ligne de commande (CLI) .NET Core pour créer des applications console multiplateformes de base.

Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../sdk.md).

## <a name="prerequisites"></a>Prérequis

Avant de commencer, vérifiez que vous disposez des [outils d’interface de ligne de commande (CLI) .NET Core les plus récents](https://www.microsoft.com/net/core). Vous aurez également besoin d’un éditeur de texte.

## <a name="hello-console-app"></a>Application console Hello

Accédez à un dossier ou créez-en un avec le nom de votre choix. « Hello » est le nom choisi pour l’exemple de code qui se trouve [ici](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/Hello).

Ouvrez une invite de commandes, puis tapez les commandes suivantes :

```
$ dotnet new
$ dotnet restore
$ dotnet run
```

Suivons une procédure pas à pas rapide :

1. `$ dotnet new`

   [`dotnet new`](../tools/dotnet-new.md) crée un fichier `project.json` à jour avec les dépendances NuGet nécessaires pour générer une application console.  Il crée également `Program.cs`, un fichier de base contenant le point d’entrée pour l’application.
   
   `project.json`:
   ```json
   {
        "version": "1.0.0-*",
        "buildOptions": {
            "emitEntryPoint": true
        },
        "dependencies": {
            "Microsoft.NETCore.App": {
                "type": "platform",
                "version": "1.0.0"
            }
        },   
       "frameworks": {
            "netcoreapp1.0": {
                "imports": "dnxcore50"
            }
        }
   }
   ```
   `Program.cs`:
   ```csharp
   using System;

   namespace ConsoleApplication
   {
       public class Program
       {
           public static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) appelle NuGet pour restaurer l’arborescence de dépendances. NuGet analyse le fichier `project.json`, télécharge les dépendances indiquées dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier `project.lock.json`.  Le fichier `project.lock.json` est nécessaire pour pouvoir effectuer la compilation et l’exécution.
   
   Le fichier `project.lock.json` est un ensemble persistant et complet du graphique de dépendances NuGet et d’autres informations qui décrivent une application.  Ce fichier est lu par d’autres outils, tels que `dotnet build` et `dotnet run`, ce qui leur permet de traiter le code source avec un ensemble approprié de dépendances NuGet et de résolutions de liaison.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) appelle `dotnet build` pour garantir que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.
   
```
$ dotnet run
Hello, World!
```

Vous pouvez également exécuter [`dotnet build`](../tools/dotnet-build.md) pour compiler le code sans exécuter les applications console de la build.

### <a name="building-a-self-contained-application"></a>Création d’une application autonome

Essayons de compiler une application autonome plutôt qu’une application portable. Pour en savoir plus sur les différents types d’applications et sur la façon dont ils sont déployés, vous pouvez consultez des informations supplémentaires sur les [types de portabilité dans .NET Core](../deploying/index.md).

Pour indiquer aux outils de générer une application autonome, vous devez apporter certaines modifications à votre fichier `project.json`. Vous pouvez voir ces modifications dans le projet [HelloNative](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloNative) du répertoire d’exemples.

Le premier changement consiste à supprimer l’élément `"type": "platform"` de toutes les dépendances. La seule dépendance de ce projet pour le moment est `"Microsoft.NETCore.App"`. La section `dependencies` doit ressembler à ceci :

```json
"dependencies": {
    "Microsoft.NETCore.App": {
        "version": "1.0.0"
    }
},
```

Ensuite, vous devez ajouter un nœud `runtimes` pour spécifier tous les environnements d’exécution cibles. Par exemple, le nœud `runtimes` suivant indique au système de build de créer des exécutables pour la version 64 bits de Windows 10 et pour la version 64 bits de Mac OS X version 10.11.
Le système de build génère des exécutables natifs pour l’environnement actuel. Si vous exécutez cette procédure sur un ordinateur Windows, vous allez générer un exécutable Windows. Si vous exécutez cette procédure sur un Mac, vous allez générer un exécutable OS X.

```json 
"runtimes": {
  "win10-x64": {},
  "osx.10.11-x64": {}
}
```

Consultez la liste complète des runtimes pris en charge dans le [catalogue des identificateurs de runtime](../rid-catalog.md). 
 
Après avoir apporté ces deux modifications, vous exécutez `dotnet restore`, suivi de `dotnet build` pour créer l’exécutable natif. Vous pouvez ensuite exécuter cet exécutable natif généré. 

L’exemple suivant présente les commandes pour Windows. L’exemple montre où l’exécutable natif est généré et suppose que le répertoire du projet s’appelle HelloNative.

```
$ dotnet restore 
$ dotnet build 
$ .\bin\Debug\netcoreapp1.0\win10-x64\HelloNative.exe
Hello World!
```

Vous pouvez remarquer que la génération de l’application native prend un peu plus de temps, mais son exécution est légèrement plus rapide. Ce comportement devient plus évident à mesure que la taille de l’application augmente.

Le processus de génération génère plusieurs fichiers quand votre `project.json` crée une version native. Ces fichiers sont créés dans `bin\Debug\netcoreapp1.0\<platform>`, où `<platform>` est l’identificateur de runtime choisi. En plus du fichier `HelloNative.dll` du projet, il existe un fichier `HelloNative.exe` qui charge le runtime et démarre l’application.
Notez que le nom de l’application générée a changé, car le nom du répertoire du projet a changé.  

Vous pouvez empaqueter cette application pour l’exécuter sur un ordinateur qui n’inclut pas le runtime .NET.
Pour ce faire, utilisez la commande `dotnet publish`. La commande `dotnet publish` crée un sous-répertoire sous le répertoire `./bin/Debug/netcoreapp1.0/<platform>`, appelé `publish`. Il copie l’exécutable, toutes les DLL dépendantes et le framework dans ce sous-répertoire. Vous pouvez empaqueter ce répertoire sur un autre ordinateur (ou dans un conteneur), puis y exécuter l’application. 

Comparons ce comportement à celui de `dotnet publish` dans le premier exemple Hello World. Cette application est une *application portable*, qui est le type d’application par défaut pour .NET Core. Une application portable nécessite que .NET Core soit installé sur l’ordinateur cible. Les applications portables peuvent être générées sur un ordinateur et exécutées n’importe où. Les applications natives doivent être générées séparément pour chaque ordinateur cible. `dotnet publish` crée un répertoire contenant la DLL de l’application, ainsi que toutes les DLL dépendantes qui ne font pas partie de l’installation de la plateforme.

### <a name="augmenting-the-program"></a>Augmentation du programme

Nous allons modifier juste un peu le fichier.  Les nombres Fibonacci sont amusants. Donc, faisons un essai (à l’aide de la version native) :

`Program.cs`:

```csharp
using static System.Console;

namespace ConsoleApplication
{
    public class Program
    {
        public static int FibonacciNumber(int n)
        {
            int a = 0;
            int b = 1;
            int tmp;
            
            for (int i = 0; i < n; i++)
            {
                tmp = a;
                a = b;
                b += tmp;
            }
            
            return a;   
        }
        
        public static void Main(string[] args)
        {
            WriteLine("Hello World!");
            WriteLine("Fibonacci Numbers 1-15:");
            
            for (int i = 0; i < 15; i++)
            {
                WriteLine($"{i+1}: {FibonacciNumber(i)}");
            }
        }
    }
}
```

Et l’exécution du programme (en supposant que vous êtes sur Windows et que vous avez remplacé le nom de répertoire du projet par Fibonacci) :

```
$ dotnet build
$ .\bin\Debug\netcoreapp1.0\win10-x64\Fibonacci.exe
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

## <a name="adding-some-new-files"></a>Ajouter de nouveaux fichiers

Les fichiers uniques conviennent aux programmes ponctuels simples, mais vous voulez peut-être diviser les éléments en plusieurs fichiers si vous créez quelque chose qui comporte plusieurs composants.  Pour cela, vous pouvez utiliser plusieurs fichiers.

Créez un fichier et attribuez-lui un espace de noms unique :

```csharp
using System;

namespace NumberFun
{
    // code can go here
} 
```

Ensuite, incluez-le dans votre fichier `Program.cs` :

```csharp
using static System.Console;
using NumberFun;
```

Et enfin, vous pouvez le générer :

`$ dotnet build`

Maintenant, la partie amusante : faire faire quelque chose au nouveau fichier !

### <a name="example-a-fibonacci-sequence-generator"></a>Exemple : Un générateur de séquence Fibonacci

Supposons que vous souhaitez vous appuyer sur l’[exemple Fibonacci](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/Fibonacci) précédent en mettant en cache certaines valeurs Fibonacci et ajouter une touche récursive.  Votre code pour un [meilleur exemple Fibonacci](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/FibonacciBetter) peut se présenter comme ceci :

```csharp
using System;
using System.Collections.Generic;

namespace NumberFun
{
    public class FibonacciGenerator
    {
        private Dictionary<int, int> _cache = new Dictionary<int, int>();
        
        private int Fib(int n) => n < 2 ? n : FibValue(n - 1) + FibValue(n - 2);
        
        private int FibValue(int n)
        {
            if (!_cache.ContainsKey(n))
            {
                _cache.Add(n, Fib(n));
            }
            
            return _cache[n];
        }
        
        public IEnumerable<int> Generate(int n)
        {
            for (int i = 0; i < n; i++)
            {
                yield return FibValue(i);
            }
        }
    }
}
```

Notez que l’utilisation de `Dictionary<int, int>` et de `IEnumerable<int>` suppose d’incorporer l’espace de noms `System.Collections`.
Le package `Microsoft.NetCore.App` est un *métapackage* qui contient un grand nombre des assemblys principaux du .NET Framework. En incluant ce métapackage, vous avez déjà inclus l’assembly `System.Collections.dll` dans le cadre de votre projet. Vous pouvez le vérifier en exécutant `dotnet publish` et en examinant les fichiers qui font partie du package installé. Vous verrez `System.Collections.dll` dans la liste. 

```json
{ 
  "version": "1.0.0-*", 
  "buildOptions": { 
    "debugType": "portable", 
    "emitEntryPoint": true 
  }, 
  "dependencies": {}, 
  "frameworks": { 
    "netcoreapp1.0": { 
      "dependencies": { 
        "Microsoft.NETCore.App": { 
          "version": "1.0.0" 
        } 
      }, 
      "imports": "dnxcore50" 
    } 
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.11-x64": {}
  }
}
```

Ajustez maintenant la méthode `Main()` dans votre fichier `Program.cs`comme indiqué ci-dessous. L’exemple suppose que `Program.cs` a une instruction `using System;`. Si vous avez une instruction `using static System.Console;`, supprimez `Console.` de `Console.WriteLine`.  

```csharp
public static void Main(string[] args)
{
    var generator = new FibonacciGenerator();
    foreach (var digit in generator.Generate(15))
    {
        WriteLine(digit);
    }
}
```

Pour finir, exécutez-la !

```
$ dotnet run
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

Et voilà !

## <a name="using-folders-to-organize-code"></a>Utilisation de dossiers pour organiser le code

Supposons que vous souhaitiez introduire de nouveaux types sur lesquels travailler.  Pour cela, ajoutez des fichiers supplémentaires et veillez à leur donner des espaces de noms que vous pouvez inclure dans votre fichier `Program.cs`.

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__project.json
```

Cela fonctionne très bien quand la taille de votre projet est relativement petite.  Toutefois, si vous avez une application plus volumineuse avec nombreux types de données différents et potentiellement plusieurs couches, vous pouvez organiser les éléments de façon logique.  C’est alors que des dossiers entrent en jeu.  Vous pouvez soit suivre [l’exemple de projet NewTypes](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypes) traité dans ce guide, soit créer vos propres fichiers et dossiers.

Pour commencer, créez un dossier sous la racine de votre projet.  `/Model` est choisi ici.

```
/NewTypes
|__/Model
|__Program.cs
|__project.json
```

Ajoutez maintenant de nouveaux types dans le dossier :

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__project.json
```

À présent, exactement comme s’il s’agissait de fichiers du même répertoire, donnez-leur à tous le même espace de noms afin de pouvoir les inclure dans votre `Program.cs`.

### <a name="example-pet-types"></a>Exemple : Types d’animaux

Cet exemple crée deux types, `Dog` et `Cat`, puis leur fait implémenter une interface, `IPet`.

Structure du dossier :

```
/NewTypes
|__/Pets
   |__Dog.cs
   |__Cat.cs
   |__IPet.cs
|__Program.cs
|__project.json
```

`IPet.cs`:
```csharp
using System;

namespace Pets
{
    public interface IPet
    {
        string TalkToOwner();
    }
}
```

`Dog.cs`:
```csharp
using System;

namespace Pets
{
    public class Dog : IPet
    {
        public string TalkToOwner() => "Woof!";
    }
}
```

`Cat.cs`:
```csharp
using System;

namespace Pets
{
    public class Cat : IPet
    {
        public string TalkToOwner() => "Meow!";
    }
}
```

`Program.cs`:
```csharp
using System;
using Pets;
using System.Collections.Generic;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            List<IPet> pets = new List<IPet>
            {
                new Dog(),
                new Cat()  
            };
            
            foreach (var pet in pets)
            {
                Console.WriteLine(pet.TalkToOwner());
            }
        }
    }
}
```

`project.json`:
```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "emitEntryPoint": true
  },
  "dependencies": {
    "Microsoft.NETCore.App": {
      "type": "platform",
      "version": "1.0.0"
    }
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": "dnxcore50"
    }
  }
}
```

Et si vous exécutez ce code :

```
$ dotnet restore
$ dotnet run
Woof!
Meow!
```

De nouveaux types d’animaux peuvent être ajoutés (comme `Bird`), ce qui étend ce projet.

## <a name="testing-your-console-app"></a>Test de votre application console

Vous voudrez probablement tester vos projets à un moment donné.  Voici une bonne façon de procéder :

1. Déplacez n’importe quelle source de votre projet existant dans un nouveau dossier `src`.

   ```
   /Project
   |__/src
   ```

2. Créez un répertoire `/test`.

   ```
   /Project
   |__/src
   |__/test
   ```

3. Créez un fichier `global.json` :

   ```
   /Project
   |__/src
   |__/test
   |__global.json
   ```

   `global.json`:
   ```json
   {
      "projects": [
         "src", "test"
      ]
   }
   ```

   Ce fichier indique au système de build qu’il s’agit d’un système à projets multiples, ce qui lui permet de rechercher des dépendances dans d’autres dossiers que celui actuel dans lequel il est en cours d’exécution.  Cela est important car vous pouvez ainsi placer une dépendance sur le code testé dans votre projet de test.
   
### <a name="example-extending-the-newtypes-project"></a>Exemple : Extension du projet NewTypes

Maintenant que le système de projet est en place, vous pouvez créer votre projet de test et commencer à écrire des tests !  À partir de maintenant, ce guide va utiliser et étendre [l’exemple de projet de types](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypes).  De plus, il utilisera le framework de test [Xunit](https://xunit.github.io/).  N’hésitez pas à poursuivre avec des tests sur un système à projets multiples ou à créer votre propre système.


La structure de projet complète doit ressembler à ceci :

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__project.json
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__project.json
|__global.json
```

Il existe deux nouvelles façons de vérifier que vous avez, dans votre projet de test :

1. Un `project.json` correct avec les éléments suivants :

   * Une référence à `xunit`
   * Une référence à `dotnet-test-xunit`
   * Une référence à l’espace de noms correspondant au code testé

2. Une classe de test Xunit.

`NewTypesTests/project.json`:
```json
{
  "version": "1.0.0-*",
  "testRunner": "xunit",

  "dependencies": {
    "Microsoft.NETCore.App": {
      "type":"platform",
      "version": "1.0.0"
    },
    "xunit":"2.2.0-beta2-build3300",
    "dotnet-test-xunit": "2.2.0-preview2-build1029",
    "NewTypes": "1.0.0"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "portable-net45+win8" 
      ]
    }
  }
}
```

`PetTests.cs`: 
```csharp
using System;
using Xunit;
using Pets;
public class PetTests
{
    [Fact]
    public void DogTalkToOwnerTest()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.Equal(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerTest()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.Equal(expected, actual);
    }
}
```
   
Vous pouvez maintenant exécuter les tests !  La commande [`dotnet test`](../tools/dotnet-test.md) exécute l’exécuteur de tests que vous avez spécifié dans votre projet. Prenez soin de démarrer dans le répertoire de niveau supérieur.
 
```
$ dotnet restore
$ cd test/NewTypesTests
$ dotnet test
```
 
La sortie doit se présenter comme suit :
 
```
xUnit.net .NET CLI test runner (64-bit win10-x64)
  Discovering: NewTypesTests
  Discovered:  NewTypesTests
  Starting:    NewTypesTests
  Finished:    NewTypesTests
=== TEST EXECUTION SUMMARY ===
   NewTypesTests  Total: 2, Errors: 0, Failed: 0, Skipped: 0, Time: 0.144s
SUMMARY: Total: 1 targets, Passed: 1, Failed: 0.
```
 
## <a name="conclusion"></a>Conclusion
 
Nous espérons que ce guide vous a permis de découvrir comment créer une application console .NET Core, depuis les concepts de base jusqu’à un système à projets multiples comprenant des tests unitaires.  L’étape suivante consiste à créer vos propres applications console !
 
Si vous êtes intéressé par un exemple d’application console plus avancé, récupérez le didacticiel suivant : [Utilisation des outils CLI pour écrire des applications console : Guide pas à pas avancé](cli-console-app-tutorial-advanced.md).



<!--HONumber=Nov16_HO3-->


