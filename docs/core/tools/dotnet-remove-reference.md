---
title: Commande dotnet remove reference - Interface CLI .NET Core
description: "La commande dotnet remove reference est une option pratique pour supprimer des références entre projets."
keywords: dotnet-remove, CLI, commande CLI, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 7cb84c2dc7fc4d16b00bd6459132390ab80131f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet remove reference` - Supprime des références entre projets.

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
