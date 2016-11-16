---
title: Commande dotnet-restore | SDK .NET Core
description: "Découvrez comment restaurer les dépendances et les outils spécifiques aux projets avec la commande dotnet-restore."
keywords: "dotnet-restore, CLI, commande CLI, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 60489b25-38de-47e6-bed1-59d9f42e2d46
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: 3c6c651aebfac0c27f340021d7779d37aa8bfe38

---

#<a name="dotnetrestore"></a>dotnet-restore

## <a name="name"></a>Nom

`dotnet-restore` : restaure les dépendances et les outils d’un projet

## <a name="synopsis"></a>Résumé

`dotnet restore [root] [--help] [--force-english-output] [--source]  
    [--packages] [--disable-parallel] [--fallbacksource] [--configfile] 
    [--no-cache] [--infer-runtimes] [--verbosity] [--ignore-failed-sources]`

## <a name="description"></a>Description

La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier [project.json](project-json.md). Par défaut, la restauration des dépendances et celle des outils sont effectuées en parallèle.

Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages. Les flux sont généralement fournis par le fichier de configuration NuGet.config. Un flux par défaut est disponible au moment de l’installation des outils CLI. Vous pouvez spécifier plusieurs flux en créant votre propre fichier NuGet.config dans le répertoire du projet. Les flux peuvent également être spécifiés par appel dans l’invite de commandes. 

Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`. Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation (par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows).

Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier [project.json](project-json.md). 

## <a name="options"></a>Options

`[root]` 
    
 Liste des projets ou des dossiers du projet à restaurer. Chaque valeur peut être le chemin d’un fichier [project.json](project-json.md) ou [global.json](global-json.md), ou d’un dossier. Si un dossier est spécifié, l’opération de restauration recherchera de manière récursive un fichier [project.json](project-json.md) dans tous les sous-répertoires et restaurations pour chaque fichier [project.json](project-json.md) trouvé.

`-h|--help`

Affiche une aide brève pour la commande.

 `--force-english-output`

Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).

`-s|--source <SOURCE>`

Spécifie la source de package NuGet à utiliser pendant l’opération de restauration. Cela remplace toutes les sources spécifiées dans les fichiers NuGet.config. Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.

`--packages <PACKAGES_DIRECTORY]`

Spécifie le répertoire dans lequel placer les packages restaurés. 

`--disable-parallel`

Désactive la restauration de plusieurs projets en parallèle. 

`-f|--fallbacksource <FEED>`

Spécifie la liste des sources de packages à utiliser comme solutions de secours lors de la restauration si toutes les autres sources échouent. Tous les formats de flux valides sont autorisés. Vous pouvez spécifier plusieurs sources de secours en spécifiant cette option plusieurs fois.

`--configfile <FILE>`

Fichier de configuration NuGet (NuGet.config) à utiliser pour l’opération de restauration.

`--no-cache`

Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.

`--infer-runtimes`

Option temporaire permettant d’autoriser NuGet à déduire les identificateurs de runtime pour les dépôts hérités.

`--verbosity [LEVEL]`

Niveau de détail à utiliser pour la journalisation. Valeurs autorisées : `Debug`, `Verbose`, `Information`, `Minimal`, `Warning` et `Error`.

` --ignore-failed-sources`

Avertir en cas d’échec des sources uniquement si des packages répondent aux exigences de versions.

## <a name="examples"></a>Exemples

Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :

`dotnet restore` 

Restaurez des dépendances et des outils pour le projet `app1` se trouvant à l’emplacement donné :

`dotnet restore ~/projects/app1/project.json`
    
Restaurez les dépendances et les outils pour le projet se trouvant dans le répertoire actif en utilisant le chemin de fichier fourni comme source de secours :

`dotnet restore -f c:\packages\mypackages` 

Restaurez les dépendances et les outils pour le projet se trouvant dans le répertoire actif en utilisant les deux chemins de fichiers fournis comme sources de secours :

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages` 

Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif et affichez uniquement les erreurs dans la sortie :

`dotnet restore --verbosity Error`


<!--HONumber=Nov16_HO1-->


