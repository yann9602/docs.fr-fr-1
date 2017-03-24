---
title: "Outils de l’interface de ligne de commande (CLI) .NET Core │ Microsoft Docs"
description: "Présentation de l’interface de ligne de commande (CLI) et de ses principales fonctionnalités"
keywords: "CLI, outils CLI, .NET, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 7c5eee9f-d873-4224-8f5f-ed83df329a59
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 4e3137d8506342662d145481d5e9fde1d53b9ba3
ms.lasthandoff: 03/13/2017

---

# <a name="net-core-command-line-interface-tools-net-core-sdk-10-tools"></a>Outils de l’interface de ligne de commande .NET Core (outils SDK .NET Core 1.0)

L’interface de ligne de commande (CLI) de .NET Core est une nouvelle chaîne d’outils multiplateforme fondamentale pour le développement d’applications .NET Core. Elle est dite « de fondation », car il s’agit de la couche principale sur laquelle les autres outils de niveau supérieur, tels que les environnements de développement intégré (IDE), les éditeurs et les orchestrateurs de builds, peuvent se baser. 

Elle est également multiplateforme par défaut et sa surface est la même sur toutes les plateformes prises en charge. Cela signifie que vous pouvez les utiliser de la même façon sur toutes les plateformes prises en charge. 

## <a name="installation"></a>Installation
Comme pour n’importe quel ensemble d’outils, la première étape consiste à se procurer les outils sur l’ordinateur. Selon le cas, vous pouvez utiliser les programmes d’installation natifs pour installer les outils CLI ou utiliser le script de l’interpréteur de commandes d’installation.

