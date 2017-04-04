---
title: Commande dotnet-remove reference - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-remove reference est une option pratique pour supprimer des références entre projets."
keywords: dotnet-remove, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 889c6b7e-a313-40b1-9fd3-6a6f4c52f1d0
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 22db4037195afa2c49ef038832e09a99c6a0d54e
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-remove-reference"></a>dotnet-remove reference

## <a name="name"></a>Nom

`dotnet-remove reference` - Supprime des références entre projets.

## <a name="synopsis"></a>Résumé

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet remove reference` est une option pratique pour supprimer des références de projet d’un projet.

## <a name="arguments"></a>Arguments

`PROJECT`

Fichier projet cible. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

`PROJECT_REFERENCES`

Références entre projets (P2P) à supprimer. Vous pouvez spécifier un ou plusieurs projets. Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

`-f|--framework <FRAMEWORK>`

Ne supprime une référence que quand [framework](../../standard/frameworks.md) spécifique est ciblé.

## <a name="examples"></a>Exemples

Supprimer une référence de projet du projet spécifié :

`dotnet remove app/app.csproj reference lib/lib.csproj`

Supprimer plusieurs références de projet du projet dans le répertoire actuel :

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

Supprimer plusieurs références de projet à l’aide du modèle Glob sous Unix/Linux :

`dotnet remove app/app.csproj reference **/*.csproj`

