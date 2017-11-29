---
title: Commande dotnet vstest - Interface CLI .NET Core
description: "La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances."
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: c5a7ee0ba306cea641b0ff34f0b521c92bd03719
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

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
