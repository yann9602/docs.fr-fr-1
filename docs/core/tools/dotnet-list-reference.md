---
title: Commande dotnet list reference - Interface CLI .NET Core
description: "La commande dotnet list reference est une option pratique pour lister des références entre projets."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: a4ceadb6d070d7997e75b472624bbe2c1650396d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet list reference` : Répertorie des références entre projets.

## <a name="synopsis"></a>Résumé

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet list reference` est une option pratique pour répertorier des références de projet pour un projet donné.

## <a name="arguments"></a>Arguments

`PROJECT`

Spécifie le fichier projet à utiliser pour répertorier les références. Si aucun fichier n’est spécifié, la commande recherche un fichier projet dans le répertoire actif.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

Lister les références de projet pour le projet spécifié :

`dotnet list app/app.csproj reference`

Lister les références de projet du projet dans le répertoire actuel :

`dotnet list reference`
