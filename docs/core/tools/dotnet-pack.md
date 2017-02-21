---
title: Commande dotnet-pack | Microsoft Docs
description: "La commande dotnet-pack crée des packages NuGet pour votre projet .NET Core."
keywords: "dotnet-pack, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8b4b8cef-f56c-4a10-aa01-fde8bfaae53e
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: d439dc83cc4538b44634197f3dce1bf7ad2ad6c7

---

#<a name="dotnet-pack"></a>dotnet-pack

> [!WARNING]
> Cette rubrique s'applique aux outils .NET Core Preview 2. Pour la version RC4 des outils .NET Core, consultez la rubrique [dotnet-pack (outils .NET Core RC4)](../preview3/tools/dotnet-pack.md).

## <a name="name"></a>Nom

`dotnet-pack` : Place le code dans un package NuGet.

## <a name="synopsis"></a>Résumé

`dotnet pack [--help] [--output]  
    [--no-build] [--build-base-path]  
    [--configuration]  [--version-suffix]
    [project]`  

## <a name="description"></a>Description

La commande `dotnet pack` génère le projet et crée les packages NuGet. Cette opération entraîne la création de deux packages avec l’extension `nupkg`. L’un d’eux contient le code et l’autre contient les symboles de débogage. 

Les dépendances NuGet du projet empaqueté sont ajoutées dans le fichier nuspec, pour pouvoir être résolues lorsque le package est installé. Les références entre projets ne sont pas empaquetées à l’intérieur du projet. Vous devez disposer d’un package par projet si vous avez des dépendances entre projets.

`dotnet pack` par défaut, génère d’abord le projet. Pour éviter ce problème, passez l’option `--no-build`. Cela peut être utile dans les scénarios de build d’intégration continue, pour lesquels vous savez que le code vient d’être créé, par exemple. 

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`[project]` 
    
Projet à empaqueter. Il peut s’agir du chemin d’un fichier [project.json](project-json.md) ou d’un répertoire. Si aucune valeur n’est spécifiée, le répertoire actif est choisi par défaut. 

`-o|--output <OUTPUT_DIRECTORY>`

Place les packages générés dans le répertoire spécifié. 

`--no-build`

Ne génère pas le projet avant de créer le package. 

`--build-base-path`

Place les artefacts de build temporaires dans le répertoire spécifié. Par défaut, ils sont placés dans le répertoire `obj` du répertoire actif. 

`-c|--configuration <Debug|Release>`

Configuration à utiliser lors de la génération du projet. Si aucune valeur n’est spécifiée, la valeur utilisée par défaut sera `Debug`.

`--version-suffix`

Remplace l’étoile du suffixe de version de package `-*` par une chaîne spécifiée.

## <a name="examples"></a>Exemples

Empaquetez le projet dans le répertoire actif :

`dotnet pack`

Empaquetez le projet app1 :

`dotnet pack ~/projects/app1/project.json`
    
Empaquetez le projet dans le répertoire actif et placez les packages résultants dans le dossier spécifié :

`dotnet pack --output nupkgs`

Empaquetez le projet dans le répertoire actif du dossier spécifié et ignorez l’étape de génération :

`dotnet pack --no-build --output nupkgs`

Empaquetez le projet en cours et mettez à jour la version des packages obtenus avec le suffixe donné. Par exemple, la version `1.0.0-*` sera remplacée par `1.0.0-ci-1234`.

`dotnet pack --version-suffix "ci-1234"`


<!--HONumber=Feb17_HO2-->


