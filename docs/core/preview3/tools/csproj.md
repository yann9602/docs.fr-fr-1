---
title: "Informations de référence sur csproj | Microsoft Docs"
description: "Découvrir les différences entre les fichiers csproj existants et les fichiers csproj .NET Core"
keywords: "référence, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 07/02/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 0402707f98af8b716b041ba1260162cd227918cc
ms.openlocfilehash: 98f6ced2a199bdbe2f91f46e48ffd3ac52438cf8

---

# <a name="additions-to-the-csproj-format-for-net-core"></a>Ajouts au format csproj pour .NET Core

[!INCLUDE[preview-warning](../../../includes/warning.md)]

Ce document décrit les modifications apportées aux fichiers csproj dans le cadre du passage de `project.json` à `csproj` et [MSBuild](https://github.com/Microsoft/MSBuild). Pour plus d’informations de référence ou syntaxiques générales sur les fichiers projet, consultez la documentation sur les [fichiers projet MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference).  

## <a name="additions"></a>Ajouts

* Élément PackageReference qui spécifie une dépendance NuGet dans le projet. L’attribut `Include` spécifie l’ID du package. 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

## <a name="version"></a>Version
`Version` spécifie la version du package à restaurer. L’élément respecte les règles du schéma de version de NuGet.

## <a name="includeassets"></a>IncludeAssets
L’attribut `IncludeAssets` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` doivent être utilisées. 

L’attribut peut contenir une ou plusieurs des valeurs suivantes :

* `Compile` : Le contenu du dossier lib est disponible pour la compilation.
* `Runtime` : Le contenu du dossier runtime est distribué.
* `ContentFiles` : Le contenu du dossier contentfiles est utilisé.
* `Build` : Les propriétés/cibles du dossier de génération sont utilisées.
* `Native` : Le contenu des ressources natives est copié dans le dossier de sortie de l’exécution.
* `Analyzers` : Les analyseurs sont utilisés.

Sinon, l’attribut peut contenir :

* `None` : Aucune ressource n’est utilisée.
* `All` : Toutes les ressources sont utilisées.

## <a name="excludeassets"></a>ExcludeAssets
L’attribut `ExcludeAssets` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` ne doivent pas être utilisées.

L’attribut peut contenir une ou plusieurs des valeurs suivantes :

* `Compile` : Le contenu du dossier lib est disponible pour la compilation.
* `Runtime` : Le contenu du dossier runtime est distribué.
* `ContentFiles` : Le contenu du dossier contentfiles est utilisé.
* `Build` : Les propriétés/cibles du dossier de génération sont utilisées.
* `Native` : Le contenu des ressources natives est copié dans le dossier de sortie de l’exécution.
* `Analyzers` : Les analyseurs sont utilisés.

Sinon, l’élément peut contenir :

* `None` : Aucune ressource n’est utilisée.
* `All` : Toutes les ressources sont utilisées.

## <a name="privateassets"></a>PrivateAssets
L’attribut `PrivateAssets` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` doivent être utilisées, mais sans être reprises dans le projet suivant. 

> [!NOTE]
> Il s’agit d’un nouveau terme pour l’élément `SuppressParent` project.json/xproj. 

L’attribut peut contenir une ou plusieurs des valeurs suivantes :

* `Compile` : Le contenu du dossier lib est disponible pour la compilation.
* `Runtime` : Le contenu du dossier runtime est distribué.
* `ContentFiles` : Le contenu du dossier contentfiles est utilisé.
* `Build` : Les propriétés/cibles du dossier de génération sont utilisées.
* `Native` : Le contenu des ressources natives est copié dans le dossier de sortie de l’exécution.
* `Analyzers` : Les analyseurs sont utilisés.

Sinon, l’attribut peut contenir :

* `None` : Aucune ressource n’est utilisée.
* `All` : Toutes les ressources sont utilisées.

* L’élément `<DotnetCliToolReference>` DotnetCliToolReference spécifie l’outil CLI que l’utilisateur veut restaurer dans le contexte du projet. Il constitue une alternative au nœud `tools` dans `project.json`. 

```xml
<DotnetCliToolReference Include="<package-id>" Version="" />
```

## <a name="version"></a>Version
`Version` spécifie la version du package à restaurer. L’attribut respecte les règles du schéma de version de NuGet.

* RuntimeIdentifiers L’élément `<RuntimeIdentifiers>` vous permet de spécifier une liste délimitée par des points-virgules d’[identificateurs de runtime (RID)](../../rid-catalog.md) pour le projet. Les RID permettent de publier des déploiements autonomes. 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```


* RuntimeIdentifier L’élément `<RuntieIdentifier>` vous permet de spécifier un seul [identificateur de runtime (RID)](../../rid-catalog.md) pour le projet. Les RID permettent de publier un déploiement autonome. 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```


* PackageTargetFallback L’élément `<PackageTargetFallback>` vous permet de spécifier un jeu de cibles compatibles à utiliser lors de la restauration des packages. Il est conçu pour permettre aux packages qui utilisent le moniker du Framework cible DotNet de fonctionner avec les packages qui ne déclarent pas de moniker du Framework cible DotNet. Si votre projet utilise le moniker du Framework cible DotNet, tous les packages dont vous dépendez doivent également avoir un moniker du Framework cible DotNet, sauf si vous ajoutez `<PackageTargetFallback>` à votre projet afin de permettre à des plateformes autres que DotNet d’être compatibles avec DotNet. 

L’exemple suivant fournit les solutions de secours pour toutes les cibles dans votre projet : 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

L’exemple suivant spécifie les solutions de secours uniquement pour la cible `netcoreapp1.0` :

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>Propriétés de métadonnées NuGet
Avec le passage à MSbuild, nous avons transféré les métadonnées d’entrée utilisées lors de la compression d’un package NuGet des fichiers project.json aux fichiers csproj. Les entrées sont des propriétés MSBuild. Voici la liste des propriétés qui sont utilisées comme entrées dans le processus de compression lors de l’utilisation de la commande `dotnet pack` ou de la cible MSBuild `Pack` qui fait partie du SDK. 

* IsPackable
* PackageVersion
* PackageId
* Titre
* Auteurs
* Description
* Copyright
* PackageRequireLicenseAcceptance
* PackageLicenseUrl
* PackageProjectUrl
* PackageIconUrl
* PackageReleaseNotes
* PackageTags
* PackageOutputPath
* IncludeSymbols
* IncludeSource
* PackageTypes
* IsTool
* RepositoryUrl
* RepositoryType
* NoPackageAnalysis
* MinClientVersion
* IncludeBuildOutput
* IncludeContentInPack
* BuildOutputTargetFolder
* ContentTargetFolders
* NuspecFile
* NuspecBasePath
* NuspecProperties


<!--HONumber=Feb17_HO2-->


