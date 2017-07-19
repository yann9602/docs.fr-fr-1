---
title: "Télémétrie des outils .NET Core | Microsoft Docs"
description: .NET Core
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.translationtype: Human Translation
ms.sourcegitcommit: 6f3dc4235c75d7438f019838cb22192f4dc7c41a
ms.openlocfilehash: b7de81f38c0d4fa259f1c9d8ada675197930e945
ms.contentlocale: fr-fr
ms.lasthandoff: 05/30/2017

---

<a id="net-core-tools-telemetry" class="xliff"></a>

# Télémétrie des outils .NET Core

Les outils .NET Core incluent une [fonctionnalité de télémétrie](https://github.com/dotnet/cli/pull/2145) qui recueille des informations d’utilisation. Il est important pour l’équipe .NET de comprendre la façon dont les outils sont utilisés, afin de pouvoir les améliorer.

Les données collectées sont anonymes, et sont destinées à être regroupées, puis publiées par les ingénieurs Microsoft et les ingénieurs de la communauté, sous la [licence Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).

<a id="scope" class="xliff"></a>

## Portée

La commande `dotnet` permet de lancer des applications et les outils .NET Core. La commande `dotnet` ne permet pas de collecter des données de télémétrie. Ce sont les outils .NET Core, qui sont exécutés via la commande `dotnet`, qui collectent les données de télémétrie.

Commandes .NET Core (télémétrie non activée) :

- `dotnet`
- `dotnet [path-to-app]`

[Commandes](index.md) des outils .NET Core (télémétrie activée) :

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

<a id="behavior" class="xliff"></a>

## Comportement

La fonctionnalité de télémétrie des outils .NET Core est activée par défaut. Vous pouvez ne pas adhérer à la fonctionnalité de télémétrie en définissant une variable d’environnement DOTNET_CLI_TELEMETRY_OPTOUT (par exemple, `export` sous Linux/Mac OS, `set` sur Windows) sur True (par exemple, « true », 1).

<a id="data-points" class="xliff"></a>

## Points de données

La fonctionnalité recueille les données suivantes :

- La commande utilisée (par exemple, « build », « restore »)
- L’ExitCode de la commande
- Pour les projets de test, le Test Runner utilisé
- L’horodatage de l’appel
- Le framework utilisé
- Si des ID d’exécution se trouvent sous le nœud « Runtimes »
- La version CLI utilisée

La fonctionnalité ne collecte pas les informations personnelles, telles que les noms d’utilisateurs et les adresses e-mail. Elle n’analyse pas votre code et n’extrait pas de données relatives au projet qui peuvent être considérées comme sensibles, telles que le nom, le dépôt ou l’auteur (si ceux-ci ont été définis dans votre project.json). Nous souhaitons savoir comment vous utilisez les outils, et non ce que vous créez avec les outils. Si vous vous rendez compte que des données sensibles ont été collectées, il s’agit d’un bogue. Dans ce cas, [signalez le problème](https://github.com/dotnet/cli/issues) pour que celui-ci soit résolu.

<a id="license" class="xliff"></a>

## Licence

La distribution Microsoft de .NET Core est concédée sous licence avec le [CLUF de la BIBLIOTHÈQUE .NET MICROSOFT](https://aka.ms/dotnet-core-eula). Celui-ci comprend la section « DATA » ci-dessous, qui permet d’activer la télémétrie.

Les [packages NuGet .NET](https://www.nuget.org/profiles/dotnetframework) utilisent la même licence, mais ne permettent pas la télémétrie (voir la section [Portée](#scope) ci-dessus).

> 2. DONNÉES. Le logiciel peut collecter des informations sur vous et votre utilisation du logiciel et les envoyer à Microsoft. Microsoft peut utiliser ces informations pour améliorer ses produits et services. Vous pouvez en savoir plus sur la collecte et l’utilisation des données dans la documentation d’aide et la déclaration de confidentialité http://go.microsoft.com/fwlink/?LinkId=528096. Votre utilisation du logiciel est considérée comme votre acceptation de ces pratiques.

<a id="disclosure" class="xliff"></a>

## Divulgation d’informations

Les outils .NET Core affichent le texte suivant lorsque vous exécutez une commande pour la première fois (par exemple, `dotnet restore`). Lors de cette première exécution, Microsoft vous informe sur la collecte de données. C’est à ce moment-là que votre cache NuGet est alimenté avec les bibliothèques du SDK .NET Core, ce qui vous évite d’avoir à recourir à NuGet.org (ou autres flux NuGet) pour obtenir ces bibliothèques.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience.
The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.

Configuring...
-------------------
A command is running to initially populate your local package cache, to improve restore speed and enable offline access. This command will take up to a minute to complete and will only happen once.
```

