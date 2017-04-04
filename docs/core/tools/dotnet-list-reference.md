---
title: Commande dotnet-list reference - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-list reference est une option pratique pour répertorier des références entre projets."
keywords: dotnet-list, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8f954a0c-03f8-4fbc-a529-b313ab12c623
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: fdaf2a6f66801be68507ccabe7e0f2fea5433e65
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-list-reference"></a>dotnet-list reference

## <a name="name"></a>Nom

`dotnet-list reference` : Répertorie des références entre projets.

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

