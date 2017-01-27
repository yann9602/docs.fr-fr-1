---
title: "Organiser et tester des projets avec la ligne de commande .NET Core (SDK Preview 3)"
description: "Organiser et tester des projets avec la ligne de commande .NET Core (SDK Preview 3)"
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
ms.sourcegitcommit: 07b62bd7163193eff8dc8f61fda7a45a924bba2b
ms.openlocfilehash: 0a3122a3c10838b74801bcc910070745cb9bf0d5

---

# <a name="organizing-and-testing-projects-with-the-net-core-command-line-sdk-preview-3"></a>Organiser et tester des projets avec la ligne de commande .NET Core (SDK Preview 3)

Ce didacticiel suit [Bien démarrer avec .NET Core sur Windows/Linux/Mac OS à l’aide de la ligne de commande (SDK Preview 3)](./using-with-xplat-cli-msbuild.md) pour montrer comment aller au-delà des scénarios « hello world » simples et ouvrir la voie à des applications plus avancées et bien organisées.

## <a name="using-folders-to-organize-code"></a>Utilisation de dossiers pour organiser le code

Supposons que vous souhaitiez introduire de nouveaux types sur lesquels travailler.  Pour cela, ajoutez des fichiers supplémentaires et veillez à leur donner des espaces de noms que vous pouvez inclure dans votre fichier `Program.cs`.

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
```

Cela fonctionne très bien quand la taille de votre projet est relativement petite.  Toutefois, si vous avez une application plus volumineuse avec nombreux types de données différents et potentiellement plusieurs couches, vous pouvez organiser les éléments de façon logique. C’est alors que des dossiers entrent en jeu.  Vous pouvez soit suivre [l’exemple de projet NewTypes](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) traité dans ce guide, soit créer vos propres fichiers et dossiers.

Pour commencer, créez un dossier sous la racine de votre projet. `/Model` est choisi ici.

```
/NewTypes
|__/Model
|__Program.cs
|__NewTypes.csproj
```

Ajoutez maintenant de nouveaux types dans le dossier :

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__NewTypes.csproj
```

À présent, exactement comme s’il s’agissait de fichiers du même répertoire, donnez-leur à tous le même espace de noms afin de pouvoir les inclure dans votre `Program.cs`.

### <a name="example-pet-types"></a>Exemple : Types d’animaux

Cet exemple crée deux types, `Dog` et `Cat`, puis leur fait implémenter une interface commune, `IPet`.

Structure du dossier :

```
/NewTypes
|__/Pets
   |__Dog.cs
   |__Cat.cs
   |__IPet.cs
|__Program.cs
|__NewTypes.csproj
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

`NewTypes.csproj`:
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

2. Créez un répertoire `/test`, puis `cd` dans celui-ci.

   ```
   /Project
   |__/src
   |__/test
   ```

3. Initialisez le répertoire avec une commande `dotnet new -t Xunittest`. Cela suppose le recours à Xunit, mais vous pouvez également utiliser MS Test en remplaçant `Xunittest` par `Mstest`.
   
### <a name="example-extending-the-newtypes-project"></a>Exemple : Extension du projet NewTypes

Maintenant que le système de projet est en place, vous pouvez créer votre projet de test et commencer à écrire des tests ! À partir de maintenant, ce guide va utiliser et étendre [l’exemple de projet de types](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild). De plus, il utilisera le framework de test [Xunit](https://xunit.github.io/). N’hésitez pas à poursuivre avec des tests sur un système à projets multiples ou à créer votre propre système.

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
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

Il existe deux nouvelles façons de vérifier que vous avez, dans votre projet de test :

1. Un fichier `NewTypesTests.csproj` correct avec les éléments suivants :

   * Une référence à `xunit`
   * Une référence à `dotnet-test-xunit`
   * Une référence à l’espace de noms correspondant au code testé

   Cela peut être généré en exécutant simplement `dotnet new -t Xunittest` à partir de la ligne de commande dans le répertoire `NewTypesTests`, puis en ajoutant une référence de projet au projet `NewTypes`.

    `NewTypesTests/NewTypesTests.csproj`:
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
        <PackageReference Include="Microsoft.NET.Test.Sdk">
          <Version>15.0.0-preview-20161024-02</Version>
        </PackageReference>
        <PackageReference Include="xunit">
          <Version>2.2.0-beta3-build3402</Version>
        </PackageReference>
        <PackageReference Include="xunit.runner.visualstudio">
          <Version>2.2.0-beta4-build1188</Version>
        </PackageReference>
        <ProjectReference Include="../../src/NewTypes/NewTypes.csproj"/>
      </ItemGroup>

      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

2. Une classe de test Xunit.

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
$ cd test/NewTypesTests
$ dotnet restore
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



<!--HONumber=Nov16_HO3-->


