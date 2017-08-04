---
title: Commande dotnet-run - Interface CLI .NET Core
description: "La commande dotnet-run fournit une option pratique pour exécuter votre application à partir du code source."
keywords: "dotnet-run, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f0a6fce4f83808076b7cbcabdaa948badde2cf80
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-run"></a>dotnet-run

## <a name="name"></a>Nom 

`dotnet-run` - Exécute le code source sans commandes explicites de compilation ou de démarrage.

## <a name="synopsis"></a>Résumé

`dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande. Elle est utile pour le développement itératif rapide en ligne de commande. Elle dépend de la commande [`dotnet build`](dotnet-build.md) pour générer le code. Les conditions requises pour la génération, par exemple le fait que le projet doit être restauré en premier, s’appliquent également à `dotnet run`. 

Les fichiers de sortie sont écrits dans l’emplacement par défaut, à savoir `bin/<configuration>/<target>`. Par exemple, si vous avez une application `netcoreapp1.0` et que vous exécutez `dotnet run`, la sortie est placée dans `bin/Debug/netcoreapp1.0`. Les fichiers sont remplacés, si nécessaire. Les fichiers temporaires sont placés dans le répertoire `obj`. 

Si le projet spécifie plusieurs frameworks, l’exécution de `dotnet run` entraîne une erreur, sauf si l’option `-f|--framework <FRAMEWORK>` est utilisée pour spécifier le framework.

La commande `dotnet run` est utilisée pour des projets, et pas pour des assemblys générés. Si vous tentez d’exécuter plutôt une DLL d’applications dépendantes du framework, vous devez utiliser [dotnet](dotnet.md) sans commande. Par exemple, pour exécuter `myapp.dll`, utilisez :
 
```
dotnet myapp.dll
```

Pour plus d’informations sur le pilote `dotnet`, consultez la rubrique [Outils en ligne de commande (CLI) .NET Core](index.md).

Pour exécuter l’application, la commande `dotnet run` résout les dépendances de l’application externes au runtime partagé à partir du cache NuGet. Dans la mesure où elle utilise la mise en cache des dépendances, il n’est pas recommandé d’utiliser `dotnet run` pour exécuter des applications en production. [Créez plutôt un déploiement](../deploying/index.md) à l’aide de la commande [`dotnet publish`](dotnet-publish.md) et déployez le résultat publié. 

## <a name="options"></a>Options

`--`

Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution. Tous les arguments après celui-ci sont passés à l’application exécutée. 

`-h|--help`

Affiche une aide brève pour la commande.

`-c|--configuration <CONFIGURATION>`

Configuration à utiliser pour générer le projet. La valeur par défaut est `Debug`.

`-f|--framework <FRAMEWORK>`

Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié. Le framework doit être spécifié dans le fichier projet.

`-p|--project <PATH/PROJECT.csproj>`

Spécifie le chemin d’accès et le nom du fichier projet. (Voir la REMARQUE.) Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

> [!NOTE]
> Utilisez le chemin d’accès et le nom du fichier projet avec l’option `-p|--project`. Une régression dans l’interface CLI empêche de fournir un chemin d’accès de dossier pour l’instant. Pour plus d’informations et pour suivre ce problème, consultez la page [dotnet run -p, impossible de démarrer un projet (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).

## <a name="examples"></a>Exemples

Exécutez le projet dans le répertoire actif :

`dotnet run` 

Exécutez le projet spécifié :

`dotnet run --project /projects/proj1/proj1.csproj`

Exécuter le projet situé dans le répertoire actif (l’argument `--help` de cet exemple est passé à l’application, puisque l’argument `--` est utilisé) :

`dotnet run --configuration Release -- --help`

