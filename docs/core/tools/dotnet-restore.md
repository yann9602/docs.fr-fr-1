---
title: Commande dotnet-restore - CLI .NET Core | Microsoft Docs
description: "Découvrez comment restaurer les dépendances et les outils spécifiques du projet avec la commande dotnet restore."
keywords: "dotnet-restore, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fd7a5769-afbe-4838-bbaf-3ae0cfcbb914
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 92da0806eb6c365a4622668242edc28d9966ed26
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-restore"></a>dotnet-restore

## <a name="name"></a>Nom

`dotnet-restore` : Restaure les dépendances et les outils d’un projet.

## <a name="synopsis"></a>Résumé

`dotnet restore [<ROOT>] [-s|--source] [-r|--runtime] [--packages] [--disable-parallel] [--configfile] [--no-cache] [--ignore-failed-sources] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet. Par défaut, la restauration des dépendances et celle des outils sont effectuées en parallèle.

Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages. Les flux sont généralement fournis par le fichier de configuration *NuGet.config*. Un fichier de configuration par défaut est fourni lors de l’installation des outils CLI. Vous pouvez spécifier d’autres flux en créant votre propre fichier *NuGet.config* dans le répertoire du projet. Vous pouvez également spécifier des flux supplémentaires par appel dans une invite de commandes. 

Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`. Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation (par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows).

Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.

## <a name="arguments"></a>Arguments

`ROOT` 
    
Chemin facultatif du fichier projet à restaurer.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

`-s|--source <SOURCE>`

Spécifie la source de package NuGet à utiliser pendant l’opération de restauration. Cela remplace toutes les sources spécifiées dans le(s) fichier(s) *NuGet.config*. Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Spécifie un runtime pour la restauration du package. Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.

`--packages <PACKAGES_DIRECTORY]`

Spécifie le répertoire des packages restaurés. 

`--disable-parallel`

Désactive la restauration de plusieurs projets en parallèle. 

`--configfile <FILE>`

Fichier de configuration NuGet (*NuGet.config*) à utiliser pour l’opération de restauration.

`--no-cache`

Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.

`--ignore-failed-sources`

N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.

`--no-dependencies`

En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.

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

Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif et affichez uniquement les erreurs dans la sortie :

`dotnet restore --verbosity Error`

