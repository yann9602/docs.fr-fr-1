---
title: Commande dotnet-new | Microsoft Docs
description: "La commande dotnet-new crée de nouveaux projets .NET Core dans le répertoire actif."
keywords: "dotnet-new, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 02/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
translationtype: Human Translation
ms.sourcegitcommit: 96fd8ea3e55ea33e0bdd0bf3c50a10d0de6db1a1
ms.openlocfilehash: f0c62647c5817db2057c60a7a95a62f08f7889a5

---
#<a name="dotnet-new-net-core-tools-rc4"></a>dotnet-new (outils .NET Core RC4)

> [!WARNING]
> Cette rubrique s’applique aux outils .NET Core RC4. Pour la version Preview 2 des outils .NET Core, consultez la rubrique [dotnet-new](../../tools/dotnet-new.md).

## <a name="name"></a>Nom
dotnet-new : Crée un projet .NET Core dans le répertoire actif

## <a name="synopsis"></a>Résumé
```
dotnet new [template] [-lang|--language] [-n|--name] [-o|--output] [-h|--help]
dotnet new [template] [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>Description
La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide et d’obtenir un exemple de code source pour tester l’ensemble d’outils de l’interface de ligne de commande (CLI). 

Cette commande est appelée dans le contexte d’un répertoire. Quand elle est appelée, la commande structure les ressources et fichiers en fonction du modèle et des options qui lui sont passés. 

Après cela, le projet est prêt à être compilé et/ou édité. 

## <a name="arguments"></a>Arguments
template : Modèle à instancier quand la commande est appelée.

La commande contient une liste par défaut de modèles ; utilisez `dotnet new --help`. 

## <a name="options"></a>Options

`-l|--list`         

Répertorie les modèles contenant le nom spécifié.

`-lang|--language`  

Spécifie la langue du modèle à créer

`-n|--name`         

Nom de la sortie en cours de création. Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.

`-o|--output`       

Emplacement où placer la sortie générée.

`-all|--show-all`   

Affiche tous les modèles pour un type de projet spécifique.

`-h|--help`

Affiche l’aide pour la commande.

## <a name="template-options"></a>Options de modèle
Chaque modèle de projet peut présenter d’autres options disponibles. Les modèles de base, par exemple, disposent des éléments suivants.

**console, xunit, mstest**

`-f|--framework` : Indique l’infrastructure à cibler. Valeurs : netcoreapp1.0 ou netcoreapp1.1 (par défaut : netcoreapp1.0)

**web, webapi**

`-f|--framework` : Indique l’infrastructure à cibler. Valeurs : netcoreapp1.0 ou netcoreapp1.1 (par défaut : netcoreapp1.0)
 
**mvc**

`-f|--framework` : Indique l’infrastructure à cibler. Valeurs : netcoreapp1.0 ou netcoreapp1.1 (par défaut : netcoreapp1.0)

`-au|--authentication` : Type d’authentification à utiliser. Valeurs : Aucune ou Individual (Individuelle) (par défaut : Aucune)

`-uld|--use-local-db` : Indique s’il convient ou non d’utiliser LocalDB au lieu de SQLite. Valeurs : true ou false (par défaut : false)

**classlib**

`-f|--framework` : Indique l’infrastructure à cibler. Valeurs : netcoreapp1.0, netcoreapp1.1 et netstandard1.0 à 1.6 (par défaut : netstandard1.4).

## <a name="examples"></a>Exemples

Créez un projet d’application console F# dans le répertoire actif :

`dotnet new console -lang f#` 
   
Créez un projet d’application ASP.NET Core C# MVC dans le répertoire actif sans authentification ciblant .NET Core 1.0 :  

`dotnet new mvc -au None -f netcoreapp1.0`
 
Créez une application XUnit ciblant .NET Core 1.1 :

`dotnet new xunit --Framework netcoreapp1.1`

Répertoriez tous les modèles disponibles pour MVC :

`dotnet new mvc -l`


<!--HONumber=Feb17_HO3-->