Les programmes d’installation natifs s’adressent principalement aux ordinateurs des développeurs. Les outils CLI sont distribués selon le mécanisme d’installation natif de chaque plateforme prise en charge, par exemple des packages DEB sur Ubuntu ou des ensembles MSI sur Windows. Ces programmes d’installation installent et configurent l’environnement comme il se doit pour permettre à l’utilisateur d’utiliser les outils CLI immédiatement après l’installation. Cependant, ils nécessitent aussi de disposer de privilèges d’administration sur l’ordinateur. Vous pouvez consulter les instructions d’installation dans la [page de prise en main de .NET Core](https://aka.ms/dotnetcoregs).

Les scripts d’installation, quant à eux, ne nécessitent pas de privilèges d’administration. En revanche, ils n’installent pas les prérequis sur l’ordinateur ; vous devez tous les installer manuellement. Les scripts visent principalement à configurer les serveurs de builds et permettent d’installer les outils sans privilèges d’administration (notez les mises en garde concernant les prérequis répertoriés ci-dessus). Vous trouverez des informations complémentaires dans la [rubrique de référence sur les scripts d’installation](dotnet-install-script.md). Pour savoir comment configurer les outils CLI sur votre serveur de builds avec intégration continue, consultez la rubrique [Outils CLI et serveurs d’intégration continue](using-ci-with-cli.md). 

Par défaut, les outils CLI sont installés « côte à côte ». Cela signifie que plusieurs versions des outils CLI peuvent coexister à un moment donné sur un même ordinateur. La façon dont la version appropriée est utilisée est expliquée plus en détail dans la section [Pilote](#driver). 

### <a name="what-commands-come-in-the-box"></a>Quelles sont les commandes fournies ?
Les commandes suivantes sont installées par défaut :

* [new](dotnet-new.md)
* [migrate](dotnet-migrate.md)
* [restore](dotnet-restore.md)
* [run](dotnet-run.md)
* [build](dotnet-build.md)
* [test](dotnet-test.md)
* [publish](dotnet-publish.md)
* [pack](dotnet-pack.md)

Il existe également un moyen d’importer davantage de commandes pour chaque projet et d’ajouter vos propres commandes. Vous en trouverez une explication détaillée dans la [section relative à l’extensibilité](#extensibility). 

## <a name="working-with-the-cli"></a>Utilisation des outils CLI

Avant de rentrer dans les détails, voyons comment utiliser les outils CLI. L’exemple suivant utilise plusieurs commandes de l’installation standard des outils CLI pour initialiser une application console simple, restaurer les dépendances, générer l’application, puis l’exécuter. 

```console
dotnet new console
dotnet restore
dotnet build --output /stuff
dotnet /stuff/new.dll
```

Comme vous pouvez le voir dans l’exemple précédent, l’utilisation des outils CLI suit un modèle. Dans ce modèle, nous pouvons identifier les trois parties principales de chaque commande :

1. [Le pilote (« dotnet »)](#driver)
2. [La commande, ou « verbe »](#the-verb)
3. [Les arguments de la commande](#the-arguments)

### <a name="driver"></a>Pilote
Le pilote s’appelle [dotnet](dotnet.md). Il s’agit de la première partie de ce que vous appelez. Le pilote est chargé de deux choses :

1. L’exécution des applications portables
2. L’exécution du verbe

Son action dépend de ce qui est spécifié sur la ligne de commande. Dans le premier cas, vous devez spécifier une DLL d’application portable que `dotnet` exécute comme ceci : `dotnet /path/to/your.dll`. 

Dans le deuxième cas, le pilote tente d’appeler la commande spécifiée. Cela démarre alors le processus d’exécution de la commande CLI. D’abord, le pilote détermine la version des outils que vous souhaitez. Vous pouvez spécifier la version dans le fichier [global.json](global-json.md) à l’aide de la propriété `version`. S’il n’est pas disponible, le pilote recherche la dernière version des outils qui est installée sur le disque, et utilise cette version. Une fois que la version est déterminée, il exécute la commande. 

### <a name="the-verb"></a>Le « verbe »
Le verbe est une commande qui exécute une action. `dotnet build` génère le code. `dotnet publish` publie le code. Le verbe est implémenté comme une application console qui est nommée `dotnet-{verb}`, conformément à la convention. Toute la logique est implémentée dans l’application console qui représente le verbe. 

### <a name="the-arguments"></a>Les arguments
Les arguments que vous passez sur la ligne de commande sont les arguments du verbe ou de la commande appelé(e). Par exemple, lorsque vous tapez `dotnet publish --output publishedapp`, l’argument `--output` est passé à la commande `publish`. 

## <a name="types-of-application-portability"></a>Types de portabilité des applications
Les outils CLI permettent aux applications d’être portables principalement de deux manières :

1. Avec des applications entièrement portables pouvant s’exécuter là où .NET Core est installé
2. Avec des déploiements autonomes

Pour plus d’informations sur ces deux méthodes, consultez la rubrique [Déploiement d’applications .NET Core](../deploying/index.md). 

## <a name="migration-from-projectjson"></a>Migration à partir de project.json
Si vous avez utilisé les outils Preview 2 et des projets *project.json*, vous pouvez consulter la documentation sur la commande [dotnet migrate](dotnet-migrate.md) pour vous familiariser avec la commande et la migration de votre projet. 

> [!NOTE]
> La commande `dotnet migrate` ne migre pas les fichiers *project.json* antérieurs à Preview 2. 

## <a name="extensibility"></a>Extensibilité
Bien sûr, tous les outils que vous utilisiez précédemment ne font pas partie des outils CLI. Toutefois, les outils CLI .NET Core possèdent un modèle d’extensibilité qui vous permet de spécifier des outils supplémentaires pour vos projets. Pour plus d’informations, consultez la rubrique [Modèle d’extensibilité des outils CLI .NET Core](extensibility.md).

## <a name="summary"></a>Résumé
Vous venez de voir une brève présentation des principales fonctionnalités des outils CLI. Pour plus d’informations, consultez les rubriques de référence et les rubriques conceptuelles de ce site. D’autres ressources sont également disponibles :
* Dépôt GitHub [dotnet/CLI](https://github.com/dotnet/cli/)
* [Instructions pour bien démarrer](https://aka.ms/dotnetcoregs/)

