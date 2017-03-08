---
title: Commande dotnet-nuget-delete | Microsoft Docs
description: La commande nuget-dotnet-delete supprime ou retire un package du serveur.
keywords: dotnet-nuget-delete, CLI, commande CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 2ce157e3f32f3e899245e38bb4520b17be3e0b32
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-nuget-delete"></a>dotnet-nuget-delete

## <a name="name"></a>Nom

`dotnet-nuget-delete` -Supprime ou retire un package du serveur. 

## <a name="synopsis"></a>Résumé

```
dotnet nuget delete [<package_name> <package_version>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet nuget delete` supprime ou retire un package du serveur. Pour NuGet.org, l’action consiste à supprimer le package de la liste.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-s|--source <SOURCE>`

Spécifie l’URL du serveur. Les URL prises en charge pour nuget.org incluent `http://www.nuget.org`, `http://www.nuget.org/api/v3` et `http://www.nuget.org/api/v2/package`. Pour les flux privés, remplacez le nom d’hôte (par exemple, `%hostname%/api/v3`).

`--non-interactive`

Ne demande pas de saisie ou de confirmation de la part de l’utilisateur.

`-k|--api-key <API_KEY>`

Clé d’API pour le serveur.

`--force-english-output`

Oblige la sortie de la ligne de commande à être en anglais.

## <a name="examples"></a>Exemples

Supprime la version 1.0 du package MyPackage :

`dotnet nuget delete MyPackage 1.0` 

Supprime la version 1.0 du package MyPackage sans inviter l’utilisateur à fournir ses informations d’identification ou d’autres données :

`dotnet nuget delete MyPackage 1.0 --non-interactive`

