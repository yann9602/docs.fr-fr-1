---
title: Commande dotnet-sln - CLI .NET Core | Microsoft Docs
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
keywords: dotnet-sln, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 04/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
ms.translationtype: Human Translation
ms.sourcegitcommit: 7d7f0864ee1641627c4a55192d81ed76f2f44450
ms.openlocfilehash: 0a832765d01609aebd10b13387a4317a6a246c30
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---

# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>Nom

`dotnet-sln` : Modifie un fichier solution .NET Core.

## <a name="synopsis"></a>Résumé

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet sln` offre un moyen pratique d’ajouter, de supprimer et de lister des projets dans un fichier solution.

## <a name="commands"></a>Commandes

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Ajoute un ou plusieurs projets au fichier solution. Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

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

Ajouter un projet C# à une solution :

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Supprimer un projet C# d’une solution :

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Ajouter plusieurs projets C# à une solution :

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Supprimer plusieurs projets C# d’une solution :

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Ajouter plusieurs projets C# à une solution avec un modèle d’utilisation des caractères génériques :

`dotnet sln todo.sln add **/*.csproj`

Supprimer plusieurs projets C# d’une solution avec un modèle d’utilisation des caractères génériques :

`dotnet sln todo.sln remove **/*.csproj`

