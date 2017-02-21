---
title: Commande dotnet-test | Microsoft Docs
description: "La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné."
keywords: "dotnet-test, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
translationtype: Human Translation
ms.sourcegitcommit: 02f39bc959a56ab0fc2cfa57ce13f300a8a46107
ms.openlocfilehash: 204ebdb5a945dcd0c9277f1d95c113e829303b32

---

#<a name="dotnet-test-net-core-tools-rc4"></a>dotnet-test (outils .NET Core RC4)

> [!WARNING]
> Cette rubrique s’applique aux outils .NET Core RC4. Pour la version Preview 2 des outils .NET Core, consultez la rubrique [dotnet-test](../../tools/dotnet-test.md).

## <a name="name"></a>Nom

`dotnet-test` - Pilote de test .NET

## <a name="synopsis"></a>Résumé

`dotnet test [project] [--help] 
    [--settings] [--list-tests] [--filter] 
    [--test-adapter-path] [--logger] 
    [--configuration] [--framework] [--output] [--diag]
    [--no-build] [--verbosity]`

## <a name="description"></a>Description

La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné. Les tests unitaires sont des projets de bibliothèques de classes qui ont des dépendances dans le framework de test unitaire (par exemple, NUnit ou xUnit) et dans le Test Runner dotnet de ce framework de test unitaire. Ils sont empaquetés sous forme de packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.

Les projets de test doivent également spécifier le test Runner. Pour ce faire, vous pouvez utiliser un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :

[!code-xml[Modèle XUnit de base](../../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="options"></a>Options

`[project]`
    
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

`-c|--configuration <Debug|Release>`

Configuration dans laquelle effectuer la génération. La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.

`-f|--framework <FRAMEWORK>`

Recherche des binaires de test pour un framework spécifique.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel rechercher les binaires à exécuter.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié. 

`--no-build` 

Ne génère pas le projet de test avant de l’exécuter.

`-v|--verbosity [quiet|minimal|normal|diagnostic]`

Définit le niveau de détail de la commande. Vous pouvez spécifier les niveaux de détail suivants : q[uiet], m[inimal], n[ormal], d[etailed] et diag[nostic]. 

## <a name="examples"></a>Exemples

Exécutez les tests du projet dans le répertoire actif :

`dotnet test` 

Exécutez les tests dans le projet test1 :

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>Voir aussi

[Frameworks](../../../standard/frameworks.md)

[Catalogue d’identificateurs de runtime (RID)](../../rid-catalog.md)



<!--HONumber=Feb17_HO2-->


