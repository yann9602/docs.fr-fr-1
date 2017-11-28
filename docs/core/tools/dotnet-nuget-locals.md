---
title: Commande dotnet nuget locals - Interface CLI .NET Core
description: "La commande dotnet nuget locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 2b66198ac3e33c640abda0c96fb05944f5ea91df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet nuget locals` - Efface ou liste les ressources NuGet locales.

## <a name="synopsis"></a>Résumé

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet nuget locals` efface ou liste les ressources NuGet locales dans le cache de requête HTTP, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.

## <a name="arguments"></a>Arguments

`CACHE_LOCATION`

Une des valeurs suivantes :

* `all` : indique que l’opération spécifiée est appliquée à tous les types de cache : le cache de requête HTTP, le cache des packages globaux et le cache temporaire.
* `http-cache` : indique que l’opération spécifiée est appliquée uniquement au cache de requête HTTP. Les autres emplacements de cache ne sont pas affectés.
* `global-packages` : indique que l’opération spécifiée est appliquée uniquement au cache des packages globaux. Les autres emplacements de cache ne sont pas affectés.
* `temp` : indique que l’opération spécifiée est appliquée uniquement au cache temporaire. Les autres emplacements de cache ne sont pas affectés.

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

Pour plus d’informations sur les problèmes et erreurs courants liés à l’utilisation de la commande `dotnet nuget locals`, consultez la page [Gestion du cache NuGet](/nuget/consume-packages/managing-the-nuget-cache).