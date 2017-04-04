---
title: Commande dotnet-nuget-locals - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-nuget-locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur."
keywords: dotnet-nuget-locals, CLI, commande CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: d0acfaa6ff1a11f49a0d3751b675ea94bd6ae3a3
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-nuget-locals"></a>dotnet-nuget locals

## <a name="name"></a>Nom

`dotnet-nuget locals` - Efface ou liste les ressources NuGet locales. 

## <a name="synopsis"></a>Résumé

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet nuget locals` efface ou liste les ressources NuGet locales dans le cache de requête HTTP, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.

## <a name="arguments"></a>Arguments

`CACHE_LOCATION`

Une des valeurs suivantes :

`all`

Indique que l’opération spécifiée est appliquée à tous les types de cache : le cache de requête HTTP, le cache des packages globaux et le cache temporaire.

`http-cache`

Indique que l’opération spécifiée est appliquée uniquement au cache de requête HTTP. Les autres emplacements de cache ne sont pas affectés.

`global-packages`

Indique que l’opération spécifiée est appliquée uniquement au cache des packages globaux. Les autres emplacements de cache ne sont pas affectés.

`temp`

Indique que l’opération spécifiée est appliquée uniquement au cache temporaire. Les autres emplacements de cache ne sont pas affectés.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-c|--clear`

L’option clear effectue une opération d’effacement sur le type de cache spécifié. Le contenu des répertoires de cache est supprimé de manière récursive. Le groupe ou l’utilisateur qui effectue l’opération doit disposer de droits sur les fichiers des répertoires de cache. Sinon, une erreur s’affiche, indiquant les fichiers ou dossiers qui n’ont pas été effacés.

`-l|--list`

L’option list est utilisée pour afficher l’emplacement du type de cache spécifié. 

`--force-english-output`

Oblige la sortie de la ligne de commande à être en anglais.

## <a name="examples"></a>Exemples

Afficher les chemins d’accès de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :

`dotnet nuget locals –l all`

Affiche le chemin du répertoire du cache http local :

`dotnet nuget locals --list http-cache`

Effacer tous les fichiers de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :

`dotnet nuget locals --clear all`

Effacer tous les fichiers du répertoire du cache des packages globaux local :

`dotnet nuget locals -c global-packages`

Effacer tous les fichiers du répertoire du cache temporaire local :

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>Résolution des problèmes

Pour plus d’informations sur les problèmes et erreurs courants liés à l’utilisation de la commande `dotnet nuget locals`, consultez la page [Gestion du cache NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-nuget-cache).

