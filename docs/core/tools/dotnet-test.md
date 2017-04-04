---
title: Commande dotnet-test - CLI .NET Core | Microsoft Docs
description: "La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné."
keywords: "dotnet-test, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 26b5834135db8041995a137f5008d00cdf14d820
ms.lasthandoff: 03/22/2017

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>Nom

`dotnet-test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.

## <a name="synopsis"></a>Résumé

`dotnet test [<PROJECT>] [-s|--settings] [-t|--list-tests] [--filter] [-a|--test-adapter-path] [-l|--logger] [-c|--configuration] [-f|--framework] [-o|--output] [-d|--diag] [--no-build] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné. Les tests unitaires sont des projets de bibliothèques de classes qui ont des dépendances dans le framework de test unitaire (par exemple, MSText, NUnit ou xUnit) et dans le lanceur de tests dotnet du framework de test unitaire. Ils sont empaquetés sous forme de packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.

Les projets de test doivent également spécifier le lanceur de tests. Pour ce faire, vous pouvez utiliser un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :

[!code-xml[Modèle XUnit de base](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="options"></a>Options

`PROJECT`
    
Spécifie le chemin du projet de test. Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

`-h|--help`

Affiche une aide brève pour la commande.

`-s|--settings <SETTINGS_FILE>`

Paramètres à utiliser durant l’exécution des tests. 

`-t|--list-tests`

Répertorie tous les tests découverts dans le projet actuel. 

`--filter <EXPRESSION>`

Filtre les tests dans le projet actuel à l’aide de l’expression donnée. Pour plus d’informations sur la prise en charge du filtrage, consultez [Running selective unit tests in Visual Studio using TestCaseFilter](https://aka.ms/vstest-filtering).

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests. 

`-l|--logger <LoggerUri/FriendlyName>`

Spécifie un enregistreur d’événements pour les résultats de tests. 

`-c|--configuration <CONFIGURATION>`

Configuration dans laquelle effectuer la génération. La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.

`-f|--framework <FRAMEWORK>`

Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel rechercher les binaires à exécuter.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié. 

`--no-build` 

Ne génère pas le projet de test avant de l’exécuter.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="examples"></a>Exemples

Exécutez les tests du projet dans le répertoire actif :

`dotnet test` 

Exécuter les tests dans le projet `test1` :

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>Voir aussi

* [Frameworks cibles](../../standard/frameworks.md)
* [Catalogue d’identificateurs de runtime (RID)](../rid-catalog.md)
