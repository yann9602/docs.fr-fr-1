---
title: "Modèle d’extensibilité des outils CLI .NET Core"
description: "Modèle d’extensibilité des outils CLI .NET Core"
keywords: "CLI, extensibilité, commandes personnalisées, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 1bebd25a-120f-48d3-8c25-c89965afcbcd
translationtype: Human Translation
ms.sourcegitcommit: aeb199a9aeb1584570ad2a2942e2f22c75a59616
ms.openlocfilehash: 4223f296224c9b62c88b72f0f643c8b8b6fc9f6b

---

# <a name="net-core-cli-extensibility-model"></a>Modèle d’extensibilité des outils CLI .NET Core 

## <a name="overview"></a>Vue d'ensemble
Ce document explique les principales méthodes permettant d’étendre les outils CLI, et décrit les scénarios dans lesquels elles sont utilisées. Ce document décrit comment utiliser les outils et explique brièvement comment créer ces deux types d’outils. 

## <a name="how-to-extend-cli-tools"></a>Extension des outils CLI
Les outils CLI peuvent être étendus de deux façons :

1. Via les packages NuGet, par projet
2. Via le chemin (PATH) du système

Les deux mécanismes d’extensibilité présentés ci-dessus ne sont pas exclusifs. Vous pouvez n’en utiliser qu’un ou les deux à la fois. Le choix de la méthode dépend en grande partie de l’objectif de votre extension.

## <a name="per-project-based-extensibility"></a>Extensibilité par projet
Les outils par projet sont des [applications console portables](../deploying/index.md) qui sont distribuées dans les packages NuGet. Les outils sont uniquement disponibles dans le contexte du projet qui les référence et pour lequel ils sont restaurés. Les appels en dehors du contexte du projet (par exemple, en dehors du répertoire qui contient le projet) échoueront, car la commande ne pourra pas être trouvée.

Ces outils sont également parfaits pour les serveurs de build, puisque rien en dehors de `project.json` n’est nécessaire. Le processus de génération exécute la restauration pour le projet qu’il génère, et des outils seront disponibles. Les projets de langage, tels que F#, figurent également dans cette catégorie. Chaque projet ne peut être écrit que dans un langage. 

