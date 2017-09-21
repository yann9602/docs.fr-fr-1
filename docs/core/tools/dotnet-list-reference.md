---
title: Commande dotnet list reference - Interface CLI .NET Core
description: "La commande dotnet list reference est une option pratique pour lister des références entre projets."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

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

Affiche une aide élémentaire de la commande.

## <a name="examples"></a>Exemples

Lister les références de projet pour le projet spécifié :

`dotnet list app/app.csproj reference`

Lister les références de projet du projet dans le répertoire actuel :

`dotnet list reference`

