---
title: Commande dotnet-add reference - Interface CLI .NET Core
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 98491efc183ad62f47275d0832a32dde5899373d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-add-reference"></a>dotnet-add reference

## <a name="name"></a>Nom

`dotnet-add reference` : ajoute des références entre projets (P2P).

## <a name="synopsis"></a>Résumé

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet. Une fois que vous avez exécuté la commande, les éléments [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) sont ajoutés au fichier projet.

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

