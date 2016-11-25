---
title: Commande dotnet-migrate | SDK .NET Core
description: "La commande dotnet-migrate permet de migrer un projet et l’ensemble de ses dépendances."
keywords: "dotnet-migrate, CLI, commande CLI, .NET Core"
author: mairaw
manager: wpickett
ms.date: 11/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 70285a83-4103-4617-be8b-d0e1e9a4a91d
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 150d70e3f0a80f7f6e733abee3691a0fe420919f

---

#<a name="dotnet-migrate"></a>dotnet-migrate

## <a name="name"></a>Nom 
dotnet-migrate : migre un projet .NET Core Preview 2 vers un projet .NET Core Preview 3

## <a name="synopsis"></a>Résumé

`dotnet migrate [--help] [--template-file]  
    [--sdk-package-version] [--xproj-file]  
    [--skip-project-references]  [--report-file] [--format-report-file-json]
    [--skip-backup]
    [<arguments>]`

## <a name="description"></a>Description
La commande `dotnet migrate` migre un projet `project.json` Preview 2 valide vers un projet `csproj` Preview 3 valide. Par défaut, la commande migre le projet racine et toutes les références de projet qu’il contient. Ce comportement peut être désactivé à l’aide de l’option `--skip-project-references` au moment de l’exécution. 

La migration peut être effectuée sur :

* Un projet unique en spécifiant le fichier `project.json` à migrer
* Tous les répertoires spécifiés dans le fichier `global.json` en passant le chemin du fichier `global.json`
* Sur tous les sous-répertoires du répertoire donné de manière récursive 

La commande migrate conserve le fichier `project.json` migré dans un répertoire `backup`, qu’elle crée s’il n’existe pas. Cette opération peut être ignorée à l’aide de l’option `--skip-backup`. 

Par défaut, l’opération de migration affiche l’état du processus de migration dans la sortie standard (STDOUT). Si vous utilisez l’option `--report-file`, cette sortie est également enregistrée dans un fichier que vous spécifiez. 

À compter de Preview 3, la commande `dotnet migrate` prend en charge uniquement les fichiers `project.json` Preview 2 valides. Cela signifie que vous ne pouvez pas l’utiliser pour migrer des fichiers `project.json` Preview 1 ou DNX anciens vers csproj ; vous devez les migrer vers des fichiers project.json Preview 2, puis vers des fichiers csproj. À l’avenir, nous ajouterons une prise en charge pour les projets Preview 1. 

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-t|--template-file <TEMPLATE_FILE>`

Fichier csproj de modèle à utiliser pour la migration. Par défaut, le même modèle que celui déposé par `dotnet new` est utilisé. 

`-v|--sdk-package-version <VERSION>`

Version du package de SDK à référencer dans l’application migrée. La valeur par défaut est la version du SDK dans dotnet new.

`-x|--xproj-file <FILE>`

Chemin du fichier xproj à utiliser. Requis quand il existe plusieurs xproj dans un répertoire de projet.

`-s|--skip-project-references [Debug|Release]`

Ignore la migration des références de projet. Par défaut, les références de projet sont migrées de manière récursive.

`-r|--report-file <REPORT_FILE>`

Génère un rapport de migration dans un fichier, en plus de le faire dans la console.

`--format-report-file-json <REPORT_FILE>`

Génère le fichier de rapport de migration au format json plutôt que sous la forme de messages utilisateur.

`--skip-backup`

Ignore le déplacement de project.json, global.json et \*.xproj vers un répertoire `backup` après la migration.

## <a name="examples"></a>Exemples

Migrer un projet et toutes ses dépendances de projet à projet vers le répertoire actif :

`dotnet migrate`

Migrer tous les projets vers lesquels pointe le fichier `global.json` :

`dotnet migrate path/to/global.json`

Migrer uniquement le projet actuel et aucune dépendance de projet à projet et utiliser une version de SDK spécifique :

`dotnet migrate -s -v 1.0.0-preview3`




<!--HONumber=Nov16_HO3-->


