---
title: Commande dotnet-nuget-locals | Microsoft Docs
description: "La commande dotnet-nuget-locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur."
keywords: dotnet-nuget-locals, CLI, commande CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 3d8ca57c3c9c25a59b98552784b057182c9100a3
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-nuget-locals"></a>dotnet-nuget-locals

## <a name="name"></a>Nom

`dotnet-nuget-locals` - Efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur. 

## <a name="synopsis"></a>Résumé

```
dotnet nuget locals <cache_location> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

Où `<cache_location>` peut avoir l’une des valeurs suivantes : `all`, `http-cache`, `packages-cache`, `global-packages` ou `temp`.

## <a name="description"></a>Description

La commande `dotnet nuget locals` efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.

## <a name="arguments"></a>Arguments

`all`

Indique que l’opération spécifiée doit être appliquée à tous les types de cache, à savoir, le cache de requête http, le cache des packages globaux et le cache temporaire.

`http-cache`

Indique que l’opération spécifiée doit être appliquée uniquement au cache de requête http. Les autres emplacements de cache ne sont pas affectés.

`global-packages`

Indique que l’opération spécifiée doit être appliquée uniquement au cache des packages globaux. Les autres emplacements de cache ne sont pas affectés.

`temp`

Indique que l’opération spécifiée doit être appliquée uniquement au cache temporaire. Les autres emplacements de cache ne sont pas affectés.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-c|--clear`

L’option clear est utilisée pour effectuer une opération d’effacement sur le type de cache spécifié. Le contenu des répertoires de cache est supprimé de manière récursive. Pour que l’opération réussisse, le groupe ou l’utilisateur qui l’effectue doit disposer de droits sur les fichiers des répertoires de cache. Sinon, une erreur est affichée, indiquant les fichiers ou dossiers qui n’ont pas été effacés.

`-l|--list`

L’option list est utilisée pour afficher l’emplacement du type de cache spécifié. 

`--force-english-output`

Oblige la sortie de la ligne de commande à être en anglais.

## <a name="examples"></a>Exemples

Affiche les chemins de tous les répertoires de cache local, à savoir, le répertoire du cache http, le répertoire du cache des packages globaux et le répertoire du cache temporaire.

`dotnet nuget locals –l all`

Affiche le chemin du répertoire du cache http local :

`dotnet nuget locals --list http-cache`

Efface tous les fichiers de tous les répertoires de cache local, à savoir, le répertoire du cache http, le répertoire du cache des packages globaux et le répertoire du cache temporaire.

`dotnet nuget locals --clear all`

Efface tous les fichiers du répertoire du cache des packages globaux local :

`dotnet nuget locals -c global-packages`

Efface tous les fichiers du répertoire du cache temporaire local :

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>Résolution des problèmes

Pour plus d’informations sur les problèmes et erreurs les plus courants pendant l’utilisation de la commande `dotnet-nuget-locals`, consultez [Managing the NuGet cache](https://docs.microsoft.com/nuget/consume-packages/managing-the-nuget-cache) (Gestion du cache NuGet).

