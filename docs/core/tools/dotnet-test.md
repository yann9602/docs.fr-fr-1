---
title: Commande dotnet-test - Interface CLI .NET Core
description: "La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné."
keywords: "dotnet-test, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/25/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3308488672df2621c04de40f642c732f81284019
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

#<a name="dotnet-test"></a><span data-ttu-id="98c8c-104">dotnet-test</span><span class="sxs-lookup"><span data-stu-id="98c8c-104">dotnet-test</span></span>

## <a name="name"></a><span data-ttu-id="98c8c-105">Nom</span><span class="sxs-lookup"><span data-stu-id="98c8c-105">Name</span></span>

<span data-ttu-id="98c8c-106">`dotnet-test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="98c8c-106">`dotnet-test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="98c8c-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="98c8c-107">Synopsis</span></span>

`dotnet test [<PROJECT>] [-s|--settings] [-t|--list-tests] [--filter] [-a|--test-adapter-path] [-l|--logger] [-c|--configuration] [-f|--framework] [-o|--output] [-d|--diag] [--no-build] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="98c8c-108">Description</span><span class="sxs-lookup"><span data-stu-id="98c8c-108">Description</span></span>

<span data-ttu-id="98c8c-109">La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné.</span><span class="sxs-lookup"><span data-stu-id="98c8c-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="98c8c-110">Les tests unitaires sont des projets d’application console qui ont des dépendances dans l’infrastructure de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et dans le Test Runner dotnet de l’infrastructure de tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="98c8c-110">Unit tests are console application projects that have dependencies on the unit test framework (for example, MSTest, NUnit, or xUnit) and the dotnet test runner for the unit testing framework.</span></span> <span data-ttu-id="98c8c-111">Ils sont empaquetés sous forme de packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.</span><span class="sxs-lookup"><span data-stu-id="98c8c-111">These are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="98c8c-112">Les projets de test doivent également spécifier le lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="98c8c-112">Test projects also must specify the test runner.</span></span> <span data-ttu-id="98c8c-113">Pour ce faire, vous pouvez utiliser un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="98c8c-113">This is specified using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

<span data-ttu-id="98c8c-114">[!code-xml[Modèle XUnit de base](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]</span><span class="sxs-lookup"><span data-stu-id="98c8c-114">[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]</span></span>

## <a name="options"></a><span data-ttu-id="98c8c-115">Options</span><span class="sxs-lookup"><span data-stu-id="98c8c-115">Options</span></span>

`PROJECT`
    
<span data-ttu-id="98c8c-116">Spécifie le chemin du projet de test.</span><span class="sxs-lookup"><span data-stu-id="98c8c-116">Specifies a path to the test project.</span></span> <span data-ttu-id="98c8c-117">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="98c8c-117">If omitted, it defaults to current directory.</span></span>

`-h|--help`

<span data-ttu-id="98c8c-118">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="98c8c-118">Prints out a short help for the command.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="98c8c-119">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="98c8c-119">Settings to use when running tests.</span></span> 

`-t|--list-tests`

<span data-ttu-id="98c8c-120">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="98c8c-120">List all of the discovered tests in the current project.</span></span> 

`--filter <EXPRESSION>`

<span data-ttu-id="98c8c-121">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="98c8c-121">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="98c8c-122">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="98c8c-122">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="98c8c-123">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="98c8c-123">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="98c8c-124">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="98c8c-124">Use the custom test adapters from the specified path in the test run.</span></span> 

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="98c8c-125">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="98c8c-125">Specifies a logger for test results.</span></span> 

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="98c8c-126">Configuration dans laquelle effectuer la génération.</span><span class="sxs-lookup"><span data-stu-id="98c8c-126">Configuration under which to build.</span></span> <span data-ttu-id="98c8c-127">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="98c8c-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="98c8c-128">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="98c8c-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="98c8c-129">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="98c8c-129">Directory in which to find the binaries to run.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="98c8c-130">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="98c8c-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span> 

`--no-build` 

<span data-ttu-id="98c8c-131">Ne génère pas le projet de test avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="98c8c-131">Does not build the test project prior to running it.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="98c8c-132">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="98c8c-132">Sets the verbosity level of the command.</span></span> <span data-ttu-id="98c8c-133">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="98c8c-133">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="98c8c-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="98c8c-134">Examples</span></span>

<span data-ttu-id="98c8c-135">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="98c8c-135">Run the tests in the project in the current directory:</span></span>

`dotnet test` 

<span data-ttu-id="98c8c-136">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="98c8c-136">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="98c8c-137">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="98c8c-137">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="98c8c-138">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="98c8c-138">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="98c8c-139">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="98c8c-139">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="98c8c-140">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="98c8c-140">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="98c8c-141">Infrastructure de test</span><span class="sxs-lookup"><span data-stu-id="98c8c-141">Test Framework</span></span> | <span data-ttu-id="98c8c-142">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="98c8c-142">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="98c8c-143">MSTest</span><span class="sxs-lookup"><span data-stu-id="98c8c-143">MSTest</span></span>         | <ul><li><span data-ttu-id="98c8c-144">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="98c8c-144">FullyQualifiedName</span></span></li><li><span data-ttu-id="98c8c-145">Nom</span><span class="sxs-lookup"><span data-stu-id="98c8c-145">Name</span></span></li><li><span data-ttu-id="98c8c-146">ClassName</span><span class="sxs-lookup"><span data-stu-id="98c8c-146">ClassName</span></span></li><li><span data-ttu-id="98c8c-147">Priorité</span><span class="sxs-lookup"><span data-stu-id="98c8c-147">Priority</span></span></li><li><span data-ttu-id="98c8c-148">TestCategory</span><span class="sxs-lookup"><span data-stu-id="98c8c-148">TestCategory</span></span></li></ul> |
| <span data-ttu-id="98c8c-149">Xunit</span><span class="sxs-lookup"><span data-stu-id="98c8c-149">Xunit</span></span>          | <ul><li><span data-ttu-id="98c8c-150">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="98c8c-150">FullyQualifiedName</span></span></li><li><span data-ttu-id="98c8c-151">DisplayName</span><span class="sxs-lookup"><span data-stu-id="98c8c-151">DisplayName</span></span></li><li><span data-ttu-id="98c8c-152">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="98c8c-152">Traits</span></span></li></ul>                                   |

<span data-ttu-id="98c8c-153">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="98c8c-153">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="98c8c-154">Opérateur</span><span class="sxs-lookup"><span data-stu-id="98c8c-154">Operator</span></span> | <span data-ttu-id="98c8c-155">Fonction</span><span class="sxs-lookup"><span data-stu-id="98c8c-155">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="98c8c-156">Correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="98c8c-156">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="98c8c-157">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="98c8c-157">Not exact match</span></span> |
| `~`      | <span data-ttu-id="98c8c-158">Contient</span><span class="sxs-lookup"><span data-stu-id="98c8c-158">Contains</span></span>        |

<span data-ttu-id="98c8c-159">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="98c8c-159">`<value>` is a string.</span></span> <span data-ttu-id="98c8c-160">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="98c8c-160">All the lookups are case insensitive.</span></span>

<span data-ttu-id="98c8c-161">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="98c8c-161">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="98c8c-162">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="98c8c-162">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="98c8c-163">Opérateur</span><span class="sxs-lookup"><span data-stu-id="98c8c-163">Operator</span></span> | <span data-ttu-id="98c8c-164">Fonction</span><span class="sxs-lookup"><span data-stu-id="98c8c-164">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="98c8c-165">OU</span><span class="sxs-lookup"><span data-stu-id="98c8c-165">OR</span></span>       |
| `&`      | <span data-ttu-id="98c8c-166">AND</span><span class="sxs-lookup"><span data-stu-id="98c8c-166">AND</span></span>      |

<span data-ttu-id="98c8c-167">Vous pouvez inclure des expressions entre parenthèses lorsque vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="98c8c-167">You can enclose expressions in paranthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="98c8c-168">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="98c8c-168">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98c8c-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98c8c-169">See also</span></span>

<span data-ttu-id="98c8c-170">[Frameworks et cibles](../../standard/frameworks.md) </span><span class="sxs-lookup"><span data-stu-id="98c8c-170">[Frameworks and Targets](../../standard/frameworks.md) </span></span>  
[<span data-ttu-id="98c8c-171">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="98c8c-171">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

