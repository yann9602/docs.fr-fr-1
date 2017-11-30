---
title: Commande dotnet publish - Interface CLI .NET Core
description: "La commande dotnet publish publie votre projet .NET Core dans un répertoire."
author: mairaw
ms.author: mairaw
ms.date: 09/01/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: d59ba8cf74a63c7d4a2234989477b5778fa0148f
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet publish` - Empaquette l’application et ses dépendances dans un dossier en vue d’un déploiement sur un système d’hébergement.

## <a name="synopsis"></a>Résumé

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Description

`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire. La sortie contient les éléments suivants :

* Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.
* Le fichier *.deps.json* qui contient toutes les dépendances du projet.
* Le fichier *.runtime.config.json* qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, le type de garbage collection).
* Les dépendances de l’application. Ces dernières sont copiées du cache NuGet vers le dossier de sortie.

Le résultat de la commande `dotnet publish` est prêt pour le déploiement sur un système hôte (par exemple, un serveur, un PC, un Mac ou un ordinateur portable) et pour l’exécution ; c’est le seul moyen officiellement pris en charge de préparer l’application en vue de son déploiement. En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement. Pour plus d’informations, consultez la page [Déploiement d’applications .NET Core](../deploying/index.md). Pour connaître la structure des répertoires d’une application publiée, consultez la page [Structure de répertoires](/aspnet/core/hosting/directory-structure).

## <a name="arguments"></a>Arguments

`PROJECT`

Projet à publier. S’il n’est pas spécifié, la valeur utilisée par défaut est le répertoire actif.

## <a name="options"></a>Options

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`.

`-f|--framework <FRAMEWORK>`

Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

`--force`

Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Cette opération équivaut à supprimer le fichier *project.assets.json*.

`-h|--help`

Affiche une aide brève pour la commande.

`--manifest <PATH_TO_MANIFEST_FILE>`

Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application. Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md). Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste. Cette option est disponible à partir du SDK .NET Core 2.0.

`--no-dependencies`

Ignore les références entre projets et restaure uniquement le projet racine.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Spécifie le chemin d’accès du répertoire de sortie. Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]* pour un déploiement autonome.
Si un chemin d’accès relatif est fournie, le répertoire de sortie généré par rapport à l’emplacement du fichier projet, pas au répertoire de travail actuel.

`--self-contained`

Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible. Si un identificateur de runtime est spécifié, sa valeur par défaut est `true`. Pour plus d’informations sur les différents types de déploiement, consultez [déploiement d’application .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publie l’application pour un runtime donné. Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd). Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`.

`-f|--framework <FRAMEWORK>`

Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

`-h|--help`

Affiche une aide brève pour la commande.

`--manifest <PATH_TO_MANIFEST_FILE>`

Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application. Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md). Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste. Cette option est disponible à partir du SDK .NET Core 2.0.

`-o|--output <OUTPUT_DIRECTORY>`

Spécifie le chemin d’accès du répertoire de sortie. Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]* pour un déploiement autonome.
Si un chemin d’accès relatif est fournie, le répertoire de sortie généré par rapport à l’emplacement du fichier projet, pas au répertoire de travail actuel.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publie l’application pour un runtime donné. Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd). Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.

---

## <a name="examples"></a>Exemples

Publier le projet dans le répertoire actif :

`dotnet publish`

Publier l’application à l’aide du fichier projet spécifié :

`dotnet publish ~/projects/app1/app1.csproj`
    
Publier le projet dans le répertoire actif à l’aide du framework `netcoreapp1.1` :

`dotnet publish --framework netcoreapp1.1`
    
Publier l’application actuelle à l’aide du framework `netcoreapp1.1` et du runtime pour `OS X 10.10` (vous devez lister cet identificateur de runtime dans le fichier projet) :

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a>Voir aussi

* [Frameworks cibles](../../standard/frameworks.md)
* [Catalogue d’identificateurs de runtime (RID)](../rid-catalog.md)
