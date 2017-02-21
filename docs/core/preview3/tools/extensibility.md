---
title: "Modèle d’extensibilité des outils CLI .NET Core | Microsoft Docs"
description: "Modèle d’extensibilité des outils CLI .NET Core"
keywords: "CLI, extensibilité, commandes personnalisées, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 02/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
translationtype: Human Translation
ms.sourcegitcommit: 5a1ba8984d93795e4628a7b911307d513e8de8d1
ms.openlocfilehash: 1b6bc46639fda60e4a23c1ea66d0d0ca8b58acb7

---

# <a name="net-core-cli-extensibility-model-net-core-tools-rc4"></a>Modèle d’extensibilité des outils CLI .NET Core (outils .NET Core RC4)

> [!WARNING]
> Cette rubrique s’applique aux outils .NET Core RC4. Pour la version Preview 2 des outils .NET Core, consultez la rubrique [Modèle d’extensibilité des outils CLI .NET Core](../../tools/dotnet-test.md).

## <a name="overview"></a>Vue d'ensemble
Ce document explique les principales méthodes permettant d’étendre les outils CLI, et décrit les scénarios dans lesquels elles sont utilisées. Ce document décrit comment utiliser les outils et explique brièvement comment créer ces deux types d’outils. 

## <a name="how-to-extend-cli-tools"></a>Extension des outils CLI
Vous pouvez étendre les outils CLI RC4 de trois façons :

1. Via les packages NuGet, par projet
2. Via les packages NuGet avec des cibles personnalisées  
3. Via le chemin (PATH) du système

Les trois mécanismes d’extensibilité présentés ci-dessus ne sont pas exclusifs. Vous pouvez utiliser un seul, une partie ou la totalité d’entre eux. Le choix de la méthode dépend en grande partie de l’objectif de votre extension.

## <a name="per-project-based-extensibility"></a>Extensibilité par projet
Les outils par projet sont des [déploiements dépendants du framework](../deploying/index.md) qui sont distribués dans les packages NuGet. Les outils sont uniquement disponibles dans le contexte du projet qui les référence et pour lequel ils sont restaurés. Les appels en dehors du contexte du projet (par exemple, en dehors du répertoire qui contient le projet) échoueront, car la commande ne pourra pas être trouvée.

Ces outils sont parfaits pour les serveurs de build, puisque rien en dehors du fichier projet n’est nécessaire. Le processus de génération exécute la restauration pour le projet qu’il génère, et des outils seront disponibles. Les projets de langage, tels que F#, figurent également dans cette catégorie. Chaque projet ne peut être écrit que dans un langage. 

