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
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 6fb08a8765ad720b51e796aa0991087413d02e44

---

#<a name="dotnet-restore"></a>dotnet-restore

## <a name="name"></a>Nom

`dotnet-restore` : restaure les dépendances et les outils d’un projet

## <a name="synopsis"></a>Résumé

`dotnet restore [root] [--help] [--source]  
    [--packages] [--disable-parallel] [--configfile] 
    [--no-cache] [--ignore-failed-sources] [--no-dependencies]`

## <a name="description"></a>Description

La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet. Par défaut, la restauration des dépendances et celle des outils sont effectuées en parallèle.

Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages. Les flux sont généralement fournis par le fichier de configuration NuGet.config. Un flux par défaut est disponible au moment de l’installation des outils CLI. Vous pouvez spécifier plusieurs flux en créant votre propre fichier NuGet.config dans le répertoire du projet. Les flux peuvent également être spécifiés par appel dans l’invite de commandes. 

Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`. Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation (par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows).

Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.

## <a name="options"></a>Options

`[root]` 
    
Chemin facultatif du fichier projet à restaurer. 

`-h|--help`

Affiche une aide brève pour la commande.

`-s|--source <SOURCE>`

Spécifie la source de package NuGet à utiliser pendant l’opération de restauration. Cela remplace toutes les sources spécifiées dans les fichiers NuGet.config. Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.

`--packages <PACKAGES_DIRECTORY]`

Spécifie le répertoire dans lequel placer les packages restaurés. 

`--disable-parallel`

Désactive la restauration de plusieurs projets en parallèle. 

`--configfile <FILE>`

Fichier de configuration NuGet (NuGet.config) à utiliser pour l’opération de restauration.

`--no-cache`

Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.

` --ignore-failed-sources`

Avertir en cas d’échec des sources uniquement si des packages répondent aux exigences de versions.

`--no-dependencies`

Quand vous restaurez un projet avec des références de P2P, ne restaurez pas les références, uniquement le projet racine. 

## <a name="examples"></a>Exemples

Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :

`dotnet restore` 

Restaurez des dépendances et des outils pour le projet `app1` se trouvant à l’emplacement donné :

`dotnet restore ~/projects/app1/app1.csproj``
    
Restaurez les dépendances et les outils pour le projet se trouvant dans le répertoire actif en utilisant le chemin de fichier fourni comme source de secours :

`dotnet restore -f c:\packages\mypackages` 

Restaurez les dépendances et les outils pour le projet se trouvant dans le répertoire actif en utilisant les deux chemins de fichiers fournis comme sources de secours :

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages` 

Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif et affichez uniquement les erreurs dans la sortie :

`dotnet restore --verbosity Error`



<!--HONumber=Nov16_HO3-->


