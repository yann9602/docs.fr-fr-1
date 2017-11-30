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
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="155dc-103">Tester la sortie publiée avec dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="155dc-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="155dc-104">Vous pouvez exécuter des tests sur sortie déjà publié à l’aide de la `dotnet vstest` commande.</span><span class="sxs-lookup"><span data-stu-id="155dc-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="155dc-105">Cela fonctionne sur xUnit, MSTest et NUnit tests.</span><span class="sxs-lookup"><span data-stu-id="155dc-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="155dc-106">Simplement rechercher le fichier DLL qui faisait partie de votre sortie publiée et exécutez :</span><span class="sxs-lookup"><span data-stu-id="155dc-106">Simply locate the DLL file that was part of your published output and run:</span></span>
```
dotnet vstest <MyPublishedTests>.dll
```
<span data-ttu-id="155dc-107">où `<MyPublishedTests>` est le nom de votre projet de test publié.</span><span class="sxs-lookup"><span data-stu-id="155dc-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

### <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="155dc-108">Exemple de l’exécution des tests sur une DLL publiée</span><span class="sxs-lookup"><span data-stu-id="155dc-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] <span data-ttu-id="155dc-109">Remarque : Si votre application cible une infrastructure autre que `netcoreapp` vous pouvez toujours exécuter le `dotnet vstest` commande en passant dans le .NET framework avec un indicateur de framework ciblé.</span><span class="sxs-lookup"><span data-stu-id="155dc-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="155dc-110">Par exemple, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="155dc-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="155dc-111">Dans Visual Studio 2017 mise à jour 5 le souhaitée du .NET framework est détecté automatiquement.</span><span class="sxs-lookup"><span data-stu-id="155dc-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

### <a name="related-topics"></a><span data-ttu-id="155dc-112">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="155dc-112">Related topics</span></span>
- [<span data-ttu-id="155dc-113">Tests unitaires avec test de dotnet et xUnit</span><span class="sxs-lookup"><span data-stu-id="155dc-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="155dc-114">Tests unitaires avec un test de dotnet et de MSTest</span><span class="sxs-lookup"><span data-stu-id="155dc-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
