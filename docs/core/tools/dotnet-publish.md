---
title: Commande dotnet-publish - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-publish publie votre projet .NET Core dans un répertoire."
keywords: "dotnet-publish, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 48bfe6c77ee6c5d905069f47da5512ac63a24b2a
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>Nom

`dotnet-publish` - Empaquette l’application et ses dépendances dans un dossier en vue d’un déploiement sur un système d’hébergement.

## <a name="synopsis"></a>Résumé

`dotnet publish [<PROJECT>] [-f|--framework] [-r|--runtime] [-o|--output] [-c|--configuration] [--version-suffix] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Description

`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire. La sortie contient les éléments suivants :

* Le code de langage intermédiaire (IL) dans un assembly avec l’extension `*.dll`.
* Le fichier *\*.deps.json* qui contient toutes les dépendances du projet.
* Le fichier *\*.runtime.config.json* qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, le type de garbage collection).
* Les dépendances de l’application. Ces dernières sont copiées du cache NuGet vers le dossier de sortie.

Le résultat de la commande `dotnet publish` est prêt pour le déploiement sur un système hôte (par exemple, un serveur, un PC, un Mac ou un ordinateur portable) et pour l’exécution ; c’est le seul moyen officiellement pris en charge de préparer l’application en vue de son déploiement. En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement. Pour plus d’informations, consultez la page [Déploiement d’applications .NET Core](../deploying/index.md). Pour connaître la structure des répertoires d’une application publiée, consultez la page [Structure de répertoires](https://docs.microsoft.com/en-us/aspnet/core/hosting/directory-structure).

## <a name="arguments"></a>Arguments

`PROJECT` 

Projet à publier. S’il n’est pas spécifié, la valeur utilisée par défaut est le répertoire actif. 

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-f|--framework <FRAMEWORK>`

Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publie l’application pour un runtime donné. Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd). Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-o|--output <OUTPUT_DIRECTORY>`

Spécifie le chemin d’accès du répertoire de sortie. Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]* pour un déploiement autonome.

`-c|--configuration <CONFIGURATION>`

Configuration à utiliser lors de la génération du projet. La valeur par défaut est `Debug`.

`--version-suffix <VERSION_SUFFIX>`

Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

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
