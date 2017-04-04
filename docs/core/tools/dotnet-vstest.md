---
title: Commande dotnet-vstest | Microsoft Docs
description: "La commande dotnet-vstest permet de générer un projet et l’ensemble de ses dépendances."
keywords: "dotnet-vstest, CLI, commande CLI, .NET Core"
author: guardrex
ms.author: mairaw
ms.date: 03/09/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0e36c070-2242-41d3-96f1-aea0aca48d4d
translationtype: Human Translation
ms.sourcegitcommit: 4a1f0c88fb1ccd6694f8d4f5687431646adbe000
ms.openlocfilehash: 27b96e74ae1abc83ba527cb799db33bec7af35bf
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-vstest"></a>dotnet-vstest

## <a name="name"></a>Nom

`dotnet-vstest` - Exécute les tests à partir des fichiers spécifiés.

## <a name="synopsis"></a>Résumé

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a>Description

La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour exécuter des tests unitaires automatisés et des tests d’application de l’interface utilisateur codée.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Exécute les tests à partir des fichiers spécifiés. Séparez les noms d’assembly de test par des espaces.

## <a name="options"></a>Options

`--Settings|/Settings:<Settings File>`

Paramètres à utiliser durant l’exécution des tests.

`--Tests|/Tests:<Test Names>`

Exécutez les tests avec les noms qui correspondent aux valeurs fournies. Séparez les valeurs par des virgules.

`--TestAdapterPath|/TestAdapterPath`

Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.

`--Platform|/Platform:<Platform type>`

Architecture de plateforme cible utilisée pour l’exécution des tests. Les valeurs valides sont `x86`, `x64` et `ARM`.

`--Framework|/Framework:<Framework Version>`

Version .NET Framework cible utilisée pour l’exécution des tests. Les valeurs valides sont par exemple `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Les valeurs `Framework35`, `Framework40`, `Framework45` et `FrameworkCore10` sont également prises en charge.

`--Parallel|/Parallel`

Exécutez des tests en parallèle. Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables. Définissez un nombre de cœurs explicite avec un fichier de paramètres.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Exécutez les tests qui correspondent à l'expression donnée. `<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`.  L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`. Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.

`-?|--Help|/?|/Help`

Affiche une aide brève pour la commande.

`--logger|/logger:<Logger Uri/FriendlyName>`

Spécifiez un journal pour les résultats de tests.  

* Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`. Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné. Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Répertorie les tests détectés dans le conteneur de tests donné.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID du processus parent chargé de lancer le processus actif.

`--Port|/Port:<Port>`

Spécifie le port de la connexion de socket et la réception des messages d’événement.

`--Diag|/Diag:<Path to log file>`

Active les journaux détaillés de la plateforme de test. Les journaux sont écrits dans le fichier fourni.

`args`

Spécifie des arguments supplémentaires à passer à l’adaptateur. Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument. Utilisez un espace pour séparer plusieurs arguments.

## <a name="examples"></a>Exemples

Exécuter des tests dans `mytestproject.dll` :

`dotnet vstest mytestproject.dll`

Exécuter des tests dans `mytestproject.dll` et `myothertestproject.exe` :

`dotnet vstest mytestproject.dll myothertestproject.exe`

Exécuter des tests `TestMethod1` :

`dotnet vstest /Tests:TestMethod1`

Exécuter des tests `TestMethod1` et `TestMethod2` :

`dotnet vstest /Tests:TestMethod1,TestMethod2`

