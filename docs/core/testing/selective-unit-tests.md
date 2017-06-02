---
title: "Exécution de tests unitaires sélectifs | Microsoft Docs"
description: "Vous montre comment utiliser une expression de filtre pour exécuter des tests unitaires sélectifs avec la commande de test dotnet."
keywords: ".NET, .NET Core, test unitaire, test sélectif"
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.translationtype: Human Translation
ms.sourcegitcommit: ae036cfcad341ffc859336a7ab2a49feec145715
ms.openlocfilehash: aceb0dc92b6c355a2b36a541d59cf1cd3cf4d0d4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/18/2017

---

# <a name="running-selective-unit-tests"></a>Exécution de tests unitaires sélectifs

Les exemples suivants utilisent `dotnet test`. Si vous utilisez `vstest.console.exe`, remplacez `--filter ` par `--testcasefilter:`.

## <a name="mstest"></a>MSTest

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

| Expression | Résultat |
| ---------- | ------ |
| `dotnet test --filter Method` | Exécute les tests dont `FullyQualifiedName` contient `Method`. Disponible dans `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Exécute les tests dont le nom contient `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | Exécute les tests qui sont dans la classe `MSTestNamespace.UnitTestClass1`.<br>**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTestClass1` ne fonctionnera pas. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | Exécute tous les tests sauf `MSTestNamespace.UnitTestClass1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=3` | Exécute les tests qui sont annotés avec `[Priority(3)]`.<br>**Remarque :** `Priority~3` n’est pas une valeur valide, car elle n’est pas une chaîne. |

**Utilisation des opérateurs conditionnels | et &amp;**

| Expression | Résultat |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | Exécute les tests qui ont `UnitTestClass1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | Exécute les tests qui ont `UnitTestClass1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | Exécute les tests qui ont un `FullyQualifiedName` contenant `UnitTestClass1` **et** `TestCategory` est `CategoryA` **ou** `Priority` est 1. |

## <a name="xunit"></a>xUnit

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

| Expression | Résultat |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Exécute les tests dont le nom d’affichage contient `TestClass1`. |

Dans l’exemple de code, les caractéristiques définies avec les clés `Category` et `Priority` peuvent être utilisées pour filtrer.

| Expression | Résultat |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Exécute les tests dont `FullyQualifiedName` contient `XUnit`.  Disponible dans `vstest 15.1+`. |
| `dotnet test --filter Category=bvt` | Exécute les tests qui ont `[Trait("Category", "bvt")]`. |

**Utilisation des opérateurs conditionnels | et &amp;**

| Expression | Résultat |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **ou** `Category` est `Nightly`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **et** `Category` est `Nightly`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | Exécute les tests qui ont un `FullyQualifiedName` contenant `TestClass1` **et** `Category` est `CategoryA` **ou** `Priority` est 1. |

