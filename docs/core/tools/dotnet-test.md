---
title: Commande dotnet test - Interface CLI .NET Core
description: "La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 9eb5be38549711717c11767332bfc84920ea927a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="dotnet-test"></a><span data-ttu-id="af91d-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="af91d-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="af91d-104">Nom</span><span class="sxs-lookup"><span data-stu-id="af91d-104">Name</span></span>

<span data-ttu-id="af91d-105">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="af91d-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="af91d-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="af91d-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af91d-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af91d-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af91d-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af91d-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="af91d-109">Description</span><span class="sxs-lookup"><span data-stu-id="af91d-109">Description</span></span>

<span data-ttu-id="af91d-110">La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné.</span><span class="sxs-lookup"><span data-stu-id="af91d-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="af91d-111">Les tests unitaires sont des projets d’application console qui ont des dépendances dans l’infrastructure de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et dans le Test Runner dotnet de l’infrastructure de tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="af91d-111">Unit tests are console application projects that have dependencies on the unit test framework (for example, MSTest, NUnit, or xUnit) and the dotnet test runner for the unit testing framework.</span></span> <span data-ttu-id="af91d-112">Ils sont empaquetés sous forme de packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.</span><span class="sxs-lookup"><span data-stu-id="af91d-112">These are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="af91d-113">Les projets de test doivent également spécifier le lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="af91d-113">Test projects also must specify the test runner.</span></span> <span data-ttu-id="af91d-114">Pour ce faire, vous pouvez utiliser un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="af91d-114">This is specified using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="af91d-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="af91d-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="af91d-116">Spécifie le chemin du projet de test.</span><span class="sxs-lookup"><span data-stu-id="af91d-116">Specifies a path to the test project.</span></span> <span data-ttu-id="af91d-117">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="af91d-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="af91d-118">Options</span><span class="sxs-lookup"><span data-stu-id="af91d-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af91d-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="af91d-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="af91d-120">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="af91d-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="af91d-121">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="af91d-121">Defines the build configuration.</span></span> <span data-ttu-id="af91d-122">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="af91d-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="af91d-123">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="af91d-123">Enables data collector for the test run.</span></span> <span data-ttu-id="af91d-124">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="af91d-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="af91d-125">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="af91d-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="af91d-126">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="af91d-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="af91d-127">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="af91d-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="af91d-128">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="af91d-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="af91d-129">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="af91d-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="af91d-130">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="af91d-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="af91d-131">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="af91d-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="af91d-132">Ne génère pas le projet de test avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="af91d-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="af91d-133">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="af91d-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="af91d-134">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="af91d-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="af91d-135">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="af91d-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="af91d-136">Le répertoire spécifié est créé s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="af91d-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="af91d-137">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="af91d-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="af91d-138">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="af91d-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="af91d-139">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="af91d-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="af91d-140">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="af91d-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af91d-141">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="af91d-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="af91d-142">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="af91d-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="af91d-143">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="af91d-143">Defines the build configuration.</span></span> <span data-ttu-id="af91d-144">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="af91d-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="af91d-145">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="af91d-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="af91d-146">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="af91d-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="af91d-147">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="af91d-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="af91d-148">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="af91d-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="af91d-149">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="af91d-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="af91d-150">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="af91d-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="af91d-151">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="af91d-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="af91d-152">Ne génère pas le projet de test avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="af91d-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="af91d-153">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="af91d-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="af91d-154">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="af91d-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="af91d-155">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="af91d-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="af91d-156">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="af91d-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="af91d-157">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="af91d-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="af91d-158">Exemples</span><span class="sxs-lookup"><span data-stu-id="af91d-158">Examples</span></span>

<span data-ttu-id="af91d-159">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="af91d-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="af91d-160">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="af91d-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="af91d-161">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="af91d-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="af91d-162">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="af91d-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="af91d-163">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="af91d-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="af91d-164">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="af91d-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="af91d-165">Infrastructure de test</span><span class="sxs-lookup"><span data-stu-id="af91d-165">Test Framework</span></span> | <span data-ttu-id="af91d-166">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="af91d-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="af91d-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="af91d-167">MSTest</span></span>         | <ul><li><span data-ttu-id="af91d-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="af91d-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="af91d-169">Nom</span><span class="sxs-lookup"><span data-stu-id="af91d-169">Name</span></span></li><li><span data-ttu-id="af91d-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="af91d-170">ClassName</span></span></li><li><span data-ttu-id="af91d-171">Priorité</span><span class="sxs-lookup"><span data-stu-id="af91d-171">Priority</span></span></li><li><span data-ttu-id="af91d-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="af91d-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="af91d-173">Xunit</span><span class="sxs-lookup"><span data-stu-id="af91d-173">Xunit</span></span>          | <ul><li><span data-ttu-id="af91d-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="af91d-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="af91d-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="af91d-175">DisplayName</span></span></li><li><span data-ttu-id="af91d-176">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="af91d-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="af91d-177">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="af91d-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="af91d-178">Opérateur</span><span class="sxs-lookup"><span data-stu-id="af91d-178">Operator</span></span> | <span data-ttu-id="af91d-179">Fonction</span><span class="sxs-lookup"><span data-stu-id="af91d-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="af91d-180">Correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="af91d-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="af91d-181">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="af91d-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="af91d-182">Contient</span><span class="sxs-lookup"><span data-stu-id="af91d-182">Contains</span></span>        |

<span data-ttu-id="af91d-183">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="af91d-183">`<value>` is a string.</span></span> <span data-ttu-id="af91d-184">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="af91d-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="af91d-185">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="af91d-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="af91d-186">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="af91d-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="af91d-187">Opérateur</span><span class="sxs-lookup"><span data-stu-id="af91d-187">Operator</span></span> | <span data-ttu-id="af91d-188">Fonction</span><span class="sxs-lookup"><span data-stu-id="af91d-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="af91d-189">OU</span><span class="sxs-lookup"><span data-stu-id="af91d-189">OR</span></span>       |
| `&`      | <span data-ttu-id="af91d-190">AND</span><span class="sxs-lookup"><span data-stu-id="af91d-190">AND</span></span>      |

<span data-ttu-id="af91d-191">Vous pouvez placer des expressions entre parenthèses lorsque vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="af91d-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="af91d-192">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="af91d-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af91d-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af91d-193">See also</span></span>

 [<span data-ttu-id="af91d-194">Frameworks et cibles</span><span class="sxs-lookup"><span data-stu-id="af91d-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="af91d-195">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="af91d-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
