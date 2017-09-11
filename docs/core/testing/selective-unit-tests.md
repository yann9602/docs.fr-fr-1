---
title: "Exécution de tests unitaires sélectifs"
description: "Vous montre comment utiliser une expression de filtre pour exécuter des tests unitaires sélectifs avec la commande de test dotnet."
keywords: ".NET, .NET Core, test unitaire, test sélectif"
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: af832d04d2cba530a93710a90701ab119a66deef
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="running-selective-unit-tests"></a><span data-ttu-id="57314-104">Exécution de tests unitaires sélectifs</span><span class="sxs-lookup"><span data-stu-id="57314-104">Running selective unit tests</span></span>

<span data-ttu-id="57314-105">Les exemples suivants utilisent `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="57314-105">The following examples use `dotnet test`.</span></span> <span data-ttu-id="57314-106">Si vous utilisez `vstest.console.exe`, remplacez `--filter ` par `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="57314-106">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="57314-107">MSTest</span><span class="sxs-lookup"><span data-stu-id="57314-107">MSTest</span></span>

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="57314-108">Expression</span><span class="sxs-lookup"><span data-stu-id="57314-108">Expression</span></span> | <span data-ttu-id="57314-109">Résultat</span><span class="sxs-lookup"><span data-stu-id="57314-109">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="57314-110">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="57314-110">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="57314-111">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="57314-111">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="57314-112">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="57314-112">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="57314-113">Exécute les tests qui sont dans la classe `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="57314-113">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="57314-114">**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTestClass1` ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="57314-114">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="57314-115">Exécute tous les tests sauf `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="57314-115">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="57314-116">Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="57314-116">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="57314-117">Exécute les tests qui sont annotés avec `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="57314-117">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="57314-118">**Remarque :** `Priority~3` n’est pas une valeur valide, car elle n’est pas une chaîne.</span><span class="sxs-lookup"><span data-stu-id="57314-118">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="57314-119">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="57314-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="57314-120">Expression</span><span class="sxs-lookup"><span data-stu-id="57314-120">Expression</span></span> | <span data-ttu-id="57314-121">Résultat</span><span class="sxs-lookup"><span data-stu-id="57314-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="57314-122">Exécute les tests qui ont `UnitTestClass1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="57314-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="57314-123">Exécute les tests qui ont `UnitTestClass1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="57314-123">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="57314-124">Exécute les tests qui ont un `FullyQualifiedName` contenant `UnitTestClass1` **et** `TestCategory` est `CategoryA` **ou** `Priority` est 1.</span><span class="sxs-lookup"><span data-stu-id="57314-124">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="57314-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="57314-125">xUnit</span></span>

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| <span data-ttu-id="57314-126">Expression</span><span class="sxs-lookup"><span data-stu-id="57314-126">Expression</span></span> | <span data-ttu-id="57314-127">Résultat</span><span class="sxs-lookup"><span data-stu-id="57314-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="57314-128">Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="57314-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="57314-129">Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="57314-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="57314-130">Exécute les tests dont le nom d’affichage contient `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="57314-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="57314-131">Dans l’exemple de code, les caractéristiques définies avec les clés `Category` et `Priority` peuvent être utilisées pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="57314-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="57314-132">Expression</span><span class="sxs-lookup"><span data-stu-id="57314-132">Expression</span></span> | <span data-ttu-id="57314-133">Résultat</span><span class="sxs-lookup"><span data-stu-id="57314-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="57314-134">Exécute les tests dont `FullyQualifiedName` contient `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="57314-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="57314-135">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="57314-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="57314-136">Exécute les tests qui ont `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="57314-136">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="57314-137">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="57314-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="57314-138">Expression</span><span class="sxs-lookup"><span data-stu-id="57314-138">Expression</span></span> | <span data-ttu-id="57314-139">Résultat</span><span class="sxs-lookup"><span data-stu-id="57314-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="57314-140">Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **ou** `Category` est `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="57314-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="57314-141">Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **et** `Category` est `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="57314-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="57314-142">Exécute les tests qui ont un `FullyQualifiedName` contenant `TestClass1` **et** `Category` est `CategoryA` **ou** `Priority` est 1.</span><span class="sxs-lookup"><span data-stu-id="57314-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

