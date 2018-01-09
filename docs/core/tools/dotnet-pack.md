---
title: Commande dotnet pack - Interface CLI .NET Core
description: "La commande dotnet pack crée des packages NuGet pour votre projet .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 12/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 28cd05db0643097a7271fd0488354846598ba493
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-pack"></a>dotnet pack

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet pack` : Place le code dans un package NuGet.

## <a name="synopsis"></a>Résumé

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a>Description

La commande `dotnet pack` génère le projet et crée les packages NuGet. Le résultat de cette commande est un package NuGet. Si l’option `--include-symbols` est présente, un autre package contenant les symboles de débogage est créé.

Les dépendances NuGet du projet empaqueté sont ajoutées dans le fichier *.nuspec*, pour pouvoir être correctement résolues lors de l’installation du package. Les références entre projets ne sont pas empaquetées à l’intérieur du projet. Actuellement, vous devez disposer d’un package par projet si vous avez des dépendances entre projets.

Par défaut, `dotnet pack` génère d’abord le projet. Pour éviter ce comportement, passez l’option `--no-build`. Elle est souvent utile dans les scénarios de build d’intégration continue, pour lesquels vous savez que le code a déjà été créé.

Vous pouvez fournir des propriétés MSBuild à la commande `dotnet pack` pour le processus de compression. Pour plus d’informations, consultez [Propriétés des métadonnées NuGet](csproj.md#nuget-metadata-properties) et [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). La section [Exemples](#examples) montre comment utiliser le commutateur MSBuild /p pour deux scénarios différents.

## <a name="arguments"></a>Arguments

`PROJECT`

Projet à empaqueter. Il s’agit du chemin d’accès d’un [fichier csproj](csproj.md) ou d’un répertoire. Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

## <a name="options"></a>Options

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`.

`--force` : force la résolution de toutes les dépendances même si la dernière restauration a réussi. Cette opération équivaut à supprimer le fichier *project.assets.json*.

`-h|--help`

Affiche une aide brève pour la commande.

`--include-source`

Inclut les fichiers sources dans le package NuGet. Les fichiers sources sont inclus dans le dossier `src` de `nupkg`.

`--include-symbols`

Génère les symboles `nupkg`.

`--no-build`

Ne génère pas le projet avant de créer le package.

`--no-dependencies`

Ignore les références entre projets et restaure uniquement le projet racine.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Place les packages générés dans le répertoire spécifié.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Spécifie le runtime cible pour lequel restaurer les packages. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).

`-s|--serviceable`

Définit l’indicateur d’un état pouvant faire l’objet d’une maintenance dans le package. Pour plus d’informations, consultez [Blog .NET : .NET 4.5.1 prend en charge les mises à jour de sécurité de Microsoft pour les bibliothèques NuGet .NET](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Définit la valeur de la propriété MSBuild `$(VersionSuffix)` dans le projet.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`.

`-h|--help`

Affiche une aide brève pour la commande.

`--include-source`

Inclut les fichiers sources dans le package NuGet. Les fichiers sources sont inclus dans le dossier `src` de `nupkg`.

`--include-symbols`

Génère les symboles `nupkg`.

`--no-build`

Ne génère pas le projet avant de créer le package.

`-o|--output <OUTPUT_DIRECTORY>`

Place les packages générés dans le répertoire spécifié.

`-s|--serviceable`

Définit l’indicateur d’un état pouvant faire l’objet d’une maintenance dans le package. Pour plus d’informations, consultez [Blog .NET : .NET 4.5.1 prend en charge les mises à jour de sécurité de Microsoft pour les bibliothèques NuGet .NET](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Définit la valeur de la propriété MSBuild `$(VersionSuffix)` dans le projet.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

---

## <a name="examples"></a>Exemples

Empaquetez le projet dans le répertoire actif :

`dotnet pack`

Empaqueter le projet `app1` :

`dotnet pack ~/projects/app1/project.csproj`
    
Empaqueter le projet dans le répertoire actif et placer les packages résultants dans le dossier `nupkgs` :

`dotnet pack --output nupkgs`

Empaqueter le projet dans le répertoire actif du dossier `nupkgs` et ignorer l’étape de génération :

`dotnet pack --no-build --output nupkgs`

Avec le suffixe de version du projet configuré comme `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` dans le fichier *.csproj*, empaqueter le projet actif et mettre à jour la version du package obtenue avec le suffixe donné :

`dotnet pack --version-suffix "ci-1234"`

Affectez `2.1.0` à la version du package à l’aide de la propriété MSBuild `PackageVersion` :

`dotnet pack /p:PackageVersion=2.1.0`

Empaquetez le projet pour un [framework cible](../../standard/frameworks.md) spécifique :

`dotnet pack /p:TargetFrameworks=net45`