Enfin, ce modèle d’extensibilité prend en charge la création d’outils qui ont besoin d’accéder à la sortie générée du projet. Par exemple, les outils d’affichage Razor des applications MVC [ASP.NET](https://www.asp.net/) appartiennent à cette catégorie. 

### <a name="consuming-per-project-tools"></a>Utilisation des outils par projet
L’utilisation de ces outils nécessite l’ajout d’un nœud `tools` à votre `project.json`. Dans le nœud `tools`, vous devez référencer le package dans lequel réside l’outil. Après l’exécution de `dotnet restore`, l’outil et ses dépendances sont restaurés. 

Pour les outils qui doivent charger la sortie de génération du projet pour l’exécution, il existe généralement une autre dépendance qui est répertoriée sous les dépendances régulières du fichier projet. Cela signifie que les outils qui chargent le code du projet possèdent deux composants : 

1. Le demandeur principal des outils
2. Tout autre outil contenant la logique à utiliser 

Pourquoi deux composants ? Les outils qui doivent charger la sortie de génération d’un projet doivent avoir un graphique de dépendance unifié avec le projet qu’ils utilisent. En ajoutant le bit de dépendance, nous permettons à NuGet de résoudre ces dépendances en tant que graphique unifié. Le demandeur est là pour évaluer l’emplacement, ainsi que les frameworks de l’outil de dépendance. Le demandeur peut accepter tous les arguments de redirection (`-c`, `-o`, `-b`) que l’utilisateur spécifie, et rechercher l’outil de dépendance. Il peut également implémenter des stratégies lorsqu’il existe plusieurs outils de dépendance pour plusieurs frameworks (par exemple, doit-il tous les exécuter ou n’en exécuter qu’un seul ?) En règle générale, une logique peut être entièrement partagée par ces deux outils. 

Voyons un exemple d’ajout d’un outil simple de type « tools-only » à un projet simple. Prenons un exemple de commande appelé `dotnet-api-search` qui vous permette de parcourir les packages NuGet à la recherche de l’API spécifiée. Voici le fichier `project.json` de l’application console qui utilise cet outil :

```json
{
    "version": "1.0.0",
    "compilationOptions": {
        "emitEntryPoint": true
    },
    "dependencies": {
        "Microsoft.NETCore.App": {
            "type": "platform",
            "version": "1.0.0"
        }
    },
    "tools": {
        "dotnet-api-search": {
            "version": "1.0.0",
            "imports": ["dnxcore50"]
        }
    },
    "frameworks": {
        "netcoreapp1.0": {}
    }
}
```

Le nœud `tools` est structuré de la même façon que le nœud `dependencies`. Il a besoin, au minimum, de l’ID de package du package qui contient l’outil et sa version. Dans l’exemple ci-dessus, nous voyons qu’il existe une autre instruction : `imports`. Cela influe sur le processus de restauration de l’outil et spécifie que l’outil est également compatible, en plus des frameworks ciblés dont dispose l’outil, avec le `dnxcore50` cible. Pour plus d’informations, consultez la [documentation de référence project.json](project-json.md).

### <a name="building-tools"></a>Outils de création
Comme nous l’avons mentionné précédemment, les outils sont des applications console portables. Ils peuvent être créés comme toute autre application console. Une fois l’outil créé, utilisez la commande [`dotnet pack`](dotnet-pack.md) pour créer un package NuGet (nupkg) devant contenir votre code, les informations sur ses dépendances, etc. L’auteur est libre de nommer le package comme il l’entend. Toutefois, l’application qui s’y trouve, le fichier binaire de l’outil, doit respecter la convention de `dotnet-<command>` afin de pouvoir être appelée par `dotnet`. 

Étant donné que les outils sont des applications portables, l’utilisateur qui utilise un outil doit disposer de la version des bibliothèques .NET Core à l’aide desquelles l’outil a été développé, afin de pouvoir l’exécuter. Toute autre dépendance que l’outil utilise et qui ne figure pas dans les bibliothèques .NET Core est restaurée et placée dans le cache de NuGet. L’outil entier est, par conséquent, exécuté à l’aide des assemblys des bibliothèques .NET Core et du cache de NuGet. 

Ces types d’outils ont un graphique de dépendance qui est complètement distinct du graphique de dépendance du projet qui les utilise. Le processus de restauration restaure d’abord les dépendances du projet, puis restaure chacun des outils et leurs dépendances. 

Vous trouverez des exemples plus complets dans le [dépôt sur les outils CLI .NET Core](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestProjects). Vous pouvez également voir l’[implémentation des outils utilisés](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages) dans le même dépôt. 

Le processus de création d’outils chargeant les sorties de génération du projet pour l’exécution est légèrement différent. Comme mentionné précédemment, pour ces types d’outils, il existe deux composants :

1. Un répartiteur que l’utilisateur appelle
2. Une dépendance spécifique au framework qui contient la logique de recherche et d’utilisation des sorties de génération

Les commandes [Entity Framework (EF)](https://github.com/aspnet/EntityFramework) et la commande [`dotnet test`](dotnet-test.md) constituent de bons exemples. Dans les deux cas, nous avons un outil qui est référencé dans le nœud `tools` du `project.json` et qui est le répartiteur principal. L’utilisateur appelle cet outil sur la ligne de commande. La deuxième pièce du puzzle est la dépendance donnée dans les dépendances principales du projet (les dépendances racines ou celles spécifiques au framework). Ce package contient la logique de l’outil. Le package est une dépendance normale. Il sera donc restauré dans le cadre du processus de restauration du projet. 

À la différence du type d’outils précédent, ces outils font partie du graphique du projet qui les utilise. Ceci s’explique par le fait qu’ils doivent accéder au code du projet et, potentiellement, à toutes ses dépendances. C’est le cas, par exemple, des outils Entity Framework, car ils doivent analyser les assemblys pour trouver le code dont ils ont besoin (par ex. les migrations).  

Cette solution à deux niveaux permet également un modèle d’appel plus propre. La plupart des commandes CLI qui suppriment certains artefacts du disque (par exemple, `dotnet build`, `dotnet publish`) permettent aux utilisateurs de rediriger les sorties vers un autre emplacement à l’aide de l’argument `--output`, `--build-base-path` ou `--configuration`. Pour les outils Entity Framework, par exemple, pour être en mesure de trouver la sortie de génération de votre projet, vous devez fournir les mêmes arguments avec les mêmes valeurs *à la fois* pour le pilote `dotnet` et la commande `ef`. Avec le modèle d’appel, les utilisateurs passent tous les arguments à l’outil répartiteur qui les utilise ensuite pour trouver le fichier binaire nécessaire contenant la logique parmi les répertoires de sortie. 

Un bon exemple de cette approche se trouve dans le [dépôt sur les outils CLI .NET Core](https://github.com/dotnet/cli) :

* [Exemple de fichier project.json](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/TestAssets/DesktopTestProjects/AppWithDirectDependencyDesktopAndPortable/project.json)
* [Implémentation du répartiteur](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages/dotnet-dependency-tool-invoker)
* [Implémentation de la dépendance spécifique du framework](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages/dotnet-desktop-and-portable)


### <a name="path-based-extensibility"></a>Extensibilité basée sur le chemin (PATH)
L’extensibilité basée sur le chemin est généralement utilisée pour les ordinateurs de développement qui nécessitent un outil qui traite conceptuellement plusieurs projets. Le principal inconvénient de ce mécanisme d’extension est qu’il est limité à l’ordinateur sur lequel est installé l’outil. Si vous avez besoin de l’installer sur un autre ordinateur, vous devrez le déployer.

Ce modèle d’extensibilité des outils CLI est très simple. Comme indiqué dans la [présentation des outils CLI .NET Core](index.md), le pilote `dotnet` peut exécuter toutes les commandes dont le nom respecte la convention `dotnet-<command>`. La logique de résolution par défaut sonde d’abord plusieurs emplacements avant d’arriver au chemin système. Si la commande demandée existe dans le chemin système et s’il s’agit d’un fichier binaire qui peut être appelé, le pilote `dotnet` l’appellera. 

La seule qualité indispensable au fichier binaire est d’être exécutable par le système d’exploitation. Sur les systèmes Unix, il peut s’agir de tous les fichiers dont le bit d’exécution est défini via `chmod +x`. Sur les systèmes Windows, il peut s’agir de n’importe quel fichier que Windows peut exécuter. 

Voyons par exemple une implémentation très simple d’une commande `dotnet clean`. Nous allons utiliser `bash` pour implémenter cette commande. La commande supprime les répertoires `bin/` et `obj/` situés dans le répertoire actif. Si l’argument `--lock` lui est passé, elle supprime également le fichier `project.lock.json`. L’intégralité de la commande est affichée ci-dessous. 

```bash
#!/bin/bash

# Delete the bin and obj dirs
rm -rf bin/ obj/

LOCK_FILE=$1
if [[ "$LOCK_FILE" = "--lock" ]]; then
    rm project.lock.json
fi


echo "Cleaning complete..."
```

Sur Mac OS, nous pouvons enregistrer ce script en tant que `dotnet-clean` et définir son bit exécutable avec `chmod +x dotnet-clean`. Nous pouvons ensuite créer un lien symbolique vers le script dans `/usr/local/bin` à l’aide de la commande `ln -s dotnet-clean /usr/local/bin/`. Cela permet d’appeler la commande Clean à l’aide de la syntaxe `dotnet clean`. Vous pouvez tester cela en créant une application, en exécutant `dotnet build` sur l’application, puis en exécutant `dotnet clean`. 

## <a name="conclusion"></a>Conclusion
Les outils CLI .NET Core permettent deux principaux points d’extensibilité. Les outils par projet sont contenus dans le contexte du projet, mais ils permettent une installation rapide grâce à une restauration. Les outils basés sur le chemin sont efficaces pour les outils généraux multiprojets qui sont utilisables sur un seul ordinateur. 



<!--HONumber=Nov16_HO3-->


