---
title: Effectuer des tests unitaires dans .NET Core
description: "Les tests unitaires n’ont jamais été aussi faciles. Découvrez comment utiliser les tests unitaires dans les projets .NET Core et .NET Standard."
keywords: .NET, .NET Core, .NET Standard, test unitaire
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.workload: dotnetcore
ms.openlocfilehash: cb78a66a3a6a7158a86a76d62e5230c75b51a416
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Tests unitaires dans .NET Core et .NET Standard

.NET Core a été conçu dans une optique de testabilité et pour faciliter plus que jamais la création de tests unitaires pour vos applications. Cet article présente brièvement les tests unitaires et explique ce qui les distingue des autres types de test. Les ressources liées montrent comment ajouter un projet de test à une solution et comment exécuter les tests unitaires via la ligne de commande ou Visual Studio.

.NET Core 2.0 prend en charge [.NET Standard 2.0](../../standard/net-standard.md). Les bibliothèques utilisées pour illustrer les tests unitaires dans cette section s’appuient sur .NET Standard et fonctionnent également dans d’autres types de projets.

À compter de .NET Core 2.0, il existe des modèles de projet de test unitaire pour Visual Basic et F#, ainsi que pour C#.

## <a name="getting-started-with-testing"></a>Bien démarrer avec les tests

L’utilisation d’une suite de tests automatisés est l’un des meilleurs moyens de vérifier qu’une application logicielle se comporte comme ses auteurs l’avaient prévu. Il existe différents types de test pour les applications logicielles : tests d’intégration, tests web, tests de charge, etc. Au niveau le plus bas se trouvent les tests unitaires, qui permettent de tester individuellement chaque composant logiciel ou méthode. Les tests unitaires doivent porter uniquement sur le code dont le développeur a le contrôle, et non sur les problèmes d’infrastructure comme les bases de données, les systèmes de fichiers ou les ressources réseau. Les tests unitaires peuvent être écrits en faisant appel au [développement piloté par les tests (TDD)](http://deviq.com/test-driven-development/). Ils peuvent aussi être ajoutés à du code existant pour vérifier qu’il est correct. Dans les deux cas, ils doivent être succincts, bien nommés et rapides, car dans l’idéal, vous souhaitez pouvoir en exécuter des centaines avant de répercuter vos modifications dans le référentiel de code partagé du projet.

> [!NOTE]
> Les développeurs éprouvent souvent des difficultés à trouver des noms appropriés pour leurs classes et méthodes de test. Comme point de départ, l’équipe produit ASP.NET suit [ces conventions](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Quand vous écrivez des tests unitaires, veillez à ne pas introduire accidentellement de dépendances vis-à-vis de l’infrastructure. Celles-ci ont tendance à ralentir et à fragiliser les tests. Il est donc préférable de les réserver aux tests d’intégration. Vous pouvez éviter ces dépendances cachées dans le code de votre application en suivant le [principe des dépendances explicites](http://deviq.com/explicit-dependencies-principle/) et en ayant recours à l’[injection de dépendances](/aspnet/core/fundamentals/dependency-injection) pour demander vos dépendances à partir du framework. Vous pouvez aussi conserver vos tests unitaires dans un projet distinct de celui qui abrite vos tests d’intégration et vérifier que ce dernier ne contient pas de références à des dépendances ou des dépendances à des packages d’infrastructure.

Pour en savoir plus sur les tests unitaires dans les projets .NET Core :

Les projets de test unitaire pour .NET Core sont pris en charge pour [C#](../../csharp/index.md), [F#](../../fsharp/index.md) et [Visual Basic](../../visual-basic/index.md). Vous pouvez également choisir entre [xUnit](http://xunit.github.io), [NUnit](http://nunit.org) et [MSTest](https://github.com/Microsoft/vstest-docs).

Vous pouvez en apprendre plus sur ces combinaisons dans ces procédures pas à pas :

* Créer des tests unitaires à l’aide de [*XUnit* et *C#* avec l’interface CLI .NET Core](unit-testing-with-dotnet-test.md).
* Créer des tests unitaires à l’aide de [*NUnit* et *C#* avec l’interface CLI .NET Core](unit-testing-with-nunit.md).
* Créer des tests unitaires à l’aide de [*MSTest* et *C#* avec l’interface CLI .NET Core](unit-testing-with-mstest.md).
* Créer des tests unitaires à l’aide de [*XUnit* et *F#* avec l’interface CLI .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Créer des tests unitaires à l’aide de [*NUnit* et *F#* avec l’interface CLI .NET Core](unit-testing-fsharp-with-nunit.md).
* Créer des tests unitaires à l’aide de [*MSTest* et *F#* avec l’interface CLI .NET Core](unit-testing-fsharp-with-mstest.md).
* Créer des tests unitaires à l’aide de [*XUnit* et *Visual Basic* avec l’interface CLI .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Créer des tests unitaires à l’aide de [*NUnit* et *Visual Basic* avec l’interface CLI .NET Core](unit-testing-visual-basic-with-nunit.md).
* Créer des tests unitaires à l’aide de [*MSTest* et *Visual Basic* avec l’interface CLI .NET Core](unit-testing-visual-basic-with-mstest.md).

Vous pouvez choisir différents langages pour vos bibliothèques de classes et vos bibliothèques de tests unitaires. Pour savoir comment procéder, vous pouvez mélanger et associer les procédures pas à pas référencées ci-dessus.

* Visual Studio Enterprise propose des outils de test très performants pour .NET Core. Pour en savoir plus, découvrez [Live Unit Testing](/visualstudio/test/live-unit-testing) ou la[couverture du code](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage).
* Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](selective-unit-tests.md) ou [Inclusion et exclusion de tests avec Visual Studio](/visualstudio/test/live-unit-testing#including-and-excluding-test-projects-and-test-methods).
* L’équipe XUnit a écrit un didacticiel qui explique [comment utiliser xUnit avec .NET Core et Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html).
