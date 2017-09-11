---
title: Commande dotnet-vstest
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 740e0e002b8fde1c5bfd1eb8e53be54b4113c74d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-vstest"></a><span data-ttu-id="1c90b-104">dotnet-vstest</span><span class="sxs-lookup"><span data-stu-id="1c90b-104">dotnet-vstest</span></span>

## <a name="name"></a><span data-ttu-id="1c90b-105">Nom</span><span class="sxs-lookup"><span data-stu-id="1c90b-105">Name</span></span>

<span data-ttu-id="1c90b-106">`dotnet-vstest` - Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1c90b-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1c90b-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="1c90b-107">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="1c90b-108">Description</span><span class="sxs-lookup"><span data-stu-id="1c90b-108">Description</span></span>

<span data-ttu-id="1c90b-109">La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour exécuter des tests unitaires automatisés et des tests d’application de l’interface utilisateur codée.</span><span class="sxs-lookup"><span data-stu-id="1c90b-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="1c90b-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="1c90b-110">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="1c90b-111">Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1c90b-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="1c90b-112">Séparez les noms d’assembly de test par des espaces.</span><span class="sxs-lookup"><span data-stu-id="1c90b-112">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="1c90b-113">Options</span><span class="sxs-lookup"><span data-stu-id="1c90b-113">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="1c90b-114">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="1c90b-114">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="1c90b-115">Exécutez les tests avec les noms qui correspondent aux valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="1c90b-115">Run tests with names that match the provided values.</span></span> <span data-ttu-id="1c90b-116">Séparez les valeurs par des virgules.</span><span class="sxs-lookup"><span data-stu-id="1c90b-116">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="1c90b-117">Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="1c90b-117">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="1c90b-118">Architecture de plateforme cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="1c90b-118">Target platform architecture used for test execution.</span></span> <span data-ttu-id="1c90b-119">Les valeurs valides sont `x86`, `x64` et `ARM`.</span><span class="sxs-lookup"><span data-stu-id="1c90b-119">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="1c90b-120">Version .NET Framework cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="1c90b-120">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="1c90b-121">Les valeurs valides sont par exemple `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Les valeurs `Framework35`, `Framework40`, `Framework45` et `FrameworkCore10` sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="1c90b-121">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="1c90b-122">Exécutez des tests en parallèle.</span><span class="sxs-lookup"><span data-stu-id="1c90b-122">Execute tests in parallel.</span></span> <span data-ttu-id="1c90b-123">Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables.</span><span class="sxs-lookup"><span data-stu-id="1c90b-123">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="1c90b-124">Définissez un nombre de cœurs explicite avec un fichier de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1c90b-124">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="1c90b-125">Exécutez les tests qui correspondent à l'expression donnée.</span><span class="sxs-lookup"><span data-stu-id="1c90b-125">Run tests that match the given expression.</span></span> <span data-ttu-id="1c90b-126">`<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="1c90b-126">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="1c90b-127">L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="1c90b-127">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="1c90b-128">Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.</span><span class="sxs-lookup"><span data-stu-id="1c90b-128">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="1c90b-129">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="1c90b-129">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="1c90b-130">Spécifiez un journal pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="1c90b-130">Specify a logger for test results.</span></span>  

* <span data-ttu-id="1c90b-131">Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :</span><span class="sxs-lookup"><span data-stu-id="1c90b-131">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="1c90b-132">Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`.</span><span class="sxs-lookup"><span data-stu-id="1c90b-132">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="1c90b-133">Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné.</span><span class="sxs-lookup"><span data-stu-id="1c90b-133">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="1c90b-134">Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="1c90b-134">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="1c90b-135">Répertorie les tests détectés dans le conteneur de tests donné.</span><span class="sxs-lookup"><span data-stu-id="1c90b-135">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="1c90b-136">ID du processus parent chargé de lancer le processus actif.</span><span class="sxs-lookup"><span data-stu-id="1c90b-136">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="1c90b-137">Spécifie le port de la connexion de socket et la réception des messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="1c90b-137">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="1c90b-138">Active les journaux détaillés de la plateforme de test.</span><span class="sxs-lookup"><span data-stu-id="1c90b-138">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="1c90b-139">Les journaux sont écrits dans le fichier fourni.</span><span class="sxs-lookup"><span data-stu-id="1c90b-139">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="1c90b-140">Spécifie des arguments supplémentaires à passer à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1c90b-140">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="1c90b-141">Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="1c90b-141">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="1c90b-142">Utilisez un espace pour séparer plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="1c90b-142">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="1c90b-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="1c90b-143">Examples</span></span>

<span data-ttu-id="1c90b-144">Exécuter des tests dans `mytestproject.dll` :</span><span class="sxs-lookup"><span data-stu-id="1c90b-144">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="1c90b-145">Exécuter des tests dans `mytestproject.dll` et `myothertestproject.exe` :</span><span class="sxs-lookup"><span data-stu-id="1c90b-145">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="1c90b-146">Exécuter des tests `TestMethod1` :</span><span class="sxs-lookup"><span data-stu-id="1c90b-146">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="1c90b-147">Exécuter des tests `TestMethod1` et `TestMethod2` :</span><span class="sxs-lookup"><span data-stu-id="1c90b-147">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`

