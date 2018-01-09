---
title: "Tester la sortie publiée avec dotnet vstest"
description: "Découvrez comment exécuter des tests sur une sortie publiée avec la commande dotnet vstest."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 373c557d3fc640ed9071a732bba9f082ca6a4d33
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a>Tester la sortie publiée avec dotnet vstest

Vous pouvez exécuter des tests sur la sortie déjà publiée à l’aide de la commande `dotnet vstest`. Cela s’applique aux tests sur xUnit, MSTest et NUnit. Recherchez simplement le fichier DLL qui faisait partie de votre sortie publiée et exécutez :

```
dotnet vstest <MyPublishedTests>.dll
```

où `<MyPublishedTests>` est le nom de votre projet de test publié.

## <a name="example-of-running-tests-on-a-published-dll"></a>Exemple d’exécution de tests sur une DLL publiée

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Remarque : si votre application cible une version de .NET Framework autre que `netcoreapp`, vous pouvez toujours exécuter la commande `dotnet vstest` en passant à la version de .NET Framework ciblée avec un indicateur de .NET Framework. Par exemple, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. Dans Visual Studio 2017 Update 5, la version souhaitée du .NET framework est automatiquement détectée.

## <a name="see-also"></a>Voir aussi
 [Tests unitaires avec dotnet-test et xUnit](unit-testing-with-dotnet-test.md)  
 [Tests unitaires avec dotnet-test et MSTest](unit-testing-with-mstest.md)  
