---
title: "Bien démarrer avec .NET Core sur Windows/Linux/Mac OS à l’aide de la ligne de commande (SDK Preview 3)"
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
ms.sourcegitcommit: ab71aab99505f211fe4adc86957eda4707761f1c
ms.openlocfilehash: 01b17021e79bcdb2dc69f97b709f4aa63dbab9aa

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line-sdk-preview-3"></a>Bien démarrer avec .NET Core sur Windows/Linux/Mac OS à l’aide de la ligne de commande (SDK Preview 3)

Ce guide indique comment utiliser les outils d’interface de ligne de commande (CLI) .NET Core pour créer des applications console multiplateformes.  Il démarre avec l’application console la plus simple qui s’étend finalement sur plusieurs projets, notamment le test. Vous allez ajouter ces fonctionnalités pas à pas, en vous basant sur ce que vous avez déjà vu et créé.

Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/dotnet.md).

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, vérifiez que vous disposez des [outils d’interface de ligne de commande (CLI) .NET Core Preview 3 ou version ultérieure](https://github.com/dotnet/core/blob/master/release-notes/preview3-download.md).  Vous aurez également besoin d’un éditeur de texte.

## <a name="hello-console-app"></a>Application console Hello

Tout d’abord, accédez à un dossier ou créez-en un avec le nom de votre choix.  « Hello » est le nom choisi pour l’exemple de code qui se trouve [ici](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild).

Ouvrez une invite de commandes, puis tapez les commandes suivantes :

```
$ dotnet new
$ dotnet restore
$ dotnet run
```

Suivons une procédure pas à pas rapide :

1. `$ dotnet new`

   [`dotnet new`](../tools/dotnet-new.md) crée un fichier projet `Hello.csproj` à jour avec les dépendances nécessaires pour générer une application console.  Il crée également `Program.cs`, un fichier de base contenant le point d’entrée pour l’application.
   
   `Hello.csproj`:
   ```xml
    <Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
        <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
        
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>netcoreapp1.0</TargetFramework>
        </PropertyGroup>

        <ItemGroup>
            <Compile Include="**\*.cs" />
            <EmbeddedResource Include="**\*.resx" />
        </ItemGroup>

        <ItemGroup>
            <PackageReference Include="Microsoft.NETCore.App">
                <Version>1.0.1</Version>
            </PackageReference>
            <PackageReference Include="Microsoft.NET.Sdk">
                <Version>1.0.0-alpha-20161104-2</Version>
                <PrivateAssets>All</PrivateAssets>
            </PackageReference>
        </ItemGroup>
        
        <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
   ```

   Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.

   * La balise `Import` apporte certaines propriétés qui sont communes à tous les projets .NET Core.
   * La balise `OutputType` spécifie que nous générons un fichier exécutable, autrement dit une application console.
   * La balise `TargetFramework` spécifie le runtime .NET que nous ciblons. Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération. Dans ce didacticiel, nous nous en tiendrons à une génération limitée à .NET Core 1.0.
   * La balise `Compile` indique au compilateur de générer tous les fichiers, dans le répertoire actif et dans tous ses sous-répertoires, qui ont l’extension `.cs`, en d’autres termes les fichiers C# dans le projet. Dans les scénarios avancés, il est possible d’exclure des fichiers, mais dans ce didacticiel et dans la plupart des scénarios simples, cette ligne peut rester inchangée.
   * La balise `EmbeddedResource` fait en sorte que le système de génération incorpore les fichiers de localisation avec l’extension `.resx` au fichier exécutable compilé. Nous n’utiliserons pas cette fonctionnalité dans ce didacticiel.
   * Les balises `PackageReference` spécifient les packages de dépendances qui doivent être restaurés et inclus pendant la génération de l’application. Chaque référence de package spécifie le nom du package sous l’attribut `Include` et un numéro de version. La plupart des scénarios avancés comportent plusieurs références de package. Il est également possible de référencer d’autres projets sur le disque.

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

   Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ». L’espace de noms `System` inclut des constructions de base, telles que `string`, ou des types numériques.

   Ensuite, nous définissons un espace de noms appelé « ConsoleApplication ». Vous pouvez le modifier à votre gré. Une classe nommée « Program » est définie dans cet espace de noms avec une méthode `Main` qui accepte un tableau de chaînes comme argument. Ce tableau contient la liste des arguments passés quand le programme compilé est appelé. Tel quel, ce tableau n’est pas utilisé : le programme se limite à écrire « Hello World! » dans la console. Nous pouvons rendre les choses un peu plus intéressantes en modifiant la ligne de code `Console.WriteLine` comme suit.

   ```csharp
   if (args.Length > 0)
   {
       Console.WriteLine($"Hello {args[0]}!");
   }
   else
   {
       Console.WriteLine("Hello World!");
   }
   ```

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) appelle [NuGet](http://nuget.org) (gestionnaire de package de .NET) pour restaurer l’arborescence de dépendances. NuGet analyse le fichier `Hello.csproj`, télécharge les dépendances indiquées dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier `obj/project.assets.json`.  Le fichier `project.assets.json` est nécessaire pour pouvoir effectuer la compilation et l’exécution.
   
   Le fichier `project.assets.json` est un ensemble persistant et complet du graphique de dépendances NuGet et d’autres informations qui décrivent une application.  Ce fichier est lu par d’autres outils, tels que `dotnet build` et `dotnet run`, ce qui leur permet de traiter le code source avec un ensemble approprié de dépendances NuGet et de résolutions de liaison.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) appelle `dotnet build` pour garantir que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.
   
    ```
    $ dotnet run
    Hello World!
    ```

    Si vous préférez, vous pouvez exécuter [`dotnet build`](../tools/dotnet-build.md) pour compiler le code sans exécuter les applications console de la build. Il en résulte une application compilée `bin/Debug/netcoreapp1.0/Hello.dll` qui peut être exécutée avec `dotnet bin\Debug\netcoreapp1.0\Hello.dll` sur Windows et `dotnet bin/Debug/netcoreapp1.0/Hello.dll` sur les autres systèmes. Vous pouvez spécifier un paramètre supplémentaire sur la ligne de commande (en supposant que vous êtes sur Windows) :

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll .NET
    Hello .NET!
    ```

    Dans le cadre d’un scénario avancé, vous pouvez générer l’application comme un ensemble autonome de fichiers spécifiques à la plateforme qui peuvent être déployés et exécutés sur un ordinateur sur lequel .NET Core n’est pas nécessairement installé. Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

### <a name="augmenting-the-program"></a>Augmentation du programme

Nous allons modifier juste un peu le fichier.  Les nombres Fibonacci sont amusants. Donc, faisons un essai :

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
$ dotnet bin\Debug\netcoreapp1.0\win10-x64\Fibonacci.exe
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
using NumberFun;
```

