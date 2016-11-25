---
title: Commande dotnet-run | SDK .NET Core
description: "La commande dotnet-run fournit une option pratique pour exécuter votre application à partir du code source."
keywords: "dotnet-run, CLI, commande CLI, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 495ff50b-cb30-4d30-8f20-beb3d5e7c31f
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 6f95125640e7341426c3a019771a6b8595d10e73

---

#<a name="dotnet-run"></a>dotnet-run

## <a name="name"></a>Nom 

dotnet-run -- exécute le code source « sur place » sans commandes explicites de compilation ou de démarrage

## <a name="synopsis"></a>Résumé

`dotnet run [--help] [--framework] [--configuration]
    [--project] [[--] [application arguments]]`

## <a name="description"></a>Description
La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande. Elle compile le code source, génère une sortie de programme, puis exécute ce programme. Cette commande est utile pour le développement itératif rapide et peut également être utilisée pour exécuter un programme distribué par la source (par exemple, un site web).

Cette commande repose sur [dotnet build](dotnet-build.md) pour générer des entrées sources dans un assembly .NET, avant de démarrer le programme. Les exigences de cette commande et de la gestion des entrées sources sont toutes héritées de la commande de génération. La documentation concernant la commande de génération fournit davantage d’informations sur ces exigences.

Les fichiers de sortie sont écrits dans le dossier *bin* enfant, qui est créé s’il n’en existe pas déjà un. Les fichiers seront remplacés, si nécessaire. Les fichiers temporaires sont écrits dans le dossier *obj* enfant.  

Dans le cas d’un projet avec plusieurs frameworks spécifiés, `dotnet run` sélectionne d’abord les frameworks .NET Core. Si aucun de ces frameworks n’est trouvé, une erreur est générée. Pour spécifier d’autres frameworks, utilisez l’argument `--framework`.

La commande `dotnet run` doit être utilisée pour des projets, et pas pour des assemblys générés. Si vous souhaitez exécuter une DLL d’application portable à la place, vous devez utiliser [dotnet](dotnet.md) sans aucune commande, comme dans l’exemple suivant :
 
`dotnet myapp.dll`

Pour plus d’informations sur le pilote `dotnet`, consultez la rubrique [Outils en ligne de commande .NET Core](index.md).

## <a name="options"></a>Options

`--`

Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution. Tous les arguments après celui-ci sont passés à l’application en cours d’exécution. 

`-h|--help`

Affiche une aide brève pour la commande.

`-f`, `--framework <FRAMEWORK_IDENTIFIER>`

Exécute l’application pour un identificateur de framework donné. 

`-c`, `--configuration <Debug|Release>`

Configuration à utiliser lors de la publication. La valeur par défaut est `Debug`.

`-p`, `--project [PATH]`

Spécifie le projet à exécuter. Il peut s’agir du chemin d’un fichier [csproj](csproj.md) ou d’un répertoire concernant un fichier [csproj](csproj.md). Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut. 

## <a name="examples"></a>Exemples

Exécutez le projet dans le répertoire actif : `dotnet run` 

Exécutez le projet spécifié :

`dotnet run --project /projects/proj1/proj1.csproj`

Exécutez le projet situé dans le répertoire actif (l’argument `--help` de cet exemple est passé à l’application en cours d’exécution, puisque l’argument `--` a été utilisé) :

`dotnet run --configuration Release -- --help`


<!--HONumber=Nov16_HO3-->


