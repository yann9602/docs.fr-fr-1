---
title: "Gestion des dépendances dans les outils .NET Core Preview 3"
description: "Preview 3 apporte des modifications quant à la gestion des dépendances"
keywords: "CLI, extensibilité, commandes personnalisées, .NET Core"
author: blackdwarf
manager: wpickett
ms.date: 11/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: e04d5f3b08c7f6885ed9914a91fc308234e6ce3b

---

<a name="managing-dependencies-in-net-core-preview-3-tooling"></a>Gestion des dépendances dans les outils .NET Core Preview 3
----------------------------------------------------

# <a name="overview"></a>Vue d'ensemble
Le déplacement des projets .NET Core de project.json vers csproj et MSBuild s’est accompagné d’une unification du fichier et des ressources de projet permettant le suivi des dépendances. Pour les projets .NET Core, cela est similaire à ce que project.json faisait. Il n’existe aucun fichier JSON ou XML distinct qui assure le suivi des dépendances NuGet. Avec ce changement, nous avons également introduit un autre type de *référence* dans la syntaxe csproj, appelé `<PackageReference>`. 

Ce document décrit le nouveau type de référence. Il montre également comment ajouter à votre projet une dépendance de package à l’aide de ce nouveau type de référence. 

# <a name="the-new-packagereference-element"></a>Nouvel élément <PackageReference>
`<PackageReference>` présente la structure de base suivante :

```xml
<PackageReference Include="<Package_ID>">
    <Version>PACKAGE_VERSION</Version>
</PackageReference>
```

Si vous êtes familiarisé avec MSBuild, il rappelle les autres [types de référence]() existants. La partie essentielle est l’instruction `Include` qui spécifie l’ID de package que vous souhaitez ajouter au projet. L’élément enfant `<Version>` spécifie la version à obtenir. Les versions sont spécifiées en fonction des [règles de version de NuGet](https://docs.nuget.org/ndocs/create-packages/dependency-versions#version-ranges).  

> **Remarque :** Si vous n’êtes pas familiarisé avec la syntaxe `csproj` globale, vous pouvez utiliser la [documentation de référence sur les projets MSBuild]().  

L’ajout d’une dépendance qui n’est disponible que dans une cible spécifique s’effectue à l’aide de conditions :

```xml
<PackageReference Include="<Package_ID>" Condition="'$(TargetFramework)' == 'netcoreapp1.0'">
    <Version>PACKAGE_VERSION</Version>
</PackageReference>
```

D’après le code ci-dessus, la dépendance n’est valide que si la génération se produit pour la cible donnée. Dans la condition, `$(TargetFramework)` est une propriété MSBuild définie dans le projet. Pour la plupart des applications .NET Core courantes, cela n’est pas nécessaire. 

# <a name="adding-a-dependency-to-your-project"></a>Ajout d’une dépendance à votre projet
Ajouter une dépendance à votre projet est une opération simple. Voici un exemple montrant comment ajouter `JSON.net` version `9.0.1` à votre projet. Bien entendu, cela vaut également pour toute autre dépendance NuGet. 

Quand vous ouvrez votre fichier projet, vous voyez au moins deux nœuds `<ItemGroup>`. L’un de ces nœuds contient déjà des éléments `<PackageReference>`. Vous pouvez ajouter votre nouvelle dépendance à ce nœud ou en créer un ; quel que soit votre choix, le résultat est le même. 

Dans cet exemple, nous allons utiliser le modèle par défaut qui est déposé par `dotnet new`. Il s’agit d’une application console simple. Quand nous ouvrons le projet, nous trouvons `<ItemGroup>`, qui contient déjà `<PackageReference>`. Nous y ajoutons le code suivant :

```xml
<PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1</Version>
</PackageReference>
```
Ensuite, nous enregistrons le projet et exécutons la commande `dotnet restore` pour installer la dépendance. 

Le projet complet ressemble à ceci :

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
    <PackageReference Include="Newtonsoft.Json">
        <Version>9.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>
  
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

# <a name="removing-a-dependency-from-the-project"></a>Suppression d’une dépendance du projet
Pour supprimer une dépendance du fichier projet, il suffit de supprimer `<PackageReference>` de ce fichier. 





<!--HONumber=Nov16_HO3-->


