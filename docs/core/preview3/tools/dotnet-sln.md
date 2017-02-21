---
title: Commande dotnet-sln | Microsoft Docs
description: "La commande dotnet-sln offre une option pratique pour ajouter, supprimer et répertorier des projets dans un fichier solution."
keywords: "dotnet-run, CLI, commande CLI, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 02/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
translationtype: Human Translation
ms.sourcegitcommit: 6c0474e2964043b6c090ecb4e68b46ff42ca670c
ms.openlocfilehash: c5ed2482222b02b8b50599b48a28afa5922e0135

---
# <a name="dotnet-sln"></a>dotnet-sln

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>Nom

`dotnet-sln` : Modifie un fichier solution .NET Core.

## <a name="synopsis"></a>Résumé

```
dotnet sln [<SLN_NAME>] add <project> <project>
dotnet sln [<SLN_NAME>] add **/**
dotnet sln [<SLN_NAME>] remove <project> <project>
dotnet sln [<SLN_NAME>] remove **/**
dotnet sln [<SLN_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet sln` offre un moyen pratique d’ajouter, de supprimer et de répertorier des projets dans un fichier solution.

## <a name="commands"></a>Commandes

`add <project>`

`add **/*`

Ajoute un ou plusieurs projets au fichier solution. Le modèle Glob est pris en charge sur les terminaux Unix/Linux.

`remove <project>`

`remove **/*`

Supprime un ou plusieurs projets du fichier solution. Le modèle Glob est pris en charge sur les terminaux Unix/Linux.

`list`

Répertorie tous les projets dans un fichier solution.

## <a name="arguments"></a>Arguments

`SLN_NAME`

Fichier solution à utiliser. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actif. S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.

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

Ajoutez plusieurs projets à une solution en utilisant un modèle de globbing :

`dotnet sln add **/**/*.fsproj`



<!--HONumber=Feb17_HO2-->


