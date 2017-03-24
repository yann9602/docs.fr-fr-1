---
title: "Guide pratique pour gérer les versions de dépendances de package pour .NET Core 1.0"
description: "Guide pratique pour gérer les versions de dépendances de package pour .NET Core 1.0"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: cf6c9757ab451f88c80fedb2dfebf7f5e320f365
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>Guide pratique pour gérer les versions de dépendances de package pour .NET Core 1.0

Cet article décrit ce que vous devez savoir sur les versions de package de vos applications et bibliothèques .NET Core.

## <a name="glossary"></a>Glossaire

**Fixer** : Fixer des dépendances consiste à utiliser la même « famille » de packages publiés sur NuGet pour .NET Core 1.0.

**Métapackage** : Package NuGet représentant un ensemble de packages NuGet.

**Suppression** : Opération consistant à supprimer d’un métapackage les packages dont vous ne dépendez pas.  Elle concerne les auteurs de packages NuGet.  Pour plus d’informations, consultez [Réduction des dépendances de package avec project.json](../deploying/reducing-dependencies.md). 

## <a name="fix-your-dependencies-to-net-core-10"></a>Fixer vos dépendances sur .NET Core 1.0

Pour restaurer des packages et écrire du code de manière fiable, il est important de fixer les dépendances aux versions de package fournies avec .NET Core 1.0.  Cela signifie que chaque package doit avoir une seule version sans aucun qualificateur supplémentaire.

**Exemples de packages fixés sur 1.0**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**Exemples de packages NON fixés sur 1.0**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>Pourquoi est-ce important ?

Nous garantissons que si vous avez fixé vos dépendances sur celles fournies avec .NET Core 1.0, ces packages fonctionneront ensemble.  Par contre, nous ne garantissons rien si vous utilisez des packages qui ne sont pas fixés de cette façon.

### <a name="scenarios"></a>Scénarios

Bien qu’il existe une longue liste de tous les packages et de leurs versions publiées avec .NET Core 1.0, vous n’avez pas à la parcourir si votre code correspond à certains scénarios.

**Dépendez-vous uniquement de** `NETStandard.Library`** ?**

Si c’est le cas, vous devez fixer votre package `NETStandard.Library` sur la version `1.6`.  Comme il s’agit d’un métapackage organisé, sa fermeture de package est également fixée sur 1.0.

**Dépendez-vous uniquement de** `Microsoft.NETCore.App`** ?**

Si c’est le cas, vous devez fixer votre package `Microsoft.NETCore.App` sur la version `1.0.0`.  Comme il s’agit d’un métapackage organisé, sa fermeture de package est également fixée sur 1.0.

**[Supprimez](../deploying/reducing-dependencies.md)-vous vos dépendances de métapackage** `NETStandard.Library` **ou** `Microsoft.NETCore.App` ** ?**

Si c’est le cas, vous devez vérifier que le métapackage avec lequel vous commencez est fixé sur 1.0.  Les packages individuels desquels vous dépendez après la suppression sont également fixés sur 1.0.

**Dépendez-vous de packages hors des métapackages** `NETStandard.Library` **ou** `Microsoft.NETCore.App`** ?**

Si c’est le cas, vous devez fixer vos autres dépendances sur 1.0.  Consultez les versions de package et les numéros de build appropriés à la fin de cet article.

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>Remarque sur l’utilisation d’une chaîne se terminant par un astérisque (\*) lors de la gestion de version

Vous avez peut-être adopté un modèle de gestion de version qui utilise une chaîne se terminant par un astérisque (\*) comme la suivante : `"System.Collections":"4.0.11-*"`.

**Vous ne devez pas procéder ainsi**.  L’utilisation de la chaîne se terminant par un astérisque peut entraîner la restauration de packages de différentes builds, dont certaines peuvent être plus avancées que .NET Core 1.0.  Cela pourrait alors entraîner l’incompatibilité de certains packages.

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>Packages et numéros de version organisés par métapackage

[List of all .NET Standard library packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt) (Liste de tous les packages de bibliothèque .NET Standard et leurs versions pour 1.0).

[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt)(Liste de tous les packages d’exécution et leurs versions pour 1.0).

[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt) (Liste de tous les packages d’application .NET Core et leurs versions pour 1.0).

