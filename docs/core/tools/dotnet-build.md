---
title: Commande dotnet-build - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-build permet de générer un projet et l’ensemble de ses dépendances."
keywords: dotnet-build, CLI, commande CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: e5deac8a7b8faac97ccf8b801f274a2c03268d64
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-build"></a>dotnet-build

## <a name="name"></a>Nom

`dotnet-build` : Génère un projet et l’ensemble de ses dépendances.

## <a name="synopsis"></a>Résumé

`dotnet build [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet build` génère le projet et ses dépendances dans un ensemble de fichiers binaires. Les fichiers binaires incluent le code du projet dans des fichiers en langage intermédiaire (IL) avec une extension *.dll* et les fichiers de symboles utilisés pour le débogage avec une extension *.pdb*. Un fichier JSON de dépendances (*\*.deps.json*) est généré. Il répertorie les dépendances de l’application. Un fichier *\*.runtimeconfig.json* est généré. Il spécifie le runtime partagé et sa version pour l’application.

Si le projet a des dépendances tierces, comme des bibliothèques NuGet, elles sont résolues à partir du cache NuGet et ne sont pas disponibles avec la sortie générée du projet. Par conséquent, le produit de `dotnet build` ne peut pas être transféré en l’état vers un autre ordinateur pour exécution. Ce comportement contraste avec celui du .NET Framework dans lequel la génération d’un projet exécutable (une application) produit une sortie exécutable sur n’importe quel ordinateur où le .NET Framework est installé. Pour obtenir un résultat similaire dans .NET Core, vous utilisez la commande [dotnet publish](dotnet-publish.md). Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md). 

La génération requiert le fichier *project.assets.json* qui répertorie les dépendances de votre application. Le fichier est créé lorsque vous exécutez [`dotnet restore`](dotnet-restore.md) avant de générer le projet. Si le fichier de ressources est absent, les outils ne peuvent pas résoudre les assemblys de référence, ce qui entraîne des erreurs.

La commande `dotnet build` utilise MSBuild pour générer le projet. Elle prend donc en charge les builds parallèles et les builds incrémentielles. Pour plus d’informations, consultez [Builds incrémentielles](https://docs.microsoft.com/visualstudio/msbuild/incremental-builds). 

En plus de ses options, la commande `dotnet build` accepte des options MSBuild, comme `/p` pour définir des propriétés ou `/l` pour définir un enregistreur d’événements. En savoir plus sur ces options dans les [Informations de référence sur la ligne de commande MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference). 

La possibilité d’exécuter le projet ou non est déterminée par la propriété `<OutputType>` dans le fichier projet. L’exemple suivant illustre un projet qui génère du code exécutable :

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Pour générer une bibliothèque, omettez la propriété `<OutputType>`. La principale différence dans la sortie générée est que la DLL de langage intermédiaire pour une bibliothèque ne contient pas de points d’entrée et ne peut pas être exécutée. 

## <a name="arguments"></a>Arguments

`PROJECT`

Fichier projet à générer. Si vous ne spécifiez pas de fichier projet, MSBuild recherche dans le répertoire de travail actuel un fichier avec une extension se terminant par *proj* et l’utilise.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel placer les fichiers binaires générés. Vous devez également définir `--framework` lorsque vous spécifiez cette option.

`-f|--framework <FRAMEWORK>`

Compile pour un [framework](../../standard/frameworks.md) spécifique. Le framework doit être défini dans le [fichier projet](csproj.md).

`-c|--configuration <CONFIGURATION>`

Définit la configuration de build. En cas d’omission, la configuration de build est définie par défaut sur `Debug`. Utiliser `Release` pour créer une configuration Release.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Spécifie le runtime cible. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).

`--version-suffix <VERSION_SUFFIX>`

Définit le suffixe de version pour un astérisque (`*`) dans le champ de version du fichier projet. Le format respecte les instructions de version de NuGet.

`--no-incremental`

Marque la build comme unsafe pour la génération incrémentielle. Cela désactive la compilation incrémentielle et force une régénération du graphique de dépendance du projet.

`--no-dependencies`

Ignore les références entre projets (P2P) et génère uniquement le projet racine spécifié pour la génération.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="examples"></a>Exemples

Générer un projet et ses dépendances :

`dotnet build`

Générer un projet et ses dépendances à l’aide de la configuration Release :

`dotnet build --configuration Release`

Générer un projet et ses dépendances pour un runtime spécifique (dans cet exemple, Ubuntu 16.04) :

`dotnet build --runtime ubuntu.16.04-x64`

