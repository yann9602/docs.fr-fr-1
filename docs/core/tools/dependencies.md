---
title: "Gérer les dépendances dans les outils .NET Core"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b982d72b92cefb015c584ea6827dc60999ca9a00
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="cab30-104">Gestion des dépendances avec le SDK .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="cab30-104">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="cab30-105">Le passage des projets .NET Core de project.json vers csproj et MSBuild s’est accompagné d’une unification du fichier projet et des ressources permettant le suivi des dépendances.</span><span class="sxs-lookup"><span data-stu-id="cab30-105">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="cab30-106">Pour les projets .NET Core, cela est similaire à ce que project.json faisait.</span><span class="sxs-lookup"><span data-stu-id="cab30-106">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="cab30-107">Il n’existe aucun fichier JSON ou XML distinct qui assure le suivi des dépendances NuGet.</span><span class="sxs-lookup"><span data-stu-id="cab30-107">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="cab30-108">Avec ce changement, nous avons également introduit un autre type de *référence* dans la syntaxe csproj, appelé `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="cab30-108">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="cab30-109">Ce document décrit le nouveau type de référence.</span><span class="sxs-lookup"><span data-stu-id="cab30-109">This document describes the new reference type.</span></span> <span data-ttu-id="cab30-110">Il montre également comment ajouter à votre projet une dépendance de package à l’aide de ce nouveau type de référence.</span><span class="sxs-lookup"><span data-stu-id="cab30-110">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="cab30-111">Nouvel élément \<PackageReference></span><span class="sxs-lookup"><span data-stu-id="cab30-111">The new \<PackageReference> element</span></span>
<span data-ttu-id="cab30-112">`<PackageReference>` présente la structure de base suivante :</span><span class="sxs-lookup"><span data-stu-id="cab30-112">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="cab30-113">Si vous êtes familiarisé avec MSBuild, il est similaire aux autres types de référence existants.</span><span class="sxs-lookup"><span data-stu-id="cab30-113">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="cab30-114">La partie essentielle est l’instruction `Include` qui spécifie l’ID de package que vous souhaitez ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="cab30-114">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="cab30-115">L’élément enfant `<Version>` spécifie la version à obtenir.</span><span class="sxs-lookup"><span data-stu-id="cab30-115">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="cab30-116">Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="cab30-116">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="cab30-117">Si vous n’êtes pas familiarisé avec la syntaxe `csproj` générale, consultez la documentation de [référence sur les projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="cab30-117">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="cab30-118">L’ajout d’une dépendance qui n’est disponible que dans une cible spécifique s’effectue à l’aide de conditions décrites dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cab30-118">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

<span data-ttu-id="cab30-119">D’après le code ci-dessus, la dépendance n’est valide que si la génération se produit pour la cible donnée.</span><span class="sxs-lookup"><span data-stu-id="cab30-119">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="cab30-120">Dans la condition, `$(TargetFramework)` est une propriété MSBuild définie dans le projet.</span><span class="sxs-lookup"><span data-stu-id="cab30-120">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="cab30-121">Pour la plupart des applications .NET Core courantes, cela n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cab30-121">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="cab30-122">Ajout d’une dépendance à votre projet</span><span class="sxs-lookup"><span data-stu-id="cab30-122">Adding a dependency to your project</span></span>
<span data-ttu-id="cab30-123">Ajouter une dépendance à votre projet est une opération simple.</span><span class="sxs-lookup"><span data-stu-id="cab30-123">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="cab30-124">Voici un exemple montrant comment ajouter la version `9.0.1` de Json.NET à votre projet.</span><span class="sxs-lookup"><span data-stu-id="cab30-124">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="cab30-125">Bien entendu, cela vaut également pour toute autre dépendance NuGet.</span><span class="sxs-lookup"><span data-stu-id="cab30-125">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="cab30-126">Quand vous ouvrez votre fichier projet, vous voyez au moins deux nœuds `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="cab30-126">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="cab30-127">L’un de ces nœuds contient déjà des éléments `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="cab30-127">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="cab30-128">Vous pouvez ajouter votre nouvelle dépendance à ce nœud ou en créer un ; quel que soit votre choix, le résultat est le même.</span><span class="sxs-lookup"><span data-stu-id="cab30-128">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="cab30-129">Dans cet exemple, nous allons utiliser le modèle par défaut qui est déposé par `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="cab30-129">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="cab30-130">Il s’agit d’une application console simple.</span><span class="sxs-lookup"><span data-stu-id="cab30-130">This is a simple console application.</span></span> <span data-ttu-id="cab30-131">Quand nous ouvrons le projet, nous trouvons `<ItemGroup>`, qui contient déjà `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="cab30-131">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="cab30-132">Nous y ajoutons le code suivant :</span><span class="sxs-lookup"><span data-stu-id="cab30-132">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="cab30-133">Ensuite, nous enregistrons le projet et exécutons la commande `dotnet restore` pour installer la dépendance.</span><span class="sxs-lookup"><span data-stu-id="cab30-133">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

<span data-ttu-id="cab30-134">Le projet complet ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="cab30-134">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="cab30-135">Suppression d’une dépendance du projet</span><span class="sxs-lookup"><span data-stu-id="cab30-135">Removing a dependency from the project</span></span>
<span data-ttu-id="cab30-136">Pour supprimer une dépendance du fichier projet, il suffit de supprimer `<PackageReference>` de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="cab30-136">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>

