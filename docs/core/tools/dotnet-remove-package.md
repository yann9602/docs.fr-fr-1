---
title: Commande dotnet-remove package - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-remove package est une option pratique pour supprimer une référence de package NuGet d’un projet."
keywords: dotnet-remove, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2fcc8d37-16b3-4581-8038-832160e72d36
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: a321610540534a63bd12a8f878950b75e882c3d4
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-remove-package"></a>dotnet-remove package

## <a name="name"></a>Nom

`dotnet-remove package` : Supprime une référence de package d’un fichier projet.

## <a name="synopsis"></a>Résumé

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet remove package` est une option pratique pour supprimer une référence de package NuGet d’un projet.

## <a name="arguments"></a>Arguments

`PROJECT`

Spécifie le fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actif.

`PACKAGE_NAME`

Référence de package à supprimer.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

Supprime le package NuGet `Newtonsoft.Json` d’un projet dans le répertoire actuel :

`dotnet remove package Newtonsoft.Json`
