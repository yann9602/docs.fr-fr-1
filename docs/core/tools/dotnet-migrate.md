---
title: Commande dotnet-migrate - Interface CLI .NET Core
description: "La commande dotnet-migrate permet de migrer un projet et l’ensemble de ses dépendances."
keywords: "dotnet-migrate, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0da07253-5ae1-42e9-9455-bffee9950952
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e8491d69b2e0df7b3bd2741e34abdb9631777019
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-migrate"></a>dotnet-migrate

## <a name="name"></a>Nom

`dotnet-migrate` : migre un projet .NET Core Preview 2 vers un projet SDK .NET Core 1.0.

## <a name="synopsis"></a>Résumé

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet migrate` migre un projet *project.json* Preview 2 valide vers un projet *csproj* SDK .NET Core 1.0 valide. 

Par défaut, la commande migre le projet racine et toutes les références de projet qu’il contient. Ce comportement peut être désactivé à l’aide de l’option `--skip-project-references` au moment de l’exécution. 

La migration est effectuée sur les éléments suivants :

* Un projet unique en spécifiant le fichier *project.json* à migrer.
* Tous les répertoires spécifiés dans le fichier *global.json* en passant un chemin du fichier *global.json*.
* Un fichier *solution.sln*, où il migre les projets référencés dans la solution.
* Sur tous les sous-répertoires du répertoire donné de manière récursive.

La commande `dotnet migrate` conserve le fichier *project.json* migré dans un répertoire `backup`, qu’elle crée s’il n’existe pas. Ce comportement peut être ignoré à l’aide de l’option `--skip-backup`. 

Par défaut, l’opération de migration affiche l’état du processus de migration dans la sortie standard (STDOUT). Si vous utilisez l’option `--report-file <REPORT_FILE>`, la sortie est enregistrée dans le fichier spécifié. 

La commande `dotnet migrate` prend en charge uniquement les projets *project.json* Preview 2 valides. Cela signifie que vous ne pouvez pas l’utiliser pour migrer des projets *project.json* DNX ou Preview 1 directement vers des projets MSBuild/csproj. Vous devez tout d’abord migrer manuellement le projet vers un projet *project.json* Preview 2, puis utiliser la commande `dotnet migrate` pour migrer le projet.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Le chemin d’accès à l’un des éléments suivants :

* Un fichier *project.json* à migrer.
* Un fichier *global.json*, il migre les dossiers spécifiés vers *global.json*.
* Un fichier *solution.sln*, il migre les projets référencés dans la solution.
* Un répertoire à migrer, il recherche de manière récursive les fichiers *project.json* à migrer.

Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-t|--template-file <TEMPLATE_FILE>`

Fichier csproj de modèle à utiliser pour la migration. Par défaut, le même modèle que celui déposé par `dotnet new console` est utilisé. 

`-v|--sdk-package-version <VERSION>`

Version du package de SDK à référencer dans l’application migrée. La valeur par défaut est la version du SDK dans `dotnet new`.

`-x|--xproj-file <FILE>`

Chemin du fichier xproj à utiliser. Requis quand il existe plusieurs xproj dans un répertoire de projet.

`-s|--skip-project-references [Debug|Release]`

Ignore la migration des références de projet. Par défaut, les références de projet sont migrées de manière récursive.

`-r|--report-file <REPORT_FILE>`

Génère un rapport de migration dans un fichier, en plus de le faire dans la console.

`--format-report-file-json <REPORT_FILE>`

Génère le fichier de rapport de migration au format JSON plutôt que sous la forme de messages utilisateur.

`--skip-backup`

Ignore le déplacement de *project.json*, *global.json* et *\*.xproj* vers un répertoire `backup` après la migration.

## <a name="examples"></a>Exemples

Migrer un projet et toutes ses dépendances de projet à projet vers le répertoire actif :

`dotnet migrate`

Migrer tous les projets que le fichier *global.json* contient :

`dotnet migrate path/to/global.json`

Migrer uniquement le projet actuel et aucune dépendance de projet à projet (P2P). En outre, utilisez une version de Kit de développement logiciel (SDK) spécifique :

`dotnet migrate -s -v 1.0.0-preview4`

