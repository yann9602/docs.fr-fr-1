---
title: Tests unitaires dans .NET Core | Microsoft Docs
description: Effectuer des tests unitaires dans .NET Core
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 4983af5386efc6b713f10f200687535b7dc36a11
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---

# <a name="unit-testing-in-net-core"></a>Effectuer des tests unitaires dans .NET Core

.NET Core a été conçu dans une optique de testabilité et pour faciliter plus que jamais la création de tests unitaires pour vos applications. Cet article présente brièvement les tests unitaires et explique ce qui les distingue des autres types de test. Des ressources liées montrent comment ajouter un projet de test à une solution et comment exécutez les tests unitaires via la ligne de commande ou Visual Studio.

## <a name="getting-started-with-testing"></a>Bien démarrer avec les tests
 
L’utilisation d’une suite de tests automatisés est l’un des meilleurs moyens de vérifier qu’une application logicielle se comporte comme ses auteurs l’avaient prévu. Il existe différents types de test pour les applications logicielles : tests d’intégration, tests web, tests de charge, etc. Au niveau le plus bas se trouvent les tests unitaires, qui permettent de tester individuellement chaque composant logiciel ou méthode. Les tests unitaires doivent porter uniquement sur le code dont le développeur a le contrôle, et non sur les problèmes d’infrastructure comme les bases de données, les systèmes de fichiers ou les ressources réseau. Les tests unitaires peuvent être écrits en faisant appel au [développement piloté par les tests (TDD)](http://deviq.com/test-driven-development/). Ils peuvent aussi être ajoutés à du code existant pour vérifier qu’il est correct. Dans les deux cas, ils doivent être succincts, bien nommés et rapides, car dans l’idéal, vous souhaiterez pouvoir en exécuter des centaines avant de répercuter vos modifications dans le dépôt de code partagé du projet.

> [!NOTE]
> Les développeurs éprouvent souvent des difficultés à trouver des noms appropriés pour leurs classes et méthodes de test. Comme point de départ, l’équipe produit ASP.NET suit [ces conventions](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Quand vous écrivez des tests unitaires, veillez à ne pas introduire accidentellement de dépendances vis-à-vis de l’infrastructure. Celles-ci ont tendance à ralentir et à fragiliser les tests. Il est donc préférable de les réserver aux tests d’intégration. Vous pouvez éviter ces dépendances cachées dans le code de votre application en suivant le [principe des dépendances explicites](http://deviq.com/explicit-dependencies-principle/) et en ayant recours à l’[injection de dépendances](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection) pour demander vos dépendances à partir du framework. Vous pouvez aussi conserver vos tests unitaires dans un projet distinct de celui qui abrite vos tests d’intégration et vérifier que ce dernier ne contient pas de références à des dépendances ou des dépendances à des packages d’infrastructure.

Pour en savoir plus sur les tests unitaires dans les projets .NET Core :

* Essayez cette [procédure pas à pas : création de tests unitaires avec xUnit et l’interface CLI .NET](unit-testing-with-dotnet-test.md). 
* L’équipe XUnit a écrit un didacticiel qui explique [comment utiliser xUnit avec .NET Core et Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html).
* Si vous préférez utiliser MSTest, essayez la [procédure pas à pas : création de tests unitaires avec MSTest et l’interface CLI .NET](unit-testing-with-mstest.md).
* Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).

