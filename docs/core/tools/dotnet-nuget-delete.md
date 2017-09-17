---
title: Commande dotnet nuget delete - Interface CLI .NET Core
description: La commande nuget-dotnet-delete supprime ou retire un package du serveur.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 65fe52f07ed823b4f7518c5b1f2da1f7a61b0371
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet nuget delete` -Supprime ou retire un package du serveur.

## <a name="synopsis"></a>Résumé

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet nuget delete` supprime ou retire un package du serveur. Pour [nuget.org](https://www.nuget.org/), l’action consiste à supprimer le package de la liste.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Package à supprimer.

`PACKAGE_VERSION`

Version du package à supprimer.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide élémentaire de la commande.

`-s|--source <SOURCE>`

Spécifie l’URL du serveur. Les URL prises en charge pour nuget.org incluent `http://www.nuget.org`, `http://www.nuget.org/api/v3` et `http://www.nuget.org/api/v2/package`. Pour les flux privés, remplacez le nom d’hôte (par exemple, `%hostname%/api/v3`).

`--non-interactive`

Ne demande pas de saisie ou de confirmation de la part de l’utilisateur.

`-k|--api-key <API_KEY>`

Clé d’API pour le serveur.

`--force-english-output`

Oblige la sortie de la ligne de commande à être en anglais.

## <a name="examples"></a>Exemples

Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` :

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` sans inviter l’utilisateur à fournir ses informations d’identification ou d’autres données :

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
