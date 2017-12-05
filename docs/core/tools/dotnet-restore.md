---
title: Commande dotnet restore - Interface CLI .NET Core
description: "Découvrez comment restaurer les dépendances et les outils spécifiques du projet avec la commande dotnet restore."
keywords: "dotnet-restore, CLI, commande CLI, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 11/30/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 887f562803226d99901a6ee13175c1a43956b0cd
ms.sourcegitcommit: f416ac259c1a771e4e6c72728d8c11a77082f11c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="dotnet-restore"></a>dotnet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet restore` : Restaure les dépendances et les outils d’un projet.

## <a name="synopsis"></a>Résumé

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Description

La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet. Par défaut, la restauration des dépendances et celle des outils sont effectuées en parallèle.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages. Les flux sont généralement fournis par le fichier de configuration *NuGet.config*. Un fichier de configuration par défaut est fourni lors de l’installation des outils CLI. Vous pouvez spécifier d’autres flux en créant votre propre fichier *NuGet.config* dans le répertoire du projet. Vous pouvez également spécifier des flux supplémentaires par appel dans une invite de commandes.

Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`. Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation (par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows).

Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.

Le comportement de la commande `dotnet restore` est affecté par certains paramètres du fichier *Nuget.Config*, le cas échéant. Par exemple, si vous définissez `globalPackagesFolder` dans *NuGet.Config*, les packages NuGet restaurés sont placés dans le dossier spécifié. Cette méthode permet également de spécifier l’option `--packages` sur la commande `dotnet restore`. Pour plus d’informations, consultez [Informations de référence sur NuGet.Config](/nuget/schema/nuget-config-file).

## <a name="implicit-dotnet-restore"></a>`dotnet restore` implicite

À compter de .NET Core 2.0, `dotnet restore` est au besoin exécuté implicitement quand vous exécutez les commandes suivantes :

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Dans la plupart des cas, vous n’avez plus besoin d’utiliser explicitement la commande `dotnet restore`. 

Dans certains cas, l’exécution implicite de `dotnet restore` pose problème. Par exemple, certains systèmes automatisés, comme les systèmes de génération, doivent appeler explicitement `dotnet restore` pour contrôler quand la restauration a lieu afin de pouvoir contrôler l’utilisation du réseau. Pour empêcher l’exécution implicite de `dotnet restore`, vous pouvez utiliser le commutateur `--no-restore` avec l’une de ces commandes afin de désactiver la restauration implicite.

## <a name="arguments"></a>Arguments

`ROOT`

Chemin facultatif du fichier projet à restaurer.

## <a name="options"></a>Options

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--configfile <FILE>`

Fichier de configuration NuGet (*NuGet.config*) à utiliser pour l’opération de restauration.

`--disable-parallel`

Désactive la restauration de plusieurs projets en parallèle.

`--force`

Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Cette opération équivaut à supprimer le fichier *project.assets.json*.

`-h|--help`

Affiche une aide brève pour la commande.

`--ignore-failed-sources`

N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.

`--no-cache`

Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.

`--no-dependencies`

En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.

`--packages <PACKAGES_DIRECTORY>`

Spécifie le répertoire des packages restaurés.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Spécifie un runtime pour la restauration du package. Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.

`-s|--source <SOURCE>`

Spécifie la source de package NuGet à utiliser pendant l’opération de restauration. Cela remplace toutes les sources spécifiées dans le(s) fichier(s) *NuGet.config*. Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.

`--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--configfile <FILE>`

Fichier de configuration NuGet (*NuGet.config*) à utiliser pour l’opération de restauration.

`--disable-parallel`

Désactive la restauration de plusieurs projets en parallèle.

`-h|--help`

Affiche une aide brève pour la commande.

`--ignore-failed-sources`

N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.

`--no-cache`

Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.

`--no-dependencies`

En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.

`--packages <PACKAGES_DIRECTORY>`

Spécifie le répertoire des packages restaurés.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Spécifie un runtime pour la restauration du package. Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.

`-s|--source <SOURCE>`

Spécifie la source de package NuGet à utiliser pendant l’opération de restauration. Cela remplace toutes les sources spécifiées dans le(s) fichier(s) *NuGet.config*. Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.

`--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="examples"></a>Exemples

Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :

`dotnet restore`

Restaurez des dépendances et des outils pour le projet `app1` se trouvant à l’emplacement donné :

`dotnet restore ~/projects/app1/app1.csproj`

Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif en utilisant le chemin d’accès de fichier fourni comme source :

`dotnet restore -s c:\packages\mypackages`

Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif en utilisant les deux chemins d’accès de fichiers fournis comme sources :

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif et afficher uniquement une sortie minimale :

`dotnet restore --verbosity minimal`
