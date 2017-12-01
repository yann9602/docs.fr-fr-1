---
title: "Tester la sortie publiée avec dotnet vstest"
description: "Découvrez comment exécuter des tests sur une sortie publiée avec la commande de vstest dotnet."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3965e4ca-75b8-4969-b3af-ca993c397a15
ms.openlocfilehash: 217787d41a9da6000941ded6caaa4f44d124644b
ms.sourcegitcommit: 8a4f8e6a7f1341764abcd188a332cc28d1e2d8ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a>Tester la sortie publiée avec dotnet vstest

Vous pouvez exécuter des tests sur sortie déjà publié à l’aide de la `dotnet vstest` commande. Cela fonctionne sur xUnit, MSTest et NUnit tests. Simplement rechercher le fichier DLL qui faisait partie de votre sortie publiée et exécutez :
```
dotnet vstest <MyPublishedTests>.dll
```
où `<MyPublishedTests>` est le nom de votre projet de test publié.

### <a name="example-of-running-tests-on-a-published-dll"></a>Exemple de l’exécution des tests sur une DLL publiée

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] Remarque : Si votre application cible une infrastructure autre que `netcoreapp` vous pouvez toujours exécuter le `dotnet vstest` commande en passant dans le .NET framework avec un indicateur de framework ciblé. Par exemple, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. Dans Visual Studio 2017 mise à jour 5 le souhaitée du .NET framework est détecté automatiquement.

### <a name="related-topics"></a>Rubriques connexes
- [Tests unitaires avec test de dotnet et xUnit](unit-testing-with-dotnet-test.md)
- [Tests unitaires avec un test de dotnet et de MSTest](unit-testing-with-mstest.md)
