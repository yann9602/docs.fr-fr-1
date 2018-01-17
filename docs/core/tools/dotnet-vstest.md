---
title: Commande dotnet vstest - Interface CLI .NET Core
description: "La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances."
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: f2ad875430b2dc7f0ffbadfb9a39dd83854557cb
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="dotnet-vstest"></a><span data-ttu-id="38dea-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="38dea-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="38dea-104">Name</span><span class="sxs-lookup"><span data-stu-id="38dea-104">Name</span></span>

<span data-ttu-id="38dea-105">`dotnet-vstest` - Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="38dea-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="38dea-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="38dea-106">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="38dea-107">Description</span><span class="sxs-lookup"><span data-stu-id="38dea-107">Description</span></span>

<span data-ttu-id="38dea-108">La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour exécuter des tests unitaires automatisés et des tests d’application de l’interface utilisateur codée.</span><span class="sxs-lookup"><span data-stu-id="38dea-108">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="38dea-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="38dea-109">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="38dea-110">Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="38dea-110">Run tests from the specified assemblies.</span></span> <span data-ttu-id="38dea-111">Séparez les noms d’assembly de test par des espaces.</span><span class="sxs-lookup"><span data-stu-id="38dea-111">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="38dea-112">Options</span><span class="sxs-lookup"><span data-stu-id="38dea-112">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="38dea-113">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="38dea-113">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="38dea-114">Exécutez les tests avec les noms qui correspondent aux valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="38dea-114">Run tests with names that match the provided values.</span></span> <span data-ttu-id="38dea-115">Séparez les valeurs par des virgules.</span><span class="sxs-lookup"><span data-stu-id="38dea-115">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="38dea-116">Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="38dea-116">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="38dea-117">Architecture de plateforme cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="38dea-117">Target platform architecture used for test execution.</span></span> <span data-ttu-id="38dea-118">Les valeurs valides sont `x86`, `x64` et `ARM`.</span><span class="sxs-lookup"><span data-stu-id="38dea-118">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="38dea-119">Version .NET Framework cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="38dea-119">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="38dea-120">Les valeurs valides sont par exemple `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Les valeurs `Framework35`, `Framework40`, `Framework45` et `FrameworkCore10` sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="38dea-120">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="38dea-121">Exécutez des tests en parallèle.</span><span class="sxs-lookup"><span data-stu-id="38dea-121">Execute tests in parallel.</span></span> <span data-ttu-id="38dea-122">Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables.</span><span class="sxs-lookup"><span data-stu-id="38dea-122">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="38dea-123">Définissez un nombre de cœurs explicite avec un fichier de paramètres.</span><span class="sxs-lookup"><span data-stu-id="38dea-123">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="38dea-124">Exécutez les tests qui correspondent à l'expression donnée.</span><span class="sxs-lookup"><span data-stu-id="38dea-124">Run tests that match the given expression.</span></span> <span data-ttu-id="38dea-125">`<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="38dea-125">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="38dea-126">L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="38dea-126">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="38dea-127">Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.</span><span class="sxs-lookup"><span data-stu-id="38dea-127">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="38dea-128">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="38dea-128">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="38dea-129">Spécifiez un journal pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="38dea-129">Specify a logger for test results.</span></span>  

* <span data-ttu-id="38dea-130">Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :</span><span class="sxs-lookup"><span data-stu-id="38dea-130">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="38dea-131">Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`.</span><span class="sxs-lookup"><span data-stu-id="38dea-131">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="38dea-132">Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné.</span><span class="sxs-lookup"><span data-stu-id="38dea-132">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="38dea-133">Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="38dea-133">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="38dea-134">Répertorie les tests détectés dans le conteneur de tests donné.</span><span class="sxs-lookup"><span data-stu-id="38dea-134">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="38dea-135">ID du processus parent chargé de lancer le processus actif.</span><span class="sxs-lookup"><span data-stu-id="38dea-135">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="38dea-136">Spécifie le port de la connexion de socket et la réception des messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="38dea-136">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="38dea-137">Active les journaux détaillés de la plateforme de test.</span><span class="sxs-lookup"><span data-stu-id="38dea-137">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="38dea-138">Les journaux sont écrits dans le fichier fourni.</span><span class="sxs-lookup"><span data-stu-id="38dea-138">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="38dea-139">Spécifie des arguments supplémentaires à passer à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="38dea-139">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="38dea-140">Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="38dea-140">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="38dea-141">Utilisez un espace pour séparer plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="38dea-141">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="38dea-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="38dea-142">Examples</span></span>

<span data-ttu-id="38dea-143">Exécuter des tests dans `mytestproject.dll` :</span><span class="sxs-lookup"><span data-stu-id="38dea-143">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="38dea-144">Exécuter des tests dans `mytestproject.dll`, en exportant vers un dossier personnalisé avec un nom personnalisé :</span><span class="sxs-lookup"><span data-stu-id="38dea-144">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="38dea-145">Exécuter des tests dans `mytestproject.dll` et `myothertestproject.exe` :</span><span class="sxs-lookup"><span data-stu-id="38dea-145">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="38dea-146">Exécuter des tests `TestMethod1` :</span><span class="sxs-lookup"><span data-stu-id="38dea-146">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="38dea-147">Exécuter des tests `TestMethod1` et `TestMethod2` :</span><span class="sxs-lookup"><span data-stu-id="38dea-147">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`

