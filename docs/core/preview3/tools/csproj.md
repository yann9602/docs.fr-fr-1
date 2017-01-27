---
title: "Informations de référence sur csproj │ SDK .NET Core"
description: "En savoir plus sur les différences entre les fichiers csproj existants et les fichiers csproj .NET Core"
keywords: "référence, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
manager: wpickett
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: af32bc592762d7e8cb4e3b180656d9c3464df4a5

---

<a name="additions-to-csproj-format-for-net-core"></a>Ajouts au format de csproj pour .NET Core
----------------------------------------

# <a name="overview"></a>Vue d'ensemble 
Ce document décrit les modifications qui ont été ajoutées aux fichiers csproj dans le cadre du passage de project.json à csproj et [MSBuild](https://github.com/Microsoft/MSBuild). Ce document décrit **uniquement les différences dans les fichiers csproj auxiliaires**. Pour plus d’informations de référence ou syntaxiques générales sur les fichiers projet, consultez la documentation sur les [fichiers projet MSBuild](). 

> **Remarque :** Ce document étant appelé à s’étoffer, consultez-le régulièrement pour en découvrir les nouveautés. 

# <a name="additions"></a>Ajouts

## <a name="packagereference"></a>PackageReference
Spécifie une dépendance NuGet dans le projet. L’attribut `Include` spécifie l’ID du package. 

```xml
<PackageReference Include="<package-id>">
    <Version></Version>
    <PrivateAssets></PrivateAssets>
    <IncludeAssets></IncludeAssets>
    <ExcludeAssets></ExcludeAssets>
</PackageReference>
```

### <a name="version"></a>Version
`<Version>` spécifie la version du package à restaurer. L’élément respecte les règles du schéma de version de NuGet.

### <a name="includeassets"></a>IncludeAssets
L’élément enfant `<IncludeAssets>` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` parent doivent être utilisées. 

L’élément peut contenir une ou plusieurs des valeurs suivantes :

* Compile � contenu du dossier lib disponible pour la compilation
* Runtime � contenu du dossier runtime distribué
* ContentFiles � contenu du dossier contentfiles utilisé
* Build � les propriétés/cibles dans le dossier de génération sont utilisées
* Native - contenu des ressources natives copié dans le dossier de sortie de l’exécution
* Analyzers � les analyseurs sont utilisés

Sinon, l’élément peut contenir :

* None � aucune de ces ressources n’est utilisée
* All � toutes ces ressources sont utilisées

### <a name="excludeassets"></a>ExcludeAssets
L’élément enfant `<ExcluseAssets>` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` parent ne doivent pas être utilisées.

L’élément peut contenir une ou plusieurs des valeurs suivantes :

* Compile � contenu du dossier lib disponible pour la compilation
* Runtime � contenu du dossier runtime distribué
* ContentFiles � contenu du dossier contentfiles utilisé
* Build � les propriétés/cibles dans le dossier de génération sont utilisées
* Native - contenu des ressources natives copié dans le dossier de sortie de l’exécution
* Analyzers � les analyseurs sont utilisés

Sinon, l’élément peut contenir :

* None � aucune de ces ressources n’est utilisée
* All � toutes ces ressources sont utilisées

### <a name="privateassets"></a>PrivateAssets
L’élément enfant `<PrivateAssets>` spécifie quelles ressources appartenant au package spécifié par l’élément `<PackageReference>` parent doivent être utilisées, mais sans être reprises dans le projet suivant. 

> **Remarque :** Il s’agit d’un nouveau terme pour l’élément `SupressParent` project.json/xproj. 

L’élément peut contenir une ou plusieurs des valeurs suivantes :

* Compile � contenu du dossier lib disponible pour la compilation
* Runtime � contenu du dossier runtime distribué
* ContentFiles � contenu du dossier contentfiles utilisé
* Build � les propriétés/cibles dans le dossier de génération sont utilisées
* Native - contenu des ressources natives copié dans le dossier de sortie de l’exécution
* Analyzers � les analyseurs sont utilisés

Sinon, l’élément peut contenir :

* None � aucune de ces ressources n’est utilisée
* All � toutes ces ressources sont utilisées

## <a name="dotnetclitoolreference"></a>DotnetCliToolReference
L’élément `<DotnetCliToolReference>` spécifie l’outil CLI que l’utilisateur veut restaurer dans le contexte du projet. Il constitue une alternative au nœud `tools` dans `project.json`. 

### <a name="version"></a>Version
`<Version>` spécifie la version du package à restaurer. L’élément respecte les règles du schéma de version de NuGet.

## <a name="runtimeidentifiers"></a>RuntimeIdentifiers
L’élément `<RuntimeIdentifiers>` permet de spécifier une liste délimitée par des points-virgules d’[identificateurs de runtime](../../rid-catalog.md) pour le projet. Ces derniers permettent de publier des déploiements autonomes. 




<!--HONumber=Nov16_HO3-->


