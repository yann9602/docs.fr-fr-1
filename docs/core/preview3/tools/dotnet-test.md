---
title: Commande dotnet-test | SDK .NET Core
description: "La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné."
keywords: "dotnet-test, CLI, commande CLI, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 66c9f949980612f6e21b6d441c004cc09f4eb7d3

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>Nom

`dotnet-test` - Pilote de test .NET

## <a name="synopsis"></a>Résumé

`dotnet test [project] [--help] 
    [--settings] [--listTests] [--testCaseFilter] 
    [--testAdapterPath] [--logger] 
    [--configuration] [--output] [--framework] [--diag]
    [--noBuild]`  

## <a name="description"></a>Description

La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné. Les tests unitaires sont des projets de bibliothèques de classes qui ont des dépendances dans le framework de test unitaire (par exemple, NUnit ou xUnit) et dans le Test Runner dotnet de ce framework de test unitaire. Ils sont empaquetés sous forme de packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.

Les projets de test doivent également spécifier le test Runner. Pour ce faire, vous pouvez utiliser un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :

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
  </ItemGroup>

  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="options"></a>Options

`[project]`
    
Spécifie le chemin du projet de test. Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

`-h|--help`

Affiche une aide brève pour la commande.

`-s | --settings <SETTINGS_FILE>`

Paramètres à utiliser durant l’exécution des tests. 

`-lt | --listTests`

Répertorie tous les tests découverts dans le projet actuel. 

`-tcf | --testCaseFilter <EXPRESSION>`

Filtre les tests dans le projet actuel à l’aide de l’expression donnée. 

`-tap | --testAdapterPath <TEST_ADAPTER_PATH>`

Utilise les adaptateurs de test personnalisés à partir du chemin spécifié dans cette série de tests. 

`--logger <LOGGER>`

Spécifiez un journal pour les résultats de tests. 

`-c|--configuration <Debug|Release>`

Configuration dans laquelle effectuer la génération. La valeur par défaut est `Release`. 

`-o|--output [OUTPUT_DIRECTORY]`

Répertoire dans lequel rechercher les binaires à exécuter.

`-f|--framework [FRAMEWORK]`

Recherche des binaires de test pour un framework spécifique.

`-r|--runtime [RUNTIME_IDENTIFIER]`

Recherche des binaires de test pour le runtime spécifié.

`--noBuild` 

Ne génère pas le projet de test avant de l’exécuter. 

`-d | --diag <DIAGNOSTICS_FILE>`

Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié. 

## <a name="examples"></a>Exemples

Exécutez les tests du projet dans le répertoire actif :

`dotnet test` 

Exécutez les tests dans le projet test1 :

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>Voir aussi

[Frameworks](../../../standard/frameworks.md)

[Catalogue d’identificateurs de runtime (RID)](../../rid-catalog.md)



<!--HONumber=Nov16_HO3-->