Enfin, ce modèle d’extensibilité prend en charge la création d’outils qui ont besoin d’accéder à la sortie générée du projet. Par exemple, les outils d’affichage Razor des applications MVC [ASP.NET](https://www.asp.net/) appartiennent à cette catégorie. 

### <a name="consuming-per-project-tools"></a>Utilisation des outils par projet
Vous devez ajouter à votre fichier projet un élément `<DotNetCliToolReference>` pour chaque outil que vous souhaitez utiliser. À l’intérieur de l’élément `<DotNetCliToolReference>`, vous référencez le package dans lequel réside l’outil et vous spécifiez la version dont vous avez besoin. Après l’exécution de `dotnet restore`, l’outil et ses dépendances sont restaurés. 

Pour les outils qui doivent charger la sortie de génération du projet pour l’exécution, il existe généralement une autre dépendance qui est répertoriée sous les dépendances régulières du fichier projet. Étant donné que la version RC4 de l’interface CLI utilise MSBuild comme moteur de génération, nous vous recommandons d’écrire ces parties de l’outil comme cibles et tâches MSBuild personnalisées pour qu’elles puissent participer à l’ensemble du processus de génération. Elles peuvent aussi facilement récupérer tout ou partie des données produites par la génération, telles que l’emplacement des fichiers de sortie ou la configuration en cours de génération. Toutes ces informations dans RC4 deviennent un jeu de propriétés MSBuild qui peut être lu à partir de toutes les cibles. Nous verrons comment ajouter une cible personnalisée à l’aide de NuGet plus loin dans ce document. 

Voyons un exemple d’ajout d’un outil simple de type « tools-only » à un projet simple. Prenons un exemple de commande appelé `dotnet-api-search` qui vous permette de parcourir les packages NuGet à la recherche de l’API spécifiée. Voici le fichier projet de l’application console qui utilise cet outil :


```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1/TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

L’élément `<DotNetCliToolReference>` est structuré de la même façon que l’élément `<PackageReference>`. Il a besoin, au minimum, de l’ID de package du package qui contient l’outil et sa version. 

### <a name="building-tools"></a>Outils de création
Comme nous l’avons mentionné précédemment, les outils sont des applications console portables. Ils peuvent être créés comme toute autre application console. Une fois l’outil créé, utilisez la commande [`dotnet pack`](dotnet-pack.md) pour créer un package NuGet (nupkg) devant contenir votre code, les informations sur ses dépendances, etc. L’auteur est libre de nommer le package comme il l’entend. Toutefois, l’application qui s’y trouve, le fichier binaire de l’outil, doit respecter la convention de `dotnet-<command>` afin de pouvoir être appelée par `dotnet`. 

> [!NOTE]
> Dans les versions antérieures à RC3 des outils en ligne de commande .NET Core, la commande `dotnet pack` présentait un bogue qui empêchait la compression de `runtime.config.json` avec l’outil. L’absence de ce fichier aboutit à des erreurs lors de l’exécution. Si vous rencontrez ce comportement, veillez à utiliser les outils les plus récents et essayez `dotnet pack` une nouvelle fois. 

Étant donné que les outils sont des applications portables, l’utilisateur qui utilise un outil doit disposer de la version des bibliothèques .NET Core à l’aide desquelles l’outil a été développé, afin de pouvoir l’exécuter. Toute autre dépendance que l’outil utilise et qui ne figure pas dans les bibliothèques .NET Core est restaurée et placée dans le cache de NuGet. L’outil entier est, par conséquent, exécuté à l’aide des assemblys des bibliothèques .NET Core et du cache de NuGet. 

Ces types d’outils ont un graphique de dépendance qui est complètement distinct du graphique de dépendance du projet qui les utilise. Le processus de restauration restaure d’abord les dépendances du projet, puis restaure chacun des outils et leurs dépendances. 

Vous trouverez des exemples plus complets dans le [dépôt sur les outils CLI .NET Core](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestProjects). Vous pouvez également voir l’[implémentation des outils utilisés](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages) dans le même dépôt. 

### <a name="custom-targets"></a>Cibles personnalisées
NuGet offre depuis un certain temps la possibilité d’empaqueter des fichiers de propriétés et de cibles MSBuild personnalisés, et la documentation officielle à ce sujet est disponible sur le [site de la documentation de NuGet](https://docs.microsoft.com/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). Suite à l’adoption de MSBuild dans l’interface CLI, le même mécanisme d’extensibilité s’applique aux projets .NET Core. Vous utilisez ce type d’extensibilité quand vous souhaitez étendre le processus de génération ou que vous souhaitez accéder à tous les artefacts dans le processus de génération, tels que les fichiers générés, ou inspecter la configuration sous laquelle la build est appelée, entre autres. 

Le fichier projet de l’exemple de cible est inclus ci-dessous pour référence. Il montre comment utiliser la nouvelle syntaxe `csproj` pour indiquer à la commande `dotnet pack` ce qu’elle doit empaqueter pour placer les fichiers des cibles et les assemblys dans le dossier `build` du package. Vous pouvez remarquer ci-dessous la présence d’une balise `<ItemGroup>` dont la propriété `Label` est définie sur « dotnet pack instructions ». 

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets;$(OutputPath)\*.dll;$(OutputPath)\*.json">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

L’utilisation de cibles personnalisées s’effectue en fournissant un `<PackageReference>` qui pointe vers le package et sa version dans le projet en cours d’extension. Contrairement aux outils, le package des cibles personnalisées n’est pas inclus dans la fermeture de dépendance du projet de consommation. 

L’utilisation de la cible personnalisée dépend uniquement de la façon dont vous la configurez. Puisqu’il s’agit de la cible MSBuild habituelle, elle peut dépendre d’une cible donnée, exécutée après une autre cible, et peut également être appelée manuellement à l’aide de la commande `dotnet msbuild /t:<target-name>`. 

Toutefois, si vous souhaitez procurer une meilleure expérience à vos utilisateurs, vous pouvez combiner des outils par projet et des cibles personnalisées. Dans ce scénario, l’outil par projet se contenterait essentiellement d’accepter tous les paramètres nécessaires à partir desquels il générerait l’invocation `dotnet msbuild` requise pour exécuter la cible. Vous pouvez voir un exemple de ce type de synergie sur le dépôt des [exemples du MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) du projet [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer). 

### <a name="path-based-extensibility"></a>Extensibilité basée sur le chemin (PATH)
L’extensibilité basée sur le chemin est généralement utilisée pour les ordinateurs de développement qui nécessitent un outil qui traite conceptuellement plusieurs projets. Le principal inconvénient de ce mécanisme d’extension est qu’il est limité à l’ordinateur sur lequel est installé l’outil. Si vous avez besoin de l’installer sur un autre ordinateur, vous devrez le déployer.

Ce modèle d’extensibilité des outils CLI est très simple. Comme indiqué dans la [présentation des outils CLI .NET Core](index.md), le pilote `dotnet` peut exécuter toutes les commandes dont le nom respecte la convention `dotnet-<command>`. La logique de résolution par défaut sonde d’abord plusieurs emplacements avant d’arriver au chemin système. Si la commande demandée existe dans le chemin système et s’il s’agit d’un fichier binaire qui peut être appelé, le pilote `dotnet` l’appellera. 

La seule qualité indispensable au fichier binaire est d’être exécutable par le système d’exploitation. Sur les systèmes Unix, il peut s’agir de tous les fichiers dont le bit d’exécution est défini via `chmod +x`. Sur les systèmes Windows, il peut s’agir de n’importe quel fichier que Windows peut exécuter. 

Voyons par exemple une implémentation très simple d’une commande `dotnet clean`. Nous allons utiliser `bash` pour implémenter cette commande. La commande supprime les répertoires `bin/` et `obj/` situés dans le répertoire actif. Si l’argument `--lock` lui est passé, elle supprime également le fichier `project.lock.json`. L’intégralité de la commande est affichée ci-dessous. 

```bash
#!/bin/bash

# Delete the bin and obj dirs
rm -rf bin/ obj/

LOCK_FILE=$1
if [[ "$LOCK_FILE" = "--lock" ]]; then
    rm project.lock.json
fi


echo "Cleaning complete..."
```

Sur Mac OS, nous pouvons enregistrer ce script en tant que `dotnet-clean` et définir son bit exécutable avec `chmod +x dotnet-clean`. Nous pouvons ensuite créer un lien symbolique vers le script dans `/usr/local/bin` à l’aide de la commande `ln -s dotnet-clean /usr/local/bin/`. Cela permet d’appeler la commande Clean à l’aide de la syntaxe `dotnet clean`. Vous pouvez tester cela en créant une application, en exécutant `dotnet build` sur l’application, puis en exécutant `dotnet clean`. 

## <a name="conclusion"></a>Conclusion
Les outils CLI .NET Core permettent trois principaux points d’extensibilité. Les outils par projet sont contenus dans le contexte du projet, mais ils permettent une installation rapide grâce à une restauration. Les cibles personnalisées vous permettent d’étendre facilement le processus de génération avec des tâches personnalisées. Les outils basés sur le chemin sont efficaces pour les outils généraux multiprojets qui sont utilisables sur un seul ordinateur. 




<!--HONumber=Feb17_HO2-->


