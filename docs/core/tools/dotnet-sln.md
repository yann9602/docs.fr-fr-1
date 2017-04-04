---
title: Commande dotnet-sln - CLI .NET Core | Microsoft Docs
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
keywords: dotnet-sln, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 2cdfd02f7735b106fde910b8906ba4dfae860952
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>Nom

`dotnet-sln` : Modifie un fichier solution .NET Core.

## <a name="synopsis"></a>Résumé

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add **/**
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove **/**
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet sln` offre un moyen pratique d’ajouter, de supprimer et de lister des projets dans un fichier solution.

## <a name="commands"></a>Commandes

`add <PROJECT> ...`

`add **/*`

Ajoute un ou plusieurs projets au fichier solution. Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.

`remove <PROJECT> ...`

`remove **/*`

Supprime un ou plusieurs projets du fichier solution. Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.

`list`

Liste tous les projets dans un fichier solution.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Fichier solution à utiliser. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel. S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

Ajoutez un projet à une solution :

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Ajoutez un projet à la solution dans le répertoire actif :

`dotnet sln add todo-app.csproj`

Supprimez un projet d’une solution :

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Ajouter plusieurs projets à une solution en utilisant un modèle Globbing :

`dotnet sln add **/**/*.fsproj`

