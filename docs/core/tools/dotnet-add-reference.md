---
title: Commande dotnet-add reference - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-add reference est une option pratique pour ajouter des références entre projets."
keywords: dotnet-add, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e2a3efd-443c-4f23-a1b1-a662a5387879
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 1b342f0aea19c01d7bdae94552019f4c171fd1a2
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-add-reference"></a>dotnet-add reference

## <a name="name"></a>Nom

`dotnet-add reference` : ajoute des références entre projets (P2P).

## <a name="synopsis"></a>Résumé

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet. Une fois que vous avez exécuté la commande, les éléments [`<ProjectReference>`](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-items) sont ajoutés au fichier projet.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

`PROJECT`

Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actif.

`PROJECT_REFERENCES`

Références entre projets (P2P) à ajouter. Spécifiez un ou plusieurs projets. Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les systèmes Unix/Linux.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

`-f|--framework <FRAMEWORK>`

Ajoute des références de projet uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.

## <a name="examples"></a>Exemples

Ajouter une référence de projet :

`dotnet add app/app.csproj reference lib/lib.csproj`

Ajouter plusieurs références de projet :

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Ajouter plusieurs références de projet à l’aide du modèle d’utilisation des caractères génériques (globbing) sur Linux/Unix :

`dotnet add app/app.csproj reference **/*.csproj`