Et enfin, vous pouvez le générer :

`$ dotnet build`

Maintenant, la partie amusante : faire faire quelque chose au nouveau fichier !

### <a name="example-a-fibonacci-sequence-generator"></a>Exemple : Un générateur de séquence Fibonacci

Supposons que vous souhaitez vous appuyer sur l’exemple Fibonacci précédent en mettant en cache certaines valeurs Fibonacci et ajouter une touche récursive.  Votre code pour un [meilleur exemple Fibonacci](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/FibonacciBetterMsBuild) peut utiliser un nouveau fichier `FibonacciGenerator.cs` avec le code suivant.

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

Ajustez maintenant la méthode `Main()` dans votre fichier `Program.cs`comme indiqué ci-dessous.

```csharp
using System;
using NumberFun;

class Program
{
    static void Main(string[] args)
    {
        var generator = new FibonacciGenerator();
        foreach (var digit in generator.Generate(15))
        {
            Console.WriteLine(digit);
        }
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

## <a name="conclusion"></a>Conclusion
 
Nous espérons que ce guide vous a permis de découvrir comment créer une application console .NET Core, depuis les concepts de base jusqu’à un système à projets multiples comprenant des tests unitaires.  L’étape suivante consiste à créer vos propres applications console !
 
Pour découvrir un exemple d’application console plus avancé, consultez le didacticiel suivant : [Organiser et tester des projets avec la ligne de commande .NET Core (SDK Preview 3)](using-with-xplat-cli-msbuild-folders.md).



<!--HONumber=Nov16_HO3-->


