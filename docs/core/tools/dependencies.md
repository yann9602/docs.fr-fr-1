---
title: "Gestion des dépendances dans les outils .NET Core | Microsoft Docs"
description: "Explique comment gérer les dépendances avec les outils .NET Core."
keywords: "CLI, extensibilité, commandes personnalisées, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: f3eaf007593336234c6eff20127e9d02d2d5c9fa
ms.lasthandoff: 03/13/2017

---

# <a name="managing-dependencies-with-net-core-sdk-10"></a>Gestion des dépendances avec le SDK .NET Core 1.0

Le passage des projets .NET Core de project.json vers csproj et MSBuild s’est accompagné d’une unification du fichier projet et des ressources permettant le suivi des dépendances. Pour les projets .NET Core, cela est similaire à ce que project.json faisait. Il n’existe aucun fichier JSON ou XML distinct qui assure le suivi des dépendances NuGet. Avec ce changement, nous avons également introduit un autre type de *référence* dans la syntaxe csproj, appelé `<PackageReference>`. 

Ce document décrit le nouveau type de référence. Il montre également comment ajouter à votre projet une dépendance de package à l’aide de ce nouveau type de référence. 

## <a name="the-new-packagereference-element"></a>Nouvel élément <PackageReference>
`<PackageReference>` présente la structure de base suivante :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Si vous êtes familiarisé avec MSBuild, il est similaire aux autres types de référence existants. La partie essentielle est l’instruction `Include` qui spécifie l’ID de package que vous souhaitez ajouter au projet. L’élément enfant `<Version>` spécifie la version à obtenir. Les versions sont spécifiées en fonction des [règles de version de NuGet](https://docs.microsoft.com/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Si vous n’êtes pas familiarisé avec la syntaxe `csproj` générale, consultez la documentation de [référence sur les projets MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.  

L’ajout d’une dépendance qui n’est disponible que dans une cible spécifique s’effectue à l’aide de conditions décrites dans l’exemple suivant :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

D’après le code ci-dessus, la dépendance n’est valide que si la génération se produit pour la cible donnée. Dans la condition, `$(TargetFramework)` est une propriété MSBuild définie dans le projet. Pour la plupart des applications .NET Core courantes, cela n’est pas nécessaire. 

## <a name="adding-a-dependency-to-your-project"></a>Ajout d’une dépendance à votre projet
Ajouter une dépendance à votre projet est une opération simple. Voici un exemple montrant comment ajouter la version `9.0.1` de Json.NET à votre projet. Bien entendu, cela vaut également pour toute autre dépendance NuGet. 

Quand vous ouvrez votre fichier projet, vous voyez au moins deux nœuds `<ItemGroup>`. L’un de ces nœuds contient déjà des éléments `<PackageReference>`. Vous pouvez ajouter votre nouvelle dépendance à ce nœud ou en créer un ; quel que soit votre choix, le résultat est le même. 

Dans cet exemple, nous allons utiliser le modèle par défaut qui est déposé par `dotnet new console`. Il s’agit d’une application console simple. Quand nous ouvrons le projet, nous trouvons `<ItemGroup>`, qui contient déjà `<PackageReference>`. Nous y ajoutons le code suivant :

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
Ensuite, nous enregistrons le projet et exécutons la commande `dotnet restore` pour installer la dépendance. 

Le projet complet ressemble à ceci :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a>Suppression d’une dépendance du projet
Pour supprimer une dépendance du fichier projet, il suffit de supprimer `<PackageReference>` de ce fichier.
