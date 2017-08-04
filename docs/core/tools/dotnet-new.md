---
title: Commande dotnet-new - Interface CLI .NET Core
description: "La commande dotnet-new crée de nouveaux projets .NET Core dans le répertoire actif."
keywords: "dotnet-new, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 56033295b2448b045d5a51dbd84d5429aed77451
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-new"></a>dotnet-new

## <a name="name"></a>Nom

`dotnet-new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.

## <a name="synopsis"></a>Résumé

```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide. 

La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Modèle à instancier quand la commande est appelée. Vous pouvez passer des options spécifiques pour chaque modèle. Pour plus d'informations, consultez [Options de modèle](#template-options).

La commande contient une liste par défaut de modèles. Utilisez `dotnet new -all` pour obtenir une liste des modèles disponibles. Le tableau suivant présente les modèles préinstallés avec le SDK. Le langage par défaut pour le modèle est indiqué entre crochets.

|Description du modèle  | Nom du modèle  | Langages |
|----------------------|----------------|-----------|
| Application console  | console        | [C#], F#  |
| Bibliothèque de classes        | classlib       | [C#], F#  |
| Projet de test unitaire    | mstest         | [C#], F#  |
| Projet de test xUnit   | xunit          | [C#], F#  |
| ASP.NET Core vide   | web            | [C#]      |
| Application web ASP.NET Core | mvc            | [C#], F#  |
| API web ASP.NET Core | webapi         | [C#]      |
| Config NuGet         | nugetconfig    |           |
| config web           | webconfig      |           |
| Fichier solution        | sln            |           |

## <a name="options"></a>Options

`-h|--help`

Affiche l’aide pour la commande. Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.

`-l|--list`

Liste les modèles contenant le nom spécifié. Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné. Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.

`-lang|--language {C#|F#}`

Langage du modèle à créer. Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)). Non valide pour certains modèles.

`-n|--name <OUTPUT_NAME>`

Le nom de la sortie créée. Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.

`-o|--output <OUTPUT_DIRECTORY>`

Emplacement où placer la sortie générée. La valeur par défaut correspond au répertoire actif.

`-all|--show-all`

Affiche tous les modèles pour un type de projet spécifique lors de l’exécution dans le contexte de la commande `dotnet new` seule. Lors de l’exécution dans le contexte d’un modèle spécifique, comme `dotnet new web -all`, `-all` est interprété comme un indicateur de création forcée. Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.

## <a name="template-options"></a>Options de modèle

Chaque modèle de projet peut présenter d’autres options disponibles. Les modèles de base ont les options suivantes :

**console, xunit, mstest, web, webapi**

`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp1.0` ou `netcoreapp1.1` (valeur par défaut : `netcoreapp1.0`)

**mvc**

`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp1.0` ou `netcoreapp1.1` (`Default: netcoreapp1.0`)

`-au|--auth` : type d’authentification à utiliser. Valeurs : `None` ou `Individual` (valeur par défaut : `None`)

`-uld|--use-local-db` : spécifie s’il convient ou non d’utiliser LocalDB au lieu de SQLite. Valeurs : `true` ou `false` (valeur par défaut : `false`)

**classlib**

`-f|--framework` : spécifie le [framework](../../standard/frameworks.md) à cibler. Valeurs : `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` à `netstandard1.6` (valeur par défaut : `netstandard1.4`)

## <a name="examples"></a>Exemples

Créez un projet d’application console F# dans le répertoire actif :

`dotnet new console -lang f#` 
   
Créez un projet d’application ASP.NET Core C# MVC dans le répertoire actif sans authentification ciblant .NET Core 1.0 :  

`dotnet new mvc -au None -f netcoreapp1.0`
 
Créez une application xUnit ciblant .NET Core 1.1 :

`dotnet new xunit --framework netcoreapp1.1`

Répertoriez tous les modèles disponibles pour MVC :

`dotnet new mvc -l`

