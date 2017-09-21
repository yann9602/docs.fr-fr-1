---
title: Commande dotnet remove package - Interface CLI .NET Core
description: "La commande dotnet remove package est une option pratique pour supprimer une référence de package NuGet d’un projet."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 4167f5465571259975572669e27f20c586b910da
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-remove-package"></a>dotnet remove package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet remove package` : Supprime une référence de package d’un fichier projet.

## <a name="synopsis"></a>Résumé

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet remove package` est une option pratique pour supprimer une référence de package NuGet d’un projet.

## <a name="arguments"></a>Arguments

`PROJECT`

Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actif.

`PACKAGE_NAME`

Référence de package à supprimer.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide élémentaire de la commande.

## <a name="examples"></a>Exemples

Supprime le package NuGet `Newtonsoft.Json` d’un projet dans le répertoire actuel :

`dotnet remove package Newtonsoft.Json`

