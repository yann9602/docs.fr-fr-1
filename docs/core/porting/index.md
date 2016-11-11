---
title: "Portage vers .NET Core à partir du .NET Framework"
description: "Portage vers .NET Core à partir du .NET Framework"
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 00d00d38-99af-44f4-a75f-defcd9729dc5
translationtype: Human Translation
ms.sourcegitcommit: ba6907f0054c3f4cdbaa687277ad70554670f0bb
ms.openlocfilehash: 677fe36a17b56aae0198140d82a2bfdd0d6e8224

---

# <a name="porting-to-net-core-from-net-framework"></a>Portage vers .NET Core à partir du .NET Framework

Si vous avez un code s’exécutant sur le .NET Framework, vous pouvez être intéressé par l’exécution de votre code sur .NET Core 1.0.  Cet article contient une vue d’ensemble du processus de portage et une liste des outils que peuvent s’avérer utiles lors du portage vers .NET Core.

## <a name="overview-of-the-porting-process"></a>Vue d’ensemble du processus de portage

Le processus recommandé pour le portage est constitué de la série d’étapes suivante.  Chacune de ces parties du processus est traitée plus en détail dans d’autres articles.

1. Identifiez et considérez vos dépendances tierces.

   Ceci implique de comprendre ce que sont vos dépendances tierces, comment vous en dépendez, comment faire pour voir si elles s’exécutent aussi sur .NET Core, ainsi que les étapes à réaliser si ce n’est pas le cas.
   
2. Reciblez tous les projets que vous voulez porter pour cibler le .NET Framework 4.6.2.

   Cela garantit que vous pouvez utiliser des API alternatives pour des cibles spécifiques au .NET Framework dans les cas où .NET Core ne peut pas prendre en charge une API particulière.
   
3. Utilisez l’[outil API Portability Analyzer](https://github.com/Microsoft/dotnet-apiport/) pour analyser vos assemblys et développer un plan pour réaliser le portage en fonction de ses résultats.

   L’outil API Portability Analyzer analyse vos assemblys compilés et génère un rapport qui présente résumé de portabilité générale, et une analyse de chaque API que vous utilisez et qui n’est pas disponible sur .NET Core.  Vous pouvez utiliser ce rapport parallèlement à une analyse de votre code base pour développer un plan de la façon dont vous allez porter votre code.
   
4. Porter le code de vos tests.

   Le portage vers .NET Core représentant un grand changement pour votre code base, il est fortement recommandé de porter vos tests, pour pouvoir exécuter des tests au fil du portage du code.  MSTest, xUnit et NUnit prennent tous actuellement en charge .NET Core 1.0.
   
6. Exécutez votre plan de portage !

## <a name="tools-to-help"></a>Outils pour vous aider

Voici une courte liste des outils qui peuvent vous être utiles :

* NuGet - [Client NuGet](https://dist.nuget.org/index.html) ou [Explorateur de package NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Gestionnaire de package de Microsoft pour la plateforme .NET.
* API Portability Analyzer - [Outil de ligne de commande](https://github.com/Microsoft/dotnet-apiport/releases) ou [Extension Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), une chaîne d’outils qui permet de générer un rapport sur la portabilité de votre code entre le .NET Framework et .NET Core, avec une analyse des problèmes par assembly.  Pour plus d’informations, consultez [Outils pour vous aider dans le processus](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).
* Reverse Package Search - A [service web pratique](https://packagesearch.azurewebsites.net) qui vous permet de rechercher un type et de trouver des packages contenant ce type.

## <a name="next-steps"></a>Étapes suivantes

[Analyse de vos dépendances tierces.](third-party-deps.md)
   



<!--HONumber=Nov16_HO1-->


